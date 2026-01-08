pipeline {
    agent any

    environment {
        KUBECONFIG = credentials('kubeconfig-jenkins')
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh '''
                kubectl version --client
                kubectl get nodes
                kubectl apply -f k8s/deployment.yaml
                '''
            }
        }
    }
}

