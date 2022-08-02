pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean install -DskipTests'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
    }
    
    post {
        always {
            emailext subject: "Jenkins Build ${currentBuild.currentResult}: Job \"${env.JOB_NAME}\"",
                body: "${currentBuild.currentResult}: Job \"${env.JOB_NAME}\" build ${env.BUILD_NUMBER}.\nMore info at: ${env.BUILD_URL}",
                recipientProviders: [[$class: 'DevelopersRecipientProvider'], [$class: 'RequesterRecipientProvider']]
        }
    }
}
Here, we’re telling Jenkins to always send an email to the user after the build completes, and giving it a template for how to display the information.

Go back to your Jenkins pipeline to see it running. If all went well, you should see something similar to the following and should have also received an email.



Congratulations! You have successfully set up a Jenkins pipeline to automatically build Java projects from GitLab.

