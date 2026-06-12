---
title: "Ati radeon mobility 7500!"
date: 2009-06-16
forum: Hardware
---

### Post by khael87 on 2009-06-16
HellO!
i have a problem with ubuntu 9.04 and radeon mobility (32MB of ram).
Notebook is impossible to use normally!

Notebook is very slow, when i move a window cpu go to 100%.

I try with some solution but nothing work!
what can i do?

Can i use DRI driver?

this is my xorg:
> Section "Device"
    Identifier    "Configured Video Device"
    Driver        "radeon"
    BusID        "PCI:1:0:0"
    Option "AGPMode" "4" 
    Option "AGPSize" "64"
    Option "RingSize" "8"
    Option "BufferSize" "2"
    Option "EnablePageFlip" "true"
    Option "EnableDepthMoves" "true"
    Option "RenderAccel" "true"
    # Eyecandy Stuff
    Option "AccelMethod" "4"
    Option "EnablePageFlip" "true
    Option "DDCMode"
    Option "SubPixelOrder" "NONE"
    Option "ColorTiling" "false"
EndSection

---

### Post by nolliecrooked on 2009-06-16
ummmmm, with a Notebook that old, you may wanna stick with XP.

---

### Post by overdrank on 2009-06-16
> **khael87 said:**
> HellO!
i have a problem with ubuntu 9.04 and radeon mobility (32MB of ram).
Notebook is impossible to use normally!

Notebook is very slow, when i move a window cpu go to 100%.

I try with some solution but nothing work!
what can i do?

Can i use DRI driver?

this is my xorg:

Hi and welcome, my laptop with the ATI 7500 works great with the standard driver from install.
Have you tried to reconfigure your xorg using the xfix option from recovery mode.

---

### Post by khael87 on 2009-07-07
> **nolliecrooked said:**
> ummmmm, with a Notebook that old, you may wanna stick with XP.

Thanks, but i don't think which is best solution;

I don't need compiz effect;

x overdrank:

which driver use on your system??

thank you!

---

### Post by overdrank on 2009-07-07
> **khael87 said:**
> Thanks, but i don't think which is best solution;

I don't need compiz effect;

x overdrank:

which driver use on your system??

thank you!

It is the one with the install of Ubuntu. Jaunty handles the xorg differently then past editions. Have you tried xfix from the recovery mode?

---

