---
title: "LCD brightness - HP G72"
date: 2011-01-18
forum: Hardware
---

### Post by lolke on 2011-01-18
I just installed Maverick 10.10 (32 bit) on a HP G72. One issue is that I don't have control over the brightness of the LCD. I tried the PPA ([https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight](https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight)) but that results in a blank screen that I can't control et all.

The funny thing is that in the LIVE CD environment, when I try things out, it works perfectly fine. The fn-f2 and fn-f3 keys control the brightness without any issues.

Any ideas?

Some basic stats:

$ uname -a
Linux stavanger 2.6.35-24-generic-pae #42-Ubuntu SMP Thu Dec 2 03:21:31 UTC 2010 i686 GNU/Linux

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Device 1484
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 4110 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [d0] Power Management version 3
	Kernel driver in use: i915
	Kernel modules: i915




Lolke

---

### Post by lolke on 2011-01-19
Did some more analysis this evening. I rebooted back into the LIVE CD and checked its kernel and video settings. I noticed that I was running the pae kernel and the LIVE CD environment is not. Both environment use the intel driver for video.

So I installed the generic non-pae kernel and 'voila' the brightness buttons are working now. 
Any ideas why the pae kernel would introduce this problem?

Lolke

---

### Post by awilkins on 2012-01-04
I'm not sure ; I'm also seeing this with the 64-bit kernel in Oneiric.

---

