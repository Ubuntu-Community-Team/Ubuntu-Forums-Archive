---
title: "Partition Problems"
date: 2006-07-20
forum: Hardware &amp; Laptops
---

### Post by ironfistchamp on 2006-07-20
Ok so I have two hard drives both of which are 80GB. On HDA I have a a partition that houses windows and one that is FAT32 for my junk. It is soon to be EXT3. On my other drive I have ReiserFS for Linux and a random FAT32 for more junk. I took all the junk out of the HDB FAT32 partition and stored it in the HDA FAT32 and HDB ReiserFS. I now want to get rid of the HDB FAT32, resivze the Reiser and convert the HDA FAT32. If I didn't make any sense here is a check list :p 

1)Empty hdb5 (FAT32) - Done
2)Delete hdb5 - Error (more on that later)
3)Resize hdb1 (ReiserFS)
4)Put hda2 (FAT32) contents on hdb1
5)Convert hda2 into EXT3

My partition table looks to be of interesting design. Below is a diagram to show you how it looks

HDA
|
|->UNALLOCATED 8Mb
|-> /dev/hda1 EXTENDED
..|
..|-> /dev/hda5 NTFS 29998Mb
|
|-> /dev/hda2 FAT32 46320Mb

hda5 currently has nothing on it. I am only worried about hda2. We can blitz the rest if necessary.

HDB
|
|-> /dev/hdb1 ReiserFS 38876Mb
|-> /dev/hdb2 EXTENDED
..|
..|-> /dev/hdb5 FAT32 34515Mb
..|-> /dev/hdb6 SWAP 2926Mb
  

I need to delete hdb5 and use the space for hdb1. Whenevr I try to delete hdb5 it says "Please unmount any logical partitions having a number higher than 5" I don't understand what is wrong. Can someone help me sort this whole mess out? What are logical partitons and what are these extended bits?

Thanks 

Ironfistchamp

---

### Post by reacocard on 2006-07-20
an extended partition can contain logial partitions. this lets you have more partitions than you could otherwise. since it asks you to unmount any logical partitions with a number higher than 5, it must need you to unmount your swap (hdb6) partition first. if you're using gparted, just right-click hdb6 and choose 'deactivate' to unmount your swap partition.

---

### Post by ironfistchamp on 2006-07-20
Slight problem there as everything for swap is greyed out except information. I am using a live CD so I can't see why it would be in use. Any ideas?

EDIT: Booted normally and unmounted/deactivated the Swap and got rid of that FAT32. How can I create a new swap after deleting the extended bit? I can create the new swap partition but how does linux know it is there? Is there anything specific I need to do? I seems to be called "New Partition #1" not /dev/hdb6 like it used to.

---

### Post by Sef on 2006-07-26
> Is there anything specific I need to do?

When you set up the swap, you set it up as swap, and the computer should pick it up when it is rebooted.

---

