---
title: "Enclosure-mounted External Hard Drive Not Recognized"
date: 2008-08-25
forum: Hardware
---

### Post by Bookwyrm on 2008-08-25
Greetings, Folks!

Recently my venerable Dell C610 laptop (running Ubuntu 8.04) developed terminal problems. Since the hard drive (Toshiba 80G IDE/ATA) is still functional, I decided to install it into an external enclosure (Circuit City Nexxtech NHDE25), recover the data, and use it as an external backup drive for my desktop Ubuntu system. The drive was still functional when I removed it from the failing Dell laptop; I believe it was formatted to ext3.

Now, when I connect the external enclosure to my desktop Ubuntu 8.04 computer (configuration details at end of message), the enclosure's LED lights up and, if I listen really closely, I can hear the hard drive spinning. However, Ubuntu doesn't recognize the hard drive (no icon in the desktop).

I know the hard drive isn't the problem because it is acknowledged, albeit with an unknown format, when I attach the enclosure to my Mac (OS X 10.4) and Windows (Vista & XP) systems. I suspect that my Ubuntu box doesn't recognize the enclosure; USB may be working, but the necessary drive controller driver isn't there. I do have a Win 98SE driver that came on a CD with the enclosure.

Is there anything I can do to get it to work?

Thank you.

PS: Desktop configuration -- I'm running Ubuntu 8.04.1 with the latest updates. My computer is an EliteGroup GF7100PVT-M3 mainboard with an Intel Core 2 Duo cpu, 2 GB ram, 320 GB SATA hard drive, and an nVidia GeForce 8500 GT gpu. The case is an Antec Aria with both front- and back-panel USB ports,

---

### Post by Cereus on 2008-12-01
I was wondering if anyone else has answered this issue as I am having the same problems.

I plug my external hard drive into the USB socket? and when I enter the command lsusb, there is no recognition that the device has been plugged in.

However, when I attach it to a windows machine it recognizes the external hard drive has been attached, it just doesn't mount it.

---

### Post by elasticrock on 2008-12-14
I have a similar problem with my enclosure-mounted 80gb internal drive, and I also installed Ubuntu onto it, so it's ext3 format. fdisk -l and lsusb yield nothing before and after I plug in the drive.

---

### Post by curdog on 2009-01-15
I know the post is a little old, but I've had the same problem when putting my dell xps 1530 drive (wd scorpio 320gb) into an enclosure or even my desktop.  No recognition in vista or ubuntu 8.10.  In vista i get the "installing new device message" follow by "device not recognized, unkown device."  Yet the drive definately works.

This is from coolmax's (my enclosure) website:

> Notebook or desktop units from proprietary companies like Compaq, Dell, HP, etc. may have security features that blocks detection of the drive when installed to other units or enclosures.

Dell support couldn't confirm this, however.  Anyone know about this?

btw...i have reformatted it in the laptop using gparted successfully.

---

### Post by curdog on 2009-01-16
I've been able to get mine working by 2 ways:  

One workaround is plug in both large usb connectors, let the drive spin-up, then unplug the main connector that has 2 wires.  Sometimes it takes a couple tries.

I've also used the y-usb cable from my 2.5" maxtor, & that works fine no matter what.  So it appears to be a bad cable issue, at least in my case.  Since I ordered 2 of the enclosures, I tried with both cables w/ the same problem.  Can anyone have the same problems?

---

