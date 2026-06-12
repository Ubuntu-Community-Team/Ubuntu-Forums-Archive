---
title: "Soundcard / -chip SiS 7012 not supported?"
date: 2006-03-24
forum: Hardware &amp; Laptops
---

### Post by BOK on 2006-03-24
Hi all!

On my Fujistu-Siemens Scaleo 600 (one with a P4 and SiS 648FX chipset) sound has never worked on ANY Linux-distribution before, so I'm wondering if anyone has got this working. So it's not Ubuntu or Badger specific.

The specific device with "lspci -v":

```
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
        Subsystem: Fujitsu Siemens Computer GmbH: Unknown device 1030
        Flags: medium devsel, IRQ 177
        I/O ports at 1400 [size=256]
        I/O ports at 1000 [size=128]
        Capabilities: [48] Power Management version 2
```

When using the module "snd_intel8x0" the dmesg-output is:

```
[4296201.468000] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 177
[4296202.469000] codec_ready: codec is not ready [0x340000]
[4296202.469000] ACPI: PCI interrupt for device 0000:00:02.7 disabled
[4296202.469000] Intel ICH: probe of 0000:00:02.7 failed with error -5
```

And with the other i810-module "i810_audio":

```
[4296153.634000] Intel 810 + AC97 Audio, version 1.01, 16:58:59 Mar 20 2006
[4296153.634000] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 177
[4296153.634000] i810: SiS 7012 found at IO 0x1000 and 0x1400, MEM 0x0000 and 0x0000, IRQ 177
[4296154.134000] i810_audio: Codec not ready.. wait.. no response.
[4296155.134000] i810_audio: Audio Controller supports 6 channels.
[4296155.134000] i810_audio: Defaulting to base 2 channel mode.
[4296155.134000] i810_audio: Resetting connection 0
[4296155.134000] i810_audio: Primary codec not ready.
[4296155.135000] ac97_codec: AC97 Audio codec, id: 0x8384:0x7658 (Unknown)
[4296155.135000] i810_audio: AC'97 codec 0 supports AMAP, total channels = 6
```

It always comes down to the "primary codec not ready"... :-k 
This is puzzling me for the last 3 years and one of the main reasons why I'm almost always booting Windows XP. In WinXP it's a Sigmatel STAC9758-driver doing the stuff.


Anyone ever had this combo working before?

---

