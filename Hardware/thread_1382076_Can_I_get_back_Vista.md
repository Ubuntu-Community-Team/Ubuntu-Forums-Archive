---
title: "Can I get back Vista?"
date: 2010-01-15
forum: Hardware
---

### Post by JosephGarrison on 2010-01-15
I am using a Acer Aspire 4720Z and it came with Vista. I completely got rid of it when I installed Ubuntu. Is the recovery partition still on my computer to reinstall vista? Nothing comes up when I hold alt + F10 on the startup splash screen. I attached a picture of the results from GParted. I didn't back up the partition, but I have system restores on an external hard drive if that does anything, probably not. . .

---

### Post by oldfred on 2010-01-15
You only have root, extended partition holding the swap partition. No windows or recovery. You may be able to use your system restore. The recovery partition will normally only let you recreate the system as you purchased it.

---

### Post by lisati on 2010-01-15
I see no sign of Windows on the screenshot either. 
By "system restores" are we talking something in the nature of "recovery disks", or is it more like "restore points" that Windows creates as it goes? 
As has been noted, recovery disks/partitions work best for getting systems to an "out of the box" state (i.e. what it was like when you first bought it). As I understand things, "restore points" normally require that there's a functioning copy of Windows on the system and let you undo *some* (but not all) changes.

---

### Post by JosephGarrison on 2010-01-16
> **lisati said:**
>  As has been noted, recovery disks/partitions work best for getting systems to an "out of the box" state...

When I was trolling through the Acer website, I noticed that recovery disc for this computer required windows, which I removed (Because I'm an idiot) but I noticed that there was a "windows" recovery disc for this same computer, but it was only for windows XP. I only want Windows back on my computer so that I can Update it to Windows 7 (upgrade was sent to me as a gift) then I'm going to either run Ubuntu in a virtual machine or with Wubi). Is it possible the "windows" recovery disc for xp will work on my system that came with vista. Also, does anyone know an estimated cost for xp so I can just buy it if all else fails. I'm going to look myself but I'd like a professional opinion.

Oh, and by system restores I meant literally like the system restore function windows uses inside the machine. Doesn't do me any good :(

---

### Post by IcarusR on 2010-01-16
If you deleted the windows partition when installing Ubuntu, ie used the whole disk for Ubuntu install, then windows is gone for good. No recovery disk will get it back.
Buy either xp cd & use your windows 7 upgrade disk or full windows 7 disk.

XP home edition SP2 around £60.

---

### Post by pi/roman on 2010-01-18
I remember they used to put embedded chips on the motherboard for system restoration aside from a hard drive partition.  I don't know if anyone still does that.

---

### Post by dyslexia on 2010-01-18
I'm not sacrificing any of my 7 backups (on two different external drives, and on DVD) BUT,,,

I will say that all my efforts are something of a waste.... I wouldn't go back to vista for all the tea in China.

---

### Post by t4thfavor on 2010-01-21
Let me start by saying "Thats alot of tea!". I have successfully restored my PC from ubuntu to Windows by using manufacturer supplied recovery disks. If your PC came with Vista, and it also came with disks labeled applications, and OS/applications (or something similar) than you should be able to boot to the one labeled OS, and reinstall.

Keep in mind it will be identical to when you bought it, including freeware, trial software, and no ubuntu partition.

aside from that, if you have a COA (windows key) you can just download the image from a reputable source, burn it, and install LEGALLY with your already PURCHASED key.

Hope that helps.

---

### Post by durrenmatt on 2010-01-21
> **t4thfavor said:**
> if you have a COA (windows key) you can just download the image from a reputable source, burn it, and install LEGALLY with your already PURCHASED key.

Hope that helps.

yea, if your laptop came with windows vista installed you should have a genuine cd key for it...or you are looking to save certain data from your old windows?

---

### Post by checoimg on 2010-01-23
Shouldn't the laptops come with the reinstalation CD's???

I think you want something you did on windows. I erased mine before using it.

---

### Post by mental2k on 2010-01-24
Lol, I came on as an ubuntu noob, but I may be able to help you with a windows problem.

Firstly, if you have altered your partitions at all ACER recovery doesn't like this, if you have not already burned a recovery disc, you can no longer make one.  There doesn't seem to be a recovery partition within ACER (at least not from what ACER techs have told me), and it'll cost you around £60GBP for ACER to supply you with them (thank you ACER).

Someone mentioned about getting an OEM copy, but I'll try and expand that a little for you.

If your laptop came pre-installed with Vista then there is a SLIC table in your BIOS, which vista uses, along with a manufacturer specific certificate file and a manufacturer specific generic licence key.  (Generic in the sense every manufacturer seems to have one key per windows vista version).

If you have an oem vista disc, obtained from a friend or from various sources online, then it may install the relevant certificate file and licence key automatically, or may not.  If it doesn't its just one simple step at the end to fix.

Simply repartition and install vista as best suits you.  Then have a mosey on over to 
[http://forums.mydigitallife.info/](http://forums.mydigitallife.info/) to get the relevant files and keys.  This will allow an offline activation.

NOTE: This only works if you had Vista pre-installed.

The license key printed on your laptop will also work, but you'll have to phone MS to get it activated (as its not the key your laptop was activiated with initially.)

Hope that helps.

---

