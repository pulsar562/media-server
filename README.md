# HTPC Media server docker-compose

Something like the following on debian jessie will probably work. Check the UID/GID here and within the docker-compose file.

```
apt-get update

apt-get -y install fail2ban

apt-get -y install unattended-upgrades apt-listchanges
dpkg-reconfigure -plow unattended-upgrades

apt-get -y install apt-transport-https ca-certificates curl gnupg2 software-properties-common

curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -

sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/debian \
   $(lsb_release -cs) \
   stable"
apt-get update
apt-get -y install docker-ce

curl -L https://github.com/docker/compose/releases/download/1.12.0/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose

mkdir -p /var/filez/containers/{couchpotato,plex,sonarr,sabnzbd,letsencrypt,plexrequests,htpcmanager,hydra}/config
mkdir -p /var/filez/{movies,tv,documentaries}
mkdir -p /var/filez/dl/completed/{movies,tv}
chown -R 1000 /var/filez
chgrp -R 1000 /var/filez
```

