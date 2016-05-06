# hiyokochan

## Features

- [ruboty-slack](https://github.com/r7kamura/ruboty-slack)
- [ruboty-cron](https://github.com/r7kamura/ruboty-cron)
- [ruboty-feed](https://github.com/5t111111/ruboty-feed)
- [ruboty-redis](https://github.com/r7kamura/ruboty-redis)

## Development

### Prerequisites

Before you launch hiyokochan, there are a couple of prerequisites that need to be done.

- Ruby 2.3.1
- Redis to be installed on your machine
- Checking "Enable XMPP gateway (SSL only)" in "Team Settings" - "Permissions" - "Gateways"
- An account for Ruboty bot

### Environment variables

The following environment variables are required:

- ROBOT_NAME      - Bot name (e.g. hiyokochan)
- SLACK_PASSWORD  - Account's XMPP password
- SLACK_ROOM      - Room name to join in at first (e.g. general,random)
- SLACK_TEAM      - Account's team name (e.g. piyopiyoland)
- SLACK_USERNAME  - Account's username (e.g. hiyokochan)
- REDIS_URL       - Redis URL (e.g. redis://127.0.0.1:6379/)
- REDIS_NAMESPACE - Redis namespace (e.g. hiyokochan <optional>)

The easiest way to set environment variables is using `.env` via dotenv:

__.env (example)__

```
ROBOT_NAME=hiyokochan
SLACK_USERNAME=hiyokochan
SLACK_PASSWORD=xxxxxxxxxxxxxxxxx
SLACK_ROOM=general,random
SLACK_TEAM=xxxxxxxxxxxxxxxxx
REDIS_URL=redis://127.0.0.1:6379
REDIS_NAMESPACE=hiyokochan
```

### Launch Ruboty

```
$ bundle exec ruboty
```

or if you use dotenv:

```
$ bundle exec ruboty --dotenv
```

## Heroku deployment

WIP

## Docker deployment

### Persistent volume

Create a directory to persist Redis data on the Docker host machine.

```
$ mkdir -p /var/docker_volumes/hiyokochan/redis_data
```

### Environment variables

Create `.env` for Redis and Slack integration information in the Ruboty root directory.

__.env (example)__

```
ROBOT_NAME=hiyokochan
RUBOTY_ENV=production
SLACK_USERNAME=hiyokochan
SLACK_PASSWORD=xxxxxxxxxxxxxxxxx
SLACK_ROOM=general,random
SLACK_TEAM=xxxxxxxxxxxxxxxxx
REDIS_URL="redis://${REDIS_PORT_6379_TCP_ADDR}:${REDIS_PORT_6379_TCP_PORT}"
REDIS_NAMESPACE=hiyokochan
```

### Launch containers

```
$ docker-compose up
```
