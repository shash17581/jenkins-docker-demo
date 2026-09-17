pipeline {
    agent any
    
    stages{
      
       stage('Checkout'){
           steps {
               echo 'Source code is already available in workspace'
             }
       }
       stage('Docker Build') {
           steps {
               sh 'docker build -t jenkins-docker-demo:v1 .'
           }
       }

        stage('Docker Test') {
           steps {
               sh 'docker run -d --name jenkins-docker-test -p 8081:80 jenkins-docker-demo:v1'
               sh 'sleep 3'
               sh 'curl -f http://localhost:8081'
           }
       }

        stage('Cleanup') {
           steps {
               sh 'docker rm -f jenkins-docker-test || true'
           }
       }
  }
}
