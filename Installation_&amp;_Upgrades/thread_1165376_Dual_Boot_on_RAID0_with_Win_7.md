---
title: "Dual Boot on RAID0 with Win 7"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by miocene on 2009-05-20
OK, I have windows 7 RC which is OK but stability is poor so I would like to install Ubuntu alongside and dual boot.

My problem is that I have a RAID 0 array which windows is installed on. When I go to install Ubuntu it doesn't seem to recognise my RAID array and just sees the 2 individual drives with "no operating system installed".

I would like to have Ubuntu and Windows installed on the same array with GRUB as the bootloader. Is it possible without killing my windows installation??

---

### Post by ronparent on 2009-05-23
Check out this site: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

I believe you will have to use the alternate cd which is better configured for recognizing a raid array.

---

