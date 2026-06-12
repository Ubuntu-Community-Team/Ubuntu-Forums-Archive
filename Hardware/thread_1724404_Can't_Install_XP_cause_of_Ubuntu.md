---
title: "Can't Install XP cause of Ubuntu"
date: 2011-04-08
forum: Hardware
---

### Post by Skyline649 on 2011-04-08
Hello guys,

After 3 years of using ubuntu , i was so happy about it , but recently i bought a Macbook and my old laptop has to go to my sister for a beginners laptop usage,  , and she is still 14 years old girl, so apperantly i have to give her my old laptop with Windows XP installed again. I have a original CD , but the problem is , cause of the boot loader Grub , the installation CD can't detect any hards disks on the laptop, so my question is : how to remove completely ubuntu from my HDD (only one) and to restore the windows boot loader.I've heard that i have to download some little program to burn to a CD and then to format the HDD???. Now the only thing i have on the HDD is the ubuntu 10.10 and nothing else, i don't have any important info on it, so it's no problem if something goes wrong.And also i don't need any back up of nothing, just an empty HDD where i can install a fresh copy of WIndows XP SP2 

Thanks a lot :)

---

### Post by karl0s on 2011-04-08
are you sure this is a Ubuntu problem? 

I think this is a problem in Windows installer. What exact version of Windows XP instalation disk do you have? What kind of HDD do you have in your PC? is it SATA? if the answer is yes, then I woud say that you need a special driver for windows, as older Windows XP were not able to boot from (or even install to) SATA HDD without it.

---

### Post by psusi on 2011-04-08
Yea, this has nothing to do with Ubuntu; grub can not prevent Windows from seeing the disk.  IIRC, XP does not have SATA drivers, so you have to give it the driver disk.

---

### Post by Skyline649 on 2011-04-08
Ok then, my HDD is Western DIgital 160GB , Serial ATA  , and it has SATA AHCI Controller

---

### Post by Skyline649 on 2011-04-08
so , let's say: i have an empty CD , what do i have to burn on it , to format the HDD and then to put back the Win XP CD for a fresh install?

---

### Post by karl0s on 2011-04-08
you have to download drivers for your motherboards SATA cantroler, put in on some CD, then when the windows instalers starts, it gives you oportunuity to provide 3rd party drivers, (I think it is F2 dirictly when the installer stars, but not realy sure as I have not installed XP for some time now) so at that poit give in the CD (or FDD) and let the windows istaller load it. after that place back the Windows install CD and the installer should continue. And it should be able to see your HDD.

---

### Post by mathgeek2000 on 2011-04-08
> **Skyline649 said:**
> Ok then, my HDD is Western DIgital 160GB , Serial ATA  , and it has SATA AHCI Controller

Windows XP SP3 (Service Pack 3) should be able to detect the drive, as a Serial ATA drive but if you don't have that you should be able to set the drive up as 'legacy' in the BIOS - then install XP as normal.

Once XP is installed, upgrade to SP3, and any other patches.
this site, which deals with older hardware may also be helpful for you:

[http://www.custompcblog.com/troubleshooting/installing-windows-xp-sata-hard-drive](http://www.custompcblog.com/troubleshooting/installing-windows-xp-sata-hard-drive)

---

### Post by psusi on 2011-04-08
XP will not load drivers from a CD; it insists on a Floppy.

---

### Post by karl0s on 2011-04-08
> **psusi said:**
> XP will not load drivers from a CD; it insists on a Floppy. 

oh, sorry about the missinformation :( it has been a while since I last used that. Best for **Skyline649 **would be to get instalation CD for XP SP3 which has SATA drivers integrated as mentioned by **[mathgeek2000]("http://ubuntuforums.org/member.php?u=879066")**.

---

