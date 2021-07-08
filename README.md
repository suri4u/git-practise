Reset the users Password:
------------------------
faillock --user r01298		
faillock --user r01298 --reset
=========================================
Windows server deployments:
--------------------------

Serial	Service Name	Environment	Server		Health Port	Wealth Port    service name 			Health Port   wealth port 
1		Maestro				DEV		CAWIDWEB0020	9015	 9016
2		Lotus				DEV		CAWIDWEB0019	8015   	 8016			Sharepoint service      8018			8019
3	    mainframe			DEV		CAWIDAPP0122				8015	 8016
					
4		Maestro				QA		CAWIQWEB0020	9015	 9016
5		Lotus				QA 	    CAWIQAPP0024	8015	 8016			sharepoint service		8018			8019
6		mainframe			QA		CAWIQAPP0023	8015	 8016
        Shapoint 									8018
7		Lotus				QC		CAWIQWEB0018	8015	8016			sharepoint Service       8018           8019
8		Mainframe			QC		CAWIQAPP0026	8015	8016
9		Maestro				QC		CAWIQWEB0019	9015    9016 
==========================================================================
notification
mainframe

Windows-service Creation Using nssm
-----------------------------------
D:
cd D:\binaries\nssm-2.24\win64
.\nssm.exe install maestro-wealth D:\Mimictron-Client-Wealth\startService.cmd
.\nssm.exe install mimictron-mainframe-wealth D:\Mimictron-Client_Wealth\mimictronconnector-1.0.0\startService.cmd -interactive.\nssm.exe start mimictron-mainframe-wealth

.\nssm.exe install maestro-wealth D:\MaestroTaskService_Wealth\MaestroTaskServicd ce-0.0.1-SNAPSHOT\startService.cmd

.\nssm.exe install maestro-wealth D:\MaestroTaskService_Wealth\MaestroTaskService-0.0.1-SNAPSHOT\startService.cmd

.\nssm.exe start maestro-wealth
.\nssm.exe stop maestro-wealth
.\nssm.exe remove maestro-wealth

=====


cmd /c call D:\binaries\nssm-2.24\nssm-2.24\win64\nssm.exe stop mimictron-lotus-wealth
del /s /q D:\Mimictron-Client_Wealth\mimictronconnector-1.0.0
del D:\Mimictron-Client_Wealth\mimictronconnector-1.0.0-bin.zip
COPY target\*.zip D:\Mimictron-Client_Wealth
cd D:\Mimictron-Client_Wealth
jar xf  mimictronconnector-1.0.0-bin.zip
COPY D:\Mimictron-Client_Wealth\mimictronconnector-1.0.0\bin\logback-spring.xml D:\Mimictron-Client_Wealth
COPY startService.cmd D:\Mimictron-Client_Wealth\mimictronconnector-1.0.0\
cd D:\Mimictron-Client_Wealth\mimictronconnector-1.0.0
cmd /c call D:\binaries\nssm-2.24\nssm-2.24\win64\nssm.exe start mimictron-lotus-wealth
=======================================================================================
UI-login and password:
---------------------
goutami 
c/OBEYxIF8
=======================================================================================
/apps/holmes-share/kafka_2.12-2.2.1/bin/kafka-consumer-groups.sh --bootstrap-server b-2.holmes-qc.0oxew2.c3.kafka.us-east-1.amazonaws.com:2181 --group notification_group_id --describe

/kafka-topics.sh --list --zookeeper z-2.holmes-qc.0oxew2.c3.kafka.us-east-1.amazonaws.com:2181,z-3.holmes-qc.0oxew2.c3.kafka.us-east-1.amazonaws.com:2181,z-1.holmes-qc.0oxew2.c3.kafka.us-east-1.amazonaws.com:2181|grep Queue.Docs.OCROutput

=======================================================================================
 Memory and cpu statc of service
 -------------------------------
 */10 * * * * (docker stats --no-stream --no-trunc --format "table {{.Name}}\t{{.MemUsage}}" | sort -k 3 -n | awk -F "/" {'print $1'} | grep GiB;echo "####### output at a interval of 10 min ########";echo " ";date;echo " ") >> /apps/holmes-share/memory-stats/caviqapp0069/$(date +\%m\%d)-memory_stat_container.log
#checking for container cpu utilization
*/10 * * * * (docker stats --no-stream --no-trunc --format "table {{.Name}}\t{{.CPUPerc}}" | sort -k 2 -r |awk -F "/" {'print $1'} | egrep -v 'ucp|k8s';echo "####### output at a interval of 10 min ########";echo " ";date;echo " ") >> /apps/holmes-share/cpu-stats/caviqapp0069/$(date +\%Y\%m\%d)-cpu_stat_container.log

=====================================================================================
proxy-settings:
---------------
s
yum install -y procps

iostat-m 
cpu,memory 
/var/log/sa
ifconfig -pockets


========================================================================
/etc/fstab
mount -a --> to mount the mount point 
========================================================================
systemctl enable docker
systemctl start docker
systemctl status docker
docker load -i /apps/holmes-share/ucp_images_3.2.6.tar.gz
docker swarm join --token SWMTKN-1-0nby8d70lkw6uvaxwoe32r4nohgmcp2afcfck9a4kqn6ylq5v3-69uwhmz1z5icj4lf34vhskwu2 10.207.244.37:2377
docker node update --label-add application=fni-auth hqmi5ho31f6b9hxwcarjdbfhb
docker node update --label-add application=fni-auth 123jlq98db8yod086f359ideu
docker node update --label-add application=fni-auth x016k4uset48e23bz012n5s69
docker node update --label-add application=fni-auth 8x6y17y7wn71apmj9o4mw6wnx


docker node update --label-add app_env=prod f3d8ogv797wwdhupsz0ksmfj6
added worker nodes nodes into the manager
========================================================================
Heap meamory -increase for Jboss
--------------------------------
IN /

-->>   JAVA_OPTS="-Xms2G -Xmx3G -XX:MetaspaceSize=512M -XX:MaxMetaspaceSize=2048m -Djava.net.preferIPv4Stack=true"

   JAVA_OPTS="$JAVA_OPTS -Djboss.modules.system.pkgs=$JBOSS_MODULES_SYSTEM_PKGS -Djava.awt.headless=true"
   JAVA_OPTS="$JAVA_OPTS -javaagent:/apps/holmes/install/jboss-eap-7.2/newrelic/newrelic.jar"

===========================================================================================================================
git rm -r --cached .
git add .
git commit -m "fixed untracked files"
To remove the cache for .gitignore
========================================
export http_proxy=http://10.64.85.177:3228 
export https_proxy=http://10.64.85.177:3228 



==============================================================================
http://caviqapp0074:8080/decision-central/

Username – rhdmAdmin
Password – Admin@123
==============================================================================
COPY src\main\resources\bin\logback-spring.xml D:\Sharepoint-Service
COPY D:\Sharepoint-Service\logback-spring.xml D:\Sharepoint-Service\HolmesSharepointService-0.0.1-SNAPSHOT\bin

config/dailyreports/dbbusinessreports/
appconfig/businessreport/dbdcreport/2020-12-21/12:00:00

=========================================================================================================================
Please find the console URL given below –

DEV/QA –
https://ssoauth.devqa.alight.com:7031/idp/startSSO.ping?PartnerSpId=urn%3Aamazon%3Awebservices
QC –
https://ssoauth.qc.alight.com/idp/startSSO.ping?PartnerSpId=urn%3Aamazon%3Awebservices

PRD –
https://ssoauth.alight.com/idp/startSSO.ping?PartnerSpId=urn%3Aamazon%3Awebservices

========================================================================================================================export
newrelic -python configurations:
===============================
    6  pip install newrelic
    9  newrelic-admin generate-config e02c4aa54196ee31cd132b6c99b3a3deb4f5NRAL newrelic.ini
   17  vi  newrelic.ini
   18  export NEW_RELIC_CONFIG_FILE=newrelic.ini
   19  newrelic-admin run-program gunicorn_django
   20  ls .conf.py
   21  newrelic-admin run-program gunicorn_django
   22  newrelic-admin run-program /miniconda3/bin/gunicorn
   23  newrelic-admin run-program /miniconda3/bin/gunicorn -c gunicorn.conf.py excel_formatter.wsgi
   
   /miniconda3/bin/gunicorn -c gunicorn.conf.py excel_formatter.wsgi
    22  newrelic-admin run-program /miniconda3/bin/gunicorn -c gunicorn.conf.py excel_formatter.wsgi
   27  newrelic-admin run-program /miniconda3/bin/gunicorn -c  --bind 127.0.0.1:1026 gunicorn.conf.py excel_formatter.wsgi
   28  newrelic-admin run-program /miniconda3/bin/gunicorn --bind 127.0.0.1:1026 -c gunicorn.conf.py excel_formatter.wsgi

   =============================================================================================================================
To remove the remote tags :
-------------------------

git ls-remote --tags origin | awk '/^(.*)(s+)(.*[a-zA-Z0-9])$/ {print ":" $2}' | xargs git push origin

================================================================================================================================
S.No Environment		UI-Reverse-proxy				Zuul-Reverse-proxy
1	  Dev-hws			http://cavidapp0533:7000/		  http://cavidapp0533:7001/
2	  Dev-dbdc	        http://cavidapp0530:7000/		  http://cavidapp0530:7001/
3	  Test-hws	        http://cavidapp0517:7000/		  http://cavidapp0517:7001/
4	  Qa-Hws	        http://caviqapp0051:7000/		  http://caviqapp0051:7001/
5	  Qa-dbdc	        http://caviqapp0053:7000/		  http://caviqapp0053:7001/
6	  Qc-Hws	        http://caviqapp0072:7000/		  http://caviqapp0072:7001/
7	  QC-Dbdc	        http://caviqapp0066:7000/		  http://caviqapp0066:7001/
====================
holmes_devops		Al1gh5Ho1ms#786
=========================================================
LIST:
./kafka-topics.sh --list --zookeeper z-3.holmes-idp-kafka-dev.2e7n89.c6.kafka.us-east-1.amazonaws.com:2181,z-2.holmes-idp-kafka-dev.2e7n89.c6.kafka.us-east-1.amazonaws.com:2181,z-1.holmes-idp-kafka-dev.2e7n89.c6.kafka.us-east-1.amazonaws.com:2181
CREATE
./kafka-topics.sh --create --zookeeper z-3.holmes-idp-kafka-dev.2e7n89.c6.kafka.us-east-1.amazonaws.com:2181,z-2.holmes-idp-kafka-dev.2e7n89.c6.kafka.us-east-1.amazonaws.com:2181,z-1.holmes-idp-kafka-dev.2e7n89.c6.kafka.us-east-1.amazonaws.com:2181 --replication-factor 2 --partitions 2 --topic maestro_topic 
DELETE
./kafka-topics.sh --delete --zookeeper z-3.holmes-idp-kafka-dev.2e7n89.c6.kafka.us-east-1.amazonaws.com:2181,z-2.holmes-idp-kafka-dev.2e7n89.c6.kafka.us-east-1.amazonaws.com:2181,z-1.holmes-idp-kafka-dev.2e7n89.c6.kafka.us-east-1.amazonaws.com:2181 --topic  maestro_topic lotus_topic

QA

list
./kafka-topics.sh --list --zookeeper z-2.holmes-idp-kafka-qa.7hg4lz.c6.kafka.us-east-1.amazonaws.com:2181,z-1.holmes-idp-kafka-qa.7hg4lz.c6.kafka.us-east-1.amazonaws.com:2181,z-3.holmes-idp-kafka-qa.7hg4lz.c6.kafka.us-east-1.amazonaws.com:2181 | grep Queue.Logging.OperationalMetric
delete
./kafka-topics.sh --delete --zookeeper z-2.holmes-idp-kafka-qa.7hg4lz.c6.kafka.us-east-1.amazonaws.com:2181,z-1.holmes-idp-kafka-qa.7hg4lz.c6.kafka.us-east-1.amazonaws.com:2181,z-3.holmes-idp-kafka-qa.7hg4lz.c6.kafka.us-east-1.amazonaws.com:2181 --topic maestro_topic
create
./kafka-topics.sh --create --zookeeper z-2.holmes-idp-kafka-qa.7hg4lz.c6.kafka.us-east-1.amazonaws.com:2181,z-1.holmes-idp-kafka-qa.7hg4lz.c6.kafka.us-east-1.amazonaws.com:2181,z-3.holmes-idp-kafka-qa.7hg4lz.c6.kafka.us-east-1.amazonaws.com:2181 --replication-factor 3 --partitions 1 --topic  maestro_topic

QC
LIST
./kafka-topics.sh --list --zookeeper z-2.holmes-qc.0oxew2.c3.kafka.us-east-1.amazonaws.com:2181,z-3.holmes-qc.0oxew2.c3.kafka.us-east-1.amazonaws.com:2181,z-1.holmes-qc.0oxew2.c3.kafka.us-east-1.amazonaws.com:2181|grep Queue.Docs.OCROutput

CREATE
./kafka-topics.sh --create --zookeeper z-2.holmes-qc.0oxew2.c3.kafka.us-east-1.amazonaws.com:2181,z-3.holmes-qc.0oxew2.c3.kafka.us-east-1.amazonaws.com:2181,z-1.holmes-qc.0oxew2.c3.kafka.us-east-1.amazonaws.com:2181 --replication-factor 3 --partitions 1 --topic mainframe_topic

DELETE
./bin/kafka-topics.sh --zookeeper z-2.holmes-qc.0oxew2.c3.kafka.us-east-1.amazonaws.com:2181,z-3.holmes-qc.0oxew2.c3.kafka.us-east-1.amazonaws.com:2181,z-1.holmes-qc.0oxew2.c3.kafka.us-east-1.amazonaws.com:2181
 --delete --topic remove-me
 
 ./kafka-consumer-groups.sh --bootstrap-server b-1.holmes-prod.72hlp6.c11.kafka.us-east-1.amazonaws.com:9094 --group notification_group_id --describe --command-config /apps/holmes-share/kafka_2.12-2.2.1/config/client.properties  --partionas check 
 
 ./kafka-topics.sh --list --zookeeper b-1.holmes-prod.72hlp6.c11.kafka.us-east-1.amazonaws.com:9094,b-4.holmes-prod.72hlp6.c11.kafka.us-east-1.amazonaws.com:9094,b-6.holmes-prod.72hlp6.c11.kafka.us-east-1.amazonaws.com:9094

/apps/holmes-share/kafka_2.12-2.2.1/bin/kafka-consumer-groups.sh --bootstrap-server b-1.holmes-prod.72hlp6.c11.kafka.us-east-1.amazonaws.com:9094 --command-config /apps/holmes-share/docdb/client.properties --describe --group Group_OCR_Preprocess_SP
 
 ==========================================================================================================================================
 ==> config- boolean key for prod env
 kZ$O8D*i03EbkuF0
 ==================================================================================
 sudo usermod -a G groupname username
 ===========================
 FROM holmes-docker-dev.artifactory.alight.com/amazonlinux-python_376:latest


RUN /miniconda3/bin/pip install --no-cache-dir newrelic

ENTRYPOINT ["newrelic-admin", "run-program"]

===================================================

telnet gurknd1 1352
compmgmt.msc -adding user into group in windows

================================================================
[11:09 AM] Pratyush Jha
    A1017421
​[11:09 AM] Pratyush Jha
    Book@1234

lusrmgr.msc
==============================================================================================
 cpu-and-memory stats:
 =====---------------
 */05 * * * * (docker stats --no-stream --no-trunc --format "table {{.Name}}\t{{.MemUsage}}" | sort -k 3 -n | awk -F "/" {'print $1'} | grep GiB;echo "####### output at a interval of 05 min ########";echo " ";date;echo " ") >> /apps/holmes-share/memory-stats/caviqapp0046/$(date +\%m\%d)-memory_stat_container.log
#checking for container cpu utilization
*/05 * * * * (docker stats --no-stream --no-trunc --format "table {{.Name}}\t{{.CPUPerc}}" | sort -k 2 -r |awk -F "/" {'print $1'} | egrep -v 'ucp|k8s';echo "####### output at a interval of 05 min ########";echo " ";date;echo " ") >> /apps/holmes-share/cpu-stats/caviqapp0046/$(date +\%Y\%m\%d)-cpu_stat_container.log

==============================================================================================

Kafka topic creation :
---------------------
#!/bin/bash
#################################
#This script will provide the details
#of kafka topic in QA env
#
#Author : Salil Kulshrestha
#Creation Date : 24/09/2020

##### Color Coding

RED='\033[0;31m'
GREEN='\033[0;32m'
CYAN='\033[01;36m'
NC='\033[0m'

########## Script Usage
if  [[ "$1" == "--help" ]]; then
     echo "usage : see man page"
     exit 0
fi

########## Exporting libraries and variables

LOC="/apps/holmes-share/scripts"
source /apps/holmes-share/scripts/lib/proxy
source /apps/holmes-share/scripts/ini/zookeeper-var

########### Main script starts here
create() {
echo -e "${CYAN}Creating topic : $TOPIC_NAME${NC}"
bash /apps/holmes-share/kafka_2.12-2.2.1/bin/kafka-topics.sh --$ACTION --zookeeper $zookeeper_qa --replication-factor 3 --partitions 1 --topic  $TOPIC_NAME 2> /dev/null
RET_STATUS="$?"
if [ "$RET_STATUS" == "0" ];then
        echo -e "${GREEN}Topic $TOPIC_NAME is created sucessfully.${NC}"
        echo " "
else
        echo -e "${RED}Topic may exists already or something went wrong. Please check....${NC}"
        echo " "
fi
}

delete() {
echo -e "${CYAN}Deleting topic : $TOPIC_NAME${NC}"
bash /apps/holmes-share/kafka_2.12-2.2.1/bin/kafka-topics.sh --$ACTION --zookeeper $zookeeper_qa --topic $TOPIC_NAME
RET_STATUS="$?"
if [ "$RET_STATUS" == "0" ];then
        echo -e "${GREEN}Topic $TOPIC_NAME is deleted sucessfully.${NC}"
        echo " "
else
        echo -e "${RED}Something went wrong while deleting the topic. Please check....${NC}"
        echo " "
fi
}

list(){
if [ -z "$TOPIC_NAME" ];then
echo -e "${CYAN}Listing all topics${NC}"
bash /apps/holmes-share/kafka_2.12-2.2.1/bin/kafka-topics.sh --$ACTION --zookeeper $zookeeper_qa
RET_STATUS="$?"
if [ "$RET_STATUS" == "0" ];then
        echo -e "${GREEN} Topics are listed sucessfully.${NC}"
        echo " "
else
        echo -e "${RED}Something went wrong while listing the topic. Please check....${NC}"
        echo " "
fi
elif [ ! -z "$TOPIC_NAME" ];then
echo -e "${CYAN}Checking $TOPIC_NAME is available or not${NC}"
TOPIC=`bash /apps/holmes-share/kafka_2.12-2.2.1/bin/kafka-topics.sh --$ACTION --zookeeper $zookeeper_qa | egrep -x "${TOPIC_NAME}"`
RET_STATUS="$?"
if [ "$RET_STATUS" == "0" ];then
        echo -e "${GREEN}Below Topic(s) available from the list provided \n${TOPIC}.${NC}"
        echo " "
else
        echo -e "${RED}Topic ${TOPIC_NAME} is not available${NC}"
        echo " "
fi
else
        echo -e "${RED}Something went wrong. Please check....${NC}"
        echo " "
fi


}

##############Main Function
if [ "$ACTION" == "create" ];then
create
elif [ "$ACTION" == "delete" ];then
delete
elif [ "$ACTION" == "list" ];then
list
else
echo "${RED}No Action selected. Please select atleast one action${NC}"
fi

=============================================================================================================
Jenkins-file:
------------

pipeline {
   environment {
     jfrog_repo = "holmes-docker-dev.artifactory.alight.com"
     git_url = "https://bitbucket.alight.com/scm/hfi/holmes_zuulproxygateway.git"
     git_branch = "dev"
     image_name = "holmes-zuulproxygateway"
     image_tag = "1.0-dev.${BUILD_NUMBER}"     
   }
 agent { label 'docker' } 
  stages {
    stage('Pull Source') {
      steps {
        git credentialsId: 'a95f7f45-1d92-4cf6-8c19-c230d2b7e7d6', branch: "${git_branch}", url: "${git_url}"
      }
    }
    stage('Maven Build') {
      steps {
        sh "echo 1.0.${BUILD_NUMBER} > version.txt"
        sh "if [ -f \"pom.xml\" ];then mvn -B -f pom.xml clean package -U  -Dmaven.test.skip=true && cp target/*.jar .;else echo \"This is not a Java Project\";fi"
      }
    }
    stage('Docker Build') {
      steps {
        sh "docker build --no-cache -t ${jfrog_repo}/${image_name}:${image_tag} ."
      }
    }

    stage('Docker Push') {
      steps {
  
        withCredentials([usernamePassword(credentialsId: 'f61fd776-138b-49a1-8689-14786fa7142c', passwordVariable: 'Password', usernameVariable: 'Username')]) {
          sh "docker login ${jfrog_repo} -u ${env.Username} -p ${env.Password}"
          sh "docker tag ${jfrog_repo}/${image_name}:${image_tag}   ${jfrog_repo}/${image_name}:dev-latest"
          sh "docker push ${jfrog_repo}/${image_name}:${image_tag}"
          sh "docker push ${jfrog_repo}/${image_name}:dev-latest"
        }
      }
    }
    stage('Trigger Deployment Job') {
      steps {
//		build job: 'Image-Deployment/files_and _interface-deployment', wait: false, parameters: [[$class: 'StringParameterValue', name: 'ENVIRONMENT', value: "dev", name: 'STACK',  value: "$stack_name", name: 'REMOVE_DECISION', value: "NO"]]
        build job: 'FnI-Deployment-Dev/Files_and _interface-deployment-primary'
      }
	}
    stage('Push Tags') {
      steps {
        withCredentials([[$class: 'UsernamePasswordMultiBinding', credentialsId: 'a95f7f45-1d92-4cf6-8c19-c230d2b7e7d6', usernameVariable: 'GIT_USERNAME', passwordVariable: 'GIT_PASSWORD']]) {
        sh("git config credential.username ${env.GIT_USERNAME}")
        sh("git config credential.helper '!f() { echo password=\$GIT_PASSWORD; }; f'")
        sh "git tag -m 'Tag Created through Jenkins.' '1.0-dev.${BUILD_NUMBER}'"
        sh("GIT_ASKPASS=true git push origin --tags")  
        sh("git config --unset credential.username")
        sh("git config --unset credential.helper")
        }
      }
    }    
    stage('Triggering Rever-proxy Job') {
      steps {
        build job: 'FnI-Deployment-Dev/Files_and_interface-deployment-reverseproxy'
      }
    }
  }
  post {
    always {
      deleteDir() /* cleanup the workspace */
    }
    failure {
      mail to: 'DG-Alight-Global-holmes-devops@alight.com',
      subject: "Build Status:${currentBuild.fullDisplayName}",
      body: "${env.BUILD_URL} has result ${currentBuild.result}- ${BUILD_NUMBER}"
     }
  }
}

========================================================================================================================
Dockerfie:
----------
FROM holmes-docker-dev.artifactory.alight.com/amazonlinux-jdk:latest
ENV https_proxy=http://proxycacheST.hewitt.com:3228

# Add a volume pointing to /tmp
VOLUME /tmp

# Make port 8888 available to the world outside this container
EXPOSE 8888

ARG JAVA_OPTS
ENV JAVA_OPTS=$JAVA_OPTS
ENV APP_NAME='Hws-Config-Server'

RUN mkdir -p /usr/app/configserver/lib
RUN mkdir -p /usr/app/configserver/logs

COPY src/main/resources/application.yml /usr/app/configserver/lib/
COPY src/main/resources/bootstrap.yml /usr/app/configserver/lib/
COPY src/main/resources/logback-spring.xml /usr/app/configserver/lib/

WORKDIR /usr/app/configserver/lib/
ADD ./newrelic/newrelic.jar .
ADD ./newrelic/newrelic.yml .
ADD ./version.txt/ .

COPY target/config-server-0.0.1-SNAPSHOT.jar config-server-0.0.1-SNAPSHOT.jar

ENV https_proxy=
ENV http_proxy=

#ADD ./docker/.bashrc /root/.bashrc
#ADD ./docker/exportsecret.sh /usr/app/configserver/lib/exportsecret.sh
#RUN chmod +x /usr/app/configserver/lib/exportsecret.sh


#ENTRYPOINT exec java $JAVA_OPTS -jar config-server-0.0.1-SNAPSHOT.jar
#ENTRYPOINT exec java $JAVA_OPTS -jar -Dconfig.encrypt.key="$(cat /run/secrets/config_encrypt_secret)" -Dspring.datasource.password="Wipr0t3st123" config-server-0.0.1-SNAPSHOT.jar
ENTRYPOINT exec java -javaagent:/usr/app/configserver/lib/newrelic.jar $JAVA_OPTS -jar -Dconfig.encrypt.key="$(cat /run/secrets/config_encrypt_secret)" -Dspring.datasource.password="$(cat /run/secrets/postgres_pwd)" -Dnewrelic.license_key="${NEW_RELIC_LICENSE_KEY}" -Dnewrelic.config.app_name="${NEW_RELIC_ENV}_${APP_NAME}" config-server-0.0.1-SNAPSHOT.jar

#CMD ["/usr/bin/java","-jar","-Dspring.config.location=../config/application-dev.yml","config-server-0.0.1-SNAPSHOT.jar"]
#CMD ["/usr/bin/java","-jar","config-server-0.0.1-SNAPSHOT.jar"]
#CMD /usr/bin/java -jar \
#      -Dconfig.encrypt.key="$(cat /run/secrets/config_encrypt_secret)" \
#      ./config-server-0.0.1-SNAPSHOT.jar

=========================================================================================================================

Stack-file:
-----------
version: '3.3'
services:
  holmes-eureka-service:
    image: holmes-docker-dev.artifactory.alight.com/holmes-eureka-service:dev-latest
    ports:
     - target: 9001
       published: 8006
       protocol: tcp
       mode: host
    volumes:
     - /apps/holmes-share/application-data/hfi/dev/holmes-eureka-service:/usr/app/botservice/eurekaserver/logs    
    env_file:
     - holmes-files-interface-dev.env
     - dev-newrelic.env
    environment:
     - "SPRING_PROFILES_ACTIVE=$${spring.profile.active}"
    networks:
     - fni_dev_app
    logging:
      driver: json-file
    deploy:
      restart_policy:
        condition: on-failure
      placement:
        constraints:
         - node.hostname == cavidapp0530.hewitt.com
         - node.labels.deployment == allowed
         - node.labels.app_env == dev 
         - node.labels.application == hfi
  holmes-config-server:
    image: holmes-docker-dev.artifactory.alight.com/holmes-config-server:dev-latest
    env_file:
     - holmes-files-interface-dev.env
     - dev-newrelic.env
    ports:
     - target: 8888
       published: 8107
       protocol: tcp
       mode: host
    volumes:
     - /apps/holmes-share/application-data/hfi/dev/holmes-config-server:/usr/app/configserver/logs    
    environment:
     - "SPRING_PROFILES_ACTIVE=jdbc"
     - >
       JAVA_OPTS=
       -Dspring.datasource.url=$${database.url} 
       -Dspring.datasource.username=$${username} 
       -Deureka.client.serviceUrl.defaultZone=$${eurekaserver.url}
       
    secrets:
     - source: config_encrypt_secret_dev
       target: config_encrypt_secret
     - source: postgres_pwd_dev
       target: postgres_pwd  
    networks:
     - fni_dev_app   
    logging:
      driver: json-file
    deploy:
      restart_policy:
        condition: on-failure
      placement:
        constraints:
         - node.hostname == cavidapp0531.hewitt.com
         - node.labels.deployment == allowed
         - node.labels.app_env == dev
         - node.labels.application == hfi
  holmes-zuulproxygateway:
    image: holmes-docker-dev.artifactory.alight.com/holmes-zuulproxygateway:dev-latest
    ports:
     - target: 7777
#       published: 8080
       protocol: tcp
       mode: host
    volumes:
     - /apps/holmes-share/application-data/hfi/dev/holmes-zuulproxygateway:/usr/app/botservice/zuulapigateway/logs 
    env_file:
     - holmes-files-interface-dev.env
     - dev-newrelic.env
    environment:
     - "SPRING_PROFILES_ACTIVE=$${spring.profile.active}"
     - >
       JAVA_OPTS=
       -Dspring.config.location=application.yml
       -Deureka.instance.serviceUrl.defaultZone=$${eurekaserver.url}
       -Dspring.cloud.config.profile=$${configserver.profile}
       -Dzuul.routes.RuleEngineService.url=$${ruleengine.url}
    networks:
     - fni_dev_app
    logging:
      driver: json-file
    deploy:
      restart_policy:
        condition: on-failure
      placement:
        constraints:
         - node.role == worker
         - node.labels.deployment == allowed
         - node.labels.app_env == dev
         - node.labels.application == hfi
         
secrets:
  config_encrypt_secret_dev:
      external: true
  postgres_pwd_dev:
      external: true    
         
   
networks:
  fni_dev_app:
   external: true
    
================================================================================================================================
new jenkins-file:
----------------

#!/usr/bin/env groovy
def gv
@Library('alight-library')_
pipeline {

 agent { label 'docker' }

  stages {
        stage("load vars") {
            steps {
                script {
                   gv = load "env.groovy"
                   gv.var()
                }
            }
         }

        stage('Pull Source') {
            steps {
               git branch: "${GIT_BRANCH}", credentialsId: 'a95f7f45-1d92-4cf6-8c19-c230d2b7e7d6' , url: "${gv.git_url}"
        }
      }
    stage('Maven Build') {
      steps {
        sh "if [ -f \"pom.xml\" ];then mvn -B -f pom.xml clean package && cp target/*.jar .;else echo \"This is not a Java Project\";fi"
       }
    }

    stage('Docker Build') {
      steps {
        sh "docker build --no-cache -t ${gv.jfrog_repo}/${gv.image_name}:${gv.image_tag} ."
      }
    }
    stage('Docker Push') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'f61fd776-138b-49a1-8689-14786fa7142c', passwordVariable: 'Password', usernameVariable: 'Username')]) {
          sh "docker login ${jfrog_repo} -u ${env.Username} -p ${env.Password}"
          sh "docker push ${gv.jfrog_repo}/${gv.image_name}:${gv.image_tag}"
        }
      }
    }

   stage('Trigger Deployment Job-dev') {
    when { branch 'dev' }
      steps {
         build job: 'IMG-Deployment-dev/Deployment', parameters: [string(name: 'STACKENV', value: 'dev'), string(name: 'STACKNAME', value: 'dvs-cgn-main'), string(name: 'STACKREMOVE', value: 'NO')]
        }
      }

   stage('Trigger Deployment Job-QA') {
    when { branch 'stable' }
      steps {
         build job: 'IMG-Deployment-QA/Deployment', parameters: [string(name: 'STACKENV', value: 'qa'), string(name: 'STACKNAME', value: 'dvs-cgn-main'), string(name: 'STACKREMOVE', value: 'NO')]
        }
      }
}
  post {
    always {
      deleteDir() /* cleanup the workspace */
    }
  }
}
------------------------------------------------------
env.groovy:

def var() {
jfrog_repo='holmes-docker-dev.artifactory.alight.com'
git_url='https://bitbucket.alight.com/scm/hidvs/cgn-sp-extr-ftr_y16_1.git'
image_name='cgn-sp-extr-ftr_y16_1'
image_tag='${GIT_BRANCH}-latest'
}
return this

========================================================================================================
image-retag:
-----------
[holmes_devops@cavidapp0528 scripts]$ cat image-retag.sh
#!/bin/bash
######################################
#This script will pull the image from
#holmes-docker-dev to holmes-docker-rel.
#
#Creation Date : 29/04/2020
#
#
######################################

##### Color Coding
RED='\033[0;31m'
GREEN='\033[0;32m'
NC='\033[0m'

########## Script Usage
if  [[ "$1" =~ "--help" ]]; then
     echo " "
#     cat $LOC/man/image-retag.txt
     echo "Somthing went wrong, please check..."
     exit 0
fi

########## Exporting libraries and variables
source /apps/holmes-share/scripts/lib/proxy
source /apps/holmes-share/scripts/ini/image-retag-var
JFROG_DEV=holmes-docker-dev.artifactory.alight.com
JFROG_REL=holmes-docker-rel.artifactory.alight.com
########## Pulling image from JFROG-dev
docker image pull "$JFROG_DEV/$image_name:$DEV_tag"
RET_STATUS="$?"
if [ "$RET_STATUS" == "0" ];then
        echo -e "${GREEN}image is pulled successfully from holmes-docker-dev${NC}"
        echo " "
else
        echo -e "${RED}Something went wrong while pulling the image. Please check....${NC}"
        echo " "
fi

######### Tagging the image for JFROG
docker image tag $JFROG_DEV/$image_name:$DEV_tag $JFROG_REL/$image_name:$REL_tag
RET_STATUS="$?"
if [ "$RET_STATUS" == "0" ];then
        echo -e "${GREEN}image is Tagged successfully in JFROG-REL from JFROG-DEV${NC}"
        echo " "
else
        echo -e "${RED}Something went wrong while tagging the image. Please check....{NC}"
        echo " "
fi

####### Checking image are available or not
docker image ls | grep $image_name &> /dev/null
RET_STATUS="$?"
if [ "$RET_STATUS" == "0" ];then
        echo -e "${GREEN}image is available locally${NC}"
        echo " "
else
        echo -e "${RED}Something went wrong. Please check....${NC}"
        echo " "
fi

####### Pushing image to JFROG
docker image push $JFROG_REL/$image_name:$REL_tag
RET_STATUS="$?"
if [ "$RET_STATUS" == "0" ];then
        echo -e "${GREEN}image is pushed successfully to holmes-docker-rel${NC}"
        echo " "
else
        echo -e "${RED}Something went wrong while pushing the image. Please check....${NC}"
        echo " "
fi

###########  Deleting the image locally
#image_id=`docker image ls | grep $JFROG_image_name | grep $JFROG_tag | awk -F " " {'print $3'} | head -1`
#docker image rmi $image_id --force &> /dev/null

########## Pulling back the image from JFROG
docker image pull $JFROG_REL/$image_name:$REL_tag
========================================================================================================================
health-check.sh
---------------


[holmes_devops@cavidapp0528 scripts]$ cat healthcheck.sh
#! /bin/bash

rm status.txt


Zuul="http://cavidapp0530:8080/actuator/health"
Eureka="http://cavidapp0530:8006/actuator/health"
ConfigManager="http://cavidapp0530:8080/configmanager/actuator/health"
AppConfig="http://cavidapp0530:8080/appconfig/actuator/health"
DBservice="http://cavidapp0530:8080/dbservice/actuator/health"
AuthService="http://cavidapp0530:8080/holmeauth/actuator/health"



#echo -e "Hi, \nPlease find the status of services Below :\n" >> status.txt

for i in `cat service.txt`
do
  if [ $Zuul == $i ]
  then
    if [ '{"status":"UP"}'==`curl -s "$Zuul"` ]
    then
      continue
    else
      echo "Zuul -> down ">> status.txt
    fi
  elif [ $Eureka == $i ]
  then
    if [ '{"status":"UP"}'==`curl -s "$Eureka"` ]
    then
      continue
    else
      echo "Eureka -> down ">> status.txt
    fi
  elif [ $ConfigManager == $i ]
  then
    if [ '{"status":"UP"}'==`curl -s "$ConfigManager"` ]
    then
      continue
    else
      echo "Config Manager -> down ">> status.txt
    fi
  elif [ $AppConfig == $i ]
  then
    if [ '{"status":"UP"}'==`curl -s "$AppConfig"` ]
    then
      continue
    else
      echo "App Config -> down ">> status.txt
    fi
  elif [ $DBservice == $i ]
  then
    if [ '{"status":"UP"}'==`curl -s "$DBservice"` ]
    then
      continue
    else
      echo "DB Service -> down ">> status.txt
    fi
  elif [ $AuthService == $i ]
  then
    if [ '{"status":"UP"}'==`curl -s "$AuthService"` ]
    then
      continue
    else
      echo "Auth Service -> down ">> status.txt
    fi
  fi
done
if [ -f "status.txt" ]
then
  cat /apps/holmes-share/scripts/status.txt | mail -s "Status of url" DG-Alight-Global-holmes-devops@alight.com ankur.saini.3@alight.com > /dev/null
 # cat /apps/holmes-share/scripts/status.txt | mail -s "F&I - Dev is Down" DG-Alight-Global-holmes-devops@alight.com surej.vijayan@alight.com > /dev/null
fi
=======================================================================================================================================================

Amazon-linux:jdk dockerfile
---------------------------
FROM holmes-docker-dev.artifactory.alight.com/base-amazonlinux:latest
MAINTAINER Abhilash Narayan <abhilash.narayan@alight.com>

#Install Oracle JDK 1.8.0_241

RUN yum update -y
#Installing Java version 1.8.0.242
RUN yum --showduplicates list java-1.8.0-openjdk-devel
RUN yum install -y java-1.8.0-openjdk-1.8.0.242.b08
ENV TZ=America/Chicago
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

ENV JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.242.b08-0.amzn2.0.1.x86_64/jre
CMD ["java -version"]


=======================================

platform.amazonlinux.python376:
-------------------------------
FROM holmes-docker-dev.artifactory.alight.com/base-amazonlinux:latest
MAINTAINER Abhilash Narayan <abhilash.narayan@alight.com>


RUN yum -y groupinstall development && yum -y install zlib-devel bzip2-devel ncurses-devel readline-devel sqlite-devel openssl-devel gdbm-devel tk-devel xz-devel libffi-devel
#RUN yum -y install wget && wget -O /usr/src/Python-3.7.6.tgz https://www.python.org/ftp/python/3.7.6/Python-3.7.6.tgz
RUN yum -y install wget && wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
RUN bash Miniconda3-latest-Linux-x86_64.sh -p /miniconda3 -b
RUN rm Miniconda3-latest-Linux-x86_64.sh
ENV PATH=/miniconda/bin:${PATH}
#WORKDIR /usr/src
#RUN tar -xvf Python-3.7.6.tgz && cd Python-3.7.6 && ./configure --enable-optimizations --with-ensurepip=install && make -j 8 && make install
#RUN tar -xvf Python-3.7.6.tgz && cd Python-3.7.6 && ./configure --enable-optimizations --with-ensurepip=install && make -j 8 && make altinstall
#RUN rm -rf Python-3.7.6.tgz && rm -rf Python-3.7.6
WORKDIR /
ENV TZ=America/Chicago
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN yum install -y java-1.8.0-openjdk-1.8.0.242.b08
RUN /miniconda3/bin/conda init bash

CMD ["python3"]

=========================================================================================================
[a1031852@cavidapp0528 conf]$ cat settings.xml
<?xml version="1.0" encoding="UTF-8"?>

<!--
Licensed to the Apache Software Foundation (ASF) under one
or more contributor license agreements.  See the NOTICE file
distributed with this work for additional information
regarding copyright ownership.  The ASF licenses this file
to you under the Apache License, Version 2.0 (the
"License"); you may not use this file except in compliance
with the License.  You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing,
software distributed under the License is distributed on an
"AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
KIND, either express or implied.  See the License for the
specific language governing permissions and limitations
under the License.
-->

<!--
 | This is the configuration file for Maven. It can be specified at two levels:
 |
 |  1. User Level. This settings.xml file provides configuration for a single user,
 |                 and is normally provided in ${user.home}/.m2/settings.xml.
 |
 |                 NOTE: This location can be overridden with the CLI option:
 |
 |                 -s /path/to/user/settings.xml
 |
 |  2. Global Level. This settings.xml file provides configuration for all Maven
 |                 users on a machine (assuming they're all using the same Maven
 |                 installation). It's normally provided in
 |                 ${maven.conf}/settings.xml.
 |
 |                 NOTE: This location can be overridden with the CLI option:
 |
 |                 -gs /path/to/global/settings.xml
 |
 | The sections in this sample file are intended to give you a running start at
 | getting the most out of your Maven installation. Where appropriate, the default
 | values (values used when the setting is not specified) are provided.
 |
 |-->
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
          xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
          xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 http://maven.apache.org/xsd/settings-1.0.0.xsd">
  <!-- localRepository
   | The path to the local repository maven will use to store artifacts.
   |
   | Default: ${user.home}/.m2/repository
  <localRepository>/path/to/local/repo</localRepository>
  -->
  <localRepository>/apps/holmes-share/maven_repository</localRepository>

  <!-- interactiveMode
   | This will determine whether maven prompts you when it needs input. If set to false,
   | maven will use a sensible default value, perhaps based on some other setting, for
   | the parameter in question.
   |
   | Default: true
  <interactiveMode>true</interactiveMode>
  -->

  <!-- offline
   | Determines whether maven should attempt to connect to the network when executing a build.
   | This will have an effect on artifact downloads, artifact deployment, and others.
   |
   | Default: false
  <offline>false</offline>
  -->

  <!-- pluginGroups
   | This is a list of additional group identifiers that will be searched when resolving plugins by their prefix, i.e.
   | when invoking a command line like "mvn prefix:goal". Maven will automatically add the group identifiers
   | "org.apache.maven.plugins" and "org.codehaus.mojo" if these are not already contained in the list.
   |-->
  <pluginGroups>
    <!-- pluginGroup
     | Specifies a further group identifier to use for plugin lookup.
    <pluginGroup>com.your.plugins</pluginGroup>
    -->
  </pluginGroups>

  <!-- proxies
   | This is a list of proxies which can be used on this machine to connect to the network.
   | Unless otherwise specified (by system property or command-line switch), the first proxy
   | specification in this list marked as active will be used.
   |-->
  <proxies>
    <!-- proxy
     | Specification for one proxy, to be used in connecting to the network.
     |
    <proxy>
      <id>optional</id>
      <active>true</active>
      <protocol>http</protocol>
      <username>proxyuser</username>
      <password>proxypass</password>
      <host>proxy.host.net</host>
      <port>80</port>
      <nonProxyHosts>local.net|some.host.com</nonProxyHosts>
    </proxy>
    -->
    <proxy>
      <id>alight</id>
      <active>true</active>
      <protocol>http</protocol>
      <host>10.64.85.177</host>
      <port>3228</port>
    </proxy>
  </proxies>

  <!-- servers
   | This is a list of authentication profiles, keyed by the server-id used within the system.
   | Authentication profiles can be used whenever maven must make a connection to a remote server.
   |-->
  <servers>
    <!-- server
     | Specifies the authentication information to use when connecting to a particular server, identified by
     | a unique name within the system (referred to by the 'id' attribute below).
     |
     | NOTE: You should either specify username/password OR privateKey/passphrase, since these pairings are
     |       used together.
     |
    <server>
      <id>deploymentRepo</id>
      <username>repouser</username>
      <password>repopwd</password>
    </server>
    -->

    <!-- Another sample, using keys to authenticate.
    <server>
      <id>siteServer</id>
      <privateKey>/path/to/private/key</privateKey>
      <passphrase>optional; leave empty if not used.</passphrase>
    </server>
    -->
  </servers>

  <!-- mirrors
   | This is a list of mirrors to be used in downloading artifacts from remote repositories.
   |
   | It works like this: a POM may declare a repository to use in resolving certain artifacts.
   | However, this repository may have problems with heavy traffic at times, so people have mirrored
   | it to several places.
   |
   | That repository definition will have a unique id, so we can create a mirror reference for that
   | repository, to be used as an alternate download site. The mirror site will be the preferred
   | server for that repository.
   |-->
  <mirrors>
    <!-- mirror
     | Specifies a repository mirror site to use instead of a given repository. The repository that
     | this mirror serves has an ID that matches the mirrorOf element of this mirror. IDs are used
     | for inheritance and direct lookup purposes, and must be unique across the set of mirrors.
     |
    <mirror>
      <id>mirrorId</id>
      <mirrorOf>repositoryId</mirrorOf>
      <name>Human Readable Name for this Mirror.</name>
      <url>http://my.repository.com/repo/path</url>
    </mirror>
     -->
  </mirrors>

  <!-- profiles
   | This is a list of profiles which can be activated in a variety of ways, and which can modify
   | the build process. Profiles provided in the settings.xml are intended to provide local machine-
   | specific paths and repository locations which allow the build to work in the local environment.
   |
   | For example, if you have an integration testing plugin - like cactus - that needs to know where
   | your Tomcat instance is installed, you can provide a variable here such that the variable is
   | dereferenced during the build process to configure the cactus plugin.
   |
   | As noted above, profiles can be activated in a variety of ways. One way - the activeProfiles
   | section of this document (settings.xml) - will be discussed later. Another way essentially
   | relies on the detection of a system property, either matching a particular value for the property,
   | or merely testing its existence. Profiles can also be activated by JDK version prefix, where a
   | value of '1.4' might activate a profile when the build is executed on a JDK version of '1.4.2_07'.
   | Finally, the list of active profiles can be specified directly from the command line.
   |
   | NOTE: For profiles defined in the settings.xml, you are restricted to specifying only artifact
   |       repositories, plugin repositories, and free-form properties to be used as configuration
   |       variables for plugins in the POM.
   |
   |-->
  <profiles>
    <!-- profile
     | Specifies a set of introductions to the build process, to be activated using one or more of the
     | mechanisms described above. For inheritance purposes, and to activate profiles via <activatedProfiles/>
     | or the command line, profiles have to have an ID that is unique.
     |
     | An encouraged best practice for profile identification is to use a consistent naming convention
     | for profiles, such as 'env-dev', 'env-test', 'env-production', 'user-jdcasey', 'user-brett', etc.
     | This will make it more intuitive to understand what the set of introduced profiles is attempting
     | to accomplish, particularly when you only have a list of profile id's for debug.
     |
     | This profile example uses the JDK version to trigger activation, and provides a JDK-specific repo.
    <profile>
      <id>jdk-1.4</id>

      <activation>
        <jdk>1.4</jdk>
      </activation>

      <repositories>
        <repository>
          <id>jdk14</id>
          <name>Repository for JDK 1.4 builds</name>
          <url>http://www.myhost.com/maven/jdk14</url>
          <layout>default</layout>
          <snapshotPolicy>always</snapshotPolicy>
        </repository>
      </repositories>
    </profile>
    -->

    <!--
     | Here is another profile, activated by the system property 'target-env' with a value of 'dev',
     | which provides a specific path to the Tomcat instance. To use this, your plugin configuration
     | might hypothetically look like:
     |
     | ...
     | <plugin>
     |   <groupId>org.myco.myplugins</groupId>
     |   <artifactId>myplugin</artifactId>
     |
     |   <configuration>
     |     <tomcatLocation>${tomcatPath}</tomcatLocation>
     |   </configuration>
     | </plugin>
     | ...
     |
     | NOTE: If you just wanted to inject this configuration whenever someone set 'target-env' to
     |       anything, you could just leave off the <value/> inside the activation-property.
     |
    <profile>
      <id>env-dev</id>

      <activation>
        <property>
          <name>target-env</name>
          <value>dev</value>
        </property>
      </activation>

      <properties>
        <tomcatPath>/path/to/tomcat/instance</tomcatPath>
      </properties>
    </profile>
    -->
  </profiles>

  <!-- activeProfiles
   | List of profiles that are active for all builds.
   |
  <activeProfiles>
    <activeProfile>alwaysActiveProfile</activeProfile>
    <activeProfile>anotherAlwaysActiveProfile</activeProfile>
  </activeProfiles>
  -->
</settings>
=========================================================================================
sonarqube:

version: '3.3'
services:

  sonarqube:
    image: holmes-docker-dev.artifactory.alight.com/amazonlinux-sonarqube:latest
    volumes:
      - /apps/holmes/sonarqube/logs:/opt/sonarqube/logs
      - /apps/holmes/sonarqube/data:/opt/sonarqube/data
      - /apps/holmes/sonarqube/extensions:/opt/sonarqube/extensions
      - /apps/holmes/sonarqube/temp:/opt/sonarqube/temp

    ports:
      - target: 9000
        published: 9000
        protocol: tcp
        mode: host
    networks:
     - sonarqubenet
    logging:
      driver: json-file
    deploy:
      restart_policy:
        condition: on-failure
      placement:
        constraints:
         - node.hostname == CAVIDAPP0519.hewitt.com
         
networks:
  sonarqubenet:
    external: true
	
	--------------------------------------------------------
FROM holmes-docker-dev.artifactory.alight.com/base-amazonlinux
ENV https_proxy=http://10.64.85.177:3228
ENV http_proxy=http://10.64.85.177:3228

RUN amazon-linux-extras install java-openjdk11
RUN yum install -y wget unzip tar gzip util-linux procps
RUN yum install shadow-utils.x86_64 -y  && groupadd sonar
RUN useradd -m -d /opt/sonarqube -g sonar -s /bin/bash sonar
RUN usermod -a -G sonar root

ENV JAVA_OPTS='-Xmx2048m'
WORKDIR /opt

RUN wget https://artifactory.alight.com/artifactory/holmes-binaries/sonarqube/sonarqube.zip
RUN unzip sonarqube.zip
RUN rm -rf sonarqube.zip
RUN chown -R sonar:sonar /opt/sonarqube
RUN chmod -R 777 /opt/sonarqube

ENV http_proxy =
ENV https_proxy =
ENV JAVA_HOME = /usr/lib/jvm/java-11-openjdk-11.0.5.10-0.amzn2.x86_64
EXPOSE 9000

USER sonar

CMD ["/bin/bash", "/opt/sonarqube/bin/linux-x86-64/sonar.sh", "console"]

===========================================================================================================
Db-service: qc-health : 1.0.40

usermod -a -G ACG01141 AH0155256

Hi,

I do not see your account created to access the client folder on the server caviqapp0073 server

Details needed from users for access -

user name
id with which you want to login
user email id
path on which you need the access
============================================================

chage -l A1033075			==> to check the pasword expiry date
chage -M -1 A1033075	    ==> to chnage the user expiry date to never expire 



====================================================
maestro-wealth
  758  2021-05-01 07:42:56 docker pull holmespltacr.azurecr.io/mserver:18263
  759  2021-05-01 08:31:08 cd /apps/holmes/install/mimictron-5502
  760  2021-05-01 08:31:10 ls -la
  761  2021-05-01 08:31:30 cat docker-compose.yml
  762  2021-05-01 08:32:04 docker pull holmes-docker-dev.artifactory.alight.com/mimictron-mserver:dev-latest
  763  2021-05-01 08:32:25 docker login holmes-docker-dev.artifactory.alight.com
  764  2021-05-01 08:32:41 docker pull holmes-docker-dev.artifactory.alight.com/mimictron-mserver:dev-latest
  765  2021-05-01 08:33:05 docker pull holmespltacr.azurecr.io/mserver:17843
  766  2021-05-01 08:34:27 docker tag holmes-docker-dev.artifactory.alight.com/mimictron-mserver:dev-latest holmes-docker-dev.artifactory.alight.com/mimictron-mserver:dev-latest_bak0105
  767  2021-05-01 08:34:27 docker push holmes-docker-dev.artifactory.alight.com/mimictron-mserver:dev-latest_bak0105
  768  2021-05-01 08:34:53 docker tag holmespltacr.azurecr.io/mserver:18263 holmes-docker-dev.artifactory.alight.com/mimictron-mserver:dev-latest
  769  2021-05-01 08:34:55 docker push holmes-docker-dev.artifactory.alight.com/mimictron-mserver:dev-latest
 ================================================================================================================================ 
 docker pull holmespltacr.azurecr.io/mserver:17896
 docker-compose down 
 docker image rm holmes-docker-dev.artifactory.alight.com/mimictron-mserver:dev-latest
 docker tag  holmespltacr.azurecr.io/mserver:17896 holmes-docker-dev.artifactory.alight.com/mimictron-mserver:dev-latest
 docker push holmes-docker-dev.artifactory.alight.com/mimictron-mserver:dev-latest
 docker-compose up -d 
=======================================================================================================================
docker tag holmes-docker-dev.artifactory.alight.com/mimictron-mserver:dev-latest holmes-docker-dev.artifactory.alight.com/mimictron-mserver:qa-latest

jboss-script:
============
/apps/holmes/install/jboss-eap-7.2/bin/jboss-cli.sh --connect --command=:shutdown
/apps/holmes/install/jboss-eap-7.2/bin/standalone.sh -b 0.0.0.0 &
===========================================================================================================
Ui -Credentails

​[10:08] Pratyush Jha
    Health dev-    goutami c/OBEYxIF8
    Wealth dev  - prasoon/IYpvv8<ei3
	Qc-health/wealth 	- A1019778/Coo1@2021
	
=============================================================== 
Client-path
===========

please provide the below information too -

User Name : 
AD Id : A1006989
User email Id: 
Path: Client Folder Path

=======================================================================
 grep "ACG08853" /etc/groups
  828  2021-04-26 01:53:13 grep 'ACG01366' /etc/groups
  829  2021-04-26 01:54:36 ls
  830  2021-04-26 02:04:22 history
  831  2021-04-26 02:28:53 cd /apps/holmes-share/shared-fni/UAT/prod/08853
  832  2021-04-26 02:28:55 ll
  833  2021-04-26 02:27:16 su - a0158667
  834  2021-04-26 02:29:24 cd /apps/holmes-share/scripts/
  835  2021-04-26 02:29:43 ./usercheck.sh a0158667 ACG08853
  836  2021-04-26 02:30:04 su - a0158667
  837  2021-04-26 02:30:23 ./useradd.sh VedPrakash ved.prakash.upadhyay@alight.com A67036 ACG3099
  
  838  2021-04-26 02:30:38 usermod -a -G ACG08853 a0158667
  839  2021-04-26 02:30:45 su - a0158667
  840  2021-04-26 02:47:18 su - a0144677
  841  2021-04-26 02:49:30 usermod -a -G ACG08853 a0144677
  842  2021-04-26 02:52:23 clear
  843  2021-04-26 02:52:27 su - a0144677
  844  2021-04-26 02:55:29 usermod -a -G ACG08853 a0144677
  845  2021-04-26 02:55:31 clear
  846  2021-04-26 10:16:58 cd /apps/holmes-share/shared-fni/UAT/prod/
  847  2021-04-26 10:16:59 ls
  848  2021-04-26 10:17:12 ls -ld 08853
  849  2021-04-27 04:40:47 cd /apps/holmes-share/shared-fni/UAT/prod/
  850  2021-04-27 04:40:48 ll
  
 sh useradd.sh sudhanshusharma sudhanshu.sharma.5@alight.com A1018734 ACG00186
 sh useradd.sh MayankKumar mayank.kumar.mishra@alight.com A0160305 ACG01366
 sh useradd.sh GaneshDutta gangesh.dutta.pandey@alight.com A0138997 ACG16528  -accessss
 cd dep
 chgrp -R ACG16566 16566
 chgrp -R ACG16528 16528





1.0.25  -cachestrage 

/apps/holmes-share/application-data/hfi/qa/holmes-resource-data-formatter/Fileformatter.log

/apps/holmes-share/application-data/hfi/dev/mserver
/apps/holmes-share/application-data/hfi/dev/nginx
/apps/holmes-share/application-data/hfi/dev/keycloak

=============================================================================================
Open-ssl certificate: nginx

====================

openssl req -newkey rsa:2048 -nodes -keyout nginx/nginx.key -x509 -days 365 -out nginx/nginx.crt


events {
  worker_connections  4096;  ## Default: 1024
}

http {
    server {
        listen 80;
        server_name my-site.com;
        root         /usr/share/nginx/html;
    }

    server { # This new server will watch for traffic on 443
        listen              443 ssl;
        server_name         caviqapp0534;
        ssl_certificate     /etc/nginx/nginx.crt;
        ssl_certificate_key /etc/nginx/nginx.key;
        root        /usr/share/nginx/html;
    }
}


      - /etc/ssl/certs/mimict_nginx.cert:/etc/nginx/mimict_nginx.cert
      - /etc/ssl/mimict_nginx.key:/etc/nginx/mimict_nginx.key



=========================================mclien installation============

SET https_proxy=http://10.64.85.177:3228
SET http_proxy=http://10.64.85.177:3228
python.exe get-pip.py
Scripts\pip.exe install rpaframework
Scripts\pip.exe install rpaframework-recognition
Scripts\pip.exe install cryptography
Scripts\pip.exe install pandas==1.1.5
Scripts\pip.exe install ..\..\mimictron_rpa-21.1.1-py3-none-any

{
  "Logging": {
    "LogLevel": {
      "Default": "Debug",
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Information"
    }
  },
  "MServer":{
    "Protocol":"http",
    "IpAddress": "10.207.232.89",
    "Port": 80,
    "OptionalUriPrefix": "mimictron",re
    "OptionalUriPrefix": "mimictron",re
    "OptionalUriPrefix": "mimictron",re
    "ServerPingIntervalSeconds": 5
  },
  "ClientVersion": "21.1.1",
  "PythonPath": "D:\\binaries\\18327\\python3-8-3\\python3-8-3\\Scripts\\robot.exe",
  "ScriptDownloadPath": "D:\\binaries\\18327\\mLogs"
}


=======================================================
  zzzz

psql -h holmes-qc-psql.cluster-cphsfuoxfefg.us-east-1.rds.amazonaws.com -p 5432 -U postgres_rw -d holmes
psql -h holmes-qc-psql.cluster-cphsfuoxfefg.us-east-1.rds.amazonaws.com -p 5432 -U postgres_rw -d holmes



==========================================
- select uid,status,plugin_name,client_name,job_name,start_date_time,ksd_name,pjm_id  from orch_transaction.request_queue order by create_date_time DESC limit 10;




-  select pfc.process_job_mapping_id,pfc.ksd_name,pfc.client_name,kc.frequency,kc.job_schedule_time,js.days_of_week,js.day_of_month,js.interval
 from common.process_feature_config pfc, emails_scheduler.ksd_config kc, emails_scheduler.job_schedule js where js.active_flag='T' and kc.active_flag='T' and kc.process_job_mapping_id=pfc.process_job_mapping_id and pfc.active_flag='T' and  js.ksd_config_id = kc.id and kc.job_schedule_time between '03:55' and '04:30';

=
delete from common.audit where uid ='RQ-0334000001881';
delete from common.processlog where uid ='RQ-0334000001881';
delete from orch_transaction.request_response_json where uid ='RQ-0334000001881';
delete from orch_transaction.plugin_queue where uid ='RQ-0334000001881';
delete from orch_transaction.plugin_status where uid ='RQ-0334000001881';
delete from orch_transaction.phase_status where uid ='RQ-0334000001881';
delete from orch_transaction.request_queue where uid ='RQ-0334000001881';
delete from common.lotuslogdetails where uid ='RQ-0334000001881';
delete from common.workbenchdetails where uid ='RQ-0334000001881';
delete from common.sharedservice_transaction where uid ='RQ-0334000001881';
delete from common.sharepoint_details where uid ='RQ-0334000001881';
delete from common.maestrodetails where uid='RQ-0334000001881';
=================

ELk:
===
curl -X PUT “https://localhost:9200/index.max_result_window/_settings” -H ‘Content-Type: application/json’ -d ‘{ “index” : { “max_result_window” : 5000000 } }’
curl -XGET http://10.207.230.198:9200/_cat/shards?h=index,shard,prirep,state,unassigned.reason| grep UNASSIGNED
curl -XGET http://10.207.230.198:9200/_cluster/allocation/explain?pretty
curl -XDELETE 'http://10.207.230.198:9200/filebeat-*/'
curl -XPUT "http://10.207.230.198:9200/filebeat-*/_settings" -d '{ "index" : { "max_result_window" : 500000 } }' -H "Content-Type: application/json"
    
insert into common.user_details (adid,type,role,user_name,active_flag,created_date,created_by) values ('A1045900','Leader','Leader','Mary Ekka','T',current_timestamp,'ADMIN');
