---
title: "Hard Drive reporting incorrect free space"
date: 2008-08-16
forum: Hardware
---

### Post by firstc624 on 2008-08-16
OK this just started happening, or at least i just noticed it.
I was setting up a virtual machine, knowign that my hard drive should have plenty of space since i keep the drive fairly cleaned up. this is also a relatively new install of 8.04, only about a month old.

this is the output of df -H

[code] firstc624@firstc624-laptop:~$ df -H
Filesystem Size Used Avail Use% Mounted on
/dev/sda5 28G 26G 601M 98% /
varrun 1.1G 156k 1.1G 1% /var/run
varlock 1.1G 0 1.1G 0% /var/lock
udev 1.1G 58k 1.1G 1% /dev
devshm 1.1G 25k 1.1G 1% /dev/shm
lrm 1.1G 47M 990M 5% /lib/modules/2.6.24-21-generic/volatile
[code]

and this is the output of fdisk -l

firstc624@firstc624-laptop:~$ sudo fdisk -l
[sudo] password for firstc624:

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95f3457a

Device Boot Start End Blocks Id System
/dev/sda1 1 862 6915072 27 Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2 * 862 4910 32516096 7 HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3 4910 12161 58249800 5 Extended
Partition 3 does not end on cylinder boundary.
/dev/sda5 4910 11859 55823008+ 83 Linux
/dev/sda6 11859 12161 2426728+ 82 Linux swap / Solaris


Does anyone have any idea as to what is going on?

i will try to attach pics to show what i mean.


PS a note to the mods i knwo i posted this in the 64 bit section as well, didn't know which would get a better response.

---

