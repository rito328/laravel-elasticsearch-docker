# Laravel Docker Starter
Docker development environment construction package for Laravel application. [for Mac]  

## System requirements
- Docker for Mac must be installed.
- composer (If it is not installed, it will be installed at setup time.)
## Operation confirmed environment
- macOS Mojave
- Docker Desktop for Mac: 2.0.0.2
- Docker Engine: 18.09.1
- Compose: 1.23.2
## Environment to be built
### app container
- centos: Latest edition
  - Apache: 2.4
  - PHP: 7.3
  - Laravel: Latest edition
### DB container
- MySQL: 8.0
### Elasticsearch container
- Elasticsearch: 6.5
## Project Structure
```
laravel-docker/
├── README.md
├── docker
│   ├── app
│   │   ├── Dockerfile         ... Dockerfile for applications
│   │   └── init
│   │       ├── .env           ... Laravel env file
│   │       ├── .env.testing   ... Laravel env file for testing
│   │       ├── app_setting.sh ... Shell for starting application server
│   │       └── phpunit.xml    ... Laravel phpunit.xml
│   ├── db
│   │   ├── Dockerfile         ... Dockerfile for Database
│   │   ├── conf.d
│   │   │   └── my.cnf         ... MySQL configuration file
│   │   └── init
│   │       └── create_test_db.sh ... shellscript for create testing db
│   └── docker-compose.yml     ... The app and db containers are managed by docker-compose.
├── order.sh                   ... ShellScript to operate Laravel and Docker
└── src                        ... Laravel source and configuration file installation directory
```
## Getting started
```
// Download sources
git clone https://github.com/rito328/laravel-docker.git

// Go to the laravel-docker directory.
cd /path/to/laravel-docker

// When you start setup, Laravel will be installed and the Docker environment will be launched.
sh order.sh setup
```
> !! POINT !!
>> Since migration and seeding are executed during Laravel setup, initial data can be input by defining these in advance.

When setup is complete, access localhost.
```
http://localhost/
```
Once setup is done, operation can be controlled by start / stop.
```
// stop
sh order.sh stop 

// start
sh order.sh start
```
The Laravel project will be installed under ```src/```
```
laravel-docker/
└── src
     └── laravel
```
The Laravel project mounts from an external volume, so it will be persisted.

## Commands
```
sh order.sh setup    : Set up Laravel Docker.
sh order.sh start    : Alias for setup.
sh order.sh stop     : Stop the container.
sh order.sh restart  : Reboot the container.
sh order.sh destroy  : Delete containers and images.
sh order.sh conn app : Connect to app container.
sh order.sh conn db  : Connect to MySQL in db container.
sh order.sh conn es  : Connect to Elasticsearch in es container.
sh order.sh help     : Display help.
```
## Contributions
Because it is a starter pack for a troublesome shop, it may be more convenient and the source should be still getting better. Of course, the bad part should be improved. Please send pull request by all means. We welcome your participation.

## Message
This package made Laravel easy to try under Docker environment.
Since we are also committing some configuration files, we do not recommend deploying these source file sets directly in the production environment.

Have fun Laravel & Docker life!