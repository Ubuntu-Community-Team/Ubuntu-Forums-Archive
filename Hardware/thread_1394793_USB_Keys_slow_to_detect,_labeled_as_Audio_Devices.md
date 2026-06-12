---
title: "USB Keys slow to detect, labeled as Audio Devices"
date: 2010-01-31
forum: Hardware
---

### Post by AaronRGod on 2010-01-31
Hoy there, gang!

Whenever I plug in a USB key, I get to wait up to 10 minutes before Hal detects the device; the light on the key flashes like it's rapidly being accessed, but it is unavailable until the light goes solid.

When Hal does find the key, some but not all of them are reported to be audio devices. Like this one:

```
ID 054c:0243 Sony Corp. MicroVault Flash Drive

```

I tried finding those vendor and device codes in my 10-usb-music-players.fdi, as suggested by the bug report for this issue, but they didn't exist. Just for kicks, I ran grep on every fdi in the /usr/share/hal/fdi/information/10freedesktop/ directory, but still did not find that device listed anywhere.

Can anyone take at stab at either problem?

---

