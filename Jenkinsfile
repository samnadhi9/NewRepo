node('jdk11-mvn3.8.4') {
    stage('git') {
       git branch: 'main', url: 'https://github.com/samnadhi9/NewRepo' 
    }
    stage('build') {
        sh '''
            echo "PATH=${PATH}"
            echo "M2_HOME=${M2_HOME}"
        '''
        sh '/usr/local/apache-maven-3.8.4/bin/mvn clean package'
    }
    stage('archive') {
        archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
    }
    stage('publish test reports') {
        junit '**/TEST-*.xml'
    }
}
