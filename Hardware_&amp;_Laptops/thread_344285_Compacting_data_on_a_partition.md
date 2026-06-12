---
title: "Compacting data on a partition"
date: 2007-01-22
forum: Hardware &amp; Laptops
---

### Post by detinith on 2007-01-22
hullo, i've been trying to get this to work for a couple hours to no avail. i want to shrink my ntfs partition with windows on it while expanding my linux partition, and i've come up against a wall.

i've tried quite a few free defragmentation programs, and i still cant seem to get it. all in all, i want that bit of blue to join the rest of the blue, but after 4 consecutive defrag attempts on microsofts alone, along with single attempts by other third-party programs, refuses to budge. my linux partition is dangerously full and i need to shrink this and expand on ext3 else i wont be able to do anything on my linux one :)

[IMG]http://img404.imageshack.us/img404/8497/untitled2so.jpg[/IMG]

if it is at all related, i'm using gparted 0.3.3 to resize the partitions. i've already used it a bunch of times before and i like it.

anyone know of a program that could just compact the data on this as much as possible so i can comfortably take off of the end of the partition to put into ext3? or would gparted handle that?

---

### Post by logos34 on 2007-01-22
Try this: In windows go into control panel>system and disable hibernation and swap/virtual memory.  It could also be some third-party software program, in which case you'll have to uninstall it and then reinstall after you shrink the partition.

---

