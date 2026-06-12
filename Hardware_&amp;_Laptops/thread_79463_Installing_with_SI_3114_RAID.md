---
title: "Installing with SI 3114 RAID"
date: 2005-10-20
forum: Hardware &amp; Laptops
---

### Post by Zuhaib on 2005-10-20
Hi all, 
Well i just happen to build a new system with the ASUS A8N-SLI motherboard, and one of the things it comes with is the Silicon Image Sil 3114 Raid  controller, which i have setup with my two 120GB SATA drives.  The problem is, on install it shows both drives, not the single RAID drive.  And this is a problem as i already have Windows Xp install in the same RAID drive and wish to dual boot.
So i am wondering if there are drivers or a work around as to how to get Ubuntu to show the RAID drive so i can install it on the raid drive.

I do have a single 40GB IDE drive, but i dont really want to go that route as doing the boot loader would be hell (i would have to install Linux on 40 GB, set BIOS to load 40GB drive first, install Si RAID drivers and pray it sees windows, setup Lilo/Grub to have a windows xp options and then it should work but then i still dont have linux on the SATA drives which sucks)
Thanks.

---

### Post by M_Cheevy on 2005-12-14
Zuhaib,

Don't know if you gave up on this or not yet but...
[https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto)
Has everything you need to know to get it going.

---

