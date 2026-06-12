---
title: "Can't Upgrade foomatic-db contains empty filename"
date: 2009-09-06
forum: Installation &amp; Upgrades
---

### Post by MetalTim on 2009-09-06
Any idea what's going on here?  I haven't been able to update my system in a few weeks.  Looks like an empty file in foomatic-db is causing problems, any way to reset this?  I'm not familiar with foomatic-db at all.  And yes, I did an update before the upgrade.

sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  apache2-utils dnsmasq-base gnome-terminal gnome-terminal-data
  icedtea-6-jre-cacao kdelibs-bin kdelibs-data kdelibs4c2a kdelibs5
  kdelibs5-data libc6 libc6-dev libc6-i386 libcurl3-gnutls libgl1-mesa-dri
  libgl1-mesa-glx libglu1-mesa libgnutls26 libmono-cairo2.0-cil
  libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-data2.0-cil
  libmono-getoptions2.0-cil libmono-i18n2.0-cil libmono-posix2.0-cil
  libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil
  libmono-system-data2.0-cil libmono-system-web2.0-cil libmono-system2.0-cil
  libmono0 libmono2.0-cil libnss3-1d libpurple-bin libpurple0 libvorbis0a
  libvorbisenc2 libvorbisfile3 libxml2 libxml2-utils linux-headers-2.6.28-15
  linux-headers-2.6.28-15-generic linux-image-2.6.28-15-generic linux-libc-dev
  mesa-utils mono-2.0-gac mono-2.0-runtime mono-common mono-gac mono-jit
  mono-runtime mozilla-thunderbird openjdk-6-jdk openjdk-6-jre
  openjdk-6-jre-headless openjdk-6-jre-lib pidgin pidgin-data python-libxml2
  sun-java6-bin sun-java6-jdk sun-java6-jre sun-java6-plugin thunderbird
  tzdata tzdata-java
67 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/198MB of archives.
After this operation, 1122kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... dpkg: unrecoverable fatal error, aborting:
 files list file for package `foomatic-db' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by Partyboi2 on 2009-09-06
Open a terminal and try
```
sudo mv /var/lib/dpkg/info/foomatic-db.list /var/lib/dpkg/info/foomatic-db.list.broke 
``````
sudo apt-get --reinstall install foomatic-db 
```

If that does not work you can move the broken file back with
```
sudo mv /var/lib/dpkg/info/foomatic-db.list.broke /var/lib/dpkg/info/foomatic-db.list
```

---

### Post by MetalTim on 2009-09-07
That's great!  Thanks.

I need to add that it didn't go smoothly afterwards.  For some reason when I did the upgrade afterwards, I kept getting broken packages in KDELibs.  But I gave it a reboot and the upgrade went perfectly.

Thanks again!!

---

