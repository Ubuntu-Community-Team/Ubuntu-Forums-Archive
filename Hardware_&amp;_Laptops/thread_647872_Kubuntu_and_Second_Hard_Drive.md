---
title: "Kubuntu and Second Hard Drive"
date: 2007-12-22
forum: Hardware &amp; Laptops
---

### Post by lostnytechie on 2007-12-22
I can see my second hard drive when I run sudo fdisk -l
**************
 Disk /dev/sda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xebfeebfe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7165    57552831   83  Linux
/dev/sda2            7166        7476     2498107+   5  Extended
/dev/sda5            7166        7476     2498076   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x77657765

What I can't see is the sdb in my Storage media gui.  How can I activate and start using this drive?  
Any assistance would be appreciated.

---

### Post by taurus on 2007-12-22
Doesn't look like there is any partition on that second harddrive, /dev/sdb.  Is there supposed to be something on it or is it a brand new harddrive?

---

### Post by lostnytechie on 2007-12-23
There's currently nothing on that drive.  It was wiped prior to installation of KUBUNTU.  This was originally an xp box with two harddrives and we wiped both hard drives clean so that we could start with a clean installation of kubuntu.

---

### Post by lurhesch on 2008-07-23
I have trouble with my 2nd hard drive too.

I see can it in my storage media but can not use it, have 2 problems:

- 1st is needs my password to open the drive
- 2nd it gives an error message the moment I want to store anything on it: Could not start process Unable to create io-slave: klauncher said: Unknown protocol.

Can anyone help me out on this one? 
thx a lot!

---

### Post by lurhesch on 2008-07-24
I solved the problem

I tried these commands in terminal and in Run Command, once booted from cd and once from my hard drive, one of these worked.

first command
sudo mkdir /media/sdb2

second command
mount -t ntfs /dev/sdb2 /media/sdb2

now it works!

---

