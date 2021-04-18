pipeline{
    agent any
    stages{
        stage('Build'){
            steps{
                sh "mvn clean package"
            }
        }
        stage('Test'){
            steps{
               deploy adapters: [tomcat7(credentialsId: '6d672aad-3b8d-4005-ada9-77048ae89340', path: '', 
               url: 'http://ec2-3-8-161-199.eu-west-2.compute.amazonaws.com:8080/')], contextPath: 'Test', war: '**/java-web-project.war'
            }
        }
        stage('Pre-Production'){
            steps{
                deploy adapters: [tomcat7(credentialsId: '6d672aad-3b8d-4005-ada9-77048ae89340', path: '', 
                url: 'http://ec2-3-8-161-199.eu-west-2.compute.amazonaws.com:8080/')], contextPath: 'Pre-Production', war: '**/java-web-project.war'
            }
        }
         stage('Production'){
            steps{
                deploy adapters: [tomcat7(credentialsId: '6d672aad-3b8d-4005-ada9-77048ae89340', path: '', 
                url: 'http://ec2-3-8-161-199.eu-west-2.compute.amazonaws.com:8080/')], contextPath: 'Production', war: '**/java-web-project.war'
            }
        }
    }
}
