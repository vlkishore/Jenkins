pipeline {
    agent any
    tools {
  terraform 'terraform'
   }
   stages {
       stage('Git checkout'){
           steps {
               git credentialsId: 'f5b5f20b-b48a-439b-93e0-aafd5e6da0c7', url: 'https://github.com/vlkishore/aws_terraform'
           }
       }
       stage('Terraform init'){
           steps {
               withAWS(credentials: 'aws-terraform-user', region: 'us-east-1'){
               sh 'terraform fmt'
               sh 'terraform validate'    
               sh 'terraform init'
               }
           }
       }
       stage('Terraform new plan'){
           steps {
               withAWS(credentials: 'aws-terraform-user', region: 'us-east-1'){
               sh 'terraform plan'
               }
           }
       }
        stage('Terraform apply'){
           steps {
               withAWS(credentials: 'aws-terraform-user', region: 'us-east-1'){
               sh 'terraform apply --auto-approve'
               }
           }
       }
       stage('Terraform output'){
           steps {
               withAWS(credentials: 'aws-terraform-user', region: 'us-east-1'){
               sh 'terraform output'
               }
           }
       }
       stage('Terraform destroy'){
           steps {
               withAWS(credentials: 'aws-terraform-user', region: 'us-east-1'){
               sh 'terraform destroy -auto-approve'
               }
           }
       }
   }
}