---
title: "Live CD Partition Editor not recognizing HDD Partitions"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by insanity54 on 2009-06-11
Hello.

I'm trying to upgrade from Hardy to Intrepid. More specifically, I'm trying to use the Intrepid live CD to completely overwrite my root partition, while keeping my /home partition intact. 

I've hit a snag with the Intrepid live CD, when the installation wizard gets to the partition configuration section. The manual partition editor shows my HDD as being completely unallocated, with no partitions whatsoever. 

Here is an output of "sudo fdisk -l" since the results of my googling suggest that the problem is related:

```
xxxx@xxxx:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b9e5d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       48228   387391378+   5  Extended
/dev/sda2           42004       48228    50002312+  83  Linux
/dev/sda3           48229       48352      996030   82  Linux swap / Solaris
/dev/sda4   *       48353       60801    99996592+   7  HPFS/NTFS
/dev/sda5               1       42002   337380970+  83  Linux
xxxx@xxxx:~$ 

```

note: This is a dual-boot system with windoze and Ubuntu 8.04.

Why can't the live CD see my partitions, and is this a bug or is it my fault?

---

### Post by merlinus on 2009-06-11
What does gparted show?  Can you post a screenshot?

---

### Post by insanity54 on 2009-06-11
Hi merlinus, thanks for your reply. Here is a screenshot of GParted.

[[IMG]http://img241.imageshack.us/img241/670/screenshotp.th.png[/IMG]](http://img241.imageshack.us/i/screenshotp.png/)

---

### Post by logos34 on 2009-06-11
> **insanity54 said:**
> 
> [COLOR="Red"]omitting empty partition (5)[/COLOR]

Why can't the live CD see my partitions, and is this a bug or is it my fault?

this had been known to work:
> 
sudo sfdisk -d /dev/sda | sudo sfdisk --force /dev/sda

now run fdisk and/or gparted again

---

### Post by insanity54 on 2009-06-11
Hi logos34 thanks for your reply.

I ran the command in the live CD session and got this:

```

ubuntu@ubuntu:~$ sudo sfdisk -d /dev/sda | sudo sfdisk --force /dev/sda 
Checking that no-one is using this disk right now ...
BLKRRPART: Device or resource busy

This disk is currently in use - repartitioning is probably a bad idea.
Umount all file systems, and swapoff all swap partitions on this disk.
Use the --no-reread flag to suppress this check.

Disk /dev/sda: 60801 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+  48227   48228- 387391378+   5  Extended
/dev/sda2      42003   48227    6225   50002312+  83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda3      48228   48351     124     996030   82  Linux swap / Solaris
		start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda4   *  48352   60800   12449   99996592+   7  HPFS/NTFS
		start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda5          0+  42001   42002- 337380970+  83  Linux
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1            63 774782819  774782757   5  Extended
/dev/sda2     674778195 774782819  100004625  83  Linux
/dev/sda3     774782820 776774879    1992060  82  Linux swap / Solaris
/dev/sda4   * 776774880 976768064  199993185   7  HPFS/NTFS
/dev/sda5           189 674762129  674761941  83  Linux
Successfully wrote the new partition table

Re-reading the partition table ...
BLKRRPART: Device or resource busy
The command to re-read the partition table failed
Reboot your system now, before using mkfs

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)
ubuntu@ubuntu:~$ 

```

I then ran GParted and there is no change.

Was that command meant to be run from my hardy installation?

**EDIT**

I forgot to add the fdisk output. Looks like the part about "omitting empty partition (5)" is gone?

```
xxxx@xxxx:~$ sudo fdisk -l
[sudo] password for xxxx: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b9e5d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       48228   387391378+   5  Extended
/dev/sda2           42004       48228    50002312+  83  Linux
/dev/sda3           48229       48352      996030   82  Linux swap / Solaris
/dev/sda4   *       48353       60801    99996592+   7  HPFS/NTFS
/dev/sda5               1       42002   337380970+  83  Linux
xxxx@xxxx:~$ 

```

---

### Post by logos34 on 2009-06-11
> **insanity54 said:**
> 
**EDIT**

I forgot to add the fdisk output. Looks like the part about "omitting empty partition (5)" is gone?


that's good, but I missed this:

> /dev/sda1               1       48228   387391378+   5  Extended
/dev/sda2           [COLOR="Red"]42004[/COLOR]       48228    50002312+  83  Linux

overlapping partitions (it's showing a primary partition inside an extended (sda1)--either that or the partition # is wrong. 'sda2' should be like sda**6**???)

run testdisk to fix partition table

> sudo apt-get install testdisk

sudo testdisk

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Current_partition_table_status](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Current_partition_table_status)

---

### Post by insanity54 on 2009-06-12
It looks like

```
sudo sfdisk -d /dev/sda | sudo sfdisk --force /dev/sda 
```

Made my windoze installation unable to boot.

At this point I think I'm going to dban and start over.

Thanks to everyone for the help.

---

