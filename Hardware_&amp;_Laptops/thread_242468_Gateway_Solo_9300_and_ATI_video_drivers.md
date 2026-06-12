---
title: "Gateway Solo 9300 and ATI video drivers"
date: 2006-08-23
forum: Hardware &amp; Laptops
---

### Post by dabbner on 2006-08-23
I hope I'm not duplicating content here, but I have an old Gateway Solo 9300 and the ATI drivers are messed up.  When I type glxgears, I get VERY slow gears that twitch insanely.  I have identified my graphics card as an ATI Mobility.  My Xorg.conf file reads as follows:

Section "Device"
        Identifier      "ATI Technologies, Inc. Rage Mobility P/M AGP 2x"
        Driver          "vesa"
        BusID           "PCI:1:0:0"
        VideoRam        16384
        Option          "UseFBDev"              "true"
EndSection

I went to ATI's website, and I couldn't find a driver to fix my issue.  Suggestions?

Thanks for any help you can offer.

---

### Post by dabbner on 2006-08-26
***bump***

---

### Post by hizaguchi on 2006-08-26
Vesa isn't a 3D video driver, so you need to change it to either fglrx or radeon, depending on the model of your card.

If it's a newer card, use synaptic to install everything fglrx related, then edit /etc/X11/xorg.conf and replace "vesa" with fglrx".  Also make sure (under modules) you have "dri" and "glx" loading, and that "DRI" secion says "0666" for mode.

If it's an oler card, install the radeon video drivers and put "ati" or "radeon" in xorg.conf.  The other changes are the same.

You may still need some tweaking after this to get everything working right, but this is the general direciton to head in.  There's lots of information here in the forums on the exact settings you may need to change to get it all just right.

---

### Post by dabbner on 2006-12-03
Thanks for the reply.  

I tried fglrx and ati.  I get no better result with either.  fglrx causes my gui to lock up before it even completes loading. ATI just gives me the very slow FPS I've had all along... 

ideas?

---

