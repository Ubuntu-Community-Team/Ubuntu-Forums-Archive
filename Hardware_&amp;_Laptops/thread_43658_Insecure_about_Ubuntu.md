---
title: "Insecure about Ubuntu"
date: 2005-06-22
forum: Hardware &amp; Laptops
---

### Post by paperless on 2005-06-22
So, i have just ordered some x86 + AMD64 ubuntu disks and  i have some questions.

Will i have any trouble with SATAII?, like in Windows you have to go trough a lot of hassle coz of the controllers and such, does the same happen in Ubuntu?

I have installed Suse 9.1 in the past and i had several problems because i stopped being able to start Windows when i unninstalled Suse i found out my MBR got all messed up ( i unninstalled suse because i couldnt log into it anymore ) i tried to fix the MBR etc, nothing worked so i had to format the disk and loose all the data i had.

Will i have any similar problems installing Ubuntu when Windows is already installed? i heard it would detect it automatically, what about the inverse?
Ill have 3 HDDs in total.
I want to be sure it will detect automatically and set all the things up or at least know a way that has worked with **everyone**, i dont want to go trough the same problem.

Thank you all  :wink:

---

### Post by bunced on 2005-06-23
It has worked for me on four computers, no problem. On many, I am dual booting between three OSs. And yes, it works well on AMD64, too

---

### Post by paperless on 2005-06-23
You didnt talk about the SATAII support, any problems with it?

Thanks

---

### Post by Unrivaled on 2005-06-23
From what I remember Windows doesn't use the MBR for booting. In fact, when you install WinXP, it clears the MBR and sets it's partition to active. 

To be able to boot Windows and only Windows, you would have had to boot to DOS and ran "fdisk /mbr" and that would have cleared your MBR. Then you run fdisk, and make sure your Windows partition is set active. 

Unless there's a physical hard drive problem that started your issues, your system would boot Windows. 

I'm sure this doesn't help after the fact, but for future reference.  :)

Decided to edit in a bit of stuff:

MBR = Master Boot Record. It's the first 512 bytes on your hard disk, before any partitions.

Each partition also has space for a boot record, at the beginning of the partition. 

Your computer starts up, and the BIOS looks for the drive you chose to boot off of.  It looks for an MBR, if it doesn't exist, it looks for the active partition, and gives control to that bootloader. Windows only uses the active partition method, whereas Linux can use either that or the MBR.

---

