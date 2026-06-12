---
title: "Screen Flicker on Samsung Syncmaster @ 1920, Only works on lower resolution"
date: 2011-07-01
forum: Hardware
---

### Post by sagility on 2011-07-01
I'm running Ubuntu 11.04 and just purchased a Samsung Syncmaster B2430.

If  I try to run the screen resolution @ 1920, I get bad intermittent  flickering in general use and it becomes unusable when viewing video

If I run @ 1240 - then everything is fine ... but that's not why I bought a 24" monitor.

When I run lspci -v this is what I get back for the video controller.

00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 7025 / nForce 630a] (rev a2) (prog-if 00 [VGA controller])
    Subsystem: ASRock Incorporation Device 03d6
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f9000000 (64-bit, non-prefetchable) [size=16M]
    Expansion ROM at fbfc0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nouveau
    Kernel modules: nouveau, nvidiafb


DO you have any suggestions about resolving this?

Thanks :p

---

### Post by sagility on 2011-07-01
An update to the above. My colleague, running nearly identical hardware/operating system can use the same monitor without any issues ... but with a refresh rate of 50Hz.

I don't seem to be able to change the refresh from 60Hz to 50Hz on Preferences>Monitors.

Is there another way to do this?

---

### Post by sagility on 2011-07-01
OK ... it was the restricted driver ... installed that, rebooted, works like a charm!!

How did we ever get work done on 14" screens? :p

---

