---
title: "Again?!"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by Kobayashi-kun on 2009-02-03
> torako@torako-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following extra packages will be installed:
  language-pack-gnome-en-base openoffice.org-base-core openoffice.org-core
  openoffice.org-writer python-uno
Suggested packages:
  openoffice.org-base openoffice.org-gcj
Recommended packages:
  gij java-gcj-compat openjdk-6-jre sun-java5-jre sun-java6-jre java2-runtime
  openoffice.org-filter-binfilter openoffice.org-java-common
  openoffice.org-writer2latex
The following packages will be upgraded:
  language-pack-gnome-en-base openoffice.org-base-core openoffice.org-core
  openoffice.org-writer python-uno
5 upgraded, 0 newly installed, 0 to remove and 172 not upgraded.
6 not fully installed or removed.
Need to get 0B/33.1MB of archives.
After this operation, 41.0kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 99299 files and directories currently installed.)
Preparing to replace language-pack-gnome-en-base 1:8.04+20080527 (using .../language-pack-gnome-en-base_1%3a8.04+20090105_all.deb) ...
Unpacking replacement language-pack-gnome-en-base ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/language-pack-gnome-en-base_1%3a8.04+20090105_all.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Preparing to replace python-uno 1:2.4.1-1ubuntu2 (using .../python-uno_1%3a2.4.1-1ubuntu2.1_i386.deb) ...
Unpacking replacement python-uno ...
Preparing to replace openoffice.org-writer 1:2.4.1-1ubuntu2 (using .../openoffice.org-writer_1%3a2.4.1-1ubuntu2.1_i386.deb) ...
Unpacking replacement openoffice.org-writer ...
Preparing to replace openoffice.org-core 1:2.4.1-1ubuntu2 (using .../openoffice.org-core_1%3a2.4.1-1ubuntu2.1_i386.deb) ...
Unpacking replacement openoffice.org-core ...
Preparing to replace openoffice.org-base-core 1:2.4.1-1ubuntu2 (using .../openoffice.org-base-core_1%3a2.4.1-1ubuntu2.1_i386.deb) ...
Unpacking replacement openoffice.org-base-core ...
Errors were encountered while processing:
 /var/cache/apt/archives/language-pack-gnome-en-base_1%3a8.04+20090105_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


DDDD: For gods sakes....

---

### Post by taurus on 2009-02-03
Maybe try to clean out the cache first.

```
sudo apt-get clean
sudo apt-get install -f
```

---

