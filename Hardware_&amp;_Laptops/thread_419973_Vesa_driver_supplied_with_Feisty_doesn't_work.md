---
title: "Vesa driver supplied with Feisty doesn't work"
date: 2007-04-23
forum: Hardware &amp; Laptops
---

### Post by rj686 on 2007-04-23
I've installed the newest feisty via the alternate cd because the live cd won't boot correctly under my computer. I have an ATI x1600 on a 1280x960 display. Vesa doesn't find any correct modes and just shuts down. If i install fglrx and reboot x it works perfectly. Just thought I'd report this since other people might be having the same issue. THis has only happened in feisty, not with edgy. I filed a bug at launchpad but it seems to be deleted :(

---

### Post by d_b on 2007-05-03
I'm having the exact same problem with the LiveCD.  I have a HP nc8430 with ATI Mobility x1600, 1280x800 display.    I tried Safe graphics mode and VGA=771 but had no luck.

VESA complains about hsync being too high for every mode, then fails when it can find a suitable one.  

This seems to me like a pretty major bug.   

d.

---

