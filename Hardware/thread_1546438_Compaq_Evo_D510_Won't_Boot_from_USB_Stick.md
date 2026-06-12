---
title: "Compaq Evo D510 Won't Boot from USB Stick"
date: 2010-08-05
forum: Hardware
---

### Post by jmrank on 2010-08-05
Hi all... this isn't really an Ubuntu question, but I'll ask it anyway in the hopes somebody can help.

I have an old Compaq Evo D510 desktop that I have removed the hard drive from.  I booted from an Ubuntu 8.10 install CD, and installed via the wizard to a 16G USB stick.  The install went fine, everything seems to have worked, and at the first reboot, booted correctly from the stick.

Every subsequent reboot, though, will not load.  I get the BIOS message that it's attempting to boot from USB, but it appears it's not finding the mbr on the stick.  In the setup, the stick shows up as "0.00 MB" (I'm assuming because the BIOS doesn't recognize the filesystem type, but that shouldn't matter... grub should load itself, no?).

Here's what gets me... if I put the stick in my HP laptop and tell it to boot from USB, it works fine.  The only difference is that the HP laptop has a hard drive, and has Ubuntu 9.10 on it... but if it's booting "from the USB stick," that shouldn't matter, right?  In the laptop, I get the older grub messages and it boots to 8.10, so it doesn't appear to be using anything from my HDD.

Ideally, I'd be able to put the stick in the desktop and boot from it without a hard drive.  Any thoughts from anybody?

---

### Post by lukeiamyourfather on 2010-08-05
> **jmrank said:**
> 
Ideally, I'd be able to put the stick in the desktop and boot from it without a hard drive.

That's not really a good idea. Also try the latest version of Ubuntu.

---

### Post by vbsaltydog on 2012-04-06
I know this is an old thread but I am having the same issue as the original poster and I am looking for a solution. 

I have a Compaq Evo D510 CMT that I am trying to boot from a USB stick that has Ubuntu loaded on it. If I boot from an Ubuntu live CD, the USB volume is present and the USB stick has an orange light on it but when I try to boot to the USB I get the old "non system disk" error and the USB stick is never illuminated suggesting that the USB ports are not active during the boot process. Any ideas on how to get this system to boot from a USB stick?

Thank you

---

