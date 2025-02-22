pipeline {
    agent any  // Run on any available Jenkins agent

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/utkarshgour1/simple-ci-cd.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t my-static-website .'
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                script {
                    sh 'docker tag my-static-website utkarsh786/my-static-website:latest'
                    sh 'docker login -u utkarsh786 -p 76YeOD@1'
                    sh 'docker push utkarsh786/my-static-website:latest'
                }
            }
        }

        stage('Deploy on Server') {
            steps {
                script {
                    sh 'docker pull utkarsh786/my-static-website:latest'
                    sh 'docker stop my-static-website || true'
                    sh 'docker run -d -p 8082:80 --name my-static-website utkarsh786/my-static-website:latest'
                }
            }
        }
    }
}

