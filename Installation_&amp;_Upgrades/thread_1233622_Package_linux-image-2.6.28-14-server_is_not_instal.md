---
title: "Package linux-image-2.6.28-14-server is not installed"
date: 2009-08-06
forum: Installation &amp; Upgrades
---

### Post by &#65346;&#65365;&#65363;&#65353;&#65358;&#65349;&#65363;&#65363;&#65367;&#65353;&#65358;&#65351; on 2009-08-06
I have an Dell Power Edge 1750, RAID1. 
During my installation of Ubuntu 9.04 server 32bit, I saw kvm failed. 

I). 
After installation, The linux-image-2.6.28-14-sever cannot be updated.
then,, 
It shows:
-----------------------
1. could not install '/var/cache/apt/archives/linux-image-2.6.28-14-server_2.6.28-14.47_i386.deb' package may be in a not working state. 
-- short read in buffer_copy(backend dpkg-deg during './boot/vmlinuz-2.6.28-14-server')

-> could not install the upgrades.  The upgradeis now aborted. Your system could be in an unusable state. A recovery will run now (dpkg -configre -a).

-> Upgrade complete.  The upgrade is completed but there were errors during the upgrade process. 
    In the command line, it shows: 
   Update-manager: Fatal IO error 9 (Bad file descriptor) on X server :0.0.
   Setting up dot-base (0.8.20)
   Processing 1 changed, 3 added doc-base file(s)...
Object #1174668032 should have been retrieved already at ../../lib/Storable.pm (autosplit into ../../lib/auto/Storable/thaw.al) line 415, at /usr/share/perl5/ML DBM/Serializer/Storable.pm line 27
   dpkg: error processing doc-base (--configure):
   subprocess post-installation script returned error exit status 2
   Setting up libvirt-bin (0.6.1-0buntu5.1) ...
   addgroup: The group 'libvirtd' already exists asa system group. Exiting.
  * Stopping libvirt management daemon libvirtd   [OK]
  * Starting libvirt management daemon libvirtd    [OK]

dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.28-14-server:
linux-restricted-modules-2.6.28-14-server depends on linux-image-2.6.28-14-server; however: 
 Package linux-image-2.6.28-14-server is not installed.
dpkg: error processing linux-restricted-modules-2.6.28-14-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing: 
 doc-base
 linux-restricted-modules-2.6.28-14-server
------------------------

II).
After this, I tried to report this bug, yet, it shows this is not a genuis packae. >_<..

III).
So, I return to check if my downloaded 9.04 server version's MD5SUM, it shows the same. 

so.. I returned to my server, 
IV).
I tried to install the NOT installed linux-restricted-image-2.6.28-14-server,  An error occured. It shows 
E:/var/cache/apt/archieves/linux-image-2.6.28-14-server_2.6.28-14.47_i386.deb: short read in buffer_copy (backend dpkg-deb during './boot/vmlinuz-2.6.28-14-server')... 

Does any one would help?...

---

### Post by Partyboi2 on 2009-08-06
Hi, open a terminal and try clearing the cache
```
sudo apt-get clean
sudo apt-get -f install
sudo apt-get update
sudo apt-get install linux-image-2.6.28-14-server
```

---

### Post by &#65346;&#65365;&#65363;&#65353;&#65358;&#65349;&#65363;&#65363;&#65367;&#65353;&#65358;&#65351; on 2009-08-06
Now, I try to install Language support, it shows Software database is broken, and suggests to run following. 
$sudo apt-get install -f

the result is: 

-> E: Could not get lock /var/lib/dpkg/lock -open (11 Resource temporarily unaailable)
E: Unable to lock the administratin directory (/var/lib/dpkg/), is another process using it? 

.... from here, I really dont know what to do next.. 

oh, I have tried to reinstall the ubuntu 9.04 server already, it never changed.

---

### Post by &#65346;&#65365;&#65363;&#65353;&#65358;&#65349;&#65363;&#65363;&#65367;&#65353;&#65358;&#65351; on 2009-08-06
thanks. partyboi2, 

I have tried your suggestion:

sudo apt-get clean
sudo apt-get -f install

then.. same result as I posted previously.

---

### Post by &#65346;&#65365;&#65363;&#65353;&#65358;&#65349;&#65363;&#65363;&#65367;&#65353;&#65358;&#65351; on 2009-08-06
I tried $sudo apt-get update.

the result is same as above.

---

### Post by &#65346;&#65365;&#65363;&#65353;&#65358;&#65349;&#65363;&#65363;&#65367;&#65353;&#65358;&#65351; on 2009-08-07
Again,

I tried to install swf player in the firefox, it shows the software is broken. .. it seems that I cannot install software. 

Therefore, I tried to test following code'
$sudo apt-get install linux-image-2.6.28-14-server

the result is .. 

E: Couldn't find package linux-image-2.6.28-14-server, 

again.. the following messages come.

Object #1174668032 should have been retrieved already at ../../lib/Storable.pm (autosplit into ../../lib/auto/Storable/thaw.al) line 415, at /usr/share/perl5/ML DBM/Serializer/Storable.pm line 27
dpkg: error processing doc-base (--configure):
subprocess post-installation script returned error exit status 2

---

### Post by &#65346;&#65365;&#65363;&#65353;&#65358;&#65349;&#65363;&#65363;&#65367;&#65353;&#65358;&#65351; on 2009-08-12
no one would help to solve my problem... ? ... sigh... it seems forum is always a place to post questions, yet.. hard to have real solution and/or suggestion to me. .. 

anyone? .. mm... to be .. or not to be... .,

---

