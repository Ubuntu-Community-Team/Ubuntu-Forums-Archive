---
title: "New to Ubuntu - need help on partition question!"
date: 2009-07-17
forum: Installation &amp; Upgrades
---

### Post by oogmsn on 2009-07-17
I've 2 HDD, one is a NTFS (40gb) and the other is a newly formatted 80GB (where I installed Ubuntu OS using the default option).

However, after installing and getting to the desktop, I am never able to mount or even use the drive to store any files or create folder?! :confused:

I was just googling this problem and seems like it is a fact that once you use it for the OS install..you cant mount or use it....so what am I going to use the 80gb space for?

Anyone can help to enlightened me on this? Thanks!

---

### Post by christopher.adams360 on 2009-07-17
Well, if you know you installed Ubuntu on the 80 GB HDD, then you don't have to mount it. Any files you put on the Desktop, Documents, Home, or ANY other folder will already be stored on that drive.

---

### Post by oogmsn on 2009-07-17
> **christopher.adams360 said:**
> Well, if you know you installed Ubuntu on the 80 GB HDD, then you don't have to mount it. Any files you put on the Desktop, Documents, Home, or ANY other folder will already be stored on that drive.

oh really?? :P thanks for the clarification!! Sorry about that...too used to Windows ;)

---

### Post by oogmsn on 2009-07-21
ok looks like it is not the case on my end, I've tried moving some files but it seems to indicate that I've only got 1.7gb left which is the exact partition size of where I install ubuntu on..anyone can help me on this?

---

### Post by ktat on 2009-07-21
Are you sure?  I think if you installed with default option you should have all 80Gb available.

Best way to check this is to open System Monitor and check the tab labeled "File Systems" - this will tell you what available space you have and how much you have used.

---

### Post by oogmsn on 2009-07-21
hi Ktat - thanks! Yup..actually the only thing I did is resized it first slightly...will tat be the part causing the problem? Below is my hdd configuration and "/dev/sdb2" is the partition that I cant use it until now...
I've attached the filesystem monitor as attached screenshot...sorry extremely new to ubuntu..and begnning to regret trying this out and moving away from windows...sigh


> root@oogmsn-desktop:/home/oogmsn# fdisk -l

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc1182081

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4998    40146403+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        9060        9726     5357677+   5  Extended
/dev/sdb2               1        9059    72766386   83  Linux
/dev/sdb5            9060        9690     5068476   83  Linux
/dev/sdb6            9691        9726      289138+  82  Linux swap / Solaris


---

### Post by Sef on 2009-07-21
root should be 8-10 gb.

---

### Post by oogmsn on 2009-07-21
hi sef, sorry...so you mean that this is the problem and I need to increase this partition and then I will have no problem?

Even though that I can mount the partition it seems that I do not have the permission to create any folders or moving any files into this...

---

