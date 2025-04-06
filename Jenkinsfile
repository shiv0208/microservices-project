pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'MY-EKS', contextName: '', credentialsId: 'k8-token', namespace: 'webapp', serverUrl: 'https://FB2FE0F4605E98BEAE6A7F6823E36135.yl4.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'MY-EKS', contextName: '', credentialsId: 'k8-token', namespace: 'webapp', serverUrl: 'https://FB2FE0F4605E98BEAE6A7F6823E36135.yl4.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapp"
                }
            }
        }
    }
}
