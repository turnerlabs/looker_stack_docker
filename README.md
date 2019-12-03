# What is this.

**Currently supported version of Looker: 6.24.20(automatically grabs the latest version of Looker)**

**Currently supported version of Java: OpenJDK 8**

**Currently supported operating system: Ubuntu 18.04(automatically grabs the latest version of Ubuntu)**

This is a dockerized version of the looker stack.

This code was taken from <https://github.com/troyharvey/docker_looker/tree/looker-6-docker-setup> and modified to follow the patterns that I'm using in AWS.

## Here's how to get up and running with this on a Mac

1. Install Docker for Mac. https://docs.docker.com/docker-for-mac/install/

2. Modify Docker for Mac settings to work more optimally with airflow.
    * Open up the preferences menu item on Docker for the Mac and modify each tab to look similar to this.

![General](./images/docker1.png?raw=true)

![File Sharing](./images/docker2.png?raw=true)

![Disk](./images/docker3.png?raw=true)

![Advanced](./images/docker4.png?raw=true)

![Proxies](./images/docker5.png?raw=true)

![Daemon](./images/docker6.png?raw=true)

![Kubernetes](./images/docker7.png?raw=true)


## Building, Starting and Stopping Docker.

Once Docker for Mac is up and running you need to do the following items to start using it:

** assuming you have cloned this repo and are cd'd to this directory

1. Modify ./config/database.yml to suit your needs(or not)

2. Modify ./config/provision.yml.  You will need to add your Looker license key and the the Looker user information so you can log in.  Don't modify with the host_url.

3. Modify the 3 following arguments in the docker-compose.yml file to your settings.

    * LOOKER_LICENSE_KEY=YourLicenseKeyWithNoQuotes
    * LOOKER_LICENSE_EMAIL=YourLicenseEmailWithNoQuotes

--- Run Docker Compose up to start up the looker stack(load balancer, webserver, mysql)

`docker-compose --verbose -f docker-compose.yml up -d`

--- To take everything down, use:

`docker-compose --verbose -f docker-compose.yml down`

Navigate to http://localhost:80 to the looker website and login with.
