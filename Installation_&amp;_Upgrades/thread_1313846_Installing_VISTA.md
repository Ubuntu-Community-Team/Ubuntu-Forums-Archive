---
title: "Installing VISTA"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by Haug219 on 2009-11-04
Hi, I am planning on installing windows Vista 64 bit on my friends computer that currently has 9.10 on it. He wants to get rid of ubuntu completely because he is a gamer and when I put the windows disk in it wont recognize his hard drive. Any solutions?

---

### Post by Haug219 on 2009-11-04
It says I need drivers but when I go to burn the drivers onto a disk using the ubuntu cd creator it sits at getting size forever

---

### Post by hal10000 on 2009-11-04
To get rid of linux just boot your windows cd an wipe out all your ubuntu partitions.

If you need additional drivers to install windows - well, that's a windows problem.
If you know which drivers you need, then of course you can burn them on a cd in ubuntu.
The best cd burning ool in ubuntu is k3b, which you might install with:

```
sudo apt-get install k3b
```

---

### Post by Haug219 on 2009-11-04
Thanks I appreciate your help

---

### Post by Haug219 on 2009-11-04
I the drivers on the CD it didnt work, Im thinking maybe tis the file system the hard drive is using. Windows uses ntfs I think. If I go to disk utility and change it to NTFS will that work?

---

### Post by Mark Phelps on 2009-11-04
Try booting from the Ubuntu LiveCD and seeing if GParted sees the partitions on the drive.  If it does, unmount the swap partition, and remove all the partitions (presuming you don't want to keep anything).

Reboot using the Vista DVD -- it is an installation DVD, right?

if the DVD still doesn't see the drive, you could try rebooting using the Ubuntu LiveCD, creating an NTFS partition filling the drive, and rebooting again with the Vista DVD.

If it still does not see the drive, you will have to use the drivers disk you created by pressing F6 during install, inserting that disk, and selecting the drivers.

---

### Post by Haug219 on 2009-11-04
ok I will try that out thank you so much

---

### Post by Haug219 on 2009-11-04
OK it says I need a cd/dvd drive device driver I found a flash drive and put it on there and downloaded the drivers from the hp website the only problem is the installation wont recognize .exe files on the flash drive....everything recognizes my hard drive btw bios, ubuntu, etc It is just that this one step is blocking me from partitioning

---

### Post by Bunnybugs on 2009-11-04
You can go into diskmanagement via System>Administration>Disk Utility

Resize your Ubuntu partition, and make room for a new Widdows partition?

EDIT: You can also try to install VISTA in VirtualBox OSE... this is an emulator, you can install it here with the Vista disk... and run it from Ubuntu...

Virtualbox is available in the Software repository, maybe look on the internet for more info

---

### Post by Haug219 on 2009-11-04
Yea I think I found that that isnt the problem. Thanks Anyway though. The problem is that when I go to the Vista installation it says I need a cd/dvd Device Driver. I put the drivers on a flash drive but he Vista installer doesnt recognize .exe files so I am currently extracting them to see if that works.

---

### Post by Haug219 on 2009-11-04
Ok the extract worked....thanks for all of your help guys I appreciate it. Problem Solved!

---

### Post by Mark Phelps on 2009-11-05
> **Haug219 said:**
> OK it says I need a cd/dvd drive device driver I found a flash drive and put it on there and downloaded the drivers from the hp website the only problem is the installation wont recognize .exe files on the flash drive....everything recognizes my hard drive btw bios, ubuntu, etc It is just that this one step is blocking me from partitioning

The ".exe" file you downloaded from the site is a self-extracting archive.  You run it in MS Windows and it extracts the files to a directory.  You need to copy the EXTRACTED files to a USB drive, not the .exe.

---

