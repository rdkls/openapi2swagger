# openapi2swagger

Easy way to convert OpenAPI v3 spec to v2

You may want to do this for using something that only supports v2 e.g. Postman, Restlet

## Quick usage

`docker run --rm -v $PWD:/tmp -e OPENAPI_FILE=swagger.yml rdkls/openapi2swagger > swagger.openapiv2.yml`

using [docker hub automated build](https://hub.docker.com/r/rdkls/openapi2swagger/)


## The rest from juan-lb :)

![logo](https://github.com/juan-lb/openapi2swagger/blob/master/docs/logo.png?raw=true)

Amazon AWS API Gateway claims that is compatible with Swagger.
I don't think so, just the Swagger format version 2 it is supported.

Swagger 2 evolved to Openapi 3, and fame and fortune is all for him.

But the poor souls that want to use the (almost) amazing API Gateway have to wait that Amazon guys include the new format.

Until that happen, I'm glad to anounce:

# Openapi 3 downgrade to Swagger 2

I really didn't do anything, I've just combined the great work of other people, in particular: 
[**LucyBot-Inc/api-spec-converter**](https://github.com/LucyBot-Inc/api-spec-converter)

## Usage
This repo has a `Dockerfile` that create a container with the hability of convert a Openapi3 spec file and convert it in a Swagger2 file, compatible with AWS API Gateway.

It works directly out of the box.

### Command Line

```bash
docker build -t openapi2swagger:latest .
docker run -v /directory/where/is/the/file:/tmp -e OPENAPI_FILE=the_openapi3_file.json  openapi2swagger:latest > ~/swagger2_file.json
```
#### Parameters
- **/directory/where/is/the/file** : the directory on your computer where is the Openapi3 file spec.
- **the_openapi3_file.json** : the file name.

### Notes
#### Removing the "example" property
I don't know yet why API Gateway doesn't support this property in the Swagger spec. The command inside the docker removes those lines with a  bash `sed` command.

Any clue is welcome.
