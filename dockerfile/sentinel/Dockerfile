FROM openjdk:8-jre

USER root

ARG VERSION=1.8.2

ENV BASE_DIR "home/sentinel" 
ENV FILE_NAME "sentinel-dashboard" 
ENV PROJECT_NAME "sentinel-dashboard" 
ENV DASHBOARD_SERVER localhost:8021
ENV SERVER_PORT 8021
ENV USER_NAME "sentinel"
ENV PASS_WORD "sentinel" 
ENV TIME_OUT 7200
#RUN mkdir /home/sentinel       
WORKDIR /$BASE_DIR

RUN    mkdir ./app  
RUN    mkdir ./bin  
RUN    mkdir /root/logs 
RUN    mkdir /root/logs/csp
#RUN mkdir ./bin

COPY docker-entrypoint.sh ./bin/docker-entrypoint.sh

RUN chmod +x ./bin/docker-entrypoint.sh

ADD https://github.com/alibaba/Sentinel/releases/download/${VERSION}/${FILE_NAME}-${VERSION}.jar ./
# 网络不稳定的话,可以先下载下来,然后使用本地的文件
# ADD  ${FILE_NAME}-${VERSION}.jar ./

RUN \cp -f ./${FILE_NAME}-${VERSION}.jar ./app/app.jar

EXPOSE ${SERVER_PORT}

ENTRYPOINT ["bin/docker-entrypoint.sh"]