---
title: "2Xraptor 36GB raid 0 ICH7R"
date: 2006-02-08
forum: Hardware &amp; Laptops
---

### Post by neo571 on 2006-02-08
I have this system: 
Intel Pentium D 820 2.8GHz - 2x512MB DDR2 533MHz
Asus P5LD2 - Leadtek Winfast PX6600TD - 2XRaptor 10000rpm 36.5GB

I tryed install Ubuntu but don't see the raid Disk!Ubuntu see two disk!

Exist a driver that i istall?

---

### Post by bernardfrancois on 2006-02-08
[https://wiki.ubuntu.com/FakeRaidHowto?highlight=%28raid%29](https://wiki.ubuntu.com/FakeRaidHowto?highlight=%28raid%29)

> 
Under Linux, the hardware is seen for what it is, which is simply a multi-channel IDE/SATA controller. What this means is that if you have multiple disks configured as a RAID, Linux sees individual disks. This page describes how to get Linux to see the RAID as one disk, and boot from it. In my case, I use a RAID-0 configuration, but this should also apply to RAID-1 and RAID-5.


There are also other pages on the wiki about raid. Just search there...

---

### Post by BenTyreman on 2006-02-08
Or, use linux software RAID to create the array. Unless you have an expensive RAID card that has fully hardware RAID, you won't have too much of a performance difference. I have a small boot partition on one of the drives, and the rest of the drives are allocated to be RAID.

---

### Post by neo571 on 2006-02-09
but not exist a floppy within driver as windows?

---

### Post by BenTyreman on 2006-02-09
My understanding is that the problem is not the driver for the card itself. Support for the RAID card is built into the kernel. The driver for Windows is to allow the RAID card to use to main processor for performing calculations on where the data should go, because it is not a proper hardware RAID card. Linux also has this ability, through purely software RAID, but the two systems are incompatible. dmraid is a way of allowing Linux to access arrays created by the RAID card. This is what replaces the driver for Windows.

---

### Post by neo571 on 2006-02-09
yes but i can install rmraid in installation process of ubuntu as in windows installation?

---

### Post by BenTyreman on 2006-02-09
No. The process outlines in the above link uses a Live CD to create the system, bypassing the initial part of the standard setup.

---

