node('master') {

  checkout scm

  stage('Build') {
    withMaven(maven: 'M3') {
      if (isUnix()) {
        sh label: 'Build, test and package', script: 'mvn -Dmaven.test.failure.ignore clean package'
      } else {
        bat label: 'Build, test and package', script: 'mvn -Dmaven.test.failure.ignore clean package'
      }
    }
  }

  stage('Results') {
    junit '**/target/surefire-reports/TEST-*.xml'
    archive 'target/*.jar'
  }
}
