---
title: "Desperate for help with serious installation problem"
date: 2009-06-01
forum: Installation &amp; Upgrades
---

### Post by Perspective on 2009-06-01
Hello, as a total beginner with Ubuntu and Linux.  I know a few essentials about Mac OS, but that's about it.  A while ago I bought an Asus Eee 1000H, because I could not afford a MacBook.  The operating system was Windows XP and I hated it a lot.  Surfing the net I came across ubuntu and liked the look of it.
Yesterday I downloaded the netbook remix and installed it as a double boot, using a 4GB CompactFlash card from my camera.  Everything seemed fine, I very much liked ubuntu and I deleted the os from the flash card, because I needed it for my camera again.  This morning, ubuntu told me to download a lot of important updates, but the partition for it was too small to download and install.  Because I had a partition programm in XP, I went back there and tried to make a larger partition for ubuntu.  I went out for a bike ride and when I came back, there was this message on the screen:
GRUB Loading stage1.5.
GRUB loading, please wait...
Error 22
I tried to reboot into XP but that us not available as an option any longer. 
Now I'm really stuck.  Is there any way that I can deal with this without having to buy an external cd drive or even Windows XP?  All I have available is a Mac, running Leopard 10.5.7.  I have already tried to install ubuntu on to this, to then make another flash drive, but because my drive is partitioned, bootcamp can't do another windows partition.
Any help would be very, very much appreciated.
Thanks and best wishes!
PS.  This was my stupidity, I know, and I have to say that I very much loved ubuntu, it was, while it was running an effortless and pleasant experience, free from all this patronising Windows stuff.

---

### Post by MichaelSammels on 2009-06-01
If you insert your Windows CD into the drive, and run the recovery console, you can restore the MBR to the HDD. I myself have no idea how to do this, but a quick Google should suffice. Hope this helps.

---

### Post by albinootje on 2009-06-01
> **Perspective said:**
> 
GRUB Loading stage1.5.
GRUB loading, please wait...
Error 22

Try SuperGrub from usb stick or cdrom :
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

See also here : [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by raymondh on 2009-06-01
22 : "Must load Multiboot kernel before modules"
This error is returned if the module load command is used before loading a Multiboot kernel. It only makes sense in this case anyway, as GRUB has no idea how to communicate the presence of location of such modules to a non-Multiboot-aware kernel

You now have to fix the MBR as it has been overwritten by GRUB, for you to access XP. 

Because it's a netbook, you'll need to make a flash drive for either the ubuntu liveCD or supergrubdisk.  You will need either of those to fix the MBR allowing you to boot into an OS.  Supergrubdisk is a good bet.

[http://www.supergrubdisk.org/wiki/SGD_Howto_make](http://www.supergrubdisk.org/wiki/SGD_Howto_make)
[http://www.supergrubdisk.org/wiki/SuperGrubDisk](http://www.supergrubdisk.org/wiki/SuperGrubDisk)

If you have an external CD drive and the win XP install disc, you can boot into that, navigate to a command prompt and fixMbr.

[http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console/](http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console/)

Good luck,

---

### Post by johnnylong on 2009-06-10
If this reaches you late, sorry, but I just came across your post and wanted to say that i ran into the same problem. There is nothing wrong with your windows install. The way I got around the problem was to re-install Jaunty and resize the partition making it larger when I reinstalled it.
I figure that I was not going to be using the windows partition as much as I was the Jaunty so I allocated it half of my hd (160GB) space. Since doing that I have to say I have had no problems whatsoever with either partition. Hope that helps.

---

### Post by presence1960 on 2009-06-10
> **johnnylong said:**
> If this reaches you late, sorry, but I just came across your post and wanted to say that i ran into the same problem. There is nothing wrong with your windows install. The way I got around the problem was to re-install Jaunty and resize the partition making it larger when I reinstalled it.
I figure that I was not going to be using the windows partition as much as I was the Jaunty so I allocated it half of my hd (160GB) space. Since doing that I have to say I have had no problems whatsoever with either partition. Hope that helps.

+1 

I would make another bootable usb from the Ubuntu iso and this time choose "try Ubuntu without any changes" when you boot off the usb. At Desktop  Go System > Administration > Partition Editor to resize your Ubuntu partition. Hopefully you defragged Windows prior to your original Ubuntu install. After making your Ubuntu partition larger you can try installing again. I would use the "manual" option at the Prepare disk space window of the partitioner.

---

### Post by presence1960 on 2009-06-10
> **MichaelSammels said:**
> If you insert your Windows CD into the drive, and run the recovery console, you can restore the MBR to the HDD. I myself have no idea how to do this, but a quick Google should suffice. Hope this helps.

he has a netbook-no optical drive!

---

### Post by raymondh on 2009-06-10
> **presence1960 said:**
> +1 

I would make another bootable usb from the Ubuntu iso and this time choose "try Ubuntu without any changes" when you boot off the usb. At Desktop  Go System > Administration > Partition Editor to resize your Ubuntu partition. Hopefully you defragged Windows prior to your original Ubuntu install. After making your Ubuntu partition larger you can try installing again. I would use the "manual" option at the Prepare disk space window of the partitioner.

Hey presence1960 .... are you thinking "cylinder limit" even with a newer HD and BIOS as found on netbooks?  Just curious as most times, I run into the limit on older machines/bios'.

Regards,

---

### Post by presence1960 on 2009-06-10
> **raymondhenson said:**
> Hey presence1960 .... are you thinking "cylinder limit" even with a newer HD and BIOS as found on netbooks?  Just curious as most times, I run into the limit on older machines/bios'.

Regards,

No, was thinking he needs to give ubuntu more hard disk space then reinstall. He said when it was running he got an error message that there wasn't enough space.

---

### Post by raymondh on 2009-06-10
> **presence1960 said:**
> No, was thinking he needs to give ubuntu more hard disk space then reinstall. He said when it was running he got an error message that there wasn't enough space.

aack ... you're right .... did not see that sentence *This morning, ubuntu told me to download a lot of important updates, but the partition for it was too small to download and install.*

Thanks.

---

