---
title: "Yes, I am a total n00b..."
date: 2005-01-22
forum: Installation &amp; Upgrades
---

### Post by MCZH on 2005-01-22
Well, after my friend recommended (and provided) an unbuntu Linux CD, I decided to try it, since well...I was getting tired of Windows XP.

First of all, I want to install ubuntu but I do NOT want to erase my data that's already on my computer.  My friend said you could do this, but I haven't figured out how.  Can anyone give me easy-to-understand step-by-step procedures to do this?  I have a 20 GB C drive and a 60 GB D drive, both which have files I don't want to erase.  

Thank you for helping out a total n00b...After I installed it, I'm sure I'll have more questions...

---

### Post by Adrenal on 2005-01-22
You need a partitioning tool, such as partition magic. Don't know of any free ones though

---

### Post by shmonkey on 2005-01-23
[QUOTE=Adrenal]You need a partitioning tool, such as partition magic. Don't know of any free ones though[/QUOTE]

This is not true, you can create partitions form the Ubuntu installer. The installer should recognize that you have Windows installed. Follow the instructions. Don't, choose use entire disk but them create form free space to preserve your data.

I would suggest install Ubuntu on the disk that does not contaim Windows (extra safety precaution).

When Ubuntu is installed, you will reboot your PC and see the grub boot loader from this you will be able to select Ubuntu or Windows to load.

There have been some report of grub  not booting into Windows. if the happens post your /boot/grub/menu.lst file to the forum to see if the problem can be solved.

If you ever need to restore to just Windows loading, you can use a Windows boot disk and then run:   fdisk /mbr

So before you attempt to install Ubuntu, back up your data and create a windows boot floppy/CD.

Regards

Shmonkey

---

### Post by Marquis_de_Carabas on 2005-01-23
[QUOTE=shmonkey]This is not true, you can create partitions form the Ubuntu installer. The installer should recognize that you have Windows installed. Follow the instructions. Don't, choose use entire disk but them create form free space to preserve your data.[/QUOTE]

That's only true if you *have* free - unpartitioned - space though. Most users tend to partition their entire drives (no good reason not to, unless you know you're going to be installing additional OSes), and the Ubuntu installer can't resize existing partitions.

Acronis Partition Expert seems a decent enough Windows partition tool, and I think there's a free demo version available. Or there's QTParted, a totally free Linux partitioning tool.

The easiest way is probably going to be to defrag your 60GB drive (to ensure all the files are grouped together - you won't be able to resize the partition if they're spread out right across it) and then use QTParted from Knoppix (a Linux Live CD - you can run it from the CD drive without installing anything) to shrink your existing partition and leave some free space for Ubuntu.

Knoppix has been on quite a few magazine coverdiscs and of course is available to download for free - ask your friend if he has a copy.


Edit: I should note that backing up your data before resizing any partitions is recommended. I've never had any problems when doing this, but if there are files you *really* don't want to lose then it's better to be safe I guess.

---

### Post by Skid on 2005-01-23
[QUOTE=Marquis_de_Carabas]That's only true if you *have* free - unpartitioned - space though. Most users tend to partition their entire drives (no good reason not to, unless you know you're going to be installing additional OSes), and the Ubuntu installer can't resize existing partitions.

Acronis Partition Expert seems a decent enough Windows partition tool, and I think there's a free demo version available. Or there's QTParted, a totally free Linux partitioning tool.

The easiest way is probably going to be to defrag your 60GB drive (to ensure all the files are grouped together - you won't be able to resize the partition if they're spread out right across it) and then use QTParted from Knoppix (a Linux Live CD - you can run it from the CD drive without installing anything) to shrink your existing partition and leave some free space for Ubuntu.

Knoppix has been on quite a few magazine coverdiscs and of course is available to download for free - ask your friend if he has a copy.


Edit: I should note that backing up your data before resizing any partitions is recommended. I've never had any problems when doing this, but if there are files you *really* don't want to lose then it's better to be safe I guess.[/QUOTE]
 You can do that without using that util from the Knoppix CD.. Norton have recently taken over Partition Magic (PQ Magic) - so if you get it from their site it'll let you resize paritions accordingly leaving some "free space" for an install.

---

