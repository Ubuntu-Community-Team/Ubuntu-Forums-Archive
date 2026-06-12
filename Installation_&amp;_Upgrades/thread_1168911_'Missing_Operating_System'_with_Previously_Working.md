---
title: "'Missing Operating System' with Previously Working Dual Boot"
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by bedo815 on 2009-05-24
I have a Ubuntu/XP dual boot configuration (using GRUB) with three separate hard drives - two 250 gb drives in RAID 1 for Windows and a 160 gb drive for Ubuntu.

This was all working fine until I (foolishly) offered to help a friend recover some files from a corrupt Vista drive.  After plugging the drive in and starting up, I apparently defaulted to booting off of the Vista drive, which crashed my machine.  Ever since, I have had the following issue...

When I attempt to boot off of the Ubuntu drive, I get 'Missing Operation System'.  Booting directly off of the XP drives still works fine (luckily!).  From reading around on various threads, I've seen that this problem is usually caused by issues with the GRUB installation on the MBR of the Linux drive (?).  Most people suggest trying to reinstall GRUB or manually editing the config file from the Ubuntu LiveCD.

So, I popped in my LiveCD and mounted the Ubuntu drive (which oddly shows up as '41.1 MB Media').  When I tried to take a look at the contents of the drive, I received a bunch of 'Input/Output' errors:

```
ubuntu@ubuntu:/media/disk$ ls -latr 
ls: cannot access home: Input/output error
ls: cannot access srv: Input/output error
ls: cannot access initrd.img.old: Input/output error
ls: cannot access root: Input/output error
ls: cannot access tmp: Input/output error
ls: cannot access boot: Input/output error
ls: cannot access proc: Input/output error
ls: cannot access sys: Input/output error
ls: cannot access opt: Input/output error
ls: cannot access etc: Input/output error
ls: cannot access media: Input/output error
ls: cannot access var: Input/output error
ls: cannot access mnt: Input/output error
ls: cannot access lib: Input/output error
ls: cannot access sbin: Input/output error
ls: cannot access vmlinuz: Input/output error
ls: cannot access initrd: Input/output error
ls: cannot access cdrom: Input/output error
ls: cannot access dev: Input/output error
ls: cannot access initrd.img: Input/output error
ls: cannot access bin: Input/output error
ls: cannot access vmlinuz.old: Input/output error
ls: cannot access usr: Input/output error
total 20
l?????????  ? ?    ?        ?                ? vmlinuz.old
l?????????  ? ?    ?        ?                ? vmlinuz
d?????????  ? ?    ?        ?                ? var
d?????????  ? ?    ?        ?                ? usr
d?????????  ? ?    ?        ?                ? tmp
d?????????  ? ?    ?        ?                ? sys
d?????????  ? ?    ?        ?                ? srv
d?????????  ? ?    ?        ?                ? sbin
d?????????  ? ?    ?        ?                ? root
d?????????  ? ?    ?        ?                ? proc
d?????????  ? ?    ?        ?                ? opt
d?????????  ? ?    ?        ?                ? mnt
d?????????  ? ?    ?        ?                ? media
d?????????  ? ?    ?        ?                ? lib
l?????????  ? ?    ?        ?                ? initrd.img.old
l?????????  ? ?    ?        ?                ? initrd.img
d?????????  ? ?    ?        ?                ? initrd
d?????????  ? ?    ?        ?                ? home
d?????????  ? ?    ?        ?                ? etc
d?????????  ? ?    ?        ?                ? dev
l?????????  ? ?    ?        ?                ? cdrom
d?????????  ? ?    ?        ?                ? boot
d?????????  ? ?    ?        ?                ? bin
drwx------  2 root root 16384 2008-09-30 19:15 lost+found
drwxr-xr-x 21 root root  4096 2009-02-19 04:48 .
drwxr-xr-x  4 root root   120 2009-05-24 19:01 ..

```Output of fdisk is as follows:

```
ubuntu@ubuntu:/media/disk$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           5       40131    6  FAT16
/dev/sda2               6       38914   312528896    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11261126

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30399   244179936    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11261126

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30399   244179936    7  HPFS/NTFS

Disk /dev/sdd: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x746c8107

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       24792   199141708+   7  HPFS/NTFS

```sda is the Ubuntu drive, sdb and sdc are the two XP drives and sdd is a separate media drive.

Any help here is greatly appreciated - is this salvageable?  I am just about to give up and reinstall Ubuntu from scratch, but would like to keep my existing installation if at all possible.  Thanks very much in advance for any help!

---

### Post by presence1960 on 2009-05-24
according to your sudo fdisk -l output your sda drive does not have a linux filesystem on it. It has FAT16 and NTFS-definitely not Linux! Maybe you somehow overwrote the Linux partition(s).

---

### Post by bedo815 on 2009-05-24
Ah... Yes, thank you!  Not quite sure how that happened.

---

### Post by cwsnyder on 2009-05-24
Again, as you were already told, you are going to have to re-install GRUB.

It might be simplest to simply remove the 'Ubuntu' drive, sda.  Your actual Ubuntu drive, according to your description of the original installation, is on sdd.  sda is simply the GRUB boot installation.

If you can get into sdd and the /boot/grub directory, look at the information there on how GRUB views the drives for booting into Ubuntu.

I am not a GRUB expert, but you should be able to get into GRUB by entering the Gnome Terminal and simply typing 'grub' from the Live CD, then use one of the standard GRUB tutorials to re-install GRUB.

---

### Post by presence1960 on 2009-05-24
actually **_NONE of your disks-sda, sdb, sdc or sdd are showing a Linux filesystem!_** I don't know how that happened because you say you installed Ubuntu. If that installation was overwritten you may be able to recover using testdisk. But I am not the one to instruct you on that!

---

