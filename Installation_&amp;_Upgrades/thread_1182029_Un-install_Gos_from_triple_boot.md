---
title: "Un-install Gos from triple boot"
date: 2009-06-08
forum: Installation &amp; Upgrades
---

### Post by likebikes on 2009-06-08
hi
i have a triple boot system on one physical drive. Xp was put on first,i let it have whole drive. Then ubuntu 9.04 re-partitioned drive to half for ubuntu. then put gos on and re-partitioned ubuntu partition half again for gos. the thing is i want to remove gos leaving xp and ubuntu as a dual boot. 
Unfortunately i dont know which partition is which!

help much appreciated

---

### Post by Idefix82 on 2009-06-08
The most risk-free way of doing this is by removing the Gos partition from within Ubuntu using Gparted. This way, you will not be able to format the Ubuntu partition by accident because it will be mounted.

Just start Ubuntu, install GParted
```
sudo apt-get install gparted
```
start gparted, find the ext3 partition which is not mounted (I understand that you have 3 partitions all together, one of them ntfs and two ext3) and format it. Now start gparted from the live cd and expand Ubuntu's partition into the unallocated space. Beware that the latter always has a risk of losing data, so make a backup.

---

### Post by likebikes on 2009-06-15
Thanks Idefix82 I'll give it a whirl

---

