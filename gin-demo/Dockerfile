FROM golang:1.14

WORKDIR /src/
COPY .  .
ENV GO111MODULE=on
#ENV GOPROXY https://goproxy.io
RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -mod=vendor -o main


FROM alpine
WORKDIR /target
# 拷贝后端二进制文件
COPY --from=0 /src/main .
#RUN  ssh-add -l
ENTRYPOINT [ "/target/main"]