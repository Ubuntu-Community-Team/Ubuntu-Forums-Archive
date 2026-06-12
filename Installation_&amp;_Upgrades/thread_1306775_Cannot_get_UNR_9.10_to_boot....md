---
title: "Cannot get UNR 9.10 to boot..."
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by fart_flower on 2009-10-30
I've been wanting to try UNR 9.10 on my Eeepc 1000, but it will not boot from either SD card or USB stick.  The MD5 is correct -- I even burnt it to CD and successfully booted it on my desktop computer.

However, the Eeepc does not recognize UNR as bootable.  Fedora 11 boots from SD card and USB stick, Moblin 2.0 boots from  SD card and USB stick, but UNR doesn't do anything.  I've tried a variety of iso-to-flash installers, but no luck with any of them.  (I even tried using them with the existing Fedora 11 install on my Eeepc.)

It's not a problem with the media, as I reinstalled Moblin 2.0 and it booted fine.

Any ideas?

---

### Post by fart_flower on 2009-11-01
I just tried making another "bootable" image using my parent's Vista machine.  Still does not boot.  Wonderful.

---

### Post by wilee-nilee on 2009-11-01
Have you tried deleting the partition on the SD card or USB stick then installing a fresh fat32 then doing the iso to plugin. Your SD card or USB stick may have extra stuff in there that you don't see even with show hidden files enabled. The USB installer will format it for you if it is wiped clean I believe just wipe it with gparted then format it to fat32 try that if that doesn't work try the USB installer format.

---

### Post by fart_flower on 2009-11-01
Yes, I've reformatted no less than four different SD Cards and two different USB sticks.  The problem can't be at my end.  Fedora and Moblin boot just fine.  However, I really wanted to try UNR, but I can't be bothered to waste any more time.

---

### Post by fart_flower on 2009-11-01
I ran into another forum where someone else was having a similar problem.  The answer was to install UNR 9.04, then do an upgrade to UNR 9.10.

Yes, UNR 9.04 booted without problem on the first try and I'm now in the process of upgrading.  In other words, something *MUST* be goofy with the UNR 9.10 ISO.

---

### Post by DigitaLink on 2009-11-01
I used the 9.10 UNR iso and installed it to microSD through a USB adapter using UNetBootin.  Had zero problems with it.  Only issue I've had on an Acer Aspire One is the bug where they SD slots aren't hot swappable unless there is a card in them at boot.  Solved that with an edit of grub.cfg.  Everything is workin' great.

How were you putting the UNR installer on your media?

---

### Post by fart_flower on 2009-11-01
I used a variety of programs and methods on both my desktop Ubuntu 9.10 and the then installed Fedora 11 on my Eeepc 1000.

My adventures began with the methods described on ubuntu.com, and eventually included all sorts of things -- Unetbootin, USB-creator, a handful of Vista programs, and whatever else, including the script thingy for Mobiln 2.0 and image-writer, even though those latter two are only for IMG files.  (But hey, I had nothing to lose.)  Hours and hours of wasted holiday time.  Ugh.

On the upside, UNR 9.10 does live up to it's positive reviews.  Despite the major installation woes, the OS is perfect for this sort of a device.

---

