---
title: "Intel Atom N280 not speed stepping down to lowest speed."
date: 2009-12-28
forum: Hardware
---

### Post by acascianelli on 2009-12-28
I recently got a Asus 1005HA for Christmas and I'm going to be putting Ubuntu 9.10 on it.  I've been testing things out on it booting from a USB memory stick and I noticed that the processor is only stepping down to 1000mhz instead of the 850mhz that it does in Windows.  This is having a pretty significant impact on battery life.  Has anyone ever encountered where the Intel Atom CPU will not use all it's available speed steps.

---

### Post by acascianelli on 2009-12-29
I figured out why it's happening, Asus's Super Hybrid Engine not only manages Intel's Speedstep functionality changing the multiplier, but it also over and underclocks the CPU by changing the FSB.

---

