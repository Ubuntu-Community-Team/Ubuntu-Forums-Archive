---
title: "How to improve display saturation - Intel integrated i915?"
date: 2013-02-25
forum: Hardware
---

### Post by csete on 2013-02-25
I have a new Sony VAIO T15 laptop with Ubuntu 12.10 installed.  In general, things are working pretty well, however, I'm finding that the color saturation on the display is pretty low and I'd like to kick it up a few notches.  

I've attempted to use the Color settings applet, but it doesn't seem to be working.  The display is showing "Uncalibrated", but the Calibrate... button is disabled.  Is there something I'm missing?  Here is the information about the hardware from lscpi:

```

00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 0
9) (prog-if 00 [VGA controller])
	Subsystem: Sony Corporation Device 90a8
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at c4000000 (64-bit, non-prefetchable) [size=4M]
	Memory at b0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 5000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [d0] Power Management version 2
	Capabilities: [a4] PCI Advanced Features
	Kernel driver in use: i915
	Kernel modules: i915

```

Suggestions appreciated!
Thanks,
Craig

---

### Post by mohiter4 on 2013-05-25
Facing the exact same problem with my Lenovo T420 laptop too. Though in my case the saturation is okey, though in COLOR setting display shows uncomplicated.
Any help is appreciated.

Mohit

> **csete said:**
> I have a new Sony VAIO T15 laptop with Ubuntu 12.10 installed.  In general, things are working pretty well, however, I'm finding that the color saturation on the display is pretty low and I'd like to kick it up a few notches.  

I've attempted to use the Color settings applet, but it doesn't seem to be working.  The display is showing "Uncalibrated", but the Calibrate... button is disabled.  Is there something I'm missing?  Here is the information about the hardware from lscpi:

```

00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 0
9) (prog-if 00 [VGA controller])
    Subsystem: Sony Corporation Device 90a8
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at c4000000 (64-bit, non-prefetchable) [size=4M]
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 5000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915
    Kernel modules: i915

```

Suggestions appreciated!
Thanks,
Craig

---

