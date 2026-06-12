---
title: "can't reinstall Hardy, 3 partitioners unusable"
date: 2008-12-09
forum: Installation &amp; Upgrades
---

### Post by lovestopsfear on 2008-12-09
i have Vista and Intrepid on my system and want to do a clean installation of Hardy to replace Intrepid.... because lots of stuff went buggy with Intrepid and i can't find solutions. 

i backed up everything on the partitions with Intrepid and then when i went to install Hardy, the partitioner gives me only the option to use the entire disk (160GB). i tried gparted, qtparted, and PartitionMagic in Vista to attempt to fix "clean up" or reset the partitions. 

qtparted returns the error "Can't have a partition outside the disk"  Segmentation Error.

gparted shows the entire hard drive as if its unallocated. i can't seem to do anything with gparted

Partition Magic returns an error because it won't run in Vista.

i'd like to avoid backing up everything, wiping the entire disk and starting over. can anyone explain what's happening here? does anyone have any bright ideas?

thanks in advance!

i'm running a Dell Inspiron 1521  with AMD x64

---

### Post by psusi on 2008-12-09
Post the output of sudo fdisk -lu

---

### Post by Mark Phelps on 2008-12-10
How did you install Intrepid in the first place?  Was it inside Vista, using WUBI?

The Linux-based partitioners should at least see Ext3 partitions -- if you installed Intrepid in its own partition.

Please run the fdisk command as indicated and post the results here.

---

