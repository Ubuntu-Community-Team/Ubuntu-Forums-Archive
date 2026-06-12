---
title: "Issue in &quot;sudo apt-get install -f&quot;"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by saikat ghosh on 2009-03-16
Hello,

facing issue when I executed the following commands: 

sudo apt-get install -f
and
sudo apt-get install -f bootcd*

log is attached.Please  suggest.

Regards
Saikat Ghosh

user@user-desktop:/usr/share/bootcd$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  bootcd
Suggested packages:
  ssh
The following NEW packages will be installed:
  bootcd
0 upgraded, 1 newly installed, 0 to remove and 245 not upgraded.
43 not fully installed or removed.
Need to get 0B/74.1kB of archives.
After this operation, 287kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 185824 files and directories currently installed.)
Unpacking bootcd (from .../bootcd_3.11ubuntu1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/bootcd_3.11ubuntu1_all.deb (--unpack):
 trying to overwrite `/usr/share/bootcd/bootcd-ia64.lib', which is also in package bootcd-ia64
Errors were encountered while processing:
 /var/cache/apt/archives/bootcd_3.11ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
user@user-desktop:/usr/share/bootcd$ sudo apt-get install -f bootcd*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package bootcdbackup

---

