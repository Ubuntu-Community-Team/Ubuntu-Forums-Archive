---
title: "Booting from USB is not supported"
date: 2011-03-01
forum: Hardware
---

### Post by Zucriy Amsuna on 2011-03-01
I recently got a used netbook; and it already had Ubuntu installed. However, the username is kathy, and I keep finding that it's a hassle just to change the main username. I didn't want to bother with that, so I reset the BIOS (because of an unknown password) to allow USB booting. But it doesn't have it! It's an old 2002 computer (or at least that's what the BIOS resets to). Also, the CD drive doesn't work. I keep finding ways to do it with floppy drives, but this is a netbook...

So how would I be able to re-install a Linux distribution (probably Ubuntu)? Is there a way to force USB booting? Is there a program to do it (I've heard of a Windows one)?

(I didn't know if this should be in the installation section or this section.)

---

### Post by dabl on 2011-03-01
In 2002 there weren't any netbooks.  The BIOS date may be 2002, that just means it was never updated.  One thing to do is to visit the OEM's tech support web site and see if there's a more recent BIOS for that model of laptop.  If it has a working floppy diskette drive, then you can probably flash the BIOS from a booted DOS floppy (read the instructions on the web site!).

If it truly has no ability, even after updating, to boot from USB device, then you are stuck with floppy boot diskettes, unless you can come up with a fix for the optical drive.  For example, if the optical drive is a PATA/IDE device, and you can borrow someone's computer with a working PATA/IDE optical drive, then you can just connect your IDE ribbon cable to the borrowed optical drive for as long as you need it to install a new OS.

You are permitted to state the actual brand and model of the laptop, by the way ...

---

### Post by Zucriy Amsuna on 2011-03-01
It is an Averatec 1000 series. The WinXP sticker says 2004. It has two USB ports, a CD drive that doesn't work (wodim --devices shows that something is there, but it doesn't eject or do anything), Internet ports, a VGA port and nothing else. There is no floppy drive.

I can't find how to update the BIOS. Would something like this possible work? [http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html](http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html) I don't think step 3 would work...

---

### Post by fjgaude on 2011-03-01
Most computers have a F-key, e.g., F12 or F4 that shows a menu as you just boot up to boot from other than the hard drive. Have looked into what that key might be. You would tap it just as the machine starts to boot.

---

### Post by nerdy_kid on 2011-03-01
if you are sure that the said pc can not boot from usb, then maybe try this:  [http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)
That will allow you to boot from usb, but I have never used it, or read the documentation on the site and dont know how hard it is to set up.

---

### Post by dabl on 2011-03-01
Page 4.8 of the users manual for the Averatec 1000 shows a BIOS screen shot of "Boot Menu", and it shows "USB Hard Drive".

 :rolleyes:

---

### Post by egeezer on 2011-03-01
@nerdy_kid: You should try it - PLoP can easily give old computers the option of booting from USB.  PLoP comes up right after POST but before BIOS (I'm pretty sure) and presents the choice of booting from any device the computer can "see" (i.e. is mounted).  From there you are taken directly to the grub menu for whatever device you've chosen.  You can install it on a CD or a floppy (the whole plpbt.img file is only 320kB!) very easily, or if you're skilled you can install it on the hard drive to make the USB bootability permanent.
I've used the CD method to modernize computers with BIOSs from 2002 and 2003.

---

### Post by Zucriy Amsuna on 2011-03-02
I might have to give that boot manager a try sometime. ^_^ But I, seeing that USB should be in the BIOS, decided to just plug in the flash drive and check; and--lo, and behold, a USB option appeared! For every time I plug a flash drive in for booting, I'll just have to enter the BIOS; I'm fine with that.

At this time, Ubuntu is being installed. Problem solved. Thanks. =D

---

### Post by nerdy_kid on 2011-03-04
> **egeezer said:**
> @nerdy_kid: You should try it - PLoP can easily give old computers the option of booting from USB.  PLoP comes up right after POST but before BIOS (I'm pretty sure) and presents the choice of booting from any device the computer can "see" (i.e. is mounted).  From there you are taken directly to the grub menu for whatever device you've chosen.  You can install it on a CD or a floppy (the whole plpbt.img file is only 320kB!) very easily, or if you're skilled you can install it on the hard drive to make the USB bootability permanent.
I've used the CD method to modernize computers with BIOSs from 2002 and 2003.

oh sweet, I didn't know it could run off cds.  That would simplify my life greatly!  I'm following my own link and grabbing that right now! :lolflag:

---

