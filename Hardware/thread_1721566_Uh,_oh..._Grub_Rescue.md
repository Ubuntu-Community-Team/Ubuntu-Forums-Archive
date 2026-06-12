---
title: "Uh, oh... Grub Rescue?"
date: 2011-04-04
forum: Hardware
---

### Post by Common_Sense on 2011-04-04
My Asus EEE PC 1000 has that error that's going around. PC crashed and during restart, I see this:

error: unknown filesystem.
grub rescue>

I booted off a disk so that I can retrieve some of my files before I reinstall. I have two drives and it cannot see the one that I was using prior to the crash. How do I fix this unknown filesystem error or how can I retrieve my inaccessible files?
 Thanks! :D

---

### Post by garvinrick4 on 2011-04-04
In the Live Cd what does this say:
```
sudo fdisk -l
``` (lower case L)

---

### Post by Common_Sense on 2011-04-12
Sorry for responding so late. My other computer crashed with a similar error to my eee pc. I'll deal with that later, right now I need the Netbook running. I'm running off of the disk so here you go:

> 
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000870ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         933     7490560   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2             933         981      387073    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda5             933         981      387072   82  Linux swap / Solaris

Disk /dev/sdb: 64.6 GB, 64558448640 bytes
255 heads, 63 sectors/track, 7848 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000dd698

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7523    60426240   83  Linux
/dev/sdb2            7523        7849     2616321    5  Extended
/dev/sdb5            7523        7849     2616320   82  Linux swap / Solaris
ubuntu@ubuntu:~$


Something is very wrong....

---

