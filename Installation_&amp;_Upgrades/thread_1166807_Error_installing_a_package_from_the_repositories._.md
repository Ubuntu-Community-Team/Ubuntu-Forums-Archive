---
title: "Error installing a package from the repositories. How to avoid the proxy?"
date: 2009-05-22
forum: Installation &amp; Upgrades
---

### Post by tirengarfio on 2009-05-22
Hi,

im executing "sudo apt-get install mysql-server" and i get this error:


The following NEW packages will be installed:
mysql-server mysql-server-5.0
0 upgraded, 2 newly installed, 0 to remove and 105 not upgraded.
Need to get 27.4MB/27.5MB of archives.
After this operation, 86.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main mysql-server-5.0
5.0.51a-3ubuntu5.4 403 Forbidden [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main mysql-server-5.0
5.0.51a-3ubuntu5.4 403 Forbidden [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/poo...tu5.4_i386.deb](http://archive.ubuntu.com/ubuntu/poo...tu5.4_i386.deb) 403
Forbidden [IP: 91.189.88.45 80] E: Unable to fetch some archives, maybe
run apt-get update or try with --fix-missing?

I run "apt-get update" but the error is the same.

Im connected in a public library through a proxy. Someone told me the problem could be the proxy.

Is there any way of install the package through the proxy?

Bye

---

### Post by tirengarfio on 2009-05-24
No idea?

Maybe this is not the best place to ask this...if not, where should i ask it?

---

