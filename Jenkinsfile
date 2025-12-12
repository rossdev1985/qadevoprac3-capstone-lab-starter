pipeline {
    agent any
    environment {
        TF_VAR_gcp_project = "qwiklabs-gcp-03-7f7a3bf12d89" // REPLACE WITH YOUR PROJECT ID FROM QWIKLABS
    }
    stages {
        stage("Configure Cluster") {
            steps {
                script {
                    dir('terraform') {
                        withCredentials([file(credentialsId: 'gcp_credentials', variable:'GCP_CREDENTIALS')]) {
                            sh '''
                            export GOOGLE_APPLICATION_CREDENTIALS=$GCP_CREDENTIALS
                            terraform init
                            terraform apply -auto-approve
                            '''
                        }
                    }
                }
            }
        }
    }
    post {
        always {
            cleanWs()
        }
    }
}