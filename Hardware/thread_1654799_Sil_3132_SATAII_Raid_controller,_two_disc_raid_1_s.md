---
title: "Sil 3132 SATAII Raid controller, two disc raid 1 setup, 10.10 shows both discs"
date: 2010-12-28
forum: Hardware
---

### Post by hogbola on 2010-12-28
Hi
 
Im using a generic pentium dual core 1.8ghz computer with asus mb and 4gb ddr2 ram, everyting works fine except my raid 1 configured root disc. i dualboot winXP and Ubuntu 10.10 root disc is detected as single drive in windooze but is two separate drives in 10.10, so i cant be shure my mirrored disc actually does wat it should,
 
has any one experienced this with SIL 3132 sata II raid controllers in ubuntu 10.10?

---

### Post by ronparent on 2010-12-29
You don't say but this probably happened because 10.10 wasn't installed to the fakeraid. Although dmraid (the software used to access raids) comes on the distribution cd/dvd it is not installed unless the installation is to a raid drive. The solution is simple - just install dmraid (sybaptics, the software manager, or sudo apt-get install dmraid). Once installed your shared raid drive should be seen once as a raid. If you want to partition the raid with gparted, you currently also have to install kpartx (a bug that has been fixed upstream).

---

