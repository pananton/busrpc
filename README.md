# Busrpc

Busrpc is an RPC framework designed with [microservice architecture](https://en.wikipedia.org/wiki/Microservices) principles in mind. It relies on a generalized message bus/queue/broker (for example, [NATS](https://nats.io/) or [RabbitMQ](https://rabbitmq.com/)) as a transport layer and [protocol buffers](https://developers.google.com/protocol-buffers) as message format.

The framework consists of the following components:
* Technical documentation, namely busrpc API [specification](busrpc.md), bus-dependent API [specializations](busrpc.md#specializations) and a [style guide](style.md) for an API protobuf files
* Protobuf [file](./proto/busrpc.proto) which contains definitions of the busrpc built-in protobuf types and options used by all compliant APIs
* Command-line development [tool](https://github.com/pananton/busrpc-devtool) for a busrpc microservice developers
* Bus-dependent [libraries](#libraries) for a busrpc microservice development
* Bus-dependent [clients](#clients) for testing/observing running busrpc backends

An example of busrpc API for a simple chat application backend can be found in the [*example*](https://github.com/pananton/busrpc/tree/main/example) directory.

# Libraries

Currently no client libraries designed specifically for busrpc APIs exist, which means that you will probably implement one for your platform determined by a combination of programming language and particular message bus/queue/broker. It's usually not a big deal, because you will probably use some client library from message bus/queue/broker developer (for example, see [here](https://nats.io/download/#nats-clients) for NATS client libraries or [here](https://www.rabbitmq.com/devtools.html) for RabbitMQ client libraries) and implement busrpc-specific wrappers over it. Contributions of such busrpc client libraries are highly appreciated!

# Clients

Clients allow developers to test and observe running busprc backends and usually provide at least the following commands:
* `call` - to call a busrpc method
* `impl` - to implement a busrpc method
* `observe` - to observe calls of busrpc methods

Currently the project provides the following clients:
* [NATS busrpc client](https://github.com/pananton/busrpc-nats-cli)

# Contributing

Any contributions are highly appreciated:
* suggestions to the busrpc specification
* specializations for various message bus/queue/broker techonologies
* new commands for busrpc development tool
* clients for testing/observing busrpc backends
* busrpc client libraries

If you want to discuss/suggest some feature, create an issue.

If you want to contribute code to busprc development tool, fork this repository, make your changes and create a pull request.

If you have implemented new busrpc client or library, create an issue with a link to it and I will add your client/library to the list.
