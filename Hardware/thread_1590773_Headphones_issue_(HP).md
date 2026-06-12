---
title: "Headphones issue (HP)"
date: 2010-10-08
forum: Hardware
---

### Post by WannabeHammett on 2010-10-08
Hi, 

I have installed Ubuntu 10.04 on my HP DV6 2005AX laptop [AMD Turion 2.2 GHz; 4GB RAM DDR2; IDT High Definition Audio CODEC Driver; Altec Lansing Speakers]

Problem is, when i plug in my headphones, the sound plays through but with the speakers unmuted. A way to solve this?


adarsh@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: STAC92xx Digital [STAC92xx Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
Subdevices: 1/1
Subdevice #0: subdevice #0

adarsh@ubuntu:~$ lspci -v
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
Subsystem: Hewlett-Packard Company Device 3637
Flags: bus master, slow devsel, latency 64, IRQ 16
Memory at f2400000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel

01:00.1 Audio device: ATI Technologies Inc RV710/730
Subsystem: Hewlett-Packard Company Device 3637
Flags: bus master, fast devsel, latency 0, IRQ 19
Memory at f2310000 (32-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel

Thanks in advance :)

---

