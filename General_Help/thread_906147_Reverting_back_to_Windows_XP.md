---
title: "Reverting back to Windows XP"
date: 2008-08-31
forum: General Help
---

### Post by Edigido on 2008-08-31
Okay, so I've tried to do this multiple times, and I've gotten no where with it.  I'm trying to revert the entirely of my computer back to windows XP.  Simply because of the compatibility of the masses of programs.  I'll probably resintall Ubuntu as a second operating system.

Okay, so if anyone has any ideas on how to revert to XP, that would be GREAT help.  Unfortunatly, I'm quite a n00b when it comes to terminal stuff, so if someone would be so kind as to walk me through it, that would be a great help.

---

### Post by jespdj on 2008-08-31
Insert Windows XP CD into CD-ROM drive, reboot, let computer boot from the CD, follow steps of installation program.

---

### Post by forger on 2008-08-31
1) You load your ubuntu live cd (yes, you need the live cd)
2) You go to System > Administration > Partition Editor
3) Choose your hard drive device using GParted > Devices
4) Right-click on the partition(s) you want to delete and delete them.
5) Press Apply when you're done
6) Restart, take out your ubuntu cd and put it the windows xp cd
7) "Press any key to boot from CD..." - act as told :)
8) From here onwards it should be familiar to you on how to install windows xp (?)

---

### Post by lisati on 2008-08-31
No Windows CD? Check your computer for a Windows Recovery Partition......

---

### Post by mb_webguy on 2008-08-31
> **jespdj said:**
> Insert Windows XP CD into CD-ROM drive, reboot, let computer boot from the CD, follow steps of installation program.
And if you're planning on dual-booting Ubuntu, when you're given the choice of the drive/partition to install Windows, create a partition for Windows and leave enough unallocated space to install Ubuntu later.

Actually, if you're pretty sure you want to dual-boot, it's better to decide now so you can have a good partitioning scheme.  I prefer something like this:
[LIST]
[*]10-15GB ntfs partition for Windows XP (or 20-25GB for Vista)
[*]10-15GB ext3 partition for Ubuntu root ("/")
[*]A small swap partition equal to 1.5x your system memory if you plan to use hibernation, or 1x your system memory otherwise
[*]1-5GB ext3 partition for Ubuntu home ("/home") (This can afford to be small, since the only data you'll keep here will be local configuration files.)
[*]An ntfs (or ext3) partition using the remaining drive space, to be used to store your files and shared between Windows and Ubuntu.  (I personally prefer to use the ntfs filesystem for this, since while Windows can use ext3 with a third-party driver, I believe Ubuntu's support of ntfs is more reliable.)
[/LIST]

This way, the only information that is on an OS partition is the OS itself and any programs installed for it, while your data is stored on a separate partition accessible from either operating system.  If you go with a partitioning scheme like this, you will have access to your data no matter which OS you boot into, and if you choose to uninstall one of your OSes and install a different one, you don't have to worry about about losing your files, since they won't be affected by a change in your OS partitions.

---

### Post by Jungle-Cat on 2008-08-31
If you have stuff in windows (making formatting and just wiping everything difficult), then this is how I've done it in the past:
Get the Ubuntu live CD, open the partitioner (if you can't find it, run gparted in the terminal). Delete the linux/ubuntu related ones, leaving your XP partition. Extend it over what use to be the ubuntu stuff if you want.

Now, put in your windows XP cd, and open the recovery console (I can't really help with this, I think you press R somewhere. Just look for prompts). The command to run here (just type it and hit enter) is fixmbr. This will get rid of grub and make your computer just boot into XP.

---

### Post by Edigido on 2008-09-04
Okay, my mounted Ubuntu Partition is taking up too much space, and I'm not sure how to resize it.  I remember having done this once, but that was with killdisk, and even then, XP wouldn't recognize the hard drive.  Any ideas? (and please be specific...)

---

### Post by dilla on 2008-11-15
run gparted, delete any other partitions, select your XP partition and hit resize

---

