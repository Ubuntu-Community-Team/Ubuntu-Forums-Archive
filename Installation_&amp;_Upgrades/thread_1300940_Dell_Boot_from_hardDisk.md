---
title: "Dell Boot from hardDisk"
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by silvate99 on 2009-10-25
Hi...!

... I had loaded the 9.10 Ubuntu in my D610 Dell lap top and I can not boot it from the hard drive, as it show up the following message:

Error: no such device 9a6a3b67-820d-42d0-8f5d-9ba8af0f2fbc

Press any key to continue...

(after any key is pressed)

Grub 1.97 ~beta4

Ubuntu, Linux 2.6.31-14-generic

Ubuntu, Linux 2.6.31-14-generic(Recover mode)

Mem test

Mem test

Windows XP

The recover mode has the same results...

the windowsXP works fine...

...the disk has two partitions, one in ntfs with 50Gb for windows and the rest, 196Gb to Ubuntu...



... in the console of the liveCd(that works)...




ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc961c961

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2           29611       30401     6353707+   5  Extended
/dev/sda3            6375       29610   186643170   83  Linux
/dev/sda5           29612       30401     6345675   82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: file or directory inexistent

Any idea, about what should be???

---

### Post by Mark Phelps on 2009-10-25
Ubuntu 9.10 installs GRUB2 into new installations, which no longer uses menu.lst file.

GRUB2 is a LOT more complicated than legacy GRUB to setup.

See the link below for information:

[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

---

