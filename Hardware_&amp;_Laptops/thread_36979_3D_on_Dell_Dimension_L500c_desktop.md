---
title: "3D on Dell Dimension L500c desktop"
date: 2005-05-25
forum: Hardware &amp; Laptops
---

### Post by mendoza on 2005-05-25
Hi
I am a new Ubuntu user and I use a Dell Dimension L500c desktop. Everything seems to work except the 3D. I tried to look for information on this desktop pc and linux (Google and Dell websites), but did not find anything.
This is what my xorg.conf says:

Section "Module"
    Load    "bitmap"
    Load    "dbe"
    Load    "ddc"
    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "record"
    Load    "type1"
    Load    "vbe"
EndSection


Section "Device"
    Identifier    "Intel Corporation 82810 DC-100 CGC [Chipset Graphics Controller]"
    Driver        "i810"
    BusID        "PCI:0:1:0"
EndSection

Thanks for your help  :)

---

### Post by dekoi on 2005-05-25
The problem is likely that you're using a ~5 yr. old chipset with only 4 megs of integrated video that uses system RAM to complement it. That setup wasn't a "gaming" (OpenGL/3D) platform 5+ years ago, and even less so today. N.B. you aren't going to get 3D working.

---

### Post by mendoza on 2005-05-26
Ok  :| 
Thanks anyway.

---

