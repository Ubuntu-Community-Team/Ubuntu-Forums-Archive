---
title: "Disk partitioner - I don't want a new partition"
date: 2009-01-01
forum: Installation &amp; Upgrades
---

### Post by yosepht on 2009-01-01
I am trying to install 8.10 and the Partitioner does not give me the
option to choose the partition I want to use. I already have four 
partitions on the drive and I want to reuse one of them. I do not
want to resize XP at this time.Is there a way around this or Ubuntu
does what Ubuntu wants?
                                    thank for you help
                                            :popcorn:

---

### Post by RichardRicardo on 2009-01-01
Just choose the manual option. In the next screen you will have the option to format a current partition.

---

### Post by prshah on 2009-01-01
> **yosepht said:**
> Partitioner does not give me the
option to choose the partition I want to use. I already have four 
partitions on the drive and I want to reuse one of them. I do not
want to resize XP at this time.Is there a way around this or Ubuntu
does what Ubuntu wants?

Depends on your partition setup. You can find out more (or post here for detailed explanation) by using the below command from a terminal (Applications-Accessories-Terminal)```
sudo fdisk -l
mount
``` This will list your current partition structure and mount status.

If any of the partitions are "mounted" you cannot make any structural changes to the partition table. Typically, if you already have a version of Ubuntu installed, at least the swap partition will be activated.

As a separate issue, if you already have four PRIMARY partitions, you cannot create any more. You need to then delete one PRIMARY partition, create an EXTENDED partition, and then create further LOGICAL partitions within that extended partition.

In both cases, we can give more detailed advice if we know the existing structure of your partitions (using the fdisk -l command). Please post back with that information.

---

