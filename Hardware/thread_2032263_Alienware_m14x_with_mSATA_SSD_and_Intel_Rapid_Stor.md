---
title: "Alienware m14x with mSATA SSD and Intel Rapid Storage - How to install Ubuntu?"
date: 2012-07-23
forum: Hardware
---

### Post by sjrp on 2012-07-23
Hey everyone!

I've bought a new Alienware M14xR2. And I'm really happy with it. The only thing that bothers me is when trying to install Ubuntu 12.04 (I want too dualboot with Windows).

The laptop has one 7200rpm HDD plus one SSD for caching (32GB). The caching is working with the so called Intel Rapid Storage Technology.

When rebooting into an Ubuntu Live USB and trying to partition the hdd, I can only see the empty SSD in the partitionlist. I can't choose to install anything on the "normal" hdd, which is, of course, what I want.

I tried the alternate ubuntu image and disabled raid via the installationmenu (and in bios). I was then able to see the normal hdd, but the installer couldn't do any partitioning on it because of some error. Then I tried to make the msata ssd to just a normal storage device via Intel Rapid Storage menu that appears when starting the computer (before the bootscreen). Once again I tried the alternate installer, and this time it worked! However it broke my windows installation instead, and grub didn't even list it.

After that I had to reinstall everything, and reset the computer to factory setting.
So the question is, how do I install Ubuntu 12.04 alongside Windows on an Alienware with one hdd and one cache ssd (mSATA)? AND does the caching technology work with linux?

Sorry for long post, but I thought I might aswell tell you the whole story to save you some time asking questions instead.

Please help, really want Ubuntu on this machine (have used only Ubuntu for the last 4 years or so)..

---

### Post by Kreaninw on 2012-07-23
I'm not a tech guy, but I think this post should help.

[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/)

I followed the steps above, now my Ubuntu run a lot faster than when I install it via Wubi. My laptop also come with Intel Rapid Storage but I have manage to install Ubuntu just fine. The post above really help.

---

### Post by mattolsensd on 2012-07-26
Same issue. M14xR2 with the "750GB 7,200 RPM SATA + 32GB mSATA Caching  SSD".  Disk Utility and GParted on the Ubuntu Live CD sees it as two  separate drives.  The Ubuntu Installer only sees the SSD cache.

root@ubuntu:~# fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x306e35a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
Partition 1 does not start on physical sector boundary.
/dev/sda2   *       81920    21467135    10692608    7  HPFS/NTFS/exFAT
/dev/sda3        21467136  1465141247   721837056    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xba000000

Disk /dev/sdb doesn't contain a valid partition table

> So the question is, how do I install Ubuntu 12.04 alongside  Windows on  an Alienware with one hdd and one cache ssd (mSATA)? AND  does the  caching technology work with linux?


If the caching won't work with linux, can I still use it on Windows or  will I have to disable it in the firmware for Ubuntu to run?  I'm going  to try disabling acceleration in the IRST options, installing Ubuntu,  recovering the Window boot loader / MBR, then turning the acceleration  back on after Ubuntu is installed...

---

### Post by sjrp on 2012-07-27
> **mattolsensd said:**
> Same issue. M14xR2 with the "750GB 7,200 RPM SATA + 32GB mSATA Caching  SSD".  Disk Utility and GParted on the Ubuntu Live CD sees it as two  separate drives.  The Ubuntu Installer only sees the SSD cache.

root@ubuntu:~# fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x306e35a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
Partition 1 does not start on physical sector boundary.
/dev/sda2   *       81920    21467135    10692608    7  HPFS/NTFS/exFAT
/dev/sda3        21467136  1465141247   721837056    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xba000000

Disk /dev/sdb doesn't contain a valid partition table



If the caching won't work with linux, can I still use it on Windows or  will I have to disable it in the firmware for Ubuntu to run?  I'm going  to try disabling acceleration in the IRST options, installing Ubuntu,  recovering the Window boot loader / MBR, then turning the acceleration  back on after Ubuntu is installed...
Maybe that's the way to go. Please let me know how that worked out for you. I've been thinking of doing the same thing myself. But it's really boring if the caching doesn't work with Linux. I mean, you bought it because you wanted that extra performanceboost.. :(

---

