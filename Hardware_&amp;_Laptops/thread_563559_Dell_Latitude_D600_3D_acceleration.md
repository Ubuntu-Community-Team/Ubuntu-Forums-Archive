---
title: "Dell Latitude D600 3D acceleration"
date: 2007-09-30
forum: Hardware &amp; Laptops
---

### Post by mahy on 2007-09-30
Hi y'all,

i just installed Ubuntu Feisty onto my D600 laptop. So far i made everything work, except for the 3D acceleration. This is the output from lspci:

```
ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]
```

This is the output from fglrxinfo:

```
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 1x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 6.5.2

```

And this is an excerpt from xorg.conf:

```
Section "Device"
        Identifier      "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

```

I installed the xorg-driver-fglrx package, but the Restricted Drivers Manager keeps telling me my hardware needs no restricted drivers. I'm hesitant to do any manual modification of xorg.conf if it can't be done using the GUI tool. Right now, the screensavers render fine, but PlanetPenguin Racer performs poorly (although much better than on my other laptop with ATI Mobility Radeon X300 with open-source "ati" drivers).

Ideas, anyone? Please help... TIA

---

