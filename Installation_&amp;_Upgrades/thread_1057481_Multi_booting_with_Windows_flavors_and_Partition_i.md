---
title: "Multi booting with Windows flavors and Partition issue"
date: 2009-02-01
forum: Installation &amp; Upgrades
---

### Post by MightyDingus on 2009-02-01
I have XP, Vista, and Windows 7 all installed and working on a 500gb laptop drive. I booted to the Ubuntu 8.1 live cd, used Gparted to format the remaining freespace (65gb) to ext3 so I can install Ubuntu to it. 

When I go through the install, I get to the Prepare Partitions screen, it's blank, showing no drives, partitions, etc. Obviously, it's impossible to move forward from there. 

I previously tried leaving the free space blank and unformatted, but the installer would only let me take free space from my Windows 7 partition (150gb), and wouldn't let me select the empty free space on the drive. After formatting the freespace, the partitioner doesn't show any drive info at all.

How do I get it to let me select the free space formatted to ext3 for the install? 

Also, since I already have XP, Vista, and Windows 7 installed, will the grub loader simply add Ubuntu to them? I know it's this simple with dual booting XP/Vista/Windows7 with Ubuntu. I just want to make sure it's the same with Quad booting. 

Any help or suggestions will be greatly appreciated to a Linux noob. 

Thanks.

---

### Post by MightyDingus on 2009-02-01
Looks like I have this partially figured out. If I mount just the XP, Vista, and Windows 7 drives, then it only gives me the remaining space to install to. I've learned my first thing about Linux... :D

I'm worried about the boot loader issue, so I'm installing to an external 80gig USB hard drive, and putting the Grub boot loader on the external drive too. That way I can choose to boot from the external USB drive in the BIOS to get to Ubuntu, otherwise it'll boot to my default Windows installation. 

It's installing to the external drive now. Hopefully, this will work well and I'll be able to play with and learn Ubuntu off the external drive. The only issue/problem I see with this is the degraded drive performance since it's USB. Other than that, it'll work fine in theory. 

I'll let you know how it works out.

---

### Post by MightyDingus on 2009-02-02
Looks like I have it working off the USB hard drive. Unplug the drive, drops right back to Windows installations. Best of both worlds. I think I'd rather have this installed on a USB flash drive so I can keep it with me. I'll pick up a 32gb drive so I have plenty of space. 

Is it possible to move all my programs and settings over to the USB flash drive installation, or move the entire installation over?

---

