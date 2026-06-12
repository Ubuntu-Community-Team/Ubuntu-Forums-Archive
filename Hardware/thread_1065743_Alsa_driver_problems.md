---
title: "Alsa driver problems?"
date: 2009-02-10
forum: Hardware
---

### Post by amainejr on 2009-02-10
I need some help...I think.  My sound architecture is working.  I'm using a Compaq Presario c304nr notebook that uses Intel ICH7 (82801G) family of sound card.  Recently, I tried to get the 56k modem working for fax functions.  However, when I did some research, it turns up that the fax modem is on the same chipset with the sound card.  I went to the linuxant website [www.linuxant.com](www.linuxant.com) and allowed it's installer to select and install my drivers.  It chose the Conexant HSF driver for the Intel HD audio drivers, but didn't install the modem.  

That's the premise to the actual problem I am having now.  I installed MyScribe ([www.cafescribe.com](www.cafescribe.com)) using WINE, several weeks ago, and have used it with no problems.  Now that I have attempted the driver changes, MyScribe won't load the books anymore.  A quick look at my syslogs show the kernel is reporting the following:

```
kernel: [  179.651983] ALSA /usr/lib/alsa-driver-linuxant/pci/hda/hda_intel.c:1116: Too big adjustment 32
```

Obviously that is the linuxant driver running the sound card, which actually works, however, it won't allow the MyScribe application to load beyond the main page.  I've searched on that error and found a bunch of hooplah that I don't understand. 

Here's the output from various commands:

```

lspci -v | grep intel
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp
	Kernel modules: intelfb
	Kernel modules: snd-hda-intel
	Kernel modules: intel-rng, iTCO_wdt

```

```

lspci -v
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Hewlett-Packard Company Device 30a5
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at d0340000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	Memory behind bridge: 88000000-880fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

```

```

modinfo soundcore
filename:       /lib/modules/2.6.27-11-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     E4F49ED9C4CFD1A5A923330
depends:        
vermagic:       2.6.27-11-generic SMP mod_unload modversions 586

```

Any thoughts on why there is the flag on the "Too Big Adjustment: 32"?  The hda_intel.c file says it supports the ICH7 modules.  I'm kind of lost.

---

