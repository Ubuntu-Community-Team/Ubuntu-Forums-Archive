---
title: "Will reinstalling restore XP too?"
date: 2006-01-29
forum: Installation &amp; Upgrades
---

### Post by confounded on 2006-01-29
I uninstalled Ubuntu from my dual boot computer and lost my XP. If I reinstall Ubuntu do I get my XP back?

Please see this other thread about why this happened:
[http://www.ubuntuforums.org/showthread.php?t=123125](http://www.ubuntuforums.org/showthread.php?t=123125)

---

### Post by Jiketsu on 2006-01-29
It is possible yes, if you setup Grub correctly to enable the Dual Booting, so that when your computer starts you can choose which one youd like.

But if you plan to remove Ubuntu again, well youll probably be in the same situation again. There is a way to have Windoze handle the registry again, but I cant really give you support on that. I know theres a boot disk out that that does it. Try googling for a windows XP boot disk and use that until you've backed up all your Windoze crap. And then do a reinstall precious Windoze and reclaim the partition Ubuntu has used.

---

### Post by blackant on 2006-01-29
If you just want to get back your winxp, just boot up from winxp cdrom.
Choose repair during the selection screen.

When at the command prompt, just enter 'fixmbr' and you will get back the winxp after reboot. (if your winxp partition is still around :) )

---

### Post by confounded on 2006-01-30
Jiketsu,
From your comments it is clear you do npt like Windows. I do not trust what you say. I do not want to install XP again. I Know I will lose my data that way. You do not seem to know what you are saying.

blackant,
Trying fixmbr is how I lost XP. If you read the other information you would see.

---

### Post by rfruth on 2006-01-30
[QUOTE=confounded]Jiketsu,
From your comments it is clear you do npt like Windows. I do not trust what you say. I do not want to install XP again. I Know I will lose my data that way. You do not seem to know what you are saying.

blackant,
Trying fixmbr is how I lost XP. If you read the other information you would see.[/QUOTE]

I don't mean to butt in however it sounds like your getting some good advice here, granted calling Windows windoze may not be P.C. but reinstalling XP and / or fixing the master boot record won't wipe out the data (if you do a reformat it will) - now U got my 2 cents worth, back to your bickering.

---

### Post by munga_bill on 2006-01-30
Hi, confounded, maybe I can help. 

First, lets look at the reasons why this problem has come about.
When you just had Windows installed, it had a small 'boot sector', of exactly 512 bytes in size, on the first sector of the first track of your hard disk. This 'boot sector's main job is to point the BIOS to your Windows system where it is loaded by Windows NTLoader. It is like a relay set-up. 

Then, you installed Ubuntu and 'installed GRUB to MBR', which overwrites your Windows Boot Sector, and makes it point to Ubuntu rather than Windows. Contrary to what is implied, the whole of GRUB bootloader does not really fit on a 512 byte sector, so merely the 'first stage' overwrites your 'boot sector' or MBR (two different names for basically the same thing.) All that 'first stage' does is point your computer's BIOS to Ubuntu, where the main part of the GRUB bootloader resides.
Then, if you select to boot WIndows, GRUB points your BIOS back to Windows, or,  if you select to boot Ubuntu, it boots the Ubuntu kernel. 
Again, it is a type of 'relay' set-up. 

Now because you have removed Ubuntu, you are missing a link in the relay. Your boot sector or MBR is not fixed to point straight to Windows like it used to. It is still pointing to Ubuntu, but there is nothing there anymore to re-direct it back to Windows. The main part of GRUB is gone. You erased it. Unfortunately, Ubuntu does not have an 'uninstall option' which restores your MBR to its original state.
You need to do this some other way.

Okay, so now, Windows XP and all your data are all still there, safe and sound, you
will still be able to see it all with a knoppix CD or some other live CD. You just want to be able to boot into Windows, right? So all you need to do is restore your MBR.

Well, there are lots of ways of doing that, and they are all pretty easy and simple and quick. I will go through all the choices I can think of.
1) restore Windows boot sector to its original condition by either 
a) using your Windows XP CD and going into recovery mode and doing the fixmbr trick as already suggested.
b) download a Windows 98 se boot disk program from boot-disk .com, they are free, and type fdisk/mbr after the A:\ prompt. That will work the same for XP as it does for Windows 98 se, the bootloader is the same, just on a floppy disk instead of a CD, but it still works the same and does the same job.

2) reinstall Ubuntu, and install GRUB to your MBR once again, that will work fine, (if you still want Ubuntu after all this).

3) Use an alternative CD-ROM or floppy disk based boot loader to direct your computer's BIOS to your Windows partition to boot Windows. There are many of these and they are able to boot Windows from floppy disks or CDs with or without the option to be written to your boot sector and thus cure your problem.
The brand that is most readily available to most people is GAG on 'System Rescue CD. Most people would have 'System Rescue CD', it is free and is a good help for doing all kinds of things to help you solve computer problems. 

4) Re-install WIndows from scratch and start all over again. If you have all your valuable data backed up this would be an effective thing to do, but time consuming. You will have a nice clean re-install of Windows XP. Most people I know re-install Windows XP on a more or less regular basis anyway. It does it a lot of good, as long as you have everything backed up and have some time on your hands to get all your settings back to the way you like.
I like Windows XP and Ubuntu both, myself, so I think I am giving you some good unbiased advice, I hope it helps you. bye, munga_bill

---

