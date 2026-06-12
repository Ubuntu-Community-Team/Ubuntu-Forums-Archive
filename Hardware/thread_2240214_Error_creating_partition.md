---
title: "Error creating partition"
date: 2014-08-18
forum: Hardware
---

### Post by lads on 2014-08-18
I am trying to create a new partition in a free slot of an hard drive using the Gnome Disk utility (on 14.04). I always get the message below:

   >  Error creating partition on /dev/sda: Command-line `parted --align optimal --script "/dev/sda" "mkpart logical ext2 119947MiB 225767517695b"' exited with non-zero exit status 1: Error: You requested a partition from 126GB to 226GB. The closest location we can manage is 126GB to 226GB. (udisks-error-quark, 0)

What can be the cause of this? And can it be solved?

---

### Post by yancek on 2014-08-18
> What can be the cause of this? And can it be solved? 		

Probably but not likely with the information you have posted.  You apparently have Ubuntu 14.04 installed as the only operating system on this computer but you haven't indicated how many drives/partitions you have.  You could start by posting the output of:  sudo fdisk -l(Lower Case Letter L in the command).  Also, the output of:  df -h could be useful.

---

### Post by lads on 2014-08-20
Here's a screen capture detailing this hard disk, with the partition at cause selected:

[IMG]http://i.stack.imgur.com/9GYMf.png[/IMG]

And the output from fdisk:

```
$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x15561cf8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    40646655    20322304   27  Hidden NTFS WinRE
/dev/sda2   *    40646656   245634937   102494141   83  Linux
/dev/sda3       245649976   976771071   365560548    f  W95 Ext'd (LBA)
/dev/sda5       450439168   976771071   263165952    7  HPFS/NTFS/exFAT
/dev/sda6       440952183   450430469     4739143+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

Thank you for reading.

---

### Post by anchitsingh9 on 2014-08-20
try gparted, see if it could make any difference

---

### Post by yancek on 2014-08-20
Are you using the Gnome Disk Utility from the installed Ubuntu?  Might work better if you tried it from a DVD/flash drive with Ubuntu or some other Linux which has GParted on it.  I've never used the utility you refer to so can't offer any advice on that.

---

### Post by lads on 2014-08-21
Regarding GParted, I am trying to create an encrypted partition and as far as I know this can only be made with the [Gnome Disk Utility]("https://help.ubuntu.com/community/EncryptedFilesystemsOnRemovableStorage").

But I am happy to follow alternative instructions.

---

### Post by lads on 2014-08-21
Ok, I was able to do what I wanted using both programmes:

1. Created a new, non-encrypted, ext4 partition in the unallocated space with GParted.

2. With the Disk Utility, formatted the new partition with LUKS, following the [instructions at the wiki]("https://help.ubuntu.com/community/EncryptedFilesystemsOnRemovableStorage#Encrypting_an_existing_partition").

This is not a solution to the problem, which is likely a bug with the Disk Utility.

---

