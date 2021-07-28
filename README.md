# openresty-ws-redis

Dynamically route websocket connections through Redis using OpenResty demo.

# Demo

```bash
docker-compose up
```

Will launch a OpenResty proxy, a Redis instance and a demo websocket server inside the container network.

To add entries to the Redis database:
```bash
docker exec -it openresty-ws-redis_redis_1 redis-cli
127.0.0.1:6379> SET 1 ws:8010
127.0.0.1:6379> SET 5 ws:8010
127.0.0.1:6379> SET 42 ws:8010
```

i.e. a connection made to `ws://localhost:8080/rooms/1` will be routed to the websocket server at ws:8010.

To make a websocket connection to the demo server:
```bash
wscat -c ws://localhost:8080/rooms/1
```
