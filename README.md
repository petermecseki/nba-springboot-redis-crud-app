# NBA-springboot-redis-crud-app
#### 
A simple spring-boot REST application to check NBA match statistics. It collects data from an external API and connects to Redis to store and retrieve it.
In this case, Redis is used as both a database and a cache.

A simple spring-boot REST application to check NBA match statistics. Data is collected from an external API. The app connects to Redis to store and retrieve data.
In this case, Redis is used as both a database and a cache.
REST application to check NBA match statistics <br><br>

### How to run the application

#### Software requirements:
- Docker-compose installed

#### To execute this app <br>

##### Build the jar and package it into an OCI image with buildpack
    ./gradlew bootBuildImage --imageName=nba-app

##### Start the application & Redis
    docker-compose up


##### Hit the following endpoint to list a match <br>
```
curl http://localhost:8085/game/1
```

##### Some sample queries to test the comment functionality
```
curl -X POST http://localhost:8080/comment/add/1 -H 'Content-Type: application/json' -d '{"comment":"Sample comment to add"}'
curl -X PUT http://localhost:8080/comment/edit/1 -H 'Content-Type: application/json' -d '{"comment_id":"<copy and paste id from an existing comment>","new_comment":"Sample comment to update the old comment"}'
curl -X DELETE http://localhost:8080/comment/delete/1 -H 'Content-Type: application/json' -d '{"comment_id":"<copy and paste id from an existing comment>"}'
```

##### Finally, you can stop the application and teardown the containers.
    docker-compose down
