---
title: "Grub Problems"
date: 2008-11-13
forum: General Help
---

### Post by Hellfighter_06 on 2008-11-13
Hey everyone, new here to the forums. I just tried to boot into an ubuntu partition that I've installed. I have three hard drives, a 750 GB (storage), a 250 GB (Vista Ultimate), and an 160 GB (Linux OS and swap partition). I installed Linux perfectly on that particular HDD, but hen I tried to boot up, the grub loader gives me either error 17 or 21. I tried supergrubdisk, but it still won't load. I have unplugged the OS and the storage dives, but that also doesn't work. What should I do?

The drives in boot order are
WD 750 GB
WD 250 GB
WD 160 GB

---

### Post by louieb on 2008-11-13
Does the GRUB menu show up?

Do you have a mix if ide and sata drives? 

Sounds like the GRUB installer got confused about which drive is which.
a couple of things to look at.
[IDBS GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm") [U]
[/U][Dualboot Two Hard Drives - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=179902")

---

### Post by Hellfighter_06 on 2008-11-13
They're all SATA drives

---

### Post by popuptarget on 2008-11-13
assuming when you say you unplugged OS you mean Vista.  When you say it does not work what happens when you try to boot?

V/R Jason

---

### Post by cariboo on 2008-11-13
Grub has to be installed on MBR of the first hard drive. SO you may have to use the LiveCD to reinstall grub. Here is a guide:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Jim

---

### Post by Hellfighter_06 on 2008-11-13
Will this affect my Vista mbr?

---

### Post by cdtech on 2008-11-13
What is your boot order:
```
sudo fdisk -l
```
By the way, welcome to the forum.....

If you boot the live cd you can bring up a terminal to correct the issue at hand.

**UPDATE::.**
This will effect your MBR of your VISTA drive.

---

### Post by Hellfighter_06 on 2008-11-13
Ok, so after fixing the grub issue, do I use my vista disk to rewrite it's mbr

---

### Post by Hellfighter_06 on 2008-11-13
It gave me error 15- grub not found! Where should I install it?

---

### Post by cdtech on 2008-11-13
Which drive can you boot into now?

You have your Vista as the secondary drive and you probably have your BIOS booting into the secondary drive as well. You will have to edit the /boot/grub/menu.lst on the Ubuntu drive to point to the correct drive (ie..hd1 for Vista, hd2 for Ubuntu).

Hope this helps.....

---

### Post by Hellfighter_06 on 2008-11-13
Here's the boot order

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x1f091f08

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       32302   244197376    7  HPFS/NTFS

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd463ef5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *       19123       91202   578971648    7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c80e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       18236   146480638+  83  Linux
/dev/sdc2           18237       19452     9767520    5  Extended
/dev/sdc5           18237       19452     9767488+  82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by Hellfighter_06 on 2008-11-13
So what do I change in the "/boot/grub/menu.lst" file?

---

### Post by louieb on 2008-11-14
Again when you boot does the GRUB menu show up? Does either the Ubuntu or Vista entry work?

I'n both the Ubuntu entry and the Vista entry there is the [COLOR=Red]**root (hd#,#) **[/COLOR]statement.  
From what you said the Ubuntu entry should read [COLOR=Red]root (hd2,0)[/COLOR] and the Vista entry should read  [COLOR=Red]root  (hd0,0)[/COLOR]

If you get the GRUB menu you can view and edit the entry by highlighting it and [COLOR=Red]press e[/COLOR].  Highlight the root statement and [COLOR=Red]press e[/COLOR], change the root statement the [COLOR=Red]press <enter>[/COLOR] then [COLOR=Red]press b[/COLOR] to boot and see what happens.  
The grub menu is in file [COLOR=Red]**/boot/grub/menu.lst**[/COLOR]
If that works you will have to edit /boot/grub/menu.lst to make the changes stick.

---

