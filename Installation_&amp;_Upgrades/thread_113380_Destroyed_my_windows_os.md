---
title: "Destroyed my windows os?"
date: 2006-01-06
forum: Installation &amp; Upgrades
---

### Post by kook44 on 2006-01-06
Hi-
I have two disks in PC.  I was trying to install kubuntu on the second disk and during the install, I accidentally selected "erase entire disk and partition using LVM" on the first disk (which contained winxp).  I tried to undo changes and the installer froze.  I never chose to write the changes to the disk.  I guess they were written anyway.  When I try to boot WinXP, I see the black screen w/ winxp logo & the green meter, then I get a blue screen with "UNMOUNTABLE_BOOT_VOLUME" or something of the sort.  So i finished installing kubuntu on the socond disk, and in QtParted, I can see the first disk now contains 2 partitions:
NTFS active 243.14MB start:0.0307617 end:243.171
extended 148.77GB  start:243.171 end:152586
(which contains a logical partition of unknown type that fills the whole size)
Is there any way I can recover my XP os?  Maybe by deleting the extended partiton, and growing the NTFS partition to the right to fill the whole drive?

---

### Post by nerval on 2006-01-06
Nothing can be destroyed in your hard drives (well you can, but physically). Have you made-up back-up cds for important stuff? That's the number one matter now. If you didn't; mount those partitions and check them if files are still there. If not, I remember using a recall kind of program in the stone-age; there might still be one. 

If you are using a brand-computer (dell, sony, toshiba etc.) use their recovery disks, they might have an option without formatting. 

If not, [http://easylinux.info/wiki/Ubuntu#How_to_add_Windows_entry_into_GRUB_menu](http://easylinux.info/wiki/Ubuntu#How_to_add_Windows_entry_into_GRUB_menu)
try this one. 

Good luck;
Onur

---

### Post by Lord Illidan on 2006-01-06
Use a live cd, like Knoppix to recover your data and put it on a usb key or an ftp account somewhere. That's what I did when I borked Windows (it crashed, not my fault)

---

### Post by kook44 on 2006-01-06
well, I always keep all my data on an external USB hard drive for that very reason so I'm not worried about losing any of that.  But being a geek, like I'm sure many on this board can understand ;), I have a large amount of software I use, and do a lot of OS tweaking (especially to the dreadful XP).  I had everything just the way I liked it.  A full reinstall can be a 4+ hour ordeal.  I was just wondering if the problem lies solely in the partitioning, and the actual OS was left untouched.

---

### Post by nerval on 2006-01-06
well just to learn some patience :) install gentoo (or any source-based distro), and install hell a lot of programs and then try to install it once again from the beginning after screwing up everything in it. Afterwards you will never blame the time u spend on reinstalling stuff :)

Again, if there is a recovery cd for a brand-comp; there might be an option without out screwing up what is already installed. 

"I accidentally selected "erase entire disk and partition using LVM" on the first disk (which contained winxp). I tried to undo changes and the installer froze."

=> That's a bug issue, maybe there is a problem on backing up once accidentally choosing something. Hopefully it will be fixed on the next version. To me, I hate the basic-textual debian installer in the beginning anyhow; a lot of things doesn't work properly with that. Ubuntu has nothing to do except using a different installer, it's all debian's responsibility. I would recommend debian forums, or for faster results : irc.debian.org #debian.

Cheers;
Onur

---

### Post by olliecampbell on 2006-01-06
I did the same, it doesnt actually destroy it so DONT DO ANYTHING!!!!


Get testdisk (its free - do a google for it) and put it on a floppy, create or get someone to create you a bootdisk.

Boot off that disk then insert the one with testdisk on and run that.

Complete an analysis of the disks and it will find the partitions, set the windows one as active (left and right arrows), write the changes to the disk

Before quitting get it to rewrite the MBR too.

Reboot, job done.

Youll loose the Grub (ie not get the option to choose linux or windows) and itll boot straight into windows.

I havent found a way to sort this out yet! Really annoying.

Im on a Thinkpad T42, and most people with this problem are!

---

### Post by kook44 on 2006-01-06
[QUOTE=olliecampbell]I did the same, it doesnt actually destroy it so DONT DO ANYTHING!!!!


Get testdisk (its free - do a google for it) and put it on a floppy, create or get someone to create you a bootdisk.

Boot off that disk then insert the one with testdisk on and run that.

Complete an analysis of the disks and it will find the partitions, set the windows one as active (left and right arrows), write the changes to the disk

Before quitting get it to rewrite the MBR too.

Reboot, job done.

Youll loose the Grub (ie not get the option to choose linux or windows) and itll boot straight into windows.

I havent found a way to sort this out yet! Really annoying.

Im on a Thinkpad T42, and most people with this problem are![/QUOTE]


I already tried booting from my winxp cd and running fixmbr.  didn't do anything.
I don't think we are having the exact same problem.  I had a 160g disk that was 1 large NTFS partition with winxp installed, and now it is 1 active NTFS partition that is ~243MB, and a large exentded partition that is the remainder of the disk.  It seems to me that if just the partition table is overwitten, and the actual data on the disk is untouched, I can resize that NTFS partition to fill the whole disk.  It starts to boot XP, then crahses.  Maybe because the rest of the boot information now lies in sectors outside of the 243MB NTFS partition???

It looks like there's no other way to restore it, so I'm just going to resize the partition and see what happens.

---

