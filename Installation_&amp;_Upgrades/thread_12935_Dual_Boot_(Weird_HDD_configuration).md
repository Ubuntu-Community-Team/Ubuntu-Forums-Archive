---
title: "Dual Boot (Weird HDD configuration)"
date: 2005-01-27
forum: Installation &amp; Upgrades
---

### Post by Caligatio on 2005-01-27
I'm really new to the world of Linux and GRUB (used LILO once) and am a bit concerned about the fine points of installing Ubuntu onto my setup.

I currently have 2-80 GB SATA Maxtor Drives in a RAID 0 setup up using my onboard Sil controller with WinXP.  I have been reading that trying to install Linux on a BIOS created RAID array with a pre-existing Windows install is basically impossible.  So, I got a spare 30GB EIDE HDD from someone and decided to give this another shot.

My concern is as follows:  I understand somewhat what happens when you dual boot, the boot loader bascially attaches itself to the MBR.  However, since the MBR would be on a RAID 0 array I'm afraid that the Ubuntu installer isn't going to be able to read the MBR.  Anyone have any experience with this type of install?  I'm wary of dual booting to begin with, but then to be using a SATA HDD as the MBR, and THEN to have the MBR on a RAID 0 array on SATA drives makes me loose all confidence.  Any help with this would be MUCH appreciated.

---

### Post by Caligatio on 2005-01-28
So no one has any ideas? doh

---

### Post by Caligatio on 2005-01-30
I'm going to keep this bumped until someone at least tells me it can't be done  :(

---

### Post by TheGodFather on 2005-04-04
Hi,
I've an ASUS A7N8X Deluxe mobo with a sata sil controller, there are 2 maxtor 160Gb attached there in a raid 0 configuration.
I've installed a Debian sarge distro (with a 2.6 kernel) on this system with an existing windows Xp already installed onto raid. Everything works fine for months so I can say that it's ok.
The problem is that I wasn't able to install linux directly onto raid, I've taken a third ide hd, installed linux there, and then I've configured the new distro for device mapper, installed dmraid tools ([dmraid](http://people.redhat.com/~heinzm/sw/dmraid) ), moved everything to the raid partitions and edited the fstab accordingly.
Obviously you have to use an initrd image with right modules that loads dev mapper so you can mount your real root during the boot process.
At the time of my installation Grub wasn't able to boot from raid so I've used a patched version of lilo (I've downloaded the patch and recompiled lilo).

I'll post some link to faqs and howto when I come back at home  ;)
[COLOR=Red]
EDITED:[/COLOR]

here you can find many usefule information:
[Serial ATA (SATA) on Linux](http://linuxmafia.com/faq/Hardware/sata.html) 
[BIOS RAID support on Linux 2.6.x with dmraid](http://tienstra4.flatnet.tudelft.nl/~gerte/gen2dmraid/) 
[lilo-22.6-dmraid.patch](http://tienstra4.flatnet.tudelft.nl/~gerte/gen2dmraid/lilo-22.6-dmraid.patch)

---

### Post by FhaeTon on 2005-10-03
Wow I can see I'm not the only one with this type Issue. I was wondering if anyone else has there Hard drives set up like mine, I have 2 SATA WD drives on separate lines Primary & Secondary.

---

