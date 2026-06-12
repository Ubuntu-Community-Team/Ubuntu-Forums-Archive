---
title: "Front audio output stopped working after upgrading to 16.04"
date: 2016-08-17
forum: Hardware
---

### Post by temmokan on 2016-08-17
After upgrading from 12.04 (64-bit) to 16.04 (motherboard P7H55-M PRO) front panel audio output stopped working.

I have followed all steps from

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

No visible problems there. Audio device recognized, proper kernel modules installed, sound control shows there's output, but front output plays nothing.

I have used rear jack as temporary solution, but front one is required. Is the above known problem for 16.04?

More information:

```
$ sudo lspci -v | grep -A7 -i "audio"

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
    Subsystem: ASUSTeK Computer Inc. 5 Series/3400 Series Chipset High Definition Audio
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Memory at f7ff8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link

$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: MID [HDA Intel MID], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ aplay /usr/share/sounds/alsa/Front_Center.wav
(plays expected file on rear audio jack; outputs nothing on front)


```

Thank you in advance.

---

