---
title: "hda sound card not properly detected and installed"
date: 2013-05-07
forum: Hardware
---

### Post by seedsgrow on 2013-05-07
I just got a new computer with a 7 Series/C210 Series Chipset Family High Definition Audio Controller. It is listed when I run lspci, along with the sound controller on my video card:

00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Turks/Whistler HDMI Audio [Radeon HD 6000 Series].


However, when I run cat /proc/asound/card*/codec#* | grep -i codec, all I get is the controller on the video card:

Codec: ATI R6xx HDMI.


The Intel on-board audio also does not show up in the list of devices in alsamixer. I tried a live session with a DVD of openSuSE 12.3, and it didn't detect the Intel audio controller, either. Is this a new chipset without ALSA support yet?

---

