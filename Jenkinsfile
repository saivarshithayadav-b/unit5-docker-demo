pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out project...'
                git branch: 'main',
                    url: 'https://github.com/saivarshithayadav-b/unit5-docker-demo.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image...'
                sh '/usr/local/bin/docker build -t unit5-docker-demo:v2 .'
            }
        }

        stage('Run Docker Container') {
            steps {
                echo 'Deploying application...'
                sh '/usr/local/bin/docker rm -f jenkins-demo || true'
                sh '/usr/local/bin/docker run -d --name jenkins-demo -p 8085:80 unit5-docker-demo:v2'
            }
        }
    }
}
