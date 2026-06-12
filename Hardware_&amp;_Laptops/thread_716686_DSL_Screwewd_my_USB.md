---
title: "DSL Screwewd my USB"
date: 2008-03-06
forum: Hardware &amp; Laptops
---

### Post by faraz_k86 on 2008-03-06
I have a 128 mb usb, I installed DSL on it and now it is split into 2 partitions, I have deleted DSL.

one of the partitions is 50 mb and is active and visible in widows, the other is 73 MB and is only visible in linux, how can I recombine both of them again into one partition?

---

### Post by taurus on 2008-03-06
Use gparted (System -> Administration) in Ubuntu to delete all the partitions on the drive.  Then, format it to fat32/vfat.  

If you don't have gparted on your machine, then install it from synaptic or with apt-get.

---

