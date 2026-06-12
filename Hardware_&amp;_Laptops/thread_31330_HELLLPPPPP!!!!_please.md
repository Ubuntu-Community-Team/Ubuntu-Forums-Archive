---
title: "HELLLPPPPP!!!! please"
date: 2005-05-02
forum: Hardware &amp; Laptops
---

### Post by schatterjee04 on 2005-05-02
i have a laptop that crashed twice in 2 days and i have some files on my hardrive that i can access from the comand prompt but how do i read it through the live disk???

---

### Post by alastair on 2005-05-02
Hmmm.

Your hard disk will still be something like :

/dev/hdaX

say - for primary master e..g

/dev/hda1

for partition 1 on primary master.

So, you could just do something like :

mkdir /tmp/mydisk
sudo mount /dev/hda1 /mnt/mydisk

Perhaps. If the disk is not right - see your logs (/var/log/syslog) and check partitions via "fdisk" i.e.

fdisk -l /dev/hda

---

