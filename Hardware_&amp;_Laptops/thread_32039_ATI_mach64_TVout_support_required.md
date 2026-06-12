---
title: "ATI mach64 TVout support required"
date: 2005-05-05
forum: Hardware &amp; Laptops
---

### Post by Rounan on 2005-05-05
Hello,

I recently transitioned to Ubuntu from Gentoo. I have a media-playing box in my basement with an ATI Rage card, identified in lspci as:

```
0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage I/II 215GT [Mach64 GT] (rev 41) (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc 3D Rage I/II 215GT [Mach64 GT]
        Flags: bus master, stepping, medium devsel, latency 66
        Memory at ed000000 (32-bit, non-prefetchable) [size=16M]
        I/O ports at 2000 [size=256]
        Memory at ec100000 (32-bit, non-prefetchable) [size=4K]
```

This card operates on the mach64 chipset, which is a bit of a pain to get working. Symptoms are no 3D rendering, only 2MB usable by X of 16MB in the card, and TV Out support not working.
Back on Gentoo, I had to install a specific version of XFree86 and some custom binaries (Available [here](http://www.retinalburn.net/linux/index.html), if anyone cares). This was about 18 months ago.

Since then, I understand that the mach64 chipset-specific doodads have been integrated in X.org, but disabled by default due to security concerns. They are not in the Ubuntu X.org builds, as the options I specify in Xorg.conf:
  ```
 Option       "TVOut"
   Option       "TVStandard"    "NTSC"
   ChipSet      "mach64"
```
are ignored.

I'd like to avoid having to do a custom compile of X.org. Does anyone in the community know of ubuntu-specific binary modules, or some other fancy workaround that can save me some pain?

Oh, and thanks for all the Ubuntu greatness. I'm loving it already.

--Rounan

---

### Post by Rounan on 2005-05-08
Bump.
Any ideas?

---

### Post by Rounan on 2005-05-19
Last bump.

Anyone?

---

