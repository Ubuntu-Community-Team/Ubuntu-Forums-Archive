---
title: "Xubuntu Intrepid Ibex Video Nonfunctional"
date: 2009-02-18
forum: Hardware
---

### Post by 043087m135 on 2009-02-18
Hey all,

I'm an intermediate user, been using GNU/Linux for a few years, so I know my way basically around a command prompt.

I have Xubuntu 8.04 installed on my Asus F8 Laptop, which has an ATI Radeon Mobility 3650 card (1024mb VRAM). 8.04 runs OK, but I'm having lots of difficulty with little stuff so I wanted to try an upgrade. It does work generally, but flash doesn't work in any browser and other little nitpicky problems. But the point is that I can get a functional desktop at a good resolution with good color depth in Xubuntu 8.04.

I've burned a CD of Xubuntu 8.10 and tried to boot it a few times. I also tried Mint Felicia. In BOTH of these OSes, the same thing happens: it loads and when it starts my X session all I see is twitchy grey. I've gone to the terminal using alt-f keys and tried editing my xorg.conf to force the "vesa" driver, forced the "radeon" driver, forced the "ati" driver. 

*Edit* I've also tried this with Fedora 11 Live.

With "vesa", X won't start because it says No Useable Screen - it can't find a video mode. I've poked around in the manual pages and I don't know why that might be. 
With "ati" or "radeon" (which are the same thing, I know - ati just detects the radeon driver) the twitchy grey screen comes on. I'm worried it's a problem with an upgraded radeon driver.

Using the radeon driver I don't get any error messages, it seems to just be some disconnect between the card and the monitor.

Please give me some suggestions. Thanks!

~Ender

---

