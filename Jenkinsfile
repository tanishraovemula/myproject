

node('master')
{
    stage('continuousdownload')
    {
      git 'https://github.com/intelliqittrainings/maven.git'  
    }
    stage('continuousbuild')
    {
       sh label: '', script: 'mvn package' 
    }
    stage('continuousdeployement')
    {
        sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/ScriptedPipeline1/webapp/target/webapp.war  ubuntu@172.31.55.153:/var/lib/tomcat8/webapps/testapp1.war'
    }
    stage('continuoustesting')
    {
        git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
sh label: '', script: 'java -jar /home/ubuntu/.jenkins/workspace/ScriptedPipeline1/testing.jar '
    }
    stage('continuousdeliver')
    {
        sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/ScriptedPipeline1/webapp/target/webapp.war  ubuntu@172.31.80.141:/var/lib/tomcat8/webapps/prodapp1.war'
    }
}

