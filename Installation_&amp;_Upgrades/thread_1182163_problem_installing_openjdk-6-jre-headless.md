---
title: "problem installing openjdk-6-jre-headless"
date: 2009-06-08
forum: Installation &amp; Upgrades
---

### Post by jhahoneyk on 2009-06-08
If i try to install openjdk-6-jre-headless it fails with the output-

Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  openjdk-6-jre-headless
Suggested packages:
  sun-java6-fonts
The following NEW packages will be installed:
  openjdk-6-jre-headless
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 0B/25.7MB of archives.
After this operation, 76.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 168206 files and directories currently installed.)
Unpacking openjdk-6-jre-headless (from .../openjdk-6-jre-headless_6b14-1.4.1-0ubuntu7_i386.deb) ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/openjdk-6-jre-headless_6b14-1.4.1-0ubuntu7_i386.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/openjdk-6-jre-headless_6b14-1.4.1-0ubuntu7_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I've verified the package md5 is correct. Any idea whats wrong?

---

