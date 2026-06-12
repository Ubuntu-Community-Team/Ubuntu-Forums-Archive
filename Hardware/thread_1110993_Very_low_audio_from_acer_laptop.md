---
title: "Very low audio from acer laptop"
date: 2009-03-30
forum: Hardware
---

### Post by openfreak on 2009-03-30
Very low volume on acer 4720z
Hi guys ,
I am using Acer 4720Z laptop,F10,linux kernel 2.6.29/2.6.28.3/default kernel of F10.
The problem is the sound through the speaker is barely audible whereas in windows xp it quiet loud.
Similar problem exists when using headphones - the sound is audible but not loud enough.

From dmesg:
Code:

[    1.354889] hda_codec: Unknown model for ALC268, trying auto-probe from BIOS...
[    1.355345] ALSA sound/pci/hda/hda_codec.c:3503: autoconfig: line_outs=1 (0x15/0x0/0x0/0x0/0x0)
[    1.355349] ALSA sound/pci/hda/hda_codec.c:3507:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    1.355352] ALSA sound/pci/hda/hda_codec.c:3511:    hp_outs=1 (0x14/0x0/0x0/0x0/0x0)
[    1.355355] ALSA sound/pci/hda/hda_codec.c:3512:    mono: mono_out=0x0
[    1.355358] ALSA sound/pci/hda/hda_codec.c:3520:    inputs: mic=0x19, fmic=0x18, line=0x1a, fline=0x0, cd=0x0, aux=0x0

It indicates that I have Realtek ALC268 audio Chipset

---

