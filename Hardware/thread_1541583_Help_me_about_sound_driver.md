---
title: "Help me about sound driver"
date: 2010-07-29
forum: Hardware
---

### Post by dtphong_1989 on 2010-07-29
Hi everyone. My have a problem about sound driver. My laptop is Sony Vaio VPCEB190X. 

This's information my sound: 

Output lspci -v:
```
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
   Subsystem: Sony Corporation Device 9071
   Flags: bus master, fast devsel, latency 0, IRQ 22
   Memory at f6000000 (64-bit, non-prefetchable) [size=16K]
   Capabilities: <access denied>
   Kernel driver in use: HDA Intel
   Kernel modules: snd-hda-intel
```Output aplay -l:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```Plz help me. Thank u:(:(:(:(:(
[http://www.alsa-project.org/db/?f=c168e8cbe0cd1125b578a8be79b61c6c8443da7c](http://www.alsa-project.org/db/?f=c168e8cbe0cd1125b578a8be79b61c6c8443da7c)

---

### Post by dtphong_1989 on 2010-07-29
Nobody know???

---

### Post by jerenept on 2010-07-30
What exactly is wrong? no sound?

---

### Post by dtphong_1989 on 2010-07-30
> **jerenept said:**
> What exactly is wrong? no sound?
Yes, no sound

---

### Post by lidex on 2010-07-31
Thread is marked solved, is it?
If not, you need to upgrade alsa via the alsa-upgrade link in my sig.

---

