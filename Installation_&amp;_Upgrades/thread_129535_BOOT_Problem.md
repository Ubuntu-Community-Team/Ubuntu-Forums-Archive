---
title: "BOOT Problem"
date: 2006-02-14
forum: Installation &amp; Upgrades
---

### Post by tendo on 2006-02-14
This is my first time posting in this forum. If a mod thinks this would be better answered in another section please move it :) My KUBUNTU installation was very easy, and I've got most of my devices working now, I'll read the docs on the rest. I still don't have open gl drivers, sound, or dual display set up correctly but I think I can manage. 

**My problem is that I cannot get back into Windows. ** 

Let me explain my hard drive setup: 

IDE MASTER - Where kubuntu lives - 40GB /hda1 
IDE SLAVE - NTFS Storage Drive, no windows installation - 120GB /hdb1 
SATA DRIVE - XP INSTALLATION - 160GB /sda1 

My problem is that Windows will not load, I get an "NTLDR missing" error. I have read all of the docs microsoft has posted on their "knowledge base". I tried making a bootdisk and replacing NTLDR, NTDETECT.COM, and Boot.ini. I have spent hours today on the phone with Microsoft's India tech supports and the things they tried to have me do (bootcfg /recover; chkdsk /r; etc) were unsuccessful. After that he wanted to reinstall windows. 

I have successfully mounted /hdb1 and /sda1 and I can see them in my "Media" folder in KUBUNTU. I can see the Windows NTFS drive and browse it and see that there are files there. I even loaded Partition Magic and checked the partitions on the drives. 

Also, when trying to run Windows Setup on the /sda1 SATA WINXP drive now it says that the partition is not a valid windows partition, but I think thats just the boot partition, not that installation and all my files. At least I hope not. Another thing to note is that in the WIndows Setup it shows you the drives and what channels they're on and it said: 

40GB MB DISK (/hda1 linux drive) as Disk 0 at Id 0 on bus 0 on atapi [MBR]
 120GB MB DISK (/hdb1 storage drive) as Disk 1 at Id 0 on bus 0 on atapi [MBR]
 160GB MB DISK (/sda1 WINXP Drive) as DISK 0 at Id 0 on bus 0 at atapi [MBR]

 On the second line it could be Disk 0 at Id 1, I'm not sure but it doesnt really matter. I'm fairly computer savy but I'm really stuck on this one and any help or even just a link to a doc I could read about what might be going on would be awesome. :-D

---

### Post by Robgould on 2006-02-14
have yout tried fixmbr and fixboot?

---

### Post by tendo on 2006-02-14
[QUOTE=Robgould]have yout tried fixmbr and fixboot?[/QUOTE]

Niether of those worked.

---

### Post by hellerite on 2006-02-14
Windows XP users

   1. Insert the Windows XP bootable CD into the computer.
   2. When prompted to press any key to boot from the CD, press any key.
   3. Once in the Windows XP setup menu press the "R" key to repair Windows.
   4. Log into your Windows installation by pressing the "1" key and pressing enter.
   5. You will then be prompted for your administrator password, enter that password.
   6. Copy the below two files to the root directory of the primary hard disk. In the below example we are copying these files from the CD-ROM drive letter "E". This letter may be different on your computer.

      copy e:\i386\ntldr c:\
      copy e:\i386\ntdetect.com c:\

   7. Once both of these files have been successfully copied, remove the CD from the computer and reboot.

from: [www.computerhope.com/issues/ch000492.htm](www.computerhope.com/issues/ch000492.htm)

---

### Post by tendo on 2006-02-14
[QUOTE=hellerite]Windows XP users

   1. Insert the Windows XP bootable CD into the computer.
   2. When prompted to press any key to boot from the CD, press any key.
   3. Once in the Windows XP setup menu press the "R" key to repair Windows.
   4. Log into your Windows installation by pressing the "1" key and pressing enter.
   5. You will then be prompted for your administrator password, enter that password.
   6. Copy the below two files to the root directory of the primary hard disk. In the below example we are copying these files from the CD-ROM drive letter "E". This letter may be different on your computer.

      copy e:\i386\ntldr c:\
      copy e:\i386\ntdetect.com c:\

   7. Once both of these files have been successfully copied, remove the CD from the computer and reboot.

from: [www.computerhope.com/issues/ch000492.htm](www.computerhope.com/issues/ch000492.htm)[/QUOTE]

Tried that last night with the indian guy, didn't work :-k

Not being able to play Counterstrike sucks lol

---

### Post by bela on 2006-02-15
Hi,
First I think that your /sd1 ( win$) disk is hd2,0 , the third disk ( you have 3 disks) and not hd0. try in your grub/menu.lst to correct it, or at the menu boot try to do it. I suppose that you get a correct grub menu.( your pb is at the boot or when you are inside you win$ partition ???)

best regards 
bela

best regards

---

### Post by tendo on 2006-02-15
Well if that was the case, wouldn't selecting the WINXP drive in BIOS as the boot drive still boot windows?

I don't think its a GRUB problem (although I thank you for your response bela and I will try this!), I think it's a problem with the boot sector on the NTFS XP drive. 

I wanna play me some video games :D

---

### Post by tendo on 2006-02-16
I guess I'm going to have to buy a new hard drive this weekend, install windows, back up my NTFS drive, and start over.  I guess I better do a full *nix backup before I do that, I finally have *most* of my drivers set up !! :-D

---

