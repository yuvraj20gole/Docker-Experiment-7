pipeline {
    agent any

    environment {
        PATH = "/usr/local/bin:/opt/homebrew/bin:/usr/bin:/bin"
    }

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t myapp .'
            }
        }

        stage('Remove Old Container') {
            steps {
                sh 'docker rm -f myapp-container || true'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 8082:80 --name myapp-container myapp'
            }
        }
    }
}
