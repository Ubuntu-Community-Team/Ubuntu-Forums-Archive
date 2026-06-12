---
title: "problem installing splashy..."
date: 2009-08-17
forum: Installation &amp; Upgrades
---

### Post by tanixmukherzee on 2009-08-17
i am having a problem installing splashy in ubuntu jaunty...
the console is showing something like...

tanixmukherzee@tanbuntu:~$ sudo apt-get install splashy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  splashy-themes console-common
The following NEW packages will be installed:
  splashy
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1180kB of archives.
After this operation, 1831kB of additional disk space will be used.
Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty/universe splashy 0.3.13-3ubuntu1 [1180kB]
Fetched 1180kB in 37s (31.1kB/s)                                               
(Reading database ... 216261 files and directories currently installed.)
Unpacking splashy (from .../splashy_0.3.13-3ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/splashy_0.3.13-3ubuntu1_i386.deb (--unpack):
 trying to overwrite `/etc/lsb-base-logging.sh', which is also in package lsb-base
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/splashy_0.3.13-3ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

i am seeing this error...what to do...
i was getting some problem to activate usplash screen in ubuntu jaunty...so i tried to install splashy removing usplash
any ideas?

---

### Post by Partyboi2 on 2009-08-18
Hi, you can override the file with
```
cd /var/cache/apt/archives
sudo dpkg --force-overwrite --install splashy_0.3.13-3ubuntu1_i386.deb
```
then

---

### Post by tanixmukherzee on 2009-08-18
i fixed the bug prom ppa repo... thnx neways...:)

---

### Post by jojom271 on 2009-08-18
what is splashy

---

### Post by tanixmukherzee on 2009-08-19
check dis 1... [http://en.wikipedia.org/wiki/Splashy](http://en.wikipedia.org/wiki/Splashy)
its a splash screen handler...in default jaunty config we see the ubuntu splash screen...but using splashy we can change those splash themes...jaunty has issues with usplash...
splashy is a better replacement...along with startup manager...:)

---

### Post by dkcross on 2009-09-04
I have problems with splashy, when Ubuntu is starting>  "splashy connection refused "
 
I have the configuration of grub.cf 
> linux   /boot/vmlinuz-2.6.31-9-generic root=UUID=72d3ce3c-7f97-4e72-ab7c-8b384a995f95 ro quiet vga=791 splash

I have Ubuntu Karmic Koala alpha 5, please help :o

---

