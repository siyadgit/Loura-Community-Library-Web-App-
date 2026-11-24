pipeline{
    agent none
    stages{
        stage('build'){
            agent{
                label 'build'
            }
            steps{
                deleteDir()
                sh '''
                git clone https://github.com/siyadgit/Loura-Community-Library-Web-App-.git
                ls -la
                '''
                stash name:'webpage', includes:'Loura-Community-Library-Web-App-/**'
            }
        }
        stage('deploy'){
            agent{
                label 'deploynode'
            }
            steps{
                deleteDir()
                unstash 'webpage'
                sh '''
                sudo rm -rf /var/www/html/*
                sudo cp -r Loura-Community-Library-Web-App-/* /var/www/html/
                ls -la /var/www/html/
                '''
            }
        }
    }
}
