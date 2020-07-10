# Localnet tests

Tools wrapped in a Dockerfile to **build**, **deploy** and **test** a localnet.

## Assumptions
* The main harmony repo follows the GO-PATH convention. So the path to said repo must be: 
```bash
$(go env GOPATH)/src/github.com/harmony-one/harmony
```
* This repo follows the GO-PATH convention. So the path to said repo must be:
```bash
$(go env GOPATH)/src/github.com/harmony-one/harmony-tests
```
* No extra transactions on the localnet are done prior to running the pytest in `./tests`
* The localnet faucet address is `one1zksj3evekayy90xt4psrz8h6j2v3hla4qwz4ur` 

## Build & run tests
To build the docker image locally, do:
```bash
make build
```
If you wish to build the docker image with a custom tag, do:
```bash
docker build -t "$TAG_NAME" .
``` 
> Note that you have to be in the same directory as the `Dockerfile`

To release the docker image to Dockerhub, do:
```bash
make upload
```

To run the localnet tests outside of the docker image (for dev testing), do:
```bash
make test
```
> This will test whatever is in the main repo (following GO-PATH convention). 

To run the localnet tests, do:
```bash
docker run -v "$(go env GOPATH)/src/github.com/harmony-one/harmony:/go/src/github.com/harmony-one/harmony" harmonyone/node-test 
```
> This will test whatever is in the main repo (following GO-PATH convention).