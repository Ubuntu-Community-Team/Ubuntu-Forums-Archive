---
title: "No sound-card after Kernel Update"
date: 2012-03-21
forum: Hardware
---

### Post by vip3r007 on 2012-03-21
After last kernel update my sound card driver has disappeared.
Dell Latitude E6410

System output below. I tried refreshing the drivers in ALSA no luck. Any suggestions?

sudo aplay -l
aplay: device_list:252: no soundcards found...


lspci -v | grep -A7 -i "audio"
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
	Subsystem: Dell Device 040a
	Flags: bus master, fast devsel, latency 0, IRQ 3
	Memory at e9660000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05) (prog-if 00 [Normal decode])
--
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
	Subsystem: Dell Device 040a
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at e3080000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

---

### Post by vip3r007 on 2012-03-22
*** Update ***

I believe the problem is this directory is empty:

/lib/modules/3.0.0-16-generic/kernel/sound/pci/hda

The previous versions have files in this directory. I tried copying a previous kernels files but it didn't work. How can I populate this directory properly?

---

### Post by ravpra on 2012-03-23
Hi! Did you figure this out? I'm facing this same issue on Fedora 16.

---

