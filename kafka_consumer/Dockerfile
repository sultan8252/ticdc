FROM golang:1.13 as builder
WORKDIR /go/src/github.com/pingcap/ticdc
COPY . .
RUN go mod download
RUN make kafka_consumer

FROM alpine:3.11
COPY --from=builder  /go/src/github.com/pingcap/ticdc/bin/cdc_kafka_consumer /cdc_kafka_consumer
CMD [ "/cdc_kafka_consumer" ]
