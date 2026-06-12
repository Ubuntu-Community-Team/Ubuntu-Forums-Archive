---
title: "2 hard drives, dual boot question"
date: 2006-01-27
forum: Installation &amp; Upgrades
---

### Post by loraine0622 on 2006-01-27
this may seem like a dumb question, but i'm a semi-newbie, so here goes.  i have 2 hard drives and an external hard drive.  i really want to be able to boot from either of my internal hard drives.  i have simply mepis on hda, and unbuntu 5.10 on hdb, and no os on the external hard drive.  right now i just want to be able to choose which os to boot, can i do that, and how do i do that.  not sure what i'm going to use the external for right now, but if i wanted to us is for an os, could i do that, and how to boot from that.  

thanks for any help, i have completely converted to linux and like ubuntu os the best so far.

loraine0622

---

### Post by canadianwriterman on 2006-01-27
When you installed Ubuntu on hdb, the Ubuntu install process should have written a GRUB boot menu into the master boot record on hda. So, when you boot up, it should give you the option of booting into either Mepis or Ubuntu.

---

### Post by aysiu on 2006-01-27
First of all, having used both Ubuntu and Mepis extensively, I know they *both* ask whether or not you want to install Grub to the MBR. So which installed Grub to the MBR? And if both did, who installed it last?

If you're not sure, you can look to see whether your boot menu is white with blue patches or just plain black. The former is Mepis. The latter is Ubuntu. If you don't want to bother checking, pop in Mepis and open the Mepis OS Center (password:root) and then choose to reinstall Grub and reinstall it to the MBR.

While you have Mepis open, mount the Ubuntu partition and open Ubuntu's /boot/grub/menu.lst. Copy the relevant entry from that to Mepis' /boot/grub/menu.lst.

Don't just copy and paste, though. Make sure they're in the same format. I think one makes the drive location (hd0,0) separate from the kernel and initrd.

---

### Post by crhooker on 2006-01-31
[QUOTE=canadianwriterman]When you installed Ubuntu on hdb, the Ubuntu install process should have written a GRUB boot menu into the master boot record on hda. So, when you boot up, it should give you the option of booting into either Mepis or Ubuntu.[/QUOTE]

I have something of a similar issue but a diffrent OS (XP). I installed Ubuntu on an 80Gb disk, it owns the whole disk. I have decided that I need XP for some things so I went and got a 300Gb drive ($90 at Circuit City - what a deal!). I disconnected the Ubuntu drive, plugged in the new one, installed XP to a 50Gb partition and will format the remainder for data. I had hoped to use a boot manager program I found at sourceforge but no luck so...

I am thinking my config would be the XP disk as master and the Ubuntu as slave. I am not interested in resetting my BIOS everytime I want to boot XP.

It seems to me based on what I have read here and in other threads the quick fix might be to reinstall Ubuntu on the 80Gb drive (hdb) and let GRUB write the MBR on the 300Gb disk? Of course if I can edit the GRUB file, put the Ubuntu disk as master and the XP disk as slave that would be fine too. I realize this is probably possible given the posts I have read. I have also seen posts about editing the boot.ini on the XP disk. I am just confused on what to do.

I really have read a ton of posts and know not quite enough of what to do at this point.

Thanks

carl

---

