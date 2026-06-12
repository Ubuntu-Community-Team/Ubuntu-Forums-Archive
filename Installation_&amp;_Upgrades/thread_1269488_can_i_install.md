---
title: "can i install??"
date: 2009-09-18
forum: Installation &amp; Upgrades
---

### Post by johnnie93 on 2009-09-18
can i install the live cd for ubuntu on my extra hard drive because i want to keep windows for gaming and use ubuntu on my other hard drive its an internal HDD btw:popcorn:

---

### Post by Partyboi2 on 2009-09-18
Hi, yes you can do this, at the partitioning stage of the installation choose the correct /dev/sd? to install to your 2nd hard drive. If you are not sure which hard drive is your 2nd hard drive at the partitioning stage you can boot all the way to the Desktop using the live cd and opening a terminal (Applications>Accessories>Terminal) and checking with
```
sudo fdisk -lu
```
If you are unsure on how to read the output from the above command post the output.

---

