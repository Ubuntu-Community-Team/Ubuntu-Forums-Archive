---
title: "[SOLVED] New Secondary Sata hard drive"
date: 2008-02-06
forum: Hardware &amp; Laptops
---

### Post by Dark_Man on 2008-02-06
Hey all. New user here. I have just set up ubuntu 6.10 as a dual boot with XP. My question is this. I just bought a  new internal WD SATA hard drive. I would like to use this drive as storage only for both XP and Ubuntu. Is there a way to get ubuntu to recognize the drive as is or do I need to have an OS installed. Thanks

---

### Post by taurus on 2008-02-06
You only need to format it and then mount it from Ubuntu before you use it.  I assume you want to format it to ntfs filesystem so you should consider using ntfs-3g driver so you can write to it.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by Dark_Man on 2008-02-06
Thanks for the quick response, but exactly how do I go about formating the new drive. I have gparted installed and ntfs3g. The new hard drive dosent show up in gparted.

---

