
node {
    // Get Artifactory server instance, defined in the Artifactory Plugin administration page.
    def server = Artifactory.server "artifactory"
    // Create an Artifactory Maven instance.
    def rtMaven = Artifactory.newMavenBuild()
    def buildInfo
    
 rtMaven.tool = "Maven"

    stage('Clone sources') {
        git url: 'https://github.com/piyushprashar/WebApp.git'
    }

    stage('SonarQube analysis') { 
        withSonarQubeEnv('Sonar') { 
          sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.3.0.603:sonar ' + 
          '-f pom.xml ' +
	  '-Dsonarl.url=http://35.245.160.34:9000 ' +
          '-Dsonar.projectKey=com.huettermann:all:master ' +
          '-Dsonar.login=admin' +
          '-Dsonar.password=admin' +
          ' -Dsonar.language=java ' +
          '-Dsonar.sources=. ' +
          '-Dsonar.tests=. ' +
          '-Dsonar.test.inclusions=**/*Test*/** ' +
          '-Dsonar.exclusions=**/*Test*/**'
        }
    }

   
    }
	 
