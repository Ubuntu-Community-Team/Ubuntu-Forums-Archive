---
title: "Laptop Monitor Resolution Problem"
date: 2006-03-19
forum: Hardware &amp; Laptops
---

### Post by Automata on 2006-03-19
I'm rather new to Linux, so please... be gentle.  

I have an Acer Aspire 5504NWXMi, and recently decided to try and put linux on it, to escape the spyware ridden catastrophe that is Windows XP.  After eventually fixing the blank screen woe's associated with the ATi driver problem, I have been confronted with the dilemma of my monitor not displaying it's native resolution (1280x800).  Rather it is stuck at 1024x768, and after trying numerous fixes, I have come up empty handed.  

Here's my Xorg.conf file...though it is not enclosed in a nice box...

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility X700 (RV410)"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Modeline        "1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Any help is welcome, as I'm somewhat desperate.  Thanks for your time.

---

