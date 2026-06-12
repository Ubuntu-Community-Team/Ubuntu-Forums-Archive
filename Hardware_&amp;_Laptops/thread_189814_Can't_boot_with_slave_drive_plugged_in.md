---
title: "Can't boot with slave drive plugged in"
date: 2006-06-05
forum: Hardware &amp; Laptops
---

### Post by mrmcd on 2006-06-05
Hello,
Using dapper drake RC 6.06.

I Set up a dual boot on one drive and things went flawless.  I added a slave drive I use for windows into the machine, and Ubuntu will not boot.  If I unplug the drive, Ubuntu boots fine.  

Does anyone have ideas how to fix or what the problem is?

It freezes up on "Waiting for root file system" and then drops to a terminal and says this:
```

...
Uncompressing Linux... Ok, booting the kernel.
ALERT! /dev/sda5 does not exist.  Dropping to a shell!
BusyBox v1.01 (Debian 1:1.01-4ubuntu3) Built in shell(ash)
...
/bin/sh: can't access tty; job control turned off

```


The partitions/drive scheme are somwhere along the lines of:
sda1 = ntfs / windows partition
sda2 = boot
sda3 = swap
sda4 = logical, for sda5 and sda6
sda5 = home
sda6 = 2gB of fat32 for transferring data between linux/win

*note: this is all the partitions on the main, bootable master drive

The slave drive is just one NTFS partition

Any help appreciated, thanks

---

### Post by mrmcd on 2006-06-06
Figured out the problem when listing /dev/sd* in the terminal.
sdb (which should have been the slave drive) showed 7 partitions and sda (which should have been the master drive) showed 2 partitions.  This was obviously wrong since the slave has a single NTFS partition and the master has 6 (1 NTFS, 1 swap, 1 boot, 1 logical with an ext3 and a FAT32 under it).  

Noting this, I switched the SATA cables for the drives on the motherboard and everything booted normal, master partitions as /dev/sda* and slave partitions as /dev/sdb*

I still do not know why it mattered which cable was plugged where on the motherboard, but users of intel P4 desktop motherboards should keep this in mind if the same problem ever happens.

---

