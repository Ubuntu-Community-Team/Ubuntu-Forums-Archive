---
title: "Reformatting Ubuntu"
date: 2008-07-18
forum: General Help
---

### Post by Edigido on 2008-07-18
I'm trying to reformat my hard drive, and get it ready for XP.  There are only a few things that I need to check up on first.

A/ Will there be any reason that any partitions set up through Virtual Machine will still be around?

B/ What special steps must be taken in order to make sure that all of my data is either transfered or saved?  Most of my data is already backed up, but there're a few odds and ends that I'm going to back up tonight.

C/ Will there be any remaining data that will take away from the storage space of XP?  I know that right now, I'm using about 30 gb...but it says I'm using between 80 and 90...so that's bad.

Any ideas that I can get would be very helpful.  Oh, has anyone had any bad luck getting and XP boot disk off Ebay?

---

### Post by Potatoj316 on 2008-07-18
Are you going to dual boot or completly wipe the hard drive and start with a clean install of xp?

---

### Post by mikewhatever on 2008-07-18
Can you post the output of <sudo fdisk -l> and specify which partition/s are going to be formatted.

---

### Post by dislocated on 2008-07-18
Assuming you are wiping Ubuntu off your hard drive with the XP installation:

A) As far as I know, Virtual Machine doesn't create any partitions, so no.

B) If you want to save your data and you are going to let XP install over a reformatted Ubuntu partition, then you are going to have to backup all your data first. XP doesn't provide any means of transferring your Ubuntu data over to its partition.

C) Not quite sure what you mean by these numbers, but if you do a "clean" install of XP, then it will very happily take the whole drive for its own use, regardless of any partitioning you may have done before.

---

### Post by Edigido on 2008-07-18
I'm planning on completely wiping, and going w/ a fresh start in XP

fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by Potatoj316 on 2008-07-18
Then backup everything you could ever possibly want again and boot with the Windows install disk.  You will eventually be asked where to install, tell it to use the whole HD.  You dont have to do any manual formating or partitioning.  It might ask you what filesystem to use, go with NTFS unless you really have a reson to not.

---

### Post by Edigido on 2008-07-18
kk, thanks for your help.  Do Check back, cause something might happen to throw off my plan.

---

