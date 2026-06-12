---
title: "How to get driver information"
date: 2009-04-22
forum: Hardware
---

### Post by NICU on 2009-04-22
Hi,

I'm using USB serial devices on two systems (with 2 different kernel revisions) and I'm noticing problems on one system.  Both systems are using the USB cdc-acm driver, but I don't know what version or what differences there are between the drivers in the different revs of the kernel.

Is there a way (using the command line) to tell if there are different versions or changes between the drivers?  In both cases I'm using cdc-acm.ko.  Is there any utility to get information from a .ko?

---

### Post by StuartN on 2009-04-22
cat /proc/modules will show all running modules. Once you have the correct module name, modinfo <modname> gives the version number, path and other information.

---

