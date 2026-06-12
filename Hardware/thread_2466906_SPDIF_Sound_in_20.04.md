---
title: "S/PDIF Sound in 20.04"
date: 2021-09-09
forum: Hardware
---

### Post by jsland on 2021-09-09
Just added a new PCI sound card after being unable to get S/PDIF working using motherboard based ALC892.

Much time has been spent looking for answers and trying things like adding driver packages for new emu10k1 based card.

S/PDIF was working in 14.04 before building a new desktop running 20.04.  Comparing the two alsa-base.conf files they are identical.

Using pavucontrol or Sound the new output configuration is set to Digital but testing produces no sound.

The configuration seems very close to working but I am missing something in setup like a switch to get from PCM to S/PDIF.

There are 3 sound cards listed in aplay with the wanted device shown as card 0 device 0 but it goes on to say Standard PCM Playback which I believe needs to say Generic Digital.

---

