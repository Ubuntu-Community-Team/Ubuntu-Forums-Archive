---
title: "Creating boot disk, not live cd"
date: 2009-05-17
forum: Installation &amp; Upgrades
---

### Post by Bramkaandorp on 2009-05-17
Hi all,

Here's my problem. I want to create a usb flash disk with Ubuntu on it, but when I do so with Unetbootin, it will create a livecd. I cannot install programs or drivers, I can only use it for system maintenance and installing.

So how can I create a boot disk usb flash drive, which will behave as a regular main drive? I want to use it to see whether my computer can show DVDs when Ubuntu is installed, and I cannot do that when I cannot install programs and/or drivers.

Thanks for your time.

Cheers,

Bram

---

### Post by Nasaki on 2009-05-17
The simplest way to do this would be using the USB Startup Disk Creater.
```
sudo usb-creator
```
Make sure to have the "stored in reserved space" box marked so that you create a persistent install. Again, this will create you a install, compressed in the same way as the live cd, but will keep all changes after a reboot.
If you want to do a uncompressed install, then you could simply reboot into a livecd and point the installer towards the usb drive. Although, I would recommend the former installation method simply because a uncompressed install would require 5gb+ flash drive.

---

### Post by Bramkaandorp on 2009-05-17
Space is not really an issue-my usb drive is 8 gig-, but I see your point.

Thanks for your help, I will get back when I have had time to test it.

Cheers,

Bram

---

### Post by Bramkaandorp on 2009-05-20
Well, it worked!

The only problem I get is that I can't install the graphical drivers. More specifically: I can install, but after rebooting, they seem not to have been installed at all.

I have no idea what it is, because all programs can be installed without problems.

My graphical card:

NVIDIA GeForce 9500 GT

Any ideas what can be wrong?

---

### Post by Bramkaandorp on 2009-05-24
Bump

As a bit of extra information:

I have had Ubuntu installed on my computer before, and I had the same problem.

Cheers,

Bram

---

### Post by sgosnell on 2009-05-24
Make the liveCD version on a USB drive, then use it to install to another USB drive or SD card.  Ubuntu will install to any drive, not just a HDD.  You can install and run the complete OS from a USB drive of any kind.  Just make sure that on the next-to-final screen, where you click Next (or Forward, or whatever) to install, first click on the Advanced button, and select the USB drive as the place to put the bootloader.  It will probably be (hd1), but make sure you get the right one.  DO NOT put it on (hd0), which is your internal HDD, or you won't be able to boot without having the USB drive connected.  You'll need to go into the BIOS settings and make the USB drive the first boot drive, or else the computer will just boot to the internal HDD, with whatever OS you have on it.  You might be able to press Esc at the first screen when the boot process starts, but maybe not.  Changing the BIOS settings is the way that works best for me.

---

### Post by Bramkaandorp on 2009-05-25
But what if I also have a second partition? Won't that automatically be hd1? If that's the case, would the usb stick be hd2, or am I making it too difficult for myself?

By the way: You opened my eyes! I have thought of doing this, but I never dared to, in case something would go wrong.

Cheers,

Bram

---

### Post by sgosnell on 2009-05-25
You do need to make absolutely certain you have the correct drive, of course.  A second partition on the HDD would be (hd0,1), with the first being (hd0,0).  You will be given choices, and the correct one might be sdb.  It all depends on your system, and I can't possibly see how yours is configured.  Just make sure the bootloader goes onto the USB drive, and it should work.

---

### Post by Bramkaandorp on 2009-05-27
I did it!

I have a USB boot disk, and I can play DVDs.

Sadly, the infamous Skatchup problems are in it. But I guess that's a problem which can be solved.

Cheers, and thanks a lot.

Bram

---

