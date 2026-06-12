---
title: "Use all space on different hdd"
date: 2008-07-17
forum: General Help
---

### Post by 1205919 on 2008-07-17
Hi

I installed Ubuntu 7.10 on a partition (60GB) on one of two 230GB HDD. As I am in the process of cleaning up data from the partitions on the HDD's (not in use by Ubuntu), I am moving some stuff that I still need to the 60GB partition (Ubuntu).

Because of this the 60GB is getting filled up quite rappidly , but I now sit with lots of space on the other "cleaned" hdd's

What can I do to instruct Ubuntu to automatically start using the available space on the other hdd's/partitions as space becomes available.

The other hdds are in the ext3 (?) file format as I used to have ubuntu installed on them

Thanx

---

### Post by jonian_g on 2008-07-17
Boot with live cd and resize the partition with gparted (System>Admin>Partition Editor).

---

### Post by 1205919 on 2008-07-17
> **jonian_g said:**
> Boot with live cd and resize the partition with gparted (System>Admin>Partition Editor).
thx ill try that

---

### Post by Locutus_of_Borg on 2008-07-17
once the partitions are created in your new drive, and formatted correctly, you should be able to have them mount at /home to use automatically as space

just edit /etc/fstab to mount their locations to /home

add this line:

/dev/sdb1   /home  ext3  defaults,noatime 0 0

change sdb1 to whatever the drive is

---

