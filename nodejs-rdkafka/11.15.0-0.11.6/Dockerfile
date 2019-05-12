FROM node:11.15.0-alpine
MAINTAINER Sean Costello <me@seancostello.io>

WORKDIR /root

ENV LIBRDKAFKA=v0.11.6
ENV BUILD_LIBRDKAFKA=0

RUN apk update \
    && apk upgrade \
    && apk --no-cache add --virtual build-deps gcc bash python-dev build-base git \
    && git clone https://github.com/edenhill/librdkafka.git \
    && cd /root/librdkafka \
    && git checkout ${LIBRDKAFKA} \
    && ./configure \
    && make \
    && make install \
    && ldconfig / \
    && make clean \
    && ./configure --clean \
    && cd / \
    && rm -rf /root/librdkafka