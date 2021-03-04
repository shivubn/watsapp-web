pipeline{
    agent any
    tools{
        maven 'maven3.6'
        jdk 'java8'
        dockerTool 'docker'
    }  
stages{
        stage('clone'){
            steps{
                git credentialsId: 'github', url: 'https://github.com/Prakashja/web-app.git'
            }
        }
        stage('build'){
            steps{
                script{
                    sh '''
                    mvn clean package
                    ls -ltr target/
                    '''
                }
            }
        }
        stage('docker build'){
            steps{
                script{
                  sh '''
                  sudo  docker build -t sana03/mywebapp:${BUILD_NUMBER} . -f mydockerfile
                  sudo docker push sana03/mywebapp:${BUILD_NUMBER}
                  sudo docker logout
                  '''
               }
          }
       }
    }
}

