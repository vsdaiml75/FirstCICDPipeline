pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/vsdaiml75/FirstCICDPipeline.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build('first-cicd-pipeline')
                }
            }
        }
        stage('Run Container') {
            steps {
                script {
                    sh 'docker stop first-cicd-container || true && docker rm first-cicd-container || true'
                    dockerImage.run('-d --name first-cicd-container')
                }
            }
        }
    }
    post {
        always {
            echo 'Pipeline finished.'
        }
    }
}
