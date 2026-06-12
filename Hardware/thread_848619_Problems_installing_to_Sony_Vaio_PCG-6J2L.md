---
title: "Problems installing to Sony Vaio PCG-6J2L"
date: 2008-07-03
forum: Hardware
---

### Post by bboyghost on 2008-07-03
okay, i'm new to linux and was going through the install. at the end,just before it finished an error message popped up saying "error 5 there may be issues with the disk or the hard drive" the disk is fine  which leads me to believe it has something to do with my input output. i read up a bit and saw something on BIOS so i checked mine, didnt see the problem though... also saw something about running terminal and typing in sudo fdisk -l to help the person assisting so i did and heres the info that popped up...

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfc20e3b4

Device Boot Start End Blocks Id System
/dev/sda1 1 11785 94662981 83 Linux
/dev/sda2 11786 12161 3020220 5 Extended
/dev/sda5 11786 12161 3020188+ 82 Linux swap / Solaris
ubuntu@ubuntu:~$



please help as i have no clue what else to do...

---

### Post by bboyghost on 2008-07-03
heres my partition drive set up

ubuntu@ubuntu:~$ cat /proc/partitions
major minor  #blocks  name

   8     0   97685784 sda
   8     1   94662981 sda1
   8     5    3020188 sda5
   7     0     690060 loop0

---

### Post by bboyghost on 2008-07-03
can anyone help?

---

