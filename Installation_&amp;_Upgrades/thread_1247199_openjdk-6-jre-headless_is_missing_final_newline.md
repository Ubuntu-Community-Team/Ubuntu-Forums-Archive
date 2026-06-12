---
title: "openjdk-6-jre-headless is missing final newline"
date: 2009-08-22
forum: Installation &amp; Upgrades
---

### Post by tdrobbin on 2009-08-22
Help! I am a total greenhorn when it comes to computers. I have been trying to download Adobe Flash onto my dell, but when I do I am prompted to filter out 1 broken package and fix it.  But when I try to fix it, this is what I get:

user@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  openjdk-6-jre-headless openjdk-6-jre-lib rhino
Suggested packages:
  sun-java6-fonts ttf-bengali-fonts ttf-kannada-fonts ttf-oriya-fonts
  ttf-telugu-fonts ttf-wqy-zenhei rhino-doc
Recommended packages:
  ca-certificates-java
The following NEW packages will be installed:
  rhino
The following packages will be upgraded:
  openjdk-6-jre-headless openjdk-6-jre-lib
2 upgraded, 1 newly installed, 0 to remove and 307 not upgraded.
3 not fully installed or removed.
Need to get 0B/29.2MB of archives.
After this operation, 72.1MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
user@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  openjdk-6-jre-headless openjdk-6-jre-lib rhino
Suggested packages:
  sun-java6-fonts ttf-bengali-fonts ttf-kannada-fonts ttf-oriya-fonts
  ttf-telugu-fonts ttf-wqy-zenhei rhino-doc
Recommended packages:
  ca-certificates-java
The following NEW packages will be installed:
  rhino
The following packages will be upgraded:
  openjdk-6-jre-headless openjdk-6-jre-lib
2 upgraded, 1 newly installed, 0 to remove and 307 not upgraded.
3 not fully installed or removed.
Need to get 0B/29.2MB of archives.
After this operation, 72.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: error processing /var/cache/apt/archives/openjdk-6-jre-lib_6b11-2ubuntu2.1_all.deb (--unpack):
 files list file for package `openjdk-6-jre-headless' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/openjdk-6-jre-lib_6b11-2ubuntu2.1_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

I have been searching forums high and low for an answer. Can anyone lend a hand?

---

### Post by running_rabbit07 on 2009-08-22
The best way to install flash is to go to myspace.com. Their site automatically offers three versions to install. I recommend the Adobe one. I have used that method several times now.

---

