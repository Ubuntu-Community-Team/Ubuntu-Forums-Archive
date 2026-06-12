---
title: "Syncing iPod touch?"
date: 2008-09-26
forum: General Help
---

### Post by Viridia on 2008-09-26
Ok, here's my issue. I have an iPod touch, and I'm about ready to buy an XPS m1330 with Ubuntu. I also have an XP CD. The laptop comes with 4 GB's of RAM. I want to virtualize XP, and dedicate 2 gigs of RAM to each OS. Now, I have my iPod touch, which I'm not willing to jailbreak it. Could I run iTunes in my virtualized XP and sync my ipod with it?

Or, if I had a virtualized XP, could I just boot into XP alone and use iTunes?

Thanks

---

### Post by defishguy on 2008-09-26
> **Viridia said:**
> Ok, here's my issue. I have an iPod touch, and I'm about ready to buy an XPS m1330 with Ubuntu. I also have an XP CD. The laptop comes with 4 GB's of RAM. I want to virtualize XP, and dedicate 2 gigs of RAM to each OS. Now, I have my iPod touch, which I'm not willing to jailbreak it. Could I run iTunes in my virtualized XP and sync my ipod with it?

Or, if I had a virtualized XP, could I just boot into XP alone and use iTunes?

Thanks

Wow, I have an m1330 with Vbox 2, a virtual machine with XP Service pack 3 and I just got my iPod Touch to sync for the first time.

After you install XP it probably will not have the USB controller drivers installed.  Open the device manager in XP (right click on my computer and select manage) find the yellow bang on the USB Controller, right click and then select update drivers.  Mine was able to download the intel drivers from the intertubes.

Follow this thread in the vbox forums:

[http://www.virtualbox.org/ticket/491](http://www.virtualbox.org/ticket/491)

The user crobe found the most expedient solution:

> OK, was a piece of work but I got it now.

[http://www.speedshare.org/download.php?id=1A5FEE2413](http://www.speedshare.org/download.php?id=1A5FEE2413) ( I hope its legal to post it here ) is a usbcore.ko module for Ubuntu linux-image-2.6.24-21-generic.

Go to /lib/modules/2.6.24-21-generic/kernel/drivers/usb/core, backup your current module, get mine, put it there, run "depmod -ae", run "update-initramfs -u" and reboot. Everything as root ( use sudo ).

Works perfectly with iTunes 7.7 and my iPod Touch 2.0.2.


The file path that you will copy the driver to might be different.  You can type > uname -r in a terminal window to determine what your current kernel is.

I have downloaded the usbcore.ko file so if the download fails, gets deleted or otherwise doesn't work let me know and I'll email it to you.  This works with iTunes 8 and the latest 2.1 firmware for the iPod.

---

