---
title: "Is hardware accel even possible with Mach64 chipset?"
date: 2010-11-19
forum: Hardware
---

### Post by teamgs on 2010-11-19
Greetings,
   Longtime Windows tech and network admin, but relative Noob with Linux.  I am currently messing around with an old Dell Inspiron 5000 with the ATI Rage Mobility M/P (Mach64) card, and Ubuntu 10.10 desktop.   Everything seems to be running perfectly (Even the touchpad is detected properly in this release) with the small exception of no hardware acceleration on the video card.  This isn't a deal breaker, as this machine will probably just be left in our second home for guests, but, as an old time tech geek, I hate being defeated by a problem.  

I am currently multi booting the latest mint, ubuntu, zenwalk, and knoppix, and none seem to get the 3D acceleration activated, though all seem to detect the card properly.  Here are a few info snips:

lspci: 01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)

gary@gary-Inspiron-5000:~$ glxinfo | grep renderer
OpenGL renderer string: Software Rasterizer

I have successfully created an Xorg.conf file, but can't seem to get any of the fixes I have run across on the net to work without crashing X or doing nothing.

I guess I am looking to see if this is the proverbial windmill at which I am tilting, or is it possible to get this feature active in Ubuntu and with this card.

Sorry if I have left out any salient details, but I will be happy to post any more that are requested.

Regards,

Gary

---

### Post by Fafler on 2010-11-19
I don't think any pre-Radeon (or pre-Rage?) cards have 3D support under Linux.  The Mach64 barely has any 3D support itself.

You should look into upgrading it. Taking the Mach64 it so old, i guess you don't have a AGP port. For low speed 3D, there are several options available on the second hand market.

A Matrox G200 or later. Excellent 3D support under Linux, but relatively slow hardware.
Radeon cards work with the radeon driver, albeit quite slow.
Any Nvidia PCI card should work with the Noveau driver, but i'm not sure how good it is.
The Geforce 8400 GS PCI card is probably the best PCI card you can find out there and it's definitely worth every hard earned dollar, if you choose to get one.

But first, make sure you have a spare PCI slot in your PC.

---

### Post by teamgs on 2010-11-19
Thanks for the reply.  No option to upgrade the video on this laptop.  No great need either.  The software renderer works just fine for normal activities.  This was more of a "dangit, why doesn't this work?!" problem.  This machine will most likely just be a test machine or left at our ski home for web browsing for guests.

Regards,

Gary

---

### Post by photor on 2011-01-17
the same problem

---

