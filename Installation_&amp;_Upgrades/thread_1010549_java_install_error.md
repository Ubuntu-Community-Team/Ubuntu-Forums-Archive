---
title: "java install error"
date: 2008-12-13
forum: Installation &amp; Upgrades
---

### Post by jlowery354 on 2008-12-13
Hello, I was trying to install Java with Red5 and it failed, I don't know why because I got it running on another ubuntu system. This system is ubuntu server 8.04

```

apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
Setting up sun-java5-bin (1.5.0-15-0ubuntu1) ...
Could not create the Java virtual machine.
dpkg: error processing sun-java5-bin (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of red5:
 red5 depends on sun-java5-bin; however:
  Package sun-java5-bin is not configured yet.
dpkg: error processing red5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java5-jre:
 sun-java5-jre depends on sun-java5-bin (= 1.5.0-15-0ubuntu1) | ia32-sun-java5-bin (= 1.5.0-15-0ubuntu1); however:
  Package sun-java5-bin is not configured yet.
  Package ia32-sun-java5-bin is not installed.
dpkg: error processing sun-java5-jre (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java5-bin
 red5
 sun-java5-jre
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by taurus on 2008-12-13
Are you running x86_64 and trying to install a 32bit version of java?

---

### Post by jlowery354 on 2008-12-13
no the cpu type is i386

---

### Post by taurus on 2008-12-13
Are you trying to upgrade your machine or something because you ran the "apt-get dist-upgrade" command?

What happens if you install java with

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

---

### Post by jlowery354 on 2008-12-13
I know it looks as if I were upgrading it, but im not, I tryed to upgrade to fix it, but that is what showed up. when i ran sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin; I got ```
# sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-pluginReading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sun-java6-bin

```
plus I dont understand why it wouldnt find it because i did also do sudo apt-get update

---

### Post by taurus on 2008-12-13
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by jlowery354 on 2008-12-13
Ok, here is my APT Sources

```
# cat /etc/apt/sources.list
deb http://archive.ubuntu.com/ubuntu hardy main

```

---

### Post by taurus on 2008-12-13
That's all!

Edit /etc/apt/sources.list

```
sudo nano -Bw /etc/apt/sources.list
```
and add these lines to the end.

```

deb http://archive.ubuntu.com/ubuntu hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu hardy main restricted

deb http://archive.ubuntu.com/ubuntu hardy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu hardy-updates main restricted

deb http://archive.ubuntu.com/ubuntu hardy universe
deb-src http://archive.ubuntu.com/ubuntu hardy universe

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted

deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe

deb http://archive.ubuntu.com/ubuntu hardy multiverse
deb-src http://archive.ubuntu.com/ubuntu hardy multiverse

deb http://archive.ubuntu.com/ubuntu hardy-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu hardy partner 

deb http://archive.ubuntu.com/ubuntu/ hardy main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ hardy-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe main multiverse restricted

```
Save the changes (<Ctrl>x) and then run

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

---

### Post by jlowery354 on 2008-12-13
Thanks!!! This must have been because my VPS provider only has an ubuntu minimal rebuild image.

---

