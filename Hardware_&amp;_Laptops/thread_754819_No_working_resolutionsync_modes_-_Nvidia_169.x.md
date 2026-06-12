---
title: "No working resolution/sync modes - Nvidia 169.x"
date: 2008-04-14
forum: Hardware &amp; Laptops
---

### Post by fishonadish on 2008-04-14
Hi,

I can't use the 169.x versions of the Nvidia driver because it won't send the screen a valid refresh/sync/resolution mode, so I just get a white screen.

I've tried adding modelines and various options to xorg.conf, but got nowhere.

The 100.x driver works fine, but the 169 is the default in the next Ubuntu version, so I'd like to get that working.  I first discovered this issue a few months back, and have tried posting on nvnews.net, but got no responses ([http://www.nvnews.net/vbulletin/showthread.php?t=105308](http://www.nvnews.net/vbulletin/showthread.php?t=105308))

My graphics are nVidia Corporation GeForce 8600M GT [10de:0407], which is in the supported list for the 169 driver.

If anyone has any suggestions as to how I could resolve this, I'd appreciate it.  Perhaps a bug report to Nvidia may be the only solution?

Thanks.
Fishonadish

---

### Post by fishonadish on 2008-04-21
Has no one else with this chipset experienced this problem?  It seems the EDID (whatever that is...) isn't working and so the driver can't find a resolution.  It's defaulting to 640x480, but either the resolution or the sync/refresh isn't supported by my screen.
Here's the relevant section of the log if it means anything to anyone.

```

...
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(WW) NVIDIA(GPU-0): The EDID read for display device DFP-0 is invalid: the
(WW) NVIDIA(GPU-0):     checksum for EDID version 1 is invalid.
(--) NVIDIA(GPU-0): 
(--) NVIDIA(GPU-0): Raw EDID bytes:
(--) NVIDIA(GPU-0): 
(--) NVIDIA(GPU-0):   00 ff ff ff ff ff ff 00  4c a3 58 33 00 00 00 00
(--) NVIDIA(GPU-0):   00 11 01 03 80 21 15 78  0a 87 f5 94 57 4f 8c 27
(--) NVIDIA(GPU-0):   27 50 54 00 00 00 01 01  01 01 01 01 01 01 01 01
(--) NVIDIA(GPU-0):   01 01 01 01 01 01 4c 1d  00 90 50 20 22 30 10 30
(--) NVIDIA(GPU-0):   13 00 4b cf 10 00 00 19  00 00 00 0f 00 00 00 00
(--) NVIDIA(GPU-0):   00 00 00 00 00 23 87 02  64 00 00 00 00 fe 00 58
(--) NVIDIA(GPU-0):   58 30 34 37 00 31 35 34  58 33 0a 20 00 00 00 fe
(--) NVIDIA(GPU-0):   00 26 36 40 47 6a 8f c6  ff 01 01 0a 20 20 00 80
(--) NVIDIA(GPU-0): 
(II) NVIDIA(0): NVIDIA GPU GeForce 8600M GT (G84) at PCI:1:0:0 (GPU-0)

...

(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 640 x 480
(WW) NVIDIA(0): Unable to get display device DFP-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from DFP-0's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
...

```

I'd really appreciate some help with this if anyone has any ideas.

Fishonadish

---

