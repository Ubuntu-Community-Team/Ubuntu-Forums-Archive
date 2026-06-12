---
title: "I/O loaded driver crashes"
date: 2008-10-07
forum: General Help
---

### Post by dnel on 2008-10-07
Hi, I've been using Ubuntu on my PC for a number of years and since 7.10 I've found a number of stability issues that are creeping in. 

Under normal use my PC is stable, it works for as long as you want without any issues but when I try to copy large quantities of data between hard disks I get a kernel panic after a seemingly random amount of progress, somewhere between 1.5GB and 3GB copied usually. It seems less prone to this if I don't multi-task with other programs or if I do the copy operation from a CLI terminal but it doesn't prevent it completely.

I also have a similar problem with my rt61pci wlan card, it works fine under normal operation but if I download files over 1GB sometimes, not always, it will crash the wlan driver which I can recover using rmmod and modprobe to bring it back up. 

These issues seem to be related in that they both involve a lot of i/o and a driver crash. The problem has been less pronounced since upgrading to 8.04 but it hasn't eliminated the problem which suggests to me that it is more likely a software than hardware issue. Can anyone suggest anything I might test to find to source of this problem?

My hardware specs are

Athlon XP 3000+
Asus A7V8X mobo
3x 512MB memory
4x Sata hard disks 
On-board Sata promise raid controller (in non-raid config) 
PCI Maxtor promise Sata 150 controller 

The problem exists also with Pata -> Sata transfers too

TIA
Dave

---

### Post by dnel on 2008-10-07
Also notable that the system crashes transferring files between disks on the same controller and between the two controllers.

I did a memory test today in memtest86 which was clear of errors too.

---

### Post by dnel on 2008-10-09
I've been able to copy over 250GB of data between disks by booting into Knoppix so this is definitely a problem with Ubuntu. The issue only manifests for transfers between disks not copies on the same disk.

---

### Post by fjgaude on 2008-10-09
Time for a bug report, eh?

---

### Post by TeXtonyx on 2008-10-09
Hi, I've only had one problem kind of like this and the culprit was a driver. I see that the 
history of the rt61pci wlan card driver had a problem with the connection timing out.
[http://www.ralinktech.com.tw/data/drivers/2008_0723_RT61_Linux_STA_v1.1.2.2.tar.bz2](http://www.ralinktech.com.tw/data/drivers/2008_0723_RT61_Linux_STA_v1.1.2.2.tar.bz2)   released July 23, 2008
This is the newest driver. Just recently a program from TeXlive worked in Mandriva but
not in Ubuntu. The reason is because the Ubuntu repository supplied a different version
of some file than Mandriva. Check if you can the version of the drivers that are germane
to this problem between the two distros. I think if the above driver is an update to the
driver Ubuntu now uses, and it solves the rt61pci driver crash, then it is more likely that
the problem is driver related, perhaps to the available repository version. I don't see 
this as an intrinsic Ubuntu bug, although it happens while using Ubuntu, if the fix
is to get a newer driver because repository policy doesn't abide by an objective rule for
any distro, how long does it take to become recognized as stable. It cuts both ways.

---

### Post by dnel on 2008-10-09
> **fjgaude said:**
> Time for a bug report, eh?


[https://bugs.launchpad.net/ubuntu/+bug/280825](https://bugs.launchpad.net/ubuntu/+bug/280825)

Filed, thanks :)

---

### Post by j0nny55555 on 2008-11-04
Thank you for posting this and I'd like to let the community know that I am running Ubuntu 8.04.1 on a SATA HD and then have two logical drives setup on a Promise ST EX8650 card and have everything mounted and accessible until I get the "aiee" kernel panic.  As with "dnel", it only causes a problem after large amount or high quantities of data transfer, and since it is a RAID5 store for the second logical drive and a RAID1 mirror for the first logical drive, I don't have any ability to try inner-hd copies to see if that would prevent the problem.
Ubuntu community, please tell me what to do to give you any and all information to get this fixed up (including building Promise's RAID driver from source and modprobing it into place or whatever I have to do - I've done Gentoo and I love Ubuntu and would like to keep using it).
Thanks!

---

