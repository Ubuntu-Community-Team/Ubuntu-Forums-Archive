---
title: "Audio Device Missing and No Sound Ubuntu 15.10"
date: 2015-11-15
forum: Hardware
---

### Post by salemboot2 on 2015-11-15
Installed Ubuntu 15.10.  I have no sound for my desired device (motherboard built-in sound) (Azalia device)

"lspci"
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA)
01:00.1 Audio device: NVIDIA Corporation GF108 High Definition Audio Controller (rev a1)

"alsactl init 0"
Found hardware: "HDA-Intel" "Realtek ALC889A" "HDA:10ec0885,1458a102,00100101" "0x1458" "0xa002"

Pulse audio only shows the Realtek card as Digital.  In 14.04, it also showed an Analog version.
That is, Digital & Analog  for the HDA-Intel.

It's a 785 Gigabyte motherboard with a 4200 HD Radeon video chip.  

Not sure if this is a bug in Alsa, Pulseaudio, or Kernel related.  I give up trying to post a bug report. it's just too confusing.,.,.,.,.,.

Thanks for any help.

---

