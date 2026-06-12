---
title: "No sound from Realtek ALC670"
date: 2010-10-05
forum: Hardware
---

### Post by bentkamp on 2010-10-05
Hi,

I installed Ubuntu 10.04 using Wubi. It works, but I don't hear any sound. My soundcard is Realtek ALC670. I already updated ALSA to version 1.0.23, but it still doesn't work.

Some further information:

linux@ubuntu:~$ uname -a
Linux ubuntu 2.6.32-25-generic-pae #44-Ubuntu SMP Fri Sep 17 21:57:48 UTC 2010 i686 GNU/Linux

linux@ubuntu:~$ aplay -l
**** Liste der Hardware-Geräte (PLAYBACK) ****
Karte 0: Intel [HDA Intel], Gerät 0: ALC670 Analog [ALC670 Analog]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 1: Generic [HD-Audio Generic], Gerät 3: HDMI 0 [HDMI 0]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
linux@ubuntu:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Oct  4 2010 for kernel 2.6.32-25-generic-pae (SMP).
linux@ubuntu:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC670

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI
linux@ubuntu:~$ lspci -v

[...]

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
    Subsystem: Acer Incorporated [ALI] Device 042f
    Flags: bus master, fast devsel, latency 0, IRQ 35
    Memory at c6500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

[...]

01:00.1 Audio device: ATI Technologies Inc Juniper HDMI Audio [Radeon HD 5700 Series]
    Subsystem: Acer Incorporated [ALI] Device 042e
    Flags: bus master, fast devsel, latency 0, IRQ 37
    Memory at c6420000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

[...]

Can you help me?

---

### Post by bugapi on 2010-11-11
Same issue with Maverick (Ubuntu 10.10) on an Apple mac pro 5.1.

All settings have been verified several times (mute, etc.).

Also tried the two sound cards without any difference.

Sound hardware is the same, leading to think about that drivers are the issue.

---

### Post by mastablasta on 2010-11-11
have you tried upgrading the drivers (ALSA)?

---

