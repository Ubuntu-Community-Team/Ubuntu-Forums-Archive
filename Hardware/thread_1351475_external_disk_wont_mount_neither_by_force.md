---
title: "external disk wont mount neither by force"
date: 2009-12-10
forum: Hardware
---

### Post by fcarramate on 2009-12-10
Hi all,


My external WD 500GB wont mount. on neither my systems windows XP, Ubuntu Hardy or Jaunty but it mounts at my work on windows XP.

The disk is ntfs formated, one partition.


Please the following commands output. The first command blocks when analysing the sdb device (witch is my external disk)

```
[FONT="Courier New"]fausto@desk:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001024d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6498    52195153+   7  HPFS/NTFS
/dev/sda2            6499       19457   104093167+   f  W95 Ext'd (LBA)
/dev/sda5            6499       16971    84124341    7  HPFS/NTFS
/dev/sda6           16972       17014      345366   82  Linux swap / Solaris
/dev/sda7           17015       19457    19623366   83  Linux
^C
fausto@desk:~$ ls -l /dev/sd*
brw-rw---- 1 root disk 8,  0 2009-12-10 19:25 /dev/sda
brw-rw---- 1 root disk 8,  1 2009-12-10 19:25 /dev/sda1
brw-rw---- 1 root disk 8,  2 2009-12-10 19:25 /dev/sda2
brw-rw---- 1 root disk 8,  5 2009-12-10 19:25 /dev/sda5
brw-rw---- 1 root disk 8,  6 2009-12-10 19:25 /dev/sda6
brw-rw---- 1 root disk 8,  7 2009-12-10 19:25 /dev/sda7
brw-rw---- 1 root disk 8, 16 2009-12-10 21:09 /dev/sdb
fausto@desk:~$ [/FONT]
```


Any help would be appreciated since I have no idea whats happening...

thanks :)

---

### Post by Fafler on 2009-12-11
/dev/sdb doesn't have a partition table. That not necessarily bad, but it could also indicate that something has overwritten the partition table.

What does
```
mount /dev/sdb /some/folder
```
give?

There are some Windows tools to restore data from broken filesystems. Thats probably you best bet, if the partition table is bad.

---

### Post by fcarramate on 2009-12-11
Hi,

thanks for you reply :)

When I plug the disk, /dev/sdb is listed...but i had to wait for 4minutes to get the device recognized in /dev/sdb1.

then i was able to mount it using:
```
sudo mount -t ntfs-3g /dev/sdb1 /media/WD500/
```
the output was nothing and the disk was well mounted :) then i've copyed some files and opened them from disk. that was OK!

but when I try to access some files (with 2days that i backedup from workplace) it gives me an "Input/output error".


I though formating the disk, but it would take too long to execute a complete format (+/- one week from my calcs). i've already (some weeks early) tried quick format but it always come to this behavior...

Its not power source issue because the disk has its own external power source (the power does not come from USB)



I would like to solve this issue without windows XP.
any ideias, procedures to debug?


thanks in advance,
Fausto

---

### Post by Fafler on 2009-12-12
It could still be the power supply. I have seen that before. If you possible can, try installing the disk internally. That would also rule out the entire USB part.

---

### Post by jacobs444 on 2009-12-12
could also be a failing disk. Just my 2 cents.

---

### Post by fcarramate on 2009-12-12
Hi, 

I cant take out the disk without lose warranty.

I tryed to plug it on "Mom's" desktop and it went very fine, like it did at work place...
... the problem seems to be only in my systems :S


does anyone know if there is any data (like serial number, sectors, size of sectors...) that Hardy, Jaunty (and windows XP) records for future use? and it is possible if that data is some how conflicting with new collected that each time i plug the disk?


Fausto

---

