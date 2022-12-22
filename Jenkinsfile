pipeline {
    agent {
        docker { image 'mongo' }
    }
    stages {
        stage('Git install') {
            steps {
                sh '''apt-get -y update
apt-get -y install git'''
            }
        }
		stage('Git checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/shiba93/mongodb-sample-dataset.git']]])
    }
}
        stage('Dump Data') {
            steps {
                sh '''cd mongodb-sample-dataset/ 
chmod 755 script.sh 
./script.sh localhost 7017'''
    }
}
}
}
