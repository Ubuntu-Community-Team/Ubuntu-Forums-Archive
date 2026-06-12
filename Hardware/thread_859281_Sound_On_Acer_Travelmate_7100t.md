---
title: "Sound On Acer Travelmate 7100t"
date: 2008-07-14
forum: Hardware
---

### Post by rosros-3 on 2008-07-14
Has anyone ever got sound working in Linux on this old laptop?
The technical manual supplies detailed data on the sound chip (writing a sound driver should have been possible; I [recompiled and] modprobed  all Alsa modules and tried OSS Opensound without success).
It starts with:
"NMA1 is a single audio chip that integrates OPL3 FM and its DAC, 16bit Sigma-delta CODEC, MPU401 MIDI interface, and a 3D enhanced controller including all the analog components which is suitable for multi-media application. This LSI is fully compliant with Plug and Play ISA 1.0a, and supports all the necessary features, i.e. 16bit address decode, more IRQs and DMAs in compliance with PC’96. This LSI also supports the expandability, i.e. Zoomed Video and Modem interface in a Plug and Play manner, and power management(power down, power save, partial power down, and suspend/resume) that is indispensable with power-conscious application."
Sound worked very well in Windows95.

The (BIOS) values of the on-board NMA1 sound chip can be set with isapnp (pnnpdump recognizes it as NMA2100, NeoMagic 3D sound system); original values that worked in W95 are accepted, except for the IRQ apparently in conflict with the eth0 card, and therefore set to 10 (which does not conflict with any other IRQ). Unfortunately this is not enough without the right driver; the ALSA modules snd-nm256 and snd-opl3sa2 do not work (alsamixer replies "snd_ctrl_open failed"). lspci cannot find anything but with dmesg one finds the row "isapnp: Neomagic Sound 3D system", and a similar row with hwinfo -sound. Featherlinux and DSL do not recognize the sound chip (and both freeze the computer when I plug in the net card).

---

