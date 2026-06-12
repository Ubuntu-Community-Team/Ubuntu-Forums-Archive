---
title: "Kernel Source"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by poohpeer on 2009-11-03
I'm trying to install VMware tools but it says that kernel source I have is not the one I'm running.

> What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src/linux-headers-2.6.24-24-generic/include/

The directory of kernel headers (version 2.6.24-24-generic) does not match your
running kernel (version 2.6.24-24-server).  Even if the module were to compile
successfully, it would not load into the running kernel.


Where should I look for this files?

---

