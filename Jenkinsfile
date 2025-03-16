pipeline{
    agent any
    tools {
        maven 'Maven'
    }
    stages{
        stage("Test"){
            steps{
                // mvn test
                sh "mvn test"
                
            }
        }
        stage("Build"){
            steps{
                // mvn package
                sh "mvn package"
            }
        }
        stage("Deploy on Test"){
            steps{
                // deploy on container -> plugin
                deploy adapters: [tomcat9(credentialsId: 'tomcatdetail1', path: '', url: 'http://10.0.2.15:8088')], contextPath: '/app', war: '**/*.war'
                e
            }
        }
        stage("Deploy on Prod"){
            steps{
                // deploy on container -> plugin
                deploy adapters: [tomcat9(credentialsId: 'tomcatdetail1', path: '', url: 'http://10.0.2.15:8088')], contextPath: '/app', war: '**/*.war'
            }
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}
