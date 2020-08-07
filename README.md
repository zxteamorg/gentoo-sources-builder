[![Docker Build Status](https://img.shields.io/docker/build/zxteamorg/gentoo-sources-builder?label=Status)](https://hub.docker.com/r/zxteamorg/gentoo-sources-builder/builds)
[![Docker Image Size (latest by date)](https://img.shields.io/docker/image-size/zxteamorg/gentoo-sources-builder?label=Size)](https://hub.docker.com/r/zxteamorg/gentoo-sources-builder/tags)
[![Docker Pulls](https://img.shields.io/docker/pulls/zxteamorg/gentoo-sources-builder?label=Pulls)](https://hub.docker.com/r/zxteamorg/gentoo-sources-builder)
[![Docker Image Version (latest by date)](https://img.shields.io/docker/v/zxteamorg/gentoo-sources-builder?sort=semver&label=Version)](https://hub.docker.com/r/zxteamorg/gentoo-sources-builder/tags)
[![Docker Image Info](https://images.microbadger.com/badges/image/zxteamorg/gentoo-sources-builder.svg)](https://hub.docker.com/r/zxteamorg/gentoo-sources-builder/dockerfile)

# Gentoo Sources Builder

This image based on Gentoo stage3 with additionally emerged packages to make abillity to compile Gentoo Sources Kernel in few commands on a Docker Host.


## Quick Start

```bash
docker run --rm --interactive --tty --volume $(pwd):/data [--env SITE=zxteam-desktop-hp64xx] zxteamorg/gentoo-sources-builder kernel
```

See directory `sites` for the SITE variable.

## What the image includes

TBD



## Dev notes

Debug initramfs of `zxteam-desktop-hp64xx` site

```
docker build --tag zxteamorg/gentoo-sources-builder --build-arg KERNEL_VERSION=5.4.48 --file docker/amd64/Dockerfile . && \
	docker run --rm --interactive --tty \
		--env SITE=zxteam-desktop-hp64xx \
		--volume $(pwd)/.data:/data \
		--volume $PWD/initramfs:/data/usr/src/initramfs \
		zxteamorg/gentoo-sources-builder initramfs
```