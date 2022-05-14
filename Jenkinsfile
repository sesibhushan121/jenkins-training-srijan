pipeline {
    agent any
    environment {
        dockerImage = ''
        registry = 'sesibhushansrijan/sesi24'
        registryCredential = 'dockerhub_id'
    }
    stages {
        stage('Checkout') {
            steps {
                     // Get code from a GitHub repository
                    git url: 'https://github.com/sesibhushan121/samplejenkins.git', branch: 'main',
                    credentialsId: 'git_hub'
            }
        }
        stage('Build docker image') {
            steps {
                script {
                        dockerImage = docker.build registry
                }
            }
        }
        
        stage ('Uploading Image') { 
            steps {
                script {
                         docker.withRegistry( '', registryCredential ) {
                         dockerImage.push()
                    }
                }
            }
        }
    }
}
