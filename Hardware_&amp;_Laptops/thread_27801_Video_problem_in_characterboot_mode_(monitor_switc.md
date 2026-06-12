---
title: "Video problem in character/boot mode (monitor switching/blanking every half second)"
date: 2005-04-17
forum: Hardware &amp; Laptops
---

### Post by Slade Winstone on 2005-04-17
Hi,

I'm experiencing a video problem during Hoary bootup in character mode with the video "flashing" or switching and repeatedly blanking every half second, or so, until the system starts X windows.  Once the GUI starts everything is fine, but this does make it very hard to see any of the boot process.

I suspect that the system is trying to switch to an usupported mode or frequency for my combination of video/monitor.

I'm running a cheap ASUS A7V8X-MX motherboard with VIA KM400 integrated graphics and a Compaq V75 monitor (sorry for the lack of real detail).

The strange thing is that Warty Live worked fine and I only experience problems trying to use the Hoary Live or Install CDs.  I'd actually like to install Hoary (switching from Knoppix) but I'd really like to figure out how to see what's happening at boot before I do so :)

I'm a bit of a linux newbie but willing to play with bios settings and/or video boot-up options if somebody can point me in a right direction...

Many thanks,
Slade.

---

### Post by Slade Winstone on 2005-04-24
It turns out this was a framebuffer problem that I experience with both the on-board video and my Nvidi Geforce FX5200.

Switching off the debian installer's use of the framebuffer as a boot option fixes the problem.

boot>  ... debian-installer/framebuffer=false

Hope this might help somebody else in the future.

Slade.

---

