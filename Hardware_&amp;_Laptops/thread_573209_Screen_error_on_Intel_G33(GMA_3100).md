---
title: "Screen error on Intel G33(GMA 3100)"
date: 2007-10-11
forum: Hardware &amp; Laptops
---

### Post by gage on 2007-10-11
There is a wide bar under my screen like the picture.
My board is GA-G33M-DS2R/S2

part of information by " lspci -v"
> 
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
        Subsystem: Giga-byte Technology Unknown device 5000
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02) (prog-if 00 [VGA])
        Subsystem: Giga-byte Technology Unknown device d000
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f3200000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at d200 [size=8]
        Memory at e0000000 (32-bit, prefetchable) [size=256M]
        Memory at f3000000 (32-bit, non-prefetchable) [size=1M]
        Capabilities: <access denied>



I am using compiz fusion effect but the bar is still there even I turn it off.
How can I fix it?

---

### Post by smileypaul on 2007-10-12
I had the same problem, should be fixed with the new patch released today (Oct 12)

sudo apt-get update
sudo apt-get upgrade

---

