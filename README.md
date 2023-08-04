# metabase-arm64

Multi-arch/arm64-compatible images for [metabase](https://hub.docker.com/r/metabase/metabase).

Based on [this comment](https://github.com/metabase/metabase/issues/13119#issuecomment-1000350647) from the [Metabase issue for supporting ARM](https://github.com/metabase/metabase/issues/13119).

## Building

### One-time setup

Need to use a docker driver that supports multiple platforms (otherwise buildx fails with `error: multiple platforms feature is currently not supported for docker driver. Please switch to a different driver (eg. "docker buildx create --use")`).

```sh
docker buildx create --use
```

### Building latest

```sh
docker buildx build --push --platform linux/amd64,linux/arm64 --tag loancrate/metabase:latest .
```

### Building a specific repo and/or version

```sh
docker buildx build --push --platform linux/amd64,linux/arm64 --tag loancrate/metabase:enterprise-v1.46.6.4 --build-arg metabase_repo=metabase-enterprise --build-arg metabase_version=v1.46.6.4 .
```
