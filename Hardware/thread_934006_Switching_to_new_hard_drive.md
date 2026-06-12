---
title: "Switching to new hard drive"
date: 2008-09-30
forum: Hardware
---

### Post by zieglerj on 2008-09-30
I just bought a new hard drive and would like to move my entire system from the old one to the new one. 
What is the best way to do this keeping in mind that if I had a lot of space to work with on the old one I wouldn't have bought the new one.

---

### Post by chewearn on 2008-09-30
There are probably many ways to do this, but I will mention two approaches.


If you are confident / know how to install grub, then:[INDENT]1. clone your partitions from old to new HDD.  A good tool I recommend is [gparted livecd]("http://gparted.sourceforge.net/livecd.php").
[/INDENT][INDENT]2. After cloning, install grub on the new HDD.
[/INDENT]
If you are not confident installing grub:[INDENT]1. Fresh install same version of ubuntu onto the new HDD, which will install grub into it.  Make sure the boot/root partition order is the same as old drive (i.e. if old drive in /dev/sda1, make sure the new install is the same)
[/INDENT][INDENT]2. Delete the partitions in your new HD.
[/INDENT][INDENT]3. Clone your partitions from old to new HD.
[/INDENT]

---

### Post by kpkeerthi on 2008-09-30
**Option - 1:**
1. Manually create the partitions in the new drive using gparted (use gparted live cd or system rescue cd. Hint: ask google)
2. **rsync** the respective partitions from the old HDD to the new one.
3. Install GRUB on to the new drive.

**Option - 2:**
1. Perform fresh ubuntu installation on the new drive. This will get you the GRUB menu.
2. **rsync** the partitions from the old drive to the new one. This will get you all the applications and system wide customization from your old setup.

---

