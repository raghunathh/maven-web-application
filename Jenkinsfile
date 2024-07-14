node{
def mavenHome = tool name: "maven3.9.8"

properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'RebuildSettings', autoRebuild: false, rebuildDisabled: false], pipelineTriggers([pollSCM('* * * * *')])])

stage('checkoutcode'){

git branch: 'development', credentialsId: 'f77f9f76-d86e-4359-ac96-2bcbb7fddee1', url: 'https://github.com/raghunathh/maven-web-application.git'
}

stage('Build'){
sh "${mavenHome}/bin/mvn clean package"
}

/*
stage ('ExecuteSonarQubeReport'){
sh "${mavenHome}/bin/mvn sonar:sonar"
}

stage ('uploadArtifactsIntoNexus'){
sh "${mavenHome}/bin/mvn deploy"
}

stage ('DeployAppintoTomcatServer'){

sshagent(['e9b0b5c4-902b-4ae1-8dc4-3f4c3c29a415']) {
  sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@13.210.228.162:/opt/apache-tomcat-9.0.90/webapps"
}
}

stage ('SendEmailNotification'){

emailext body: '''Build Over..

Regards,
Raghunath
8639317060''', subject: 'Build Over..', to: 'raghunathdevops69@gmail.com'
}
/*

}
