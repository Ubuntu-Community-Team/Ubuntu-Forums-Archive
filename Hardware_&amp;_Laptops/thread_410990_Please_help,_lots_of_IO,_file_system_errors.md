---
title: "Please help, lots of I/O, file system errors"
date: 2007-04-16
forum: Hardware &amp; Laptops
---

### Post by Giltine238 on 2007-04-16
First, a little about my setup:

Intel Pentium IV 2,4 GHz CPU, Abit IS7-E M/B, Nvidia Geforce FX 5600 GPU, 80 GB Maxtor HDD (SATA), 320 GB Western Digital HDD (SATA), Dual boot Windows XP and Ubuntu 6.10

And now the problem(s):

During bootup I got a lot of fsck errors like:

[xxx.xxx] (unix time i suppose) ata1: command 0xc8 timeout, stat 0x59 host_stat 0x61
[xxx.xxx] ata1: translated ATA stat/err 0x59/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[xxx.xxx] Buffer I/O error on device sda2, logical block 4248 (number increases with following errors)

and

/dev/sda2: Attempt to read block from filesystem resulted in short read while reading block 531

/dev/sda2: Attempt to read block from filesystem resulted in short read reading journal superblock

/dev/sda2: Attempt to read block from filesystem resulted in short read while checking ext3 journal for /dev/sda2

Ubuntu gets to the login screen, but it is frozen (the mouse moves but nothing else happens), CTRL-ALT-Backspace results in a permanent black screen.

The strange part (my partition setup):
80 GB Maxtor:
 sda1 : FAT32 Windows partition (32 gb)
 sda2 : ext3 partition (48 gb)

320 GB WD:
 sdb1 : 1 GB Linux swap
 sdb2 : Huge ext3 partition for Ubuntu and data

There are no problems with sdb2 (at least fsck said so), but:
 1. Ubuntu doesn't boot up fully
 2. The partition is not accessible from within Windows (using ext2ifs, I think it might be the cause of problems)
 3. sda2 is alive and well from within Windows

Can anyone help me fixing this mess?

Oh yeah it has been running for about half a year already, haven't had any problems until now

---

### Post by Giltine238 on 2007-04-17
Bumpety bump, here's what I've done:

[LIST]
[*]Ran a diagnostic check on the WD drive - everything is ok
[*]Maxtor HDD SMART doesnt show anything bad either
[*]Booted from Live CD - I can mount sdb2 and sda1 but everything hangs when I touch sda2
[/LIST]

---

