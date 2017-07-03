# craigbot

Bot for monitoring Craigslist.

## Development

Create a new Slack [bot user](https://api.slack.com/bot-users). Retrieve your bot user's API token and put it in a new file, `.docker/env`. See `.docker/env.example` for an example. Other environment variables can be placed in this file to override default settings.

With Docker installed and running, start the bot:

```
$ make run
```

If the image doesn't exist locally, Docker will pull it from [Docker Hub](https://hub.docker.com/r/rlucioni/craigbot/), create a container, and start it.

Tail a running container's logs:

```
$ make logs
```

Open a shell on a new container:

```
$ make shell
```

Build a new image:

```
$ make image
```

For information about additional Make targets:

```
$ make help
```

## Deployment

When changes are merged to master, Travis builds new images and pushes them to Docker Hub. Docker Cloud manages a service which uses the image stored in Docker Hub. The service is hosted by a node cluster deployed on Digital Ocean. Docker Cloud’s autoredeploy feature automatically redeploys the service when a new image is pushed.

If you're interested in setting up this continuous deployment system for yourself, see Docker Cloud's docs on [automated builds](https://docs.docker.com/docker-cloud/builds/automated-build/) and [deploying services](https://docs.docker.com/docker-cloud/getting-started/).
