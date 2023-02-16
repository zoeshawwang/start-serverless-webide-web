FROM golang:1.18-stretch AS builder

ENV GO111MODULE=on \
    CGO_ENABLED=0 \
    GOOS=linux \
    GOARCH=amd64

RUN apt-get update
RUN apt-get install unzip
RUN wget http://devsapp.functioncompute.com/devsapp/openvscode-server-v1.67.0.zip
RUN unzip -d /opt openvscode-server-v1.67.0.zip
RUN chmod +x /opt/openvscode-server/bin/openvscode-server
WORKDIR /src
COPY . .
RUN make release

EXPOSE 9000
ENTRYPOINT ["./target/webide-server", "-logtostderr=true"]