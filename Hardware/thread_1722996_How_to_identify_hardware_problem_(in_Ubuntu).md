---
title: "How to identify hardware problem (in Ubuntu)?"
date: 2011-04-06
forum: Hardware
---

### Post by Skara Brae on 2011-04-06
Greetings,

Probably a newbie question: How can I identify a defective hardware part from withing Ubuntu?

I have quite a not-so-new PC anymore (see signature). It has 2 x 2 S-ATA ports: two with a controller by Promise (FastTrak 378/SATA 378 ), and two with a controller by VIA (VT6420).

Some time ago, I bought a 500 GB S-ATA harddrive from Samsung, planning to (re)install Ubuntu and Win XP in dual-boot on this S-ATA drive (my first S-ATA ever).

- When I connect the HD to one of the Promise S-ATA ports, neither the BIOS, nor the XP install disk sees the S-ATA drive.
- When I connect the HD to one of the VIA (RAID) ports, the HD shows up during boot, but the XP install disk does not see the HD.

In XP, the Device Manager shows a "yellow" exclamation mark in front of the Promise-controller and a "*Code 10 error - the device does not start*". This error first appeared after I tried to install this S-ATA drive a first time. Un- and re-installing the controller in XP has no effect.
I am quite sure the HD is not defective.

So, I am starting to think that the Promise controller may be defective, or something.

Is there a way to find out from within Ubuntu if there indeed is a hardware issue with the Promise controller (like in XP's Device Manager)?
If so, how do I do that?

Thanks for any help.

---

### Post by Faravid on 2011-04-06
Check your bios is your HDD running on Raid mode or Ahci (IDE emulation), first option makes the drive invisible to XP unless you install RAID drivers on the beginning of installation, i think it was F8 button.
The second option makes the controller work like normal IDE-channel and XP + other operating systems detect it without any special drivers but you will not be able to use Raid (in most cases acceptable).

Oh and if you want to install the OS with raid mode on, you need to download preloadable raid drivers from manufacturer site.

---

