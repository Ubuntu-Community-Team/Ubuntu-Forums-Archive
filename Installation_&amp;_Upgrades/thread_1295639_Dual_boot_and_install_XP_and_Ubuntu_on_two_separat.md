---
title: "Dual boot and install XP and Ubuntu on two separate hard drives"
date: 2009-10-19
forum: Installation &amp; Upgrades
---

### Post by jiversen on 2009-10-19
:confused:I had Suse Linux and Windows XP working on two separate hard drives (2-3 years). That died, so I went out and bought two new (bigger) hard drives to start fresh. I downloaded Windows XP (Home) on the first drive. Now, I put the second drive in (unformatted) and tried to install Ubuntu 9.04 from an ISO image I burned onto a disk. During the install, it did not recognize my other hard drive so, I aborted the install for now.

What do I do next and how do I do it? How do I go about formatting the new disc? FAT32 or NTFS? Do I use the "New Partition Wizard" in Windows XP or is there another way to do this? Windows only lets me format it in NTFS. I just want to have a dual booting system like before.

Can someone point me in the right direction. I don't want to mess this up and have to start all over again. I am reading books on Linux and going to Newbie forums to learn all I can. This is still new territory for me.

I have an AMD Athlon(TM) XP 2200+
1.8 GIGz, 512 MB of RAM
ACPI Uniprocessor (32 bit)
Comcast High Speed Internet
250 G Hard Drive (IDE) with Windows XP on it
160 G Hard Drive (PATA, IDE) unformatted and just installed
Hitachi DVD ROM GD 5000
LIT-ON CD-RW SOHR-52385

---

### Post by stlsaint on 2009-10-19
well first off after you install xp disconnect that hdd from your box then connect unformatted hdd for linux. install linux than connect new hdd to box again and then add a stanza to your grub entry(not sure what it is for SUSE but for ubuntu its your menu.lst) 

```
/boot/grub/menu.lst
```

i cant give more info as im not on home machine but please see my signature on installing ubuntu for reference.

---

### Post by jiversen on 2009-10-21
Thanks for the speedy response, stlsaint! I assume that this will give me a linux boot screen that will give me a choice of which operating system (Ubuntu vs Windows XP) I can start. This is what I had before when someone set it up for me with OSuse 10.0.

 I am really new at all this computer language but I am learning as much as I can (as fast as I can). When I put both hard drives back in the machine and start it up again (according to your directions), I assume that my Bios will know to boot from the Grub menu and not be confused.

Sounds really easy. I think I will wait a few more days for version 9.10 to come out. I've tried the live CD and it looks really GREAT! In the mean time, I will read all the things that you referenced in your last post and learn as much as I can. This is so much fun (so far). Also reading the Ubuntu Kung Foo book. I think I can get the hang of this.

---

### Post by Mark Phelps on 2009-10-22
> **jiversen said:**
> ... Sounds really easy. I think I will wait a few more days for version 9.10 to come out...

Karmic uses a new GRUB (GRUB2) by default on new installations.  It does NOT use menu.lst, meaning, that it's no longer a simple process of adding five text lines to a text file to incorporate MS Windows installations into an Ubuntu boot.

---

