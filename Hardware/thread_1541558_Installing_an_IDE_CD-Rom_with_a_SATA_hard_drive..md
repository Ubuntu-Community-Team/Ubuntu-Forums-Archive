---
title: "Installing an IDE CD-Rom with a SATA hard drive."
date: 2010-07-29
forum: Hardware
---

### Post by casacerian on 2010-07-29
Last night I moves my mother board and attached hardware to a new case with a better power supply. 

My old drive setup was 1x SATA Hard drive and 1x SATA CD-ROM drive. The power supply in the new case only has one SATA power connector, so I dropped the CD-ROM and installed an old IDE CD drive. Along with a slew of other problems, the CD-ROM drive is not being picked up at all. Not by the bios, nada. Is there anything special that I may have overlooked about the setup of the CD drive? Perhaps I have a jumper error going with the mix of SATA and IDE?

Thanks in advance.

---

### Post by dabl on 2010-07-29
So your motherboard has an IDE connector?  If yes, then BIOS should see the connected optical drive.  (I have the same setup on an Intel D975XBX2 motherboard).

Those IDE ribbon cables can get flaky -- one thing to try is to replace the cable.  Also, make sure that your optical drive has power -- BIOS won't see it if it doesn't have power on it.

The jumper/position should not affect whether BIOS sees the drive, although most modern IDE devices are best left jumpered to "CS".  That way you can use BIOS to make it master, slave, channel 1, channel 2, etc.

---

### Post by casacerian on 2010-07-29
The power to the drive is good. It spins up when the computer boots, etc.

Am about to power down and swap the cable.

I thought it should see the drive regardless as well.

---

### Post by casacerian on 2010-07-29
I swapped the cable for the CD drive and the bios continues to not see the drive. Can not boot from CD etc.


Ubuntu sees it now though... Any ideas? It is showing up as UDF volume.

---

### Post by dabl on 2010-07-29
Look around in BIOS some more -- first in "storage", perhaps, as well as "bootable devices", where it needs to list the optical drive.  I think you have it "missing" in a place where it needs to be included.

---

### Post by casacerian on 2010-07-29
In the bit that lists boot-able devices it shows only my hard disk as being boot-able. The other 3 (Optical, floppy and network I believe) are listed as not installed.

There are no options available to me to adjust those either.

My BIOS is from 2006, there is an upgrade available for my machine, but I need windows to install it as far as I understand the process (exacerbated by my lack of a floppy drive). Maybe the updated BIOS would have the answer?

---

### Post by dabl on 2010-07-29
> **casacerian said:**
> In the bit that lists boot-able devices it shows only my hard disk as being boot-able. The other 3 (Optical, floppy and network I believe) are listed as not installed.

There are no options available to me to adjust those either.



That's the problem -- a bootable CD such as Ubuntu's Live CD will never boot in that machine, as long as the BIOS does not see a bootable optical drive.

The BIOS upgrade might fix it.  I would try that.  Depending on the BIOS, the upgrade might be available as an ISO file.  Of course that doesn't help if your CD won't boot it.  :(

With no floppy and no optical drive, the only option you have is to make a bootable USB stick.  It's not terribly difficult, but if you've never done it, then you will have a bit of a learning experience.  Google will help you, for example:

[http://blogs.sun.com/dragonfly/entry/dos_bootable_usb_flash_drive](http://blogs.sun.com/dragonfly/entry/dos_bootable_usb_flash_drive)

[http://forum.notebookreview.com/sager-clevo/246530-how-flash-your-bios-dos-using-usb-stick.html](http://forum.notebookreview.com/sager-clevo/246530-how-flash-your-bios-dos-using-usb-stick.html)

[http://www.bootdisk.com/usb.htm](http://www.bootdisk.com/usb.htm)

---

### Post by casacerian on 2010-07-29
Just to be clear: it is quite possible that my BIOS is bugged and/or needs an upgrade to sort myself out?

I have a DOS boot-able stick, but flashing my bios via DOS has be wringing my hands. 

Note: I am trying to set ya up as a scape-goat, just wanting crystal-clarification. :)

EDIT: It is of course worth noting that I am on the machine in question, and I do have a Ubuntu boot-able USB drive.

---

### Post by casacerian on 2010-07-30
Problem solved.

Replaces the BIOS jumper and now my bios sees all of my IDE drives.

---

