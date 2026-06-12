---
title: "No usplash on Intel graphics card"
date: 2006-12-09
forum: Hardware &amp; Laptops
---

### Post by Cybermage on 2006-12-09
Hi there,

I recently installed Edgy Eft on my old PIII laptop.
There is no Uplash logo at boot, but a black screen with some strange fragments on it.

lspci -v shows the following output:
```
00:02.0 VGA compatible controller: Intel Corporation 82815 CGC [Chipset Graphics Controller] (rev 11) (prog-if 00 [VGA])
        Subsystem: Fujitsu Limited. Unknown device 110c
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 10
        Memory at f8000000 (32-bit, prefetchable) [size=64M]
        Memory at f4000000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: [dc] Power Management version 2
```

Also there are some Problems with progress bars when running Xorg at 32bit.

Any ideas yet?

---

### Post by siucdude on 2006-12-21
i get the same on my laptop.  i am going back to old school boot

---

