pipeline {
    agent any
    
    tools {
        terraform 'Terraform'
    }
    
    environment {
        //Credentials for Prod environment
        AWS_ACCESS_KEY_ID     = credentials('AWS_ACCESS_KEY_ID') 
        AWS_SECRET_ACCESS_KEY = credentials('AWS_SECRET_ACCESS_KEY')
    }

    stages {
        stage('SCM checkout') {
            steps {
                echo 'Cloning code base with jenkins server'
                echo 'Testing CI code base with jenkins server'
                git branch: 'main', credentialsId: 'b7d91645-4a5f-4549-b3d7-d35a07b7879a', url: 'https://github.com/nucelyn/airbnb-tf-infra.git'
                sh 'ls'
            }
        }
        
        stage('terraform init') {
            steps {
                sh 'terraform init'
            }
        }
        
        stage('terraform plan') {
            steps {
                sh 'terraform plan'
            }
        } 
        
        stage('terraform action to apply or destroy plan') {
            steps {
               sh 'terraform ${action} --auto-approve'
            }
        }
    }
}    