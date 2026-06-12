---
title: "[SOLVED] Hard disks auto rearranging"
date: 2008-06-28
forum: Hardware
---

### Post by Ancibit on 2008-06-28
Hi there, I have this problem that I don't quite understand with my hard disks that seem to change their ordering on their own. I'm using Ubuntu Server Hardy Heron. The first hard disk is regular ATA, and is where the OS is stored. The other 2 are SATA and just mirror data. I'm worried about the consistency of this problem because I want to mount the disks in /etc/fstab.

```
$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60802   488386583+  ee  EFI GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488386583+  ee  EFI GPT

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d55c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        4655    37384192    7  HPFS/NTFS
/dev/sdc2            4656       10733    48821535   83  Linux
/dev/sdc3           14107       14593     3911827+   5  Extended
/dev/sdc5           14108       14593     3903795   82  Linux swap / Solaris

```

The weird thing is, the root directory is stored on sda2 as shown in fstab, but is revealed as sdc2 when I boot into the OS.

I'm not exactly sure what to do, but I have a few guesses. Does it have something to do with the data disks being using GPT? Deleting drives and restoring a backup or reinstalling is completely fine (but I'd rather leave those as last resorts). What should I do? Any help appreciated. :)

---

### Post by lswb on 2008-06-29
Write you fstab to mount by uuid and the order that disks are assigned device names won't matter. It seems that with the release of hardy this has become an occasional issue, I wonder if it's because of the change to the upstart init system or maybe because of the disk driver changes that were made. At any rate, using uuid instead of device eliminates the problem. You can find the uuid by either running

  sudo blkid

in a terminal, or look in the directory /dev/disk/by-uuid.

Then in fstab, instead of the first column being /dev/sda1, use 
  UUID=xxxLongHexUUIDforDiskxxxxxxxx

---

### Post by Ancibit on 2008-06-29
Ah! Thanks, you're a lifesaver!

---

