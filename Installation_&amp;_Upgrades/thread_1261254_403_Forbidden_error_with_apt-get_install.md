---
title: "403 Forbidden error with apt-get install"
date: 2009-09-08
forum: Installation &amp; Upgrades
---

### Post by bravo13 on 2009-09-08
Hi All,
           I was installing sun-java6-jre, using apt-get and my net connection was interrupted. So the installation was stopped in between. But once the connection is restored, I am getting the following error. 

root@bravo13:/etc/apt# apt-get -f install sun-java6-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  sun-java6-bin
Suggested packages:
  sun-java6-plugin ia32-sun-java6-plugin sun-java6-fonts
The following NEW packages will be installed:
  sun-java6-bin sun-java6-jre
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 28.3MB/34.7MB of archives.
After this operation, 99.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse sun-java6-bin 6-13-1
  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-bin_6-13-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-bin_6-13-1_i386.deb)  403 Forbidden
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
  

I am able to access the folder from firefox. I have set the http_proxy env variable to my proxy server. I tried apt-get update and apt-get -f install option, both are not working. 

                                                                                             Please help.

---

### Post by hchaseshields on 2009-09-23
I had the same problem, and in other parts of the forums found this answer:

change all the http to ftp in /etc/apt/sources.list

Worked like  charm.

---

