---
title: "Sound on Composer 5200"
date: 2005-07-16
forum: Hardware &amp; Laptops
---

### Post by dragoncow2 on 2005-07-16
Hi, I set up Ubuntu and Debian on this Composer 5200 computer, and both distros aren't detecting the sound card. I've tried recompiling the kernel to have the snd-intel8x0 module built into the kernel, and even that didn't find the audio card. As for the type of audio card it is, I'm not 100% sure, but here's the entry in lspci -v

0000:00:1b.0 0403: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
        Subsystem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at d3100000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

With the snd-intel8x0 module loaded; here is the output of `cat /proc/asound/cards`:

--- no soundcards ---


So now I'm wondering what steps I should take to get sound working....any help would be appreciative. Thanks in advance!

---

### Post by dragoncow2 on 2005-07-18
So....no one has any experience with this card? :-/

---

