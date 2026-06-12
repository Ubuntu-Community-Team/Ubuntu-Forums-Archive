---
title: "Acer 5050 SD card reader - Gutsy"
date: 2007-12-08
forum: Hardware &amp; Laptops
---

### Post by ugm6hr on 2007-12-08
My Acer 5051AWXMi (5050 derivative) has an ENE card reader.  SD cards are now recognised and auto-mounted in Gutsy, which is progress from Feisty.  Unfortunately, the are mounted read only - and I cannot find a way to change that.

Just to confirm:
The "protect" switch is off on the SD card
I can open all the files
I cannot write anything to the card, even as "root"
If I try to change the card "Permissions" via GUI - it tells me I cannot, since it is read-only.
The card works just fine in Ubuntu with my USB card reader (same laptop) - and is uto-mounted as read-write with read-write access for my username.

Hence, it must be the Ubuntu support for the reader that does not allow writing to the SD card.  Anyone else encounter this, or preferably have a solution?  I would love to be able to get rid of my USB reader!

---

### Post by jointstereotype on 2007-12-08
I filed a bug report here for similar problem:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/160863]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/160863")

Hopefully it'll make the Ubuntu programmers' to-do list. ;)

---

### Post by zipperback on 2007-12-09
> **ugm6hr said:**
> My Acer 5051AWXMi (5050 derivative) has an ENE card reader.  SD cards are now recognised and auto-mounted in Gutsy, which is progress from Feisty.  Unfortunately, the are mounted read only - and I cannot find a way to change that.



I am going to be doing a clean install of Gutsy as soon as I finish a quick project I am working on and then backup the rest of my files.

I have an Acer 5050-3371 and it has the same built in ENE card reader.

Once I get it installed I will begin working on the issue of being able to get full read and write access working for it.

I will post the information for this as soon as I get working on it.

- jack (zipperback)
:popcorn:

---

### Post by ugm6hr on 2007-12-09
> **jointstereotype said:**
> I filed a bug report here for similar problem:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/160863]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/160863")

Hopefully it'll make the Ubuntu programmers' to-do list. ;)

Just to clarify - I have only tried my 4GB SD card.  And it is FAT32 formatted.

My lspci is identical (with reference to the ENE card reader entries).

But the error is slightly different (although I only tried in nautilus - not Terminal).  It claims the card is read only.

---

### Post by zipperback on 2007-12-27
> **ugm6hr said:**
> Just to clarify - I have only tried my 4GB SD card.  And it is FAT32 formatted.

My lspci is identical (with reference to the ENE card reader entries).

But the error is slightly different (although I only tried in nautilus - not Terminal).  It claims the card is read only.

I just thought I would report back my findings with my built-in SD card reader.

I have a full clean install of Ubuntu 7.10 installed on my laptop which is an Acer 5050-3371

I have tried it with a 1GB SD card and it automounts the card correctly. An icon appears on my desktop when it mounts. I can click the icon and it allows me to browse the card, and to read and write from it without any problems.

My SD card was formatted by my Kodak EasyShare Z710 digital camera.

My suggestion is to double check that your SD card isn't set to write protect mode. On mine there is a little white slider tab which I can slide into the Lock or Unlocked position.

Check it both ways in your card reader just to be sure that the card isn't locked.

I bought my SD card at WalMart, and it's a 1GB SD card that is blue, and it says Impact SD 1GB on the side of it.

- zipperback

:popcorn:

---

### Post by ugm6hr on 2007-12-27
@zipperback:

My 4GB card behaves identically to yours, except nautilus (& also thunar - which I have just tried) tell me that I don't have write access if I try and copy files across.

However, in properties (on nautilus), it lists my username as "owner" with "Create and delete files" Folder Access, but "---" for File Access.

I have had a previous similar issue with a USB flash stick, but just unmounting and plugging back in worked.  My SD card remounts the same way each time.

How can I mount it manually with read-write access from Terminal?

It appears as /dev/mmcblk0p1 (according to GParted).  I think the problem may be that it was fomatted in my Windows Mobile 5 PDA.  Even GParted says it is fat32, but has an alarm symbol by it, which says "Unable to read the contents of this file system! Because of this some operations may be unavailable."  Maybe this is the problem - Ubuntu doesn't fully understand the fat32 system?  Again, I have had Windows formatted fat16/fat32 USB sticks that behave unusually in Ubuntu before.

---

### Post by zipperback on 2007-12-29
> **ugm6hr said:**
>   Maybe this is the problem - Ubuntu doesn't fully understand the fat32 system?  Again, I have had Windows formatted fat16/fat32 USB sticks that behave unusually in Ubuntu before.

Are you able to back up the data on that SD card by some other means? Such as an external SD card reader, or the SD card device that you use it with?

Perhaps you can mount it, then use Ubuntu to repartition and reformat it into fat32 again.

- zipperback
:popcorn:

---

### Post by zipperback on 2007-12-29
I took a look at the SD card that works for me, and the format reports back as "vfat"  not fat32.

Something you might want to consider is reformatting your SD card into vfat format instead of fat32 and see if you can then read and write to the SD card.

If it works as a vfat format but not fat32, then we should better be able to isolate the problem down to a partition format / mounting issue.

If we're lucky your pda that you also use it with, will be able to use it as a vfat sd card as well.

Another thing you might try is to reformat the sd card with your card reader, as a fat32 format like it is now, and see if it were somehow a bad formatting issue from the pda that formatted it initially.

Eitherway, make sure you backup your files before doing any of this, otherwise the files will be lost.

- zipperback
:popcorn:

---

### Post by ugm6hr on 2007-12-29
Cheers.  I think that may be the problem.  Perhaps that is why some of my USB flash sticks misbehave in a similar way.

I will try and give it a try some time soon.  Probably when I next back up my SD card.  I can't risk the data on it at the moment to experiment, and if it doesn't work in the PDA, it's no use to me at all.

---

### Post by zipperback on 2007-12-29
> **ugm6hr said:**
> Cheers.  I think that may be the problem.  Perhaps that is why some of my USB flash sticks misbehave in a similar way.

I will try and give it a try some time soon.  Probably when I next back up my SD card.  I can't risk the data on it at the moment to experiment, and if it doesn't work in the PDA, it's no use to me at all.


Sounds good. Let me know what you find out. 
- zipperback
:popcorn:

---

### Post by zipperback on 2007-12-31
I was doing some research on vfat and fat32, vfat from is limited to a maximum partition size of 2GB. So you would need to use fat32 for your card since it is 4GB.


- zipperback
:popcorn:

---

### Post by randominternet on 2008-02-15
I have same laptop and same problem.... in windows, linux and darwin

But then one day it mounted RW and shocked me

So I opened the laptop up again and found the little switch that detects the position of the protect tab was not moving over far enough. I simply fixed this by glueing it open (never use write protect anyway) and have just been able to write to an SD card!

I will post back with my results on other os later, need to reboot

---

