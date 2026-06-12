---
title: "Problem installing slocate: &quot;Could not commit changes&quot;"
date: 2006-01-05
forum: Installation &amp; Upgrades
---

### Post by Lady Owl on 2006-01-05
I am constantly running into problems with Adept - or, actually as well with simply using apt-get from the command line. Every time I try to do something with them (any package), I get something like this:
```
Setting up findutils (4.2.22-2) ... 
(Reading database ... 51366 files and directories currently installed.)
Unpacking slocate (from .../slocate_2.7-4_i386.deb) ... 
Removing 'diversion of /etc/cron.daily/find to /etc/cron.daily/find.noslocate by slocate' dpkg-divert: rename involves overwriting '/etc/cron.daily/find' eith different file '/etc/cron.daily/find.noslocate', not allowed 
dpkg: error processing /var/cache/apt/archives/slocate_2.7-4_i386.deb (--unpack): subprocess pre-installation script returned error exit status 2 
Selecting previously deselected package gzip. 
Unpacking gzip (from .../gzip_1.3.5-11ubuntu2_i386.deb) ... 
Errors were encountered while processing: /var/cache/apt/archives/slocate_2.7-4_1386.deb 
dpkg run finished!
``` 
The problem is always slocate. Adept also shows that Kubuntu-desktop package is broken. Happy for any help you can give - but remember I am a newbie admin. 

Some background information: Installed Kubuntu 5.10 on sunday, but as I can't burn a CD, had to do it from another Linux distro. The first time I encountered this problem was when I used base-config to add more packages to the base-system.

---

