---
title: "Need help fixing audio"
date: 2010-08-30
forum: Hardware
---

### Post by Vannak on 2010-08-30
Story:
Installed ubuntu, sound worked. Graphics card (ATI Mobility Radeon HD5470) didn't. The auto hardware driver didn't work so I installed manually 10.8 driver. Sound stopped working. 

Here's some info:

aplay -l:
> **** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


lspci -v:
> 00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
    Subsystem: ASUSTeK Computer Inc. Device 1183
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at feb00000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

I only copied the audio section, if you want more I can just dump it. 

So what I'm thinking is that in the process of getting my graphics card working, it's HDMI output decided all the sound in my system should go through it and not through my generic card that goes to my speakers or headphones. I don't have an HDMI cord to check if it would output sound. 

I've gone through and check the equalizers, purged pulseaudio, and even tried to disable the HDMI output (though it doesn't appear to have worked seeing as it's still listed as my audio device). Does anyone know if that is indeed my problem, and if so how to fix it?

---

