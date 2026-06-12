---
title: "Repository url typo"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by BlackMaxPhoto on 2009-10-09
I'm getting the following two error lines from 'sudo apt-get update':

W: Failed to fetch [http://mirrors.kernel.org/ubuntu/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://mirrors.kernel.org/ubuntu/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found [IP: 204.152.191.39 80]

W: Failed to fetch [http://mirrors.kernel.org/ubuntu/ubuntu/dists/karmic/universe/binary-i386/Packages.gz](http://mirrors.kernel.org/ubuntu/ubuntu/dists/karmic/universe/binary-i386/Packages.gz)  404  Not Found [IP: 204.152.191.39 80]


The actual urls should be:

[http://mirrors.kernel.org/ubuntu/dists/karmic/main/binary-i386/Packages](http://mirrors.kernel.org/ubuntu/dists/karmic/main/binary-i386/Packages)

[http://mirrors.kernel.org/ubuntu/dists/karmic/universe/binary-i386/Packages](http://mirrors.kernel.org/ubuntu/dists/karmic/universe/binary-i386/Packages)




... the question is how do I correct these in the system?

BC

:popcorn:

---

### Post by MelDJ on 2009-10-09
go to system-administration-software sources. then under the third party software tab, select the incorrect repisotory and press edit to change it

---

### Post by BlackMaxPhoto on 2009-10-09
Thanx

BC

---

