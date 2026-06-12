---
title: "fresh install Raid issues."
date: 2010-04-09
forum: Hardware
---

### Post by parlaan on 2010-04-09
I have a new system build, and have recently installed 4 - 1TB hard drives.  I have a 64G SSD as sata0 and I want to raid5 the 4 TB drives.

I have everything set up in my bios, and the live CD on both 10.04 and 9.10 sees the raid5.

I want to install "/" on my SSD, and want to install the raid 5 on "/home"

Problems:

If I use the installer, and try to install it as above, I get a format error on the raid.

If I use the installer, and manually format the raid to ext3, setting the raid to /home with no format option, the system reboots and sits waiting forever for "/home"

I can install the complete package on the SSD, Ignoring the raid and boot the system, and then manually mount the raid.

what am I doing wrong ?  and what is the simplest way to install the system the way I want?  

Thanks in advanced.

---

### Post by parlaan on 2010-04-09
easy fix.

A raid 5 is only compatible with ext2 or ext4.

thanks

---

