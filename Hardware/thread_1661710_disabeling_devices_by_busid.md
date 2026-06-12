---
title: "disabeling devices by busid"
date: 2011-01-07
forum: Hardware
---

### Post by Black Magix on 2011-01-07
I have two video cards on my laptop (Toshiba Satellite A665d) and I need to disable my weaker card so that the more powerful card is utilized. Is there a way i can do this? Both of them use the same modules so black listing the module won't cut it since then I'm SOL for both cards.

```
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeon
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
02:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series] (rev ff)
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx

```

I want to disable the Radeon 4200 and try to use the 5000 series on 2:00.0

Any ideas?

---

