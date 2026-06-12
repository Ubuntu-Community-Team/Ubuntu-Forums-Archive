---
title: "Dual Boot - Shared Partition"
date: 2009-01-23
forum: Installation &amp; Upgrades
---

### Post by eNdeRam on 2009-01-23
heres the scenario:

I want to dual boot ubuntu on a system that already has windows installed and i want to have a shared partition

now my question is (might be a dumb one but... "/ ): can i make the partition NTFS or does it have to be Ext or FAT32

---

### Post by Partyboi2 on 2009-01-24
Ubuntu can read/write to ntfs, windows can not read/write to ext3 unless you install a small program to do so, so I would suggest making a ntfs to share between the two.

---

### Post by eNdeRam on 2009-01-26
oh yea but i heard that the partitioner in the ubuntu installer doesnt create ntfs partitions

---

### Post by Partyboi2 on 2009-01-26
You can use gparted (system>Admin>Partition Editor) of the ubuntu live cd and create all your partitions before starting the install, then when installing choose to manual partition and set the mount point(s) for your created partitions.
So with  gparted you can create a 
/ (root) ext3 partition
/swap partition
ntfs partition

---

### Post by eNdeRam on 2009-01-26
thanks for your help

---

