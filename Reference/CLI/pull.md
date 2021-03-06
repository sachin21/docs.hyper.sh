## pull

    Usage: hyper pull [OPTIONS] NAME[:TAG] | [REGISTRY_HOST[:REGISTRY_PORT]/]NAME[:TAG]

    Pull an image or a repository from the registry

      --disable-content-trust=true  Skip image verification
      --help=false                  Print usage

Most of your images will be created on top of a base image from the [Docker Hub](https://hub.docker.com) registry.

[Docker Hub](https://hub.docker.com) contains many pre-built images that you can `pull` and try without needing to define and configure your own.

It is also possible to manually specify the path of a registry to pull from. For example, if you have set up a local registry, you can specify its path to pull from it. A repository path is similar to a URL, but does not contain a protocol specifier (`https://`, for example).

To download a particular image, or set of images (i.e., a repository), use `hyper pull`:

    $ hyper pull debian
    # will pull the debian:latest image and its intermediate layers
    $ hyper pull debian:testing
    # will pull the image named debian:testing and any intermediate
    # layers it is based on.
    $ hyper pull debian@sha256:cbbf2f9a99b47fc460d422812b6a5adff7dfee951d8fa2e4a98caa0382cfbdbf
    # will pull the image from the debian repository with the digest
    # sha256:cbbf2f9a99b47fc460d422812b6a5adff7dfee951d8fa2e4a98caa0382cfbdbf
    # and any intermediate layers it is based on.
    # (Typically the empty `scratch` image, a MAINTAINER layer,
    # and the un-tarred base).
    $ hyper pull registry.hub.docker.com/debian
    # manually specifies the path to the default Docker registry. This could
    # be replaced with the path to a local registry to pull from another source.
    # sudo hyper pull myhub.com:8080/test-image

Killing the `hyper pull` process, for example by pressing `CTRL-c` while it is running in a terminal, will not terminate the pull operation.
