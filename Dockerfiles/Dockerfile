FROM debian:stable-slim
MAINTAINER Nicholas, contact@luminode.systems
ENV DEBIAN_FRONTEND=noninteractive

RUN rm -rf /usr/bin/fallocate

RUN apt update \
    && apt-get -y --no-install-recommends install curl software-properties-common apt-transport-https gnupg ca-certificates openssl git tar fontconfig tzdata iproute2 lsb-release unzip wget python3 python3-pip \ 
    && useradd -d /home/container -m container

RUN curl -fsSL https://code-server.dev/install.sh | sh

USER container

ENV USER=container 

ENV HOME=/home/container

WORKDIR /home/container

COPY ./entrypoint.sh /entrypoint.sh

CMD ["/bin/bash", "/entrypoint.sh"] 

EXPOSE 8080