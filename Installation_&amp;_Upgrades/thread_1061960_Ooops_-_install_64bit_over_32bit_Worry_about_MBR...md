---
title: "Ooops - install 64bit over 32bit? Worry about MBR..."
date: 2009-02-06
forum: Installation &amp; Upgrades
---

### Post by deadmanschest on 2009-02-06
Hi all - my first post, looks like a small screw-up that I want to avoid turning into a bigger one...

Complete noob to Linux/ Ubuntu. I set up a new laptop with Vista x64 pre-installed, partitioned single 320 GB HDD into 60GB primary for Vistax64, 10GB unallocated for Ubuntu (no swap file as 4GB ram on Centrino dual core and didn't want to use up all my partition choices right away),then a big extended partition of 250 odd GB with logical partitions for media and backup images, all in Fat32 so usable with all systems.

Problem - partly Ubuntu's fault - as the .iso download page is too big to realize there is an Options field below with a choice of 32bit or 64bit...duh.

So, I had dl'd and burned the 32bit.iso and installed U8.10 into the unallocated 10GB, sweated a bit on the boot loader part, but seemed to work out okay, and now have a dual-boot option with GRUB that must be installed into/over the Vista loader?

So far so good, but the Ubuntu desktop didn't work very well, and I started to look for answers and realizied maybe I should have installed the 64bit... 

Problem - I just figure to wipe the 10GB (second) partition and re-install the 64bit Ubuntu .iso, but what is going to happen to my MBR?

Options - do nothing, but Ubuntu freezes up a lot; Wipe the partition, restore a Ghost image of Vista and hope it rebuilds m y stock MBR; or use the Vista disc to repair the startup process;
Just install 64bit over the existing (like an upgrade..);

My gut feeling - go back to ground zero, wipe Ubuntu, rebuild the stock Vista64 MBR and try again...

Any wisdom to impart?

Thanks in advance!

dmc

---

### Post by oldos2er on 2009-02-06
I can't see any point in using Vista to restore your MBR, only to have a new Ubuntu install overwrite it again. Are you able to boot into Vista via grub? Your post is not terribly clear.

---

### Post by deadmanschest on 2009-02-06
> **oldos2er said:**
> I can't see any point in using Vista to restore your MBR, only to have a new Ubuntu install overwrite it again. Are you able to boot into Vista via grub? Your post is not terribly clear.

Hi - thanks for the response. I thought it was clear...If I wipe the Ubuntu partition, I doubt that it will edit the GRUB loader out of my primary Vista disk loader and revert to my stock Vista setup.

So, I assume that I will have a Vista machine with a GRUB loader that defaults to a non-existent Ubuntu. I don't want to end up with a GRUB that has multiple Ubuntu versions and have to edit it manually. 

Right now Vista works great, the dual boot works great, but Ubuntu sucks, as it freezes and in non-responsive.

I probably have worked it thru enough in my mind that I will wipe the Ubuntu partition completely, rebuild the stock Vista MBR and start again when I get the inclination.

Thanks!

dmc

---

### Post by deadmanschest on 2009-02-06
Changed my mind, just installed the x64 package by formatting over the existing 10GB linux logical partition and installing into same, worked fine.

Vista believes that its start up process is perfect, so I guess that the GRUB loader is in the Ubuntu partition and never touched my original MBR.

Cheers

dmc

---

