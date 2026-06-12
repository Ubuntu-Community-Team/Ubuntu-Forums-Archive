---
title: "Audio problem. The same."
date: 2012-09-08
forum: Hardware
---

### Post by cklinx on 2012-09-08
Hi at all,

is the second time that i meet the same problem with audio in ubuntu 12.04.
The first time i had to reinstall all the operative system cause i really got crazy... and now again.

I really don't understand why, without any reason, when i turn off my computer the audio stop to work. I think cause the update but i am not sure about that.

i tried to reinstall alsa, pulseaudio, recompile audio driver but nothing.

Shall someone help me please?

Below some command:

aplay -l 
```
marko@marko-System-Product-Name:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```lspci
```
lspci -v | grep -A7 -i "audio"00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
    Subsystem: ASUSTeK Computer Inc. M5A88-V EVO
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at fe6f4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

--
01:05.1 Audio device: Advanced Micro Devices [AMD] nee ATI RS880 HDMI Audio [Radeon HD 4200 Series]
    Subsystem: ASUSTeK Computer Inc. M5A88-V EVO
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at fe8e8000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

```i set up all alsamixer options.

Thanks.

---

### Post by cklinx on 2012-10-07
The problem resolved itself alone after update.

---

### Post by vkadal on 2012-10-07
I opened the system settings, sound and clicked test buttons. I have seen the audio started working. No logic behind this procedure, but it may work.

---

