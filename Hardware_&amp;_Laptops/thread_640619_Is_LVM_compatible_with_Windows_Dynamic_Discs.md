---
title: "Is LVM compatible with Windows Dynamic Discs?"
date: 2007-12-14
forum: Hardware &amp; Laptops
---

### Post by InsaneDane on 2007-12-14
Alright, General setup of my system:
hd0 = 80 GB
(hd0,0)=40 GB (Windows XP)
(hd0,1)=1.5GB (swap)
(hd0,2)=38.5GB(Ubuntu 7.10)
hd1=120 GB
hd2=320 GB

Currently, I have hd1 and hd2 set up under XP to be a single extended volume using the Dynamic Disc feature. I'm wondering whether the dynamic disc feature is compatible with the similar LVM features under linux. 

In short, will I be able to read hdb1 and hdd1 as a single logical drive in both OSs, or will I have to choose 1 for it to work?

---

### Post by psusi on 2007-12-14
No it isn't compatible.  Linux can't use dynamic disks.

---

### Post by bogdan_5844 on 2007-12-14
> Dynamic disks provide the capability for software implementations of RAID. The main disadvantage of dynamic disks in Microsoft Windows is that they can only be recognized under certain operating systems, such as Windows 2000 or later (excluding home versions such as Windows Vista Home Basic and Premium), or the Linux kernel starting with version 2.4.8. at least that`s what Wikipedia is saying :lol:

---

### Post by psusi on 2007-12-14
Hrm.... maybe the kernel partition code can recognize it now, but the lvm tools certainly won't.

---

