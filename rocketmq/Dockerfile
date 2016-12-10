FROM  maven:3.3.9-jdk-8

ENV MQ_VERSION=v3.5.8

RUN groupadd admin && useradd -g admin -s /bin/bash -c Admin admin  && mkdir -p /home/admin && chown admin /home/admin
USER admin

RUN cd /home/admin && git clone -b ${MQ_VERSION} https://github.com/alibaba/RocketMQ.git
WORKDIR /home/admin/RocketMQ
RUN mvn -Dmaven.test.skip=true clean package install assembly:assembly -U
RUN ln -s target/alibaba-rocketmq-${MQ_VERSION}-alibaba-rocketmq/alibaba-rocketmq devenv

WORKDIR /home/admin/RocketMQ/devenv/bin
EXPOSE 10911
