---
title: "1152x864 resolution not available on Linux?"
date: 2010-06-30
forum: Hardware
---

### Post by Velvet Ghost on 2010-06-30
I am on an old P4 desktop with a D845GLAD motherboard, bought in 2002. No separate graphics card. SAMTRON 56V CRT monitor. Earlier, I used to have Windows XP on this machine, and had 3 monitor resolutions available to me: 800x600, 1024x768 and 1152x864. Ever since I switched to Linux, I have tried over 20 distributions on this desktop, but none of them have ever had the 1152x864 resolution available. 1024x768 works fine, though. What do you make of this? Is this a limitation of the Linux Intel drivers? Is it possible to salvage my long-lost highest resolution?

---

### Post by Velvet Ghost on 2010-07-02
Bump.

---

### Post by lykwydchykyn on 2010-07-02
I'm going to take a guess that a D845GLAD motherboard is using an intel 845G graphics chip as its onboard video.  You can confirm this by running lspci at a terminal prompt, but based on the name I'd say it's highly probable.

The intel 845G (or i845 for short) has a long history of not playing nice with Linux and Xorg, unfortunately.  You might be able to get better resolutions by upgrading your system's BIOS, if there's an upgrade available, or by switching to the VESA drivers (though that means no hardware acceleration).

You might be able to improve things by creating an xorg.conf file and making manual tweaks to it; start reading here:

[https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)

---

