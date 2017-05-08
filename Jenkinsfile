node('master') {
	stage('Setup Environment') {
		env.JAVA_HOME="${tool 'jdk_8_131'}"
		env.PATH="${env.JAVA_HOME}/bin:${env.PATH}"
		sh 'java -version'
	}
	
	stage('Setup SCM') {		
		checkout scm
	}
	
	stage('Build App') {
		sh './gradlew build'
	}
	
	stage('Publish Test Results') {
		junit allowEmptyResults: true, testResults: '**/build/test-reports/*.xml'
	}
}