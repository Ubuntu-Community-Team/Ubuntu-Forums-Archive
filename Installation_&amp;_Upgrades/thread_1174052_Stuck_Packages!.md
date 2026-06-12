---
title: "Stuck Packages!"
date: 2009-05-30
forum: Installation &amp; Upgrades
---

### Post by KiRiLoS on 2009-05-30
Hello,i tried to install KdenLive at my pc(9.04 i386,ext4) when i was installing it crashed,i hard restarted and now the package is stuck.
These are the errors i get:
```
apt-get -f install kdenlive
Reading package lists... Done
Building dependency tree       
Reading state information... Done
kdenlive is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up swh-plugins (0.4.15-0.2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing swh-plugins (--configure):
 subprocess post-installation script returned error exit status 2
Setting up ttf-dejavu-extra (2.28-1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing ttf-dejavu-extra (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 swh-plugins
 ttf-dejavu-extra
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
I tried apt-get install --reinstall , dpkg -r --force-all and yet i get the same errors.
Any help would be appreciated,thanks in advance :)

---

### Post by KiRiLoS on 2009-05-31
Ok i got it : 
```
cd /var/cache/apt/archives
dpkg --force-all -i packagename.deb
```

---

