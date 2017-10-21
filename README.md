# Build

## Build container
docker build -t $USER/aws-docker-node-template .

## List Docker images
docker images


## DEVELOPMENT


docker build -t $USER/aws-docker-node-template . && \
docker stop $(docker ps -a -q) && \
docker rmi -f $(docker images --filter "dangling=true" -q) && \
docker rm $(docker ps -a -q) && \
docker run -p 3001:80 -d $USER/aws-docker-node-template && \ 
docker ps -a && \
sleep 2 && open http://localhost:3001


## Logs
docker logs {CONTAINER_ID}


## Zip for AWS Beanstalk
zip -r publish/myapp.zip . -x "node_modules/*" -x ".git/*" -x "publish/*"