


node('master') 
{
    stage('ContinousDownload') 
    {
        git 'https://github.com/vhirewadeyar/maven-1.git'
    }
    stage('ContinousBuild')
    {
        sh 'mvn package'
    }
    stage('ContinuousDeployment')
    {
        sh 'sshpass -p "redhat" scp /var/lib/jenkins/workspace/scriptedpipeline/webapp/target/webapp.war ansadm@10.128.0.19:/var/lib/tomcat9/testapp.war'
    }
    stage('ContinuousTesting')
    {
        git 'https://github.com/selenium-saikrishna/FunctionalTesting.git'
        sh 'java -jar /var/lib/jenkins/workspace/scriptedpipeline/testing.jar'
    }
    stage('ContinuousDelivery')
    {
       sh 'sshpass -p "redhat" scp /var/lib/jenkins/workspace/scriptedpipeline/webapp/target/webapp.war ansadm@10.128.0.20:/var/lib/tomcat9/testapp.war' 
    }
}
