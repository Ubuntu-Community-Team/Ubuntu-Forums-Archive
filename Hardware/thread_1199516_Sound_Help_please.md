---
title: "Sound Help please"
date: 2009-06-29
forum: Hardware
---

### Post by yang925 on 2009-06-29
So im having sound problems on My dell opensource inspiron 15N. the sound worked when i got the laptop as Ubuntu 8.10. I upgraded to 9.04 and installed KDE and misc apps including virtual box. Now the sound dosn't work. The volume is at 95% and aplay -l:

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```

lspci -v| less:

```

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
        Subsystem: Dell Device 02aa
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at f6afc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel


```

I think its due to the kernal upgrades ether from 8.10 to 9.04 or the updated kernal from installing Virtual Box. Help Please?

---

