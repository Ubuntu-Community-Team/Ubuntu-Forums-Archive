---
title: "does not start after the version upgrade"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by riccardostocchi on 2009-10-31
Hi to all,

I have a problem with my pc, after the upgrade the system starts and at the time you see the ubuntu logo and the bar on the bottom, a black page appears and says the following things:

One or more of the mounts listed in /etc/fstab cannot yet be mounted:
(ESC for recovery shell)
/: waiting for /dev/disk/by-uuid/9d86cd51-f985-4cb8-b99c-628c328b48a8
/tmp: waiting for (null)
swap: waiting for UUID=c810c88a-48ed-48b3-99a8-aa35251efad1

I asked for an help in the Italian forum, so a user suggest me to check some things and the result is:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x27952795

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14569   117025461   83  Linux
/dev/sda2           14570       14946     3028252+   5  Extended
/dev/sda5           14570       14946     3028221   82  Linux swap / Solaris
ubuntu@ubuntu:~$ ls -la /dev/disk/by-uuid
total 0
drwxr-xr-x 2 root root  80 2009-10-30 20:15 .
drwxr-xr-x 6 root root 120 2009-10-30 20:17 ..
lrwxrwxrwx 1 root root  10 2009-10-30 20:15 9d86cd51-f985-4cb8-b99c-628c328b48a8 -> ../../sda1
lrwxrwxrwx 1 root root  10 2009-10-30 20:15 c810c88a-48ed-48b3-99a8-aa35251efad1 -> ../../sda5
ubuntu@ubuntu:~$

Can someone please help me to fix this problem?

Thank you.

---

### Post by riccardostocchi on 2009-10-31
any idea?

Thanks

---

### Post by riccardostocchi on 2009-10-31
I tried:

ubuntu@ubuntu:~$ sudo mkdir /media/disk
mkdir: cannot create directory `/media/disk': File exists
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /media/disk
mount: /dev/sda1 already mounted or /media/disk busy
mount: according to mtab, /dev/sda1 is already mounted on /media/disk
ubuntu@ubuntu:~$ cat /media/disk/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9d86cd51-f985-4cb8-b99c-628c328b48a8 /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda5
UUID=c810c88a-48ed-48b3-99a8-aa35251efad1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
ubuntu@ubuntu:~$

---

