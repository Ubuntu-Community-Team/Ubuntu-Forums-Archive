---
title: "HD Intel Audio... Still not working :("
date: 2007-08-30
forum: Hardware &amp; Laptops
---

### Post by Aryding on 2007-08-30
I installed ALSA, set the sound settings to ALSA and still nothing.  What should I do next?  Let me know if some information from the terminal can help...

---

### Post by Aryding on 2007-08-31
This is what I get when I put the follow command into the terminal:   lspci -v

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1302
        Flags: fast devsel, IRQ 22
        Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

This command:aplay --list-devices

aplay: device_list:222: no soundcards found...

---

### Post by Aryding on 2007-09-01
bump... anyone?

---

