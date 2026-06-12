---
title: "Trouble installing apps in my ubuntu server"
date: 2009-07-28
forum: Installation &amp; Upgrades
---

### Post by reghu007 on 2009-07-28
I am not able to install any apps in my ubuntu server, for example when i try installing swi-prolog, i get the following error message:

:~# apt-get install swi-prolog
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libgmp3c2
Suggested packages:
  prolog-el
Recommended packages:
  swi-prolog-doc swi-prolog-xpce
The following NEW packages will be installed:
  libgmp3c2 swi-prolog
0 upgraded, 2 newly installed, 0 to remove and 167 not upgraded.
Need to get 1711kB of archives.
After unpacking 4649kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libgmp3c2 swi-prolog
Install these packages without verification [y/N]? y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main libgmp3c2 2:4.2.1+dfsg-5ubuntu4
  404 Not Found [IP: 91.189.88.140 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe swi-prolog 5.6.14-1
  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gmp/libgmp3c2_4.2.1+dfsg-5ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gmp/libgmp3c2_4.2.1+dfsg-5ubuntu4_i386.deb)  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/s/swi-prolog/swi-prolog_5.6.14-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/s/swi-prolog/swi-prolog_5.6.14-1_i386.deb)  404 Not Found [IP: 91.189.88.140 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Any pointers please???

---

### Post by Partyboi2 on 2009-07-29
Hi, gutsy has reached its end of life, you would be better of upgrading to a later release of Ubuntu so you can get the security updates.
You can also backup and replace your sources.list  with these repos to install packages (not updates) for Gutsy.
```
deb http://old-releases.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ gutsy-security main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ gutsy-backports main/debian-installer
deb-src http://old-releases.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
```

---

