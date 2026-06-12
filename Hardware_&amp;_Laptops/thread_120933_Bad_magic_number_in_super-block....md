---
title: "Bad magic number in super-block..."
date: 2006-01-23
forum: Hardware &amp; Laptops
---

### Post by AlexanRO on 2006-01-23
I just added a 10GB hdd to my box, formatted it as ext2, then converted it to ext3 using the  tune2fs command. Then just to confirm that evertything was done properly (or so I perceived) I entered the following command:

```
root@ubu-dtc:/sbin # ./fdisk -l /dev/hdb



Disk /dev/hdb: 10.0 GB, 10005037056 bytes

16 heads, 63 sectors/track, 19386 cylinders

Units = cylinders of 1008 * 512 = 516096 bytes



   Device Boot      Start         End      Blocks   Id  System

/dev/hdb1               1       19386     9770512+  83  Linux
``` 

The strangest thing happens now when I boot, I get the following error: 

fsck failed! Bad magic number in super-block while trying to open /dev/hdb1

My response of course is -- :confused:  Huh?!

It then prompts me to correct it manaually or enter ctrl +d to continue

Here is what I tried

```
root@ubu-dtc:/home/alexanro # mount /dev/hdb1

mount: /dev/hdb1 already mounted or /sas busy

root@ubu-dtc:/home/alexanro # umount /dev/hdb1

umount: /dev/hdb1: not mounted
``` 

 :confused: unable to mount it because it is busy, however, unable to unmount because it is not mounted to begin with?

Next I tried 

```
root@ubu-dtc:/home/alexanro # debugfs /dev/hdb1

debugfs 1.35 (28-Feb-2004)

/dev/hdb1: Bad magic number in super-block while opening filesystem

debugfs:
``` 

yup mm , hmmm I already know that, then a little voice said to do this 

```
root@ubu-dtc:/home/alexanro # /sbin/./fsck -a /dev/hdb1

fsck 1.35 (28-Feb-2004)

fsck.ext3: Bad magic number in super-block while trying to open /dev/hdb1

/dev/hdb1:

The superblock could not be read or does not describe a correct ext2

filesystem.  If the device is valid and it really contains an ext2

filesystem (and not swap or ufs or something else), then the superblock

is corrupt, and you might try running e2fsck with an alternate superblock:

    e2fsck -b 8193 <device>
``` 

OK so now I am feeling like  :mad: what the fsck is going on ?!?!

so before I start over (contending that I must have missed some miniscule, nevertheless, critical element)  I did the following:


```
root@ubu-dtc:/home/alexanro # fdisk -l



Disk /dev/hda: 20.0 GB, 20020396032 bytes

255 heads, 63 sectors/track, 2434 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes



   Device Boot      Start         End      Blocks   Id  System

/dev/hda1   *           1          16      128488+  83  Linux

/dev/hda2              17        2389    19061122+   f  W95 Ext'd (LBA)

/dev/hda5              17          78      497983+  83  Linux

/dev/hda6              79        1051     7815591   83  Linux

/dev/hda7            1052        1173      979933+  83  Linux

/dev/hda8            1174        1902     5855661   83  Linux

/dev/hda9            1903        2024      979933+  83  Linux

/dev/hda10           2025        2267     1951866   83  Linux

/dev/hda11           2268        2389      979933+  82  Linux swap / Solaris



Disk /dev/hdb: 10.0 GB, 10005037056 bytes

16 heads, 63 sectors/track, 19386 cylinders

Units = cylinders of 1008 * 512 = 516096 bytes



   Device Boot      Start         End      Blocks   Id  System

/dev/hdb1               1       19386     9770512+  83  Linux



Disk /dev/hdc: 100 MB, 100663296 bytes

64 heads, 32 sectors/track, 96 cylinders

Units = cylinders of 2048 * 512 = 1048576 bytes



   Device Boot      Start         End      Blocks   Id  System

/dev/hdc4   *           1          96       98288    6  FAT16
``` 

 :confused:  How do I fix it before I run out of space on my 20GB hdd?

It is obvious that I know enough to be dangerous. On a side note I have sucessfully completed this  procedure before on another box, but perhaps my memory is out of sync.  Nonetheless, I could use some help  determining where in the process the oversight took place.  Will someone please refresh my memory?

yr2alex

---

