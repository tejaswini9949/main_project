pipeline{
    agent any
    tools{
        maven 'maven'
    
     }
     stages{
        stage("clone code"){
            steps{
              git credentialsId: 'git_credentials', url:'https://github.com/tejaswini9949/main_project.git'
                
                
                            }


        }
        stage('Build'){

            steps{

                sh 'mvn clean package'
                
            }
         post{

                success{

                    echo "Archiving the Artifacts"
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage('Deploy to tomcat server'){

            steps{
                
            deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://3.110.204.140:8080/')], contextPath: 'main', war: '**/*.war'   
               
            }
            
        }
     }
}
