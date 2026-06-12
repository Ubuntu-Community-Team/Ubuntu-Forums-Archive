---
title: "How can I auto mount my second harddrive on boot"
date: 2008-11-08
forum: General Help
---

### Post by morissette on 2008-11-08
I am relatively new to Linux. So please pretend like i know nothing when providing me support.

Every time I boot I have to manually mount my second hard drive. 
it is located at /dev/sdb1

I do not know what kind of filesystem it is using because it has been quite some time since I originally set it up. How do I check the current filesystem in use on that drive? And how do I set it up to automatically boot on start up. 

Thank you for all your help

---

### Post by taurus on 2008-11-08
If you don't remember what kind of filesystem is /dev/sdb1, open a terminal and post the output of this command.

```
sudo fdisk -l
```
Basically, all you need is to add an entry in /etc/fstab to have it mount automatically each time you boot Ubuntu.

---

### Post by morissette on 2008-11-08
Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   83  Linux

and the entry in /etc/fstab should be something like:

/dev/sdb1 /media/disk

/media/disk is the mount point

or do I just need to add /dev/sdb1?

---

### Post by taurus on 2008-11-08
unmount your /dev/sdb1.  Then, edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sdb1   /media/sdb1   ext3   defaults   0   0
```
Save the change and close gedit window.  Now, you need to create the new mount point.

```
sudo mkdir /media/sdb1
```
You can either reboot or mount /dev/sdb1 again with

```
sudo mount -a
df -h
```
/dev/sdb1 should be mounted to /media/sdb1 automatically from now on without you doing anything.

---

### Post by morissette on 2008-11-08
Okay thank you very much that definitely works, one more question though. In the Places on my panel it has always been labeled as 320.1 GB Media is there anyway I can change that name? Sorry for the newb questions I am just trying to learn.

---

### Post by Asterix1977 on 2009-08-19
Hi GUys.
I too am very new to Linux  (1 day!)  I too have been trying to add a second hard drive.  I have tried the lines above but i think it may bee something to do with my HDD and the type of formatting??
This is the disk i am trying to mount automatically on boot:

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2019db00

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19457   156288321   42  SFS

I am guessing there is a specific line i need to add to the fstab?

Please help!

---

