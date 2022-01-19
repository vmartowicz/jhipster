# Generator-jhipster : Fix 17487


## Setup


- `gateway` - Enable zipkin
  Set spring.zipkin.enables to true in  `application-dev.yml`

- `service` - Enable zipkin
  Set spring.zipkin.enables to true in  `application-dev.yml`

## Run
Run zipkin
```
docker-compose -f gateway/src/main/docker/zipkin.yml up -d
```
Run registry
```
docker-compose -f gateway/src/main/docker/jhipster-registry.yml up -d
```

Run gateway
```
In gateway directory
./mvnw -Pdev,zipkin
But the gateway does not compile because of UserRepository.USERS_BY_LOGIN_CACHE is missing
```
Run service
```
In service directory
./mvnw -Pdev,zipkin
```

## Test

- `gateway` - Play with it : http://localhost:8080
- `zipkin` - Check trace : http://localhost:9411
