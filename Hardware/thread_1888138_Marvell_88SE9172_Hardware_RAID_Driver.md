---
title: "Marvell 88SE9172 Hardware RAID Driver?"
date: 2011-11-28
forum: Hardware
---

### Post by leekyuh on 2011-11-28
Hi all,

Where can I get Marvell 88SE9172 RAID Driver for Ubuntu 11.10 64-bit for installation?

I just assembled a PC with Gigabyte X79-UD3 S2011 which has a hardware RAID chip: Marvell 88SE9172.
I set two Seagate 1TB's with RAID 1 on BIOS.
CPU is i7 3930K and 16GB RAM with BD-ROM drive.

The problem here is that Ubuntu 11.10 64-bit Alternate CD does not seem to have a driver for Marvell 88SE9172.
When I boot up with the CD, I get stuck at the partitioning stage because no drives are listed in /dev and there's nothing I can do.
If I boot up using Desktop CD, it always stops at around 7 seconds after showing attaching drives.

Marvell homepage only shows the driver for Windows, not for linux.
Windows 7 boot-up disk can load the Marvell RAID driver from my mobo cd and recognize it correctly.

How can I install the Ubuntu 11.10 with RAID 1 using Marvell 88SE9172?

Please help..!

---

### Post by leekyuh on 2011-12-01
Bump..

So there's no way that I can install Ubuntu on my machine with RAID 1 support? :(

---

### Post by SycloneMedia on 2011-12-06
[http://www.setiusa.us/showthread.php?1652-Linux-on-a-Z68-mobo](http://www.setiusa.us/showthread.php?1652-Linux-on-a-Z68-mobo)

that thread might solve your issue. seems that installing from usb might be a problem?

---

### Post by leekyuh on 2011-12-06
Hmm.. thanks. I might try searching Gentoo or CentOS forums go get some hint.
I had tried installing from CD but didn't work for me.

---

### Post by strossel on 2011-12-18
Hi,

I've got the same problem - Ubuntu doesn't recognize RAID 1 on Marvell 88SE9172. I've got Ubuntu installed on a SSD running just fine and now I would like to use a RAID 1 for storage.

Have you found a solution to the problem?

---

### Post by leekyuh on 2011-12-19
Unfortunately, no. 
I didn't have enough time to dig more.. :(

---

### Post by stolpee on 2012-02-23
Yeah, I've got the same issue on that controller...
No mather what I do I can't get Ubuntu to recognize my SSD...
Appearantly people have launched their drives running in AHCI from bios when using SATA 3, but that doesn't make any difference... Actually all modes doesn't make any difference.
 
Tried installing via the other controller on the mobo (SB950?) installation successful, but hangs when trying to boot.
 
Tried installing Ubuntu IN Windows, installation went fine, restarted and nothing, here's a pic: 
[ATTACH]213158[/ATTACH]
 
Did I mention that the drive works fine in Windows? : )

---

### Post by stolpee on 2012-02-23
Seems like a driver for this controller is under developement?

[Wikipedia <-]("http://en.wikipedia.org/wiki/List_of_Marvell_Technology_Group_chipsets#88SE91xx_Chipsets_Linux_support")

How do I look for the driver in the patch log of the latest kernel, I mean, what am I looking for?

[kernel.org]("http://www.kernel.org/")

---

### Post by madbiologist on 2012-05-28
It seems that this device has more than one PCI ID.  Support for one of them (1b4b:917a)  was added in the upstream kernel 3.4, and is under review for 3.3 and  3.2 updates.

Here is the 3.4 kernel patch for reference:

author    Matt Johnson
Fri, 27 Apr 2012 06:42:30 +0000 (01:42 -0500)
committer    Jeff Garzik
Thu, 3 May 2012 18:07:40 +0000 (14:07 -0400)
commit    642d89252201c4155fc3946bf9cdea409e5d263e
tree    f6287317640b23fe34233e4227cb07585f73e471
parent    6868225e3e92399068be9a5f1635752d91012ad5
 
ahci: Detect Marvell 88SE9172 SATA controller
 
The Marvell 88SE9172 SATA controller (PCI ID 1b4b 917a) already worked
once it was detected, but was missing an ahci_pci_tbl entry.

 Boot tested on a Gigabyte Z68X-UD3H-B3 motherboard.

 Signed-off-by: Matt Johnson
Signed-off-by: Jeff Garzik

---

### Post by leekyuh on 2012-05-28
Thanks for the information, madbiologist.

Although I cannot test any more since the server is up and running, if anybody could confirm it is actually working, please let me know so that I can mark this thread as solved.

---

