---
title: "Checking Video driver(s) installed?"
date: 2010-11-24
forum: Hardware
---

### Post by Splat_NJ on 2010-11-24
Still only under a week with Linux and love it. I have a desktop system with an old Nvidia TNT2 video card in it. When I execute lspci -v in terminal here is what it shows:

01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15) (prog-if 00 [VGA controller])
    Subsystem: nVidia Corporation Device 0001
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
    Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Memory at fa000000 (32-bit, prefetchable) [size=32M]
    Expansion ROM at fe9f0000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: nouveau
    Kernel modules: nouveau, nvidiafb, rivafb

How do I know if, and what version, video driver(s) are installed and if none should I install the "185" package I found when searching for "NVidia" in the Software Center? Thanks.

---

### Post by Splat_NJ on 2010-11-25
OK, I give! Is it something obvious I'm missing here?

---

### Post by Splat_NJ on 2010-11-26
> **Splat_NJ said:**
> OK, I give! Is it something obvious I'm missing here?

The answer is...................YES! 

Finally figured out it's using the Nouveau driver.  DOH!

---

