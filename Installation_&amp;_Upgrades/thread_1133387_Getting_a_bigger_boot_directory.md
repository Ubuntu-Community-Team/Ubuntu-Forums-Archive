---
title: "Getting a bigger /boot directory"
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by fkrogh on 2009-04-22
I'm a bit confused and I'm hoping some kind soul will help untangle
this mess.

I would like to make by boot partition bigger.  I was used to gentoo
and made it way too small for Ubnuntu.  I don't care where /boot ends
up as long as I can put something in /boot/grub/menu.lst that enables
it to be found.  Data on my system is at the bottom.

Will the following work?
cp -pr /boot  /bootnew
Using fdisk change the bootable drive to sda5 and remove the flag from sda1.
Change menu.lst to use (hd0,4) instead of (hd0,0)
Remove /dev/sda1 from /etc/fstab
mv /bootnew /boot

If this should boot then great, it is good enough.  Maybe later I
could use a different name /dev/sda1 in fstab.


If someone has a better idea I'd be willing to boot from a live CD and
run gparted.  But just what I can move and how is beyond me.  If
someone tells me to forget this and just do a fresh install, I will do
this, but this means more work that I am hoping for.

Any suggestions would be most welcome.
Many thanks,
    Fred


======= Pertinent lines from /etc/fstab
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=5dc6b6b2-d51a-4ba0-9d72-bf2e7b093901 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=ee81236c-bd4e-4533-be8d-6aa1b61df392 /boot           ext2    noatime         0       2

========== Partitions from /proc/partitions
   8     0  488386584 sda
   8     1      56196 sda1
   8     2     987997 sda2
   8     3     104422 sda3
   8     4          1 sda4
   8     5   97667136 sda5

========== Partitions from fdisk -lu
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63      112454       56196   83  Linux
/dev/sda2          112455     2088449      987997+  82  Linux swap / Solaris
/dev/sda3   *     2088450     2297294      104422+  83  Linux
/dev/sda4         2297295   197631629    97667167+   5  Extended
/dev/sda5         2297358   197631629    97667136   83  Linux

/dev/sda1   *           1           7       56196   83  Linux
/dev/sda2               8         130      987997+  82  Linux swap / Solaris
/dev/sda3   *         131         143      104422+  83  Linux
/dev/sda4             144       12302    97667167+   5  Extended
/dev/sda5             144       12302    97667136   83  Linux

=========  Lines from /boot/grub/menu.lst
title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-23-generic root=UUID=5dc6b6b2-d51a-4ba0-9d72-bf2e7b093901 ro quiet splash
initrd		/initrd.img-2.6.24-23-generic

=========  Results from running df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5             96132940  14824016  76425568  17% /
varrun                 1004780       244   1004536   1% /var/run
varlock                1004780         0   1004780   0% /var/lock
udev                   1004780        64   1004716   1% /dev
devshm                 1004780         0   1004780   0% /dev/shm
lrm                    1004780     39792    964988   4% /lib/modules/2.6.24-23-generic/volatile
/dev/sda1                52659     18231     31619  37% /boot

---

### Post by cariboo on 2009-04-22
With the size of hard drives these days, there is no need to split / into a bunch of small partitions. Back in the day when hard drive sizes where < 1Gb it was a good idea to split the partition over several drives.

I typically create a / partition of 5-6 Gb on a desktop system and 25Gb on a server.

---

