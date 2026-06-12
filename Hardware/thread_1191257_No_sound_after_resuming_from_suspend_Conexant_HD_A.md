---
title: "No sound after resuming from suspend: Conexant HD Audio"
date: 2009-06-18
forum: Hardware
---

### Post by rzrgenesys187 on 2009-06-18
After putting my computer into suspend, when it starts back up there is no sound.  I have tried messing with options in /etc/modprobe.d/alsa-base as well as running /etc/init.d/alsasound stop before to unload the sound modules and starting them back up after resume and nothing has worked.

I am running a Toshiba Satellite P105-S6177 and here is the lspci output of my sound card
```
Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Toshiba America Info Systems AC97 Data Fax SoftModem with SmartCP
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at d0340000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Count=1/1 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

---

### Post by rzrgenesys187 on 2009-06-21
bump

---

### Post by rzrgenesys187 on 2009-11-08
bump

---

