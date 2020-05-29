node("master")
{

def mavenHome = tool name: "maven3.6.2"

properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '2', daysToKeepStr: '', numToKeepStr: '2')), pipelineTriggers([pollSCM('* * * * *')])])

echo "GitHub BranchName : ${env.BRANCH_NAME}"
echo "Jenkins Job Number: ${env.BUILD_NUMBER}"
echo "Jenkins Node Name : ${env.NODE_NAME}"
echo  "Jenkins Home      : ${env.JENKINS_HOME}"
echo "Jenkins URL       : ${env.JENKINS_URL}"
echo "Job Name          : ${env.JOB_NAME}"


stage("CheckOutCode")
{
git branch: 'development', credentialsId: '731535e4-d4fa-46d2-8bc6-b0aa5be77db5', url: 'https://github.com/raj-ec-project/maven-web-application.git'
}

stage("Build")
{
 sh "${mavenHome}/bin/mvn clean package"
}
/*
stage("ExecuteSonarQubeReport")
{
sh "${mavenHome}/bin/mvn sonar:sonar" 
}

stage("UploadArtifactsontoNexus")
{
sh "${mavenHome}/bin/mvn deploy"
}
stage("DeployontoTomcat")
{
sshagent(['65276554-0d7a-4fa6-aafd-7bebc0183c88']) {
    
 sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@15.206.127.145:/opt/apache-tomcat-9.0.34/webapps/"
	}
}

stage("EmailNotification")
{
mail bcc: 'nareshpdev20@gmail.com', body: '''Build Successful

Regards,
Rajeev
DevopsEngineer''', cc: 'lraj18@gmail.com', from: '', replyTo: '', subject: 'Build Over', to: 'lraj08@gmail.com'
    
}
*/
}
