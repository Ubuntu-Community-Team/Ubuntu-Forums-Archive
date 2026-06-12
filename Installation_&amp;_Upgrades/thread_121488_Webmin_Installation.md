---
title: "Webmin Installation"
date: 2006-01-25
forum: Installation &amp; Upgrades
---

### Post by wonderc on 2006-01-25
I have two test boxes running Suse9.0 and Ubuntu 5.04, on Suse I downloaded a Tgz file for webmin and installed it and then on Ubuntu I used apt-get install but there is a big difference on the startup interfaces.

do I have to create the modules for the servers??

please help.

---

### Post by davehahn on 2006-01-26
I also just tried to install webmin using apt-get install webmin.  It looks like it started up, but nothing is running on port 10000.  I would also appreciate some help with this.  Here is the output that I got:

root@ubuntu:~# apt-get install webmin
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libauthen-pam-perl libnet-ssleay-perl openssl
Suggested packages:
  ca-certificates
Recommended packages:
  webmin-core logcheck
The following NEW packages will be installed:
  libauthen-pam-perl libnet-ssleay-perl openssl webmin
0 upgraded, 4 newly installed, 0 to remove and 2 not upgraded.
Need to get 2301kB of archives.
After unpacking 9855kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe libauthen-pam-perl 0.15-1 [35.3kB]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main openssl 0.9.7g-1ubuntu1.1 [904kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main libnet-ssleay-perl 1.25-1.1 [180kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe webmin 1.230-1 [1182kB]       
Fetched 2301kB in 3s (596kB/s)                                                   

Preconfiguring packages ...
Selecting previously deselected package libauthen-pam-perl.
(Reading database ... 61041 files and directories currently installed.)
Unpacking libauthen-pam-perl (from .../libauthen-pam-perl_0.15-1_i386.deb) ...
Selecting previously deselected package libnet-ssleay-perl.
Unpacking libnet-ssleay-perl (from .../libnet-ssleay-perl_1.25-1.1_i386.deb) ...
Selecting previously deselected package openssl.
Unpacking openssl (from .../openssl_0.9.7g-1ubuntu1.1_i386.deb) ...
Creating directory /etc/ssl
Selecting previously deselected package webmin.
Unpacking webmin (from .../webmin_1.230-1_all.deb) ...
Setting up libauthen-pam-perl (0.15-1) ...
Setting up libnet-ssleay-perl (1.25-1.1) ...
Setting up openssl (0.9.7g-1ubuntu1.1) ...

Setting up webmin (1.230-1) ...
md5sum: miniserv.pem: No such file or directory
Starting webmin: webmin.

root@ubuntu:~#

---

### Post by Gcool on 2006-01-26
Can you see webmin running among the active processes? If not, take a look in the log files, and see why it's not starting up correctly.

Also, the latest versions of webmin have to be accessed through https by default. (ex. [https://localhost:10000](https://localhost:10000))

---

### Post by ahathaway on 2006-02-03
You need to remove the apt-get version of webmin because it is old and it is a pain to configure.  Then download the newest version from the website and istall using these directions:

[http://ubuntuforums.org/showthread.php?t=7507](http://ubuntuforums.org/showthread.php?t=7507)

I had the same issue until I uninstalled the apt-get version and and installed the newest.

---

