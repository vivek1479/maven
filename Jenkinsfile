node('built-in')
{
    stage('ContinuousDownload') 
    {
        git 'https://github.com/intelliqittrainings/maven.git'
    }
    stage('ContinuousBuild') 
    {
        sh 'mvn package'
    }
    stage('ContinuousDeployment') 
    {
        deploy adapters: [tomcat9(credentialsId: '8b98063f-eb47-4f19-8505-a616d7cc542c', path: '', url: 'http://172.31.85.52:8080')], contextPath: 'testapp', war: '**/*.war'
    }
    stage('ContinuousTesting') 
    {
        git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
        sh 'java -jar /home/ubuntu/.jenkins/workspace/Scriptedpipeline/testing.jar'
    }
    stage('ContinuousDelivery') 
    {
        deploy adapters: [tomcat9(credentialsId: '8b98063f-eb47-4f19-8505-a616d7cc542c', path: '', url: 'http://172.31.80.61:8080')], contextPath: 'prodapp', war: '**/*.war'
    }
}
