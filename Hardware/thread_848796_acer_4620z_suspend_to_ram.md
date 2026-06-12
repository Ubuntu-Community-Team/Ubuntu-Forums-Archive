---
title: "acer 4620z suspend to ram"
date: 2008-07-03
forum: Hardware
---

### Post by nolster12 on 2008-07-03
I know that this is a problem with a lot of computers, but I have tried all of the tweaks to /etc/default/acpi-support that have been mentioned for other computers with hardware like mine.  With the standard set up and most of the small changes that I have tried the computer will go to suspend just fine.  When I try to wake the computer it tries to wake (lights turn green sounds like the hard drive might start to spin) but then just shuts off.  I changed a few things and got it to fail at sleeping and hang with just a blinking prompt.

---

### Post by pastalavista on 2008-07-03
The problem may be with your bios. Have you checked to make sure the suspend, aka sleep mode, is enabled?

---

### Post by nolster12 on 2008-07-04
I had not even thought of that.  I checked in all the menus for the bios and there was nothing about enabling suspend to ram.  It is a pheonix bios on this computer if that helps any.

---

### Post by lyz on 2008-07-25
Gotta bump this.  I have the same laptop and the same issue.  I've done all the commands at [http://en.opensuse.org/S2ram](http://en.opensuse.org/S2ram) and still no dice.

---

### Post by gerymate on 2008-08-18
I have similar symptoms on an Acer Extensa 5220. There is poweroff after going down to suspend.

Anyway, I had working suspend on the latest Fedora on this system, so it seems **it is not a BIOS issue**.

Maybe something around ACPI.

There are traces that some others also having the same issue. Also on some TravelMate series.

---

Update: I was messing around with the procedure described here: [https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend)
I have received the information that the problem is probably with "device ttyp7", probably also known as "device device:20".
Currently I have no clue of what this device may be. Any ideas?

---

