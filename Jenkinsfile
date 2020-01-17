stage("docker_scan"){
      sh '''
        docker run -d --name clair-db arminc/clair-db
        sleep 15 # wait for db to come up
        docker run -p 6060:6060 --link clair-db:postgres -d --name clair xmaeltht/clair:latest
        sleep 5
        ./clair-scanner --ip=${IP} tomcat:latest || exit 0
      '''
    }

