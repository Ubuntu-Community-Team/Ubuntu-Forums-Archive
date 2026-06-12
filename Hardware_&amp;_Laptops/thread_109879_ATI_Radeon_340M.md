---
title: "ATI Radeon 340M"
date: 2005-12-29
forum: Hardware &amp; Laptops
---

### Post by JeremyPrivett on 2005-12-29
In reference to [this thread](http://ubuntuforums.org/showthread.php?t=11365), is there any way to make this card's 3D work on Breezy? It was running decent to begin with but it was using Mesa. So, I tried fglrx but it crashed X. When I changed the driver back to 'ati', X worked but now the graphics are absolutely horrible. FPS ~90.

I'm using an hp pavillion ze5730us model laptop. Changing the driver to 'radeon' like in the above thread produced the same results as 'ati' ...

Suggestions? I can't play ***any*** games now, due to this problem... :(

---

### Post by roachk71 on 2005-12-31
[LEFT]Good Morning (or Afternoon),

Hmm... Same graphics chip this notebook (xt125) has.

I have two pointers for this chipset:

1:  In your computer's BIOS settings, you might want to allocate more memory to the graphics chip (default here was AUTO. Most of the time it allocated only 32MB, and since I upgraded its RAM, I've set that to a full 128MB.)

2:  Add these settings to the following section in /etc/X11/xorg.conf:

```

Section "Device"
    Identifier    "ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"
    Driver        "radeon"
    Option        "UseFBDev"        "true"
    Option        "AGPMode"        "4"
    Option        "AGPFastWrite"    "true"
    Option        "RenderAccel"        "true"
    Option        "AccelMethod"        "EXA"
    Option        "EnablePageFlip"    "true"
    Option        "DDCMode"
    Option        "SubPixelOrder"        "NONE"
    Option        "ColorTiling"        "false"
EndSection

``` 

IMPORTANT: Don't remove or change the BusID Option!

The original settings really sucked for me before these modifications; Hope this helps ya.

Update: It might be a good idea to omit the "UseFBDev" option since it forces the X Server to use the framebuffer driver (inefficient.) Oops...
[/LEFT]

---

