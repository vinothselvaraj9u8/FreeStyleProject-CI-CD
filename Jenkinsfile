pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git branch: 'dev', url: 'https://github.com/vinothselvaraj9u8/FreeStyleProject-CI-CD'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t python-flask-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop python-flask-app || true
                docker rm python-flask-app || true
                docker run -d -p 80:5000 --name python-flask-app python-flask-app
                '''
            }
        }
    }
