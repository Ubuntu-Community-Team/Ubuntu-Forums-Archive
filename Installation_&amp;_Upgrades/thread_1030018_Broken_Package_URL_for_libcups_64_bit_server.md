---
title: "Broken Package URL for libcups 64 bit server"
date: 2009-01-04
forum: Installation &amp; Upgrades
---

### Post by Sesshomurai on 2009-01-04
Hi,
  I try to apt-get install libcups2 on amd64bit server. (uname: Linux ubuntu 2.6.27-13-xen #1 SMP Sat Nov 8 23:30:17 UTC 2008 x86_64 GNU/Linux) and it cannot find the right libcups file because it doesn't exist at the repo.

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main libcups2 1.3.9-2ubuntu3
  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/cups/libcups2_1.3.9-2ubuntu3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cups/libcups2_1.3.9-2ubuntu3_amd64.deb)  404 Not Found [IP: 91.189.88.40 80]

There are files there for it, but with slightly different name (e.g. 4 instead of 3).

Who do I contact about fixing this? Or is there a way to work around it so I can install the packages I need?

thanks,
Sessh

---

### Post by Partyboi2 on 2009-01-05
Try changing your download server in Software Sources (System>Admin>Software Sources) to another one.

---

