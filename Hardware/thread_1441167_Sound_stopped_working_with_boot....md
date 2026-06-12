---
title: "Sound stopped working with boot..."
date: 2010-03-28
forum: Hardware
---

### Post by auvinen on 2010-03-28
Hi there.

I had working sound on my server, installed some security updates, now it doesn't work.

I originally got the sound working by following the sound troubleshooting guide in here:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

But now I can hear nothing... 
'alsamixer' works. And when I play stuff I get no errors. I just can't hear a thing. 

Something must have changed in the boot... But I can't figure out what.

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```lspci -v 
```
00:0f.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 06)
        Subsystem: Ensoniq ES1371 [AudioPCI-97]
        Flags: bus master, slow devsel, latency 32, IRQ 12
        I/O ports at a400 [size=64]
        Capabilities: [dc] Power Management version 1
        Kernel driver in use: ENS1371
        Kernel modules: snd-ens1371
```Anyone have idea what could cause this?

---

