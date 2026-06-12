---
title: "can not install  anything after upgrading to 8.10"
date: 2009-03-17
forum: Installation &amp; Upgrades
---

### Post by boetheus on 2009-03-17
I have upgraded from 8.04 to 8.10.  When I try install or do any apt-get -f install.  I get this error

sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  gstreamer0.10-alsa gstreamer0.10-gnomevfs gstreamer0.10-plugins-base
  gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good
  gstreamer0.10-pulseaudio gstreamer0.10-x libglib2.0-0
  libgstreamer-plugins-base0.10-0 libnss3-1d libpurple0 pidgin pidgin-data
13 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/7076kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y


(Reading database ... dpkg: error processing /var/cache/apt/archives/libglib2.0-0_2.18.2-0ubuntu2.1_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `linux-headers-2.6.27-11': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/libglib2.0-0_2.18.2-0ubuntu2.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

How do I fix this?

---

### Post by taurus on 2009-03-17
Try cleaning out your cache first.

```
sudo apt-get clean
sudo apt-get update
```

---

### Post by rmeh on 2009-03-17
1) Please check you have disk space type: df -h
2) sudo apt-get clean; sudo apt-get update; sudo apt-get upgrade

---

### Post by boetheus on 2009-03-18
It didn't work. I am trying to use Synaptic to install rapache.

I keep getting this.

E: /var/cache/apt/archives/libgda3-common_3.0.2-4.1_all.deb: failed in buffer_read(fd)

---

### Post by enjoi19 on 2009-03-18
seems like you have

1. No buffer available
2. a slow/bad hard drive?

---

### Post by boetheus on 2009-03-18
It didn't work. I am trying to use Synaptic to install rapache.

I keep getting this.

E: /var/cache/apt/archives/libgda3-common_3.0.2-4.1_all.deb: failed in buffer_read(fd)

---

