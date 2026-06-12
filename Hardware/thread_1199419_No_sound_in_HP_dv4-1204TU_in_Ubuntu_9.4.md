---
title: "No sound in HP dv4-1204TU in Ubuntu 9.4"
date: 2009-06-28
forum: Hardware
---

### Post by josevm on 2009-06-28
I've a HP dv4-1204TU with following sound card specifications.
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company Device 3627
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at da500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel
I configured latest ALSA  snapshot. But when i give,
gksudo gedit /etc/modprobe.d/alsa-base
 the output file is a blank page.
Can anyone help me out of this

---

