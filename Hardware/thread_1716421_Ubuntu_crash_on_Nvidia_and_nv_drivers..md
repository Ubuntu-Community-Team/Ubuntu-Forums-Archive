---
title: "Ubuntu crash on Nvidia and nv drivers."
date: 2011-03-28
forum: Hardware
---

### Post by chowno on 2011-03-28
So I'm seeing some behavior that is not quite what I've found on the forums.  I have an Abit NF7 v2.0 motherboard with an Nvidia GeForce 5200FX graphics card and I get the following problems.  When using the installer and afterward using the main system the OS will freeze on loading X using the nv driver unless I specify nomodeset in grub - then I get a completely stable and workable system.  Now after updating and loading nvidia's nvidia driver with or without the nomodeset option in grub I get a complete OS freeze up within 30 seconds of booting - yes I can use the GUI for about 30 seconds before complete lock up.  Also the driver seems to have the same old issue with this card and finding the correct edid values for the screen, but within the 30 second window I was able to set the screen resolution and rate to appropriate values.  Is anyone else seeing this problem?  Does anyone know of a quick fix?  Thanks.

---

### Post by kitsuneclem on 2011-03-28
I have the same Graphics Card as You and I am not having that Problem perhaps its a different piece of hardware thats acting up? how new is your computer is it possible the motherboard battery is dieing? or perhaps the cpu is on the fritz?

---

### Post by chowno on 2011-03-28
Yeah its very old (like 7 years!), I recently replaced the motherboard with the Abit one and my last (a gigabyte) didn't have this problem.  It is very weird that it would run just fine using the nv driver on nomodeset but moving to nvidia's driver has caused this problem.  Maybe it's time to move to a newer computer. ;)

---

### Post by chowno on 2011-03-28
Okay I've totally nailed down the problem.  Apparently disabling system bios caching and video caching in the bios has solved the problem. :) Also does anyone have a good idea as to what AGP Aperture size to use?  I really have no idea what this even used for and I know that my card only has like 128M of onboard memory so I set the AGP Aperture size to match, but only out of a feeling that higher than this wouldn't benefit me.  Thanks!

---

