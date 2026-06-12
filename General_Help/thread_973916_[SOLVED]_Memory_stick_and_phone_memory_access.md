---
title: "[SOLVED] Memory stick and phone memory access"
date: 2008-11-07
forum: General Help
---

### Post by TWO on 2008-11-07
Hello

Since installing Kubuntu Hardy Heron 8.04.1, I've had a host of problems with accessing partitions. When I had installed in April of this year, everything was configured automatically but this version is just giving me a headache!! I've had to use the program **pysdm** to resolve my hard disk partition issues but now accessing the memory stick and internal memory off of my mobile phones is also causing problems.

When I plug them into the USB ports, the PHONE icon appears on the desktop, however on opening them with Konqueror, I am presented with the following error message:

> mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so
 

It's becoming a pain having to log into my Win XP partition just to access my phone memory.

Here are the results of ```
$ fdisk -l
```. This is the result for the phone memory:

> Disk /dev/sdb: 64 MB, 64978944 bytes
8 heads, 16 sectors/track, 991 cylinders
Units = cylinders of 128 * 512 = 65536 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         990       63340+   6  FAT16


Trying to right click on the icon and click 'mount' is not working. I just get that error message.

If anyone can tell me what a 'bad superblock is' and why it is stopping Kubuntu from accessing the drive, and yet not effect XP, I'd be very grateful!

Thanks in advance

TWO

---

### Post by TWO on 2008-11-23
The problem has been resolved.

Basically, it stemmed from a bug that arises from installing Ubuntu via USB method.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/150872](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/150872) is the link to the Launchpad bug.

Installing via the USB created an entry for that medium used, which in turn messed up auto mounting feature in Ubuntu. That's a pretty basic description. Read the link to find out more.

Phew!

:)

---

