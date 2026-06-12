---
title: "Installing onto a USB Hard Drive"
date: 2009-06-08
forum: Installation &amp; Upgrades
---

### Post by OliverBarker on 2009-06-08
To make it as simple as possible, I have a MacBook 1.83Ghz 2Gb Ram with an external 60Gb hard drive that was originally inside it (replaced and bought a case for it). It there anyway I can install, run and boot Ubuntu 9.04 from this USB Hard Drive? It is an Intel Mac so should be able to boot from it, but would Ubuntu be able to install onto it? What partition settings to I need etc. Since this is via USB what system if not Ubuntu would you recommend that I install to get the best performance?

Thanks for the help if you reply!

---

### Post by Mighty_Joe on 2009-06-08
> **OliverBarker said:**
> but would Ubuntu be able to install onto it? 
Yes.  I run Ubuntu from an 8Gb USB flash drive.

> **OliverBarker said:**
> 
What partition settings to I need etc. 

Since I have a small drive, I use the whole drive as an Ubuntu partition.  If you have a lot of RAM (say, 2Gb+), skip the swap partition, since swapping across USB will be tedious.
A full Ubuntu install takes a little over 2Gb, so create a partition between that and your entire drive, depending on what else you need it for.
Make sure you install the Grub bootloader to the USB drive (on the last step of the installer, click "advanced").  If you don't you'll have to have the USB drive plugged in to boot OSX.

> **OliverBarker said:**
> 
Since this is via USB what system if not Ubuntu would you recommend that I install to get the best performance?


I use regular old Ubuntu on my flash drive.  Flash drives are quick to read and slow to write, so loading programs into memory is tolerable.  I don't know if it is different for USB hard drives.  There are some other steps you can take to improve performance, like moving logging to tmpfs.

---

### Post by OliverBarker on 2009-06-08
Thanks for the quick reply, however does it make a difference that I'm using an external hard drive than flash memory?

---

### Post by sabre2th on 2009-06-08
> **OliverBarker said:**
> Thanks for the quick reply, however does it make a difference that I'm using an external hard drive than flash memory?
I don't see why there'd be much of a difference.  If anything, you'll be better off because you have more storage space and don't have to worry about wearing out your flash.

Just make sure you can boot from a USB device.  Not everybody can.

---

### Post by OliverBarker on 2009-06-08
Ok, thanks for the advice. So basically I go through the installation process as if It was the main hard drive, and do I need bootloader?

---

### Post by Mighty_Joe on 2009-06-08
You need a bootloader and it must be installed to the USB drive, as I said above.

---

### Post by OliverBarker on 2009-06-08
OK well I installed Ubuntu onto the external drive, it said completed and I needed to restart. So I please ok, and I get the folder with a question mark on it. I press and hold the power button (MacBook) to get it to turn off but everytime I turn it on again I get a white screen. The only way I can get onto any sort of OS is by plugging in the 9.04 Live CD that I burnt to install. I am on it now, and jesus its slow. Please help. I've been looking around and noticed the rEFIt loader thing, however I need the CD to get onto the operating system and am not on OS X so how can I download and install this? Or otherwise fix the problem.

---

### Post by Mighty_Joe on 2009-06-08
The LiveCD has an option to boot from the first hard drive. Does that work and get you to OSX?
I don't have a macbook handy to test.  Is there a way to specify to boot from USB?  On a PC, one would use the BIOS or a boot device menu.

---

### Post by Dan_Dranath999 on 2009-06-08
I have tried 4 times to install Jaunty on a Toshiba 2.5 hard disk (it was supossed to replace a laptop's hard drive, but the laptop died, so i bought a case and made it external)

I have tried to boot the thing on 3 different machines: none of them will boot the external disk. All 3 of them have the "boot from USB" on the BIOS

I even entered in the advanced tab when installing: I had 3 options---
 install grub on sdg, sdg1(/ - partition), sdg2(/home - home partition)

I always choose sdg

---

### Post by OliverBarker on 2009-06-08
Dan, what are you on about? lol Joe, when I try to do that I simply get the flashing cursor in the top right.

---

### Post by Dan_Dranath999 on 2009-06-08
flashing cursor in the top right?

you mean the first option? (hd0)

---

### Post by Mighty_Joe on 2009-06-08
Bummer.  Try starting with the [Mac community support page]("https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages") and the [Ubuntu Apple Support forum]("http://ubuntuforums.org/forumdisplay.php?f=328"). Maybe there's something Mac-specific that we're overlooking.

---

