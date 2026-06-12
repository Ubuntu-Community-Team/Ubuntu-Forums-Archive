---
title: "removing a HD"
date: 2007-07-31
forum: Hardware &amp; Laptops
---

### Post by beelz on 2007-07-31
Hello, I am having a problem removing a hard drive from my desktop pc. I installed Windows XP on my primary master and then installed an Ubuntu L.A.M.P. server on my secondary master. Both operating systems boot fine, until I try to remove my primary slave so that I can put it into an external enclosure. The boot loader, grub, gives me an error code of 22 with the secondary master removed and no other options on start up. To make matters worse I have tried to boot into the live Desktop cd and I get what seems to be an infinite loop of read errors. The cd rom is fine. I don't want to lose my fully configured L.A.M.P. server or the Windows installation. Any suggestions?

---

### Post by logos34 on 2007-08-01
sounds like grub installed to the windows drive, in which case stage1 is trying unsuccessfully to find /boot/grub on the secondary master drive you removed.   You could try reinstalling grub to the Ubuntu drive (MBR or root partition), restore windows bootloader to the windows drive, then set the ubuntu secondary master drive as first in the bios boot order.  Modify the windows entry in menu.lst [per this guide]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk") and you should be able to boot both from grub when the ubuntu drive is connected, and from windows (-->ntldr) when it is not.

---

### Post by fredj on 2007-08-01
What made you think you could do any of these things in the first place without having to reinstall?

---

### Post by beelz on 2007-08-01
Well, it was the first time I installed Linux. It also happened to be the first time that I installed it on a computer with another OS. I'm not saying that I didn't make mistakes when I first installed it almost a year ago, it's just how it is and I would like to keep it that way, minus a secondary storage device. You have to understand that all of my previous experiences were with Microsoft operating systems. There are certain things that I never had to consider when using Windows. I like Linux and I want to keep using it. 

By the way, I don't think that I installed grub on drive C, the XP partition. /boot/grub is on the same disk that the Ubuntu filesystem is on. My hard drives are as follows:

**Primary master**-
Partition 1: Windows XP, ntfs
Partition 2: Storage, ntfs

**Primary slave**-  
Partition 1: Storage (this is the one I want to remove), ntfs

**Secondary Master**: 
Partition 1: /boot is on here, partition is only ~430 mb
Partition 2: labeled "Free space not available" ~74 gb

I don't entirely understand what I have done here. The secondary master was split in to 2 partitions, the first I believe is where the boot loader is installed. I have been saving far more than 430 mb to a drive with Ubuntu, and since the ntfs partitions are not mounted it must be on the 2nd partion of the secondary master (80 gb IDE drive) where Ubuntu is installed. 
                  

device.map contents as found in /boot/grub/

(hd0)   /dev/hda
(hd1)   /dev/hdb
(hd2)   /dev/hdc

---

### Post by beelz on 2007-08-01
Something else strange happens. I have a cdrom in yet another external enclosure (IDE to usb 2.0). I have to unplug it to keep grub from hanging on start up.

Reinstalling Ubuntu and configuring the L.A.M.P. server won't be that difficult, and I won't mind doing it so long as I don't have to reinstall Windows as well (that's just pushing it). If it is worth it just to start over what would you suggest this time? I have never had these problems before and I don't think the boot loader hanging just because something is plugged into a usb port sounds reasonable.

---

### Post by logos34 on 2007-08-01
> /boot/grub is on the same disk that the Ubuntu filesystem is on

Right.  But that doesn't necessarily mean that Grub (i.e. the 512 bytes stage1) is installed there too, either on the MBR or first sector of the root partition. In fact, given this 
> 
**(hd0) /dev/hda**
(hd1) /dev/hdb
(hd2) /dev/hd

it looks as though the windows drive is (or at least was at time of ubuntu install) first in the bios harddisk boot priority, and thus you are in fact booting to that--grub is there.  (which would be normal because grub by default installs to the mbr of hd0).  But it needs to access stage2 and menu.lst in /boot/grub on the ubuntu drive, so when you take that out, bam, error.

check what drive is listed first in the bios

you shouldn't have to reinstall the whole OS  

edit: or rather, maybe you will--wtf happened to root? I see you have a separate /boot partition:

Secondary Master:
Partition 1: /boot is on here, partition is only ~430 mb
**[B]Partition 2: labeled "Free space not available" ~74 gb**[/B]   ???

---

### Post by beelz on 2007-08-05
Since my last post I have reinstalled an updated version of Ubuntu (7.04 vs 6.06) and saved my xp installation. On my second traversal of the installation process I discovered that there was absolutely nothing wrong with the way I had it set up before, actually I had little choice in the matter. Editing the boot record on any other partition but the primary master would be inviting trouble for me. Also, when Ubuntu divides the selected installation drive into two partitions it is perfectly normal.

---

### Post by beelz on 2007-08-06
This is what I did. I used grub to boot into my XP installation and then used a utility to wipe out Ubuntu on the secondary master and move a bootable copy of it there. I then changed my boot sequence to boot from the secondary master, and the XP copy, and wiped out the original XP installation on the primary master. I then installed Ubuntu, and the grub boot loader on the primary master. I can now either use grub to boot Ubuntu or Windows XP or just change the boot sequence to the secondary master first and bypass grub and Ubuntu altogether and just boot Windows.

It may have been kind of like doing a brain surgery with a spoon but it got the desired results. I can take out any other devices without grub complaining.

---

