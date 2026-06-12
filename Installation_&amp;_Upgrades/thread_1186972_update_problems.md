---
title: "update problems"
date: 2009-06-14
forum: Installation &amp; Upgrades
---

### Post by madangopalk on 2009-06-14
Hi

I have recently upgraded from 8.10 to 9.04 

i am opening package manager so i m getting the following error.


E:Read error - read (5 Input/output error), E:The package lists or status file could not be parsed or opened.'


and even my nvidia drivers are not working .

Thanks 

Madan

---

### Post by kdi on 2009-06-14
i got the same nvidia driver issue after upgrading to 9.04. i'm using 8.10 before n installed graphic driver which i downloaded from nvidia.com. during the installation, the driver asked for kernel header (if i'm not mistaken), so i downloaded the kernel's build-essential (sudo apt-get install build-essential) in order for the graphic driver to merge with the kernel.

that was the case in my 8.10 setup.

after upgrading, it seems that the kernel is changed from 2.6.27 (ubuntu 8.10) to 2.6.28 (ubuntu 9.04). therefore i have to install the driver again to merge with the new kernel. only then i managed to get the graphic driver to load in ubuntu 9.04 successfully.

---

