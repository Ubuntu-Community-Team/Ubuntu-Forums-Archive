---
title: "Breezy Install and Live CDs hang immediately"
date: 2005-12-18
forum: Installation &amp; Upgrades
---

### Post by yaddoshi on 2005-12-18
"Uncompressing Linux... Ok, booting the kernel"

That's as far as I get before it hangs - and I get the same message from the Warty install CD that I used to install LINUX on my wife's custom PC a few months ago, although on her system I had no problems whatsoever.

I'm trying to install on a Medion Akoya LS notebook, (which is really a MSI S260 notebook with a couple Medion stickers on it), I've disabled Legacy USB support in the BIOS, disabled the Intel Speedstep, disabled the wireless, changed the shared video RAM from 8MB to 1MB, and unplugged all USB devices, all to no avail.  The install hangs in the same place every time.  Unfortunately there are no other BIOS configuration changes I can try - in fact I'm rather disappointed with the lack of config options.

What's odd to me is that I made a backup copy of my Windows XP Install CD using the exact same brand of CD-R (Maxell 700MB for Audio) and it loads properly - it never hangs.

This notebook also has a built in 3-in-1 Media card reader, I don't know if that makes any difference but I thought I would mention it.  I have no config options to control it in the BIOS.  The notebook has a Samsung brand CD-RW/DVD-ROM drive, maybe someone else has had problems with similar drive types?  I've been perusing the forum but it seems that everyone's install gets farther than mine before it hangs.

I'm on my way to the store to seek out different brands and sizes of blank CD-Rs  to make a new install disc, and I'm also planning on slowing down the record speed to see if that makes any difference, and hope to get a BIOS update installed (which is a big pain with no floppy drive) but in case anyone else has any other ideas I thought I'd put this out here.

---

### Post by Darkhack on 2005-12-18
Sorry I can't be much of a help, but one thing I would think about doing is downloading some other distrobutions and see if you get any farther.  A LiveCD will work if you don't want to install to the hard drive.  That may or may not give a little insight as to what the problem could be.  It may be a kernel issue with the version that Ubuntu is using or it could be an issue with either your CD Drive or the motherboard.  Try googling your laptop and see if there are any firmware updates for the cd drive.  If you have a phone number you could call tech support and see if they know anything about its ability to run Linux.

Other than that I can't really be much of a help.  Usually if its a configuration issue it would atleast get farther than the decompression message so I don't know what I could tell you.  Maybe you'll have better luck on another distrobution or you could try the FlightCD for Dapper.

---

### Post by yaddoshi on 2005-12-20
Oddly enough, I found your suggestion to Ibizibi ([http://www.ubuntuforums.org/showthread.php?t=103423](http://www.ubuntuforums.org/showthread.php?t=103423)) helpful, as I followed your thread link to [http://www.ubuntuforums.org/showthread.php?t=81153](http://www.ubuntuforums.org/showthread.php?t=81153) .  Using the full string (boot: linux noapic pci=irqroute pci=noacpi acpi=off irqpoll) I was able to get to the language choice screen, followed by the location and keyboard type choice screens.  Regretfully the installation hangs at 4% while testing the CD-ROM.  I burned another boot disk with different media, but perhaps I'm using another CD-R media type that's not quite agreeable with my drive.  I've got a few other brands to try before I give up entirely, although I'm considering heading back to the store and just paying for the Sony brand.

I also checked for firmware updates, but unfortunately my drive is not supported by the manufacturer (Samsung) because it was sold direct to Medion as a 3rd party vendor, and guess what...Medion doesn't have a firmware update for anything but the BIOS.  Since I installed that update before trying to install Breezy, part of me thinks that BIOS update is what is causing some of these issues.  unfortunately their utility did not give me the option to back up the old BIOS and Medion's tech support refuses to help me recover it.  I've found another BIOS for this model straight from MSI (verified the motherboard model number first of course, MS-10121) but I've been unsuccessful in trying to make a bootable CD that will allow me to boot to DOS with CD-ROM support and then not hang while trying to install MSI's BIOS.  In case you can't tell I'm not very fond of Medion's support center at the moment...but I've yet to find any computer manufacturer that offers decent support...and I digress.

I initially tried boot: linux irqpoll as you suggested to Ibizibi, but the installation hangs at the same point as it does without parameters, even with the newly created CD-R.  I have no control over IRQs in my current BIOS, which is an AMI BIOS, so that's out.  The reason I thought it might work on this unit is that it appears the 3-in-1 Card Reader is treated as multiple USB devices for some insane reason.  Unfortunately it cannot be disabled.

I am curious as to whether I could use just a part of the full string, or if it is necessary to use it in its entirity.

Anyway - thanks for sharing the info, it's nice to get a little farther in the install, even if it's not much farther.  Now I know it's either the drive or the media that's causing the hang, so first I'll try different media, and failing that, maybe it's time to ask Santa to bring me an external DVD+-R drive...

---

### Post by yaddoshi on 2005-12-21
Quick update - tried 4 different CD-R media brands (Maxell, HP, Memorex and Verbatim), oddly enough the Maxell got the furthest into the install (16% while scanning the CD-ROM).  Still need to buy some Sony media to see if that makes any difference.

Also downloaded Debian version 3.0 R1 last night and just burned it to an HP CD-R, its installer ran fine without having to add anything to the boot: prompt.  Weird.

Anyway - I'd rather have Ubuntu running, so that's what I'm working with.  If anyone feels the need to comment with ideas that I haven't thought of / tried yet please do.

---

### Post by yaddoshi on 2005-12-21
Woot!

Purchased a Sony CD-R, burned a Breezy boot CD at the slowest speed possible (4x), tried again, using "boot: linux noapic pci=irqroute pci=noacpi acpi=off irqpoll", and again it froze while scanning files on the CD-ROM, at 6%.

So I was depressed for a while, and figured I would just install Debian, then realized that I had picked Woody, not Sarge, and it wouldn't allow me to change the size of my NTFS partition without using some 3rd party software such as Partition Magic.  Which put me back into aggravation mode, especially because I knew that Ubuntu would allow this - ARGH!!!

So I did a search for LINUX IRQPOLL in Google, and found a post somewhere in this forum that explained that apic was meant for multiple processors.  Then I realized I have a Pentium M processor, and remembered that in 2003 Intel introduced processor technology that simulated multiple processor performance with only one processor.

So here's where it gets interesting:

By using "Boot: LINUX NOAPIC" I was able to complete Breezy's installation with no other difficulties.  It even automatically detected the built-in WIFI adapter.  I write this post from my newly installed Ubuntu OS.

So for those of you out there trying to figure out why you're getting a hang during installation I recommend trying only one of the following at a time:

Boot: linux noapic  (especially if you have a Pentium IV or newer Pentium class processor)
Boot: linux pci=irqroute
Boot: linux pci=noacpi
Boot: linux acpi=off
Boot: linux pci=acpi
Boot: linux nolapic
Boot: linux framebuffer=false
Boot: linux irqpoll

Combining these all at once was what was causing me to lock up during the install, even though it got past the initial load screen.  Just thought I'd mention it in case anyone else has similar issues.

:D

---

### Post by htoerrin on 2006-01-04
THANKS!

By changing from "pci=noacpi" to "noapic" I am able to operate the RF kill switch on my S260!

Havard

---

