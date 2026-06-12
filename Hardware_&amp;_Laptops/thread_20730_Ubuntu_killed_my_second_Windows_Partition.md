---
title: "Ubuntu killed my second Windows Partition"
date: 2005-03-18
forum: Hardware &amp; Laptops
---

### Post by Houmie on 2005-03-18
Hi,

I had 2 WinXP Partition installed. Ubunto however killed the boot MBR of the second one.

How do  restore it, so I still can boot from my second WinXP Partition?

Thanks

---

### Post by Buffalo Soldier on 2005-03-18
I'm always lead to belief there is always only one MBR per system, regardless of how many harddisk. But I could be wrong :p

A bit more detail about your harddisks, partitions, filesystem, content and etc? What does```
sudo fdisk -l
``` prints out? What's the content of your */etc/fstab* file?

---

