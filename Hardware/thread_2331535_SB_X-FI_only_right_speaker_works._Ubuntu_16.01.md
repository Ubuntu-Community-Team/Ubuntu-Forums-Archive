---
title: "SB X-FI only right speaker works. Ubuntu 16.01"
date: 2016-07-22
forum: Hardware
---

### Post by orca9999 on 2016-07-22
The sound card does show up in the sound dialog, but when working with it, it only outputs to the right front speaker. 

alsamixer has it listed as well, but when I switch to it, it tells me there are no controls. 

I can't find anything to fix this online, except that it is supposed to work with this version. 

I have checked, and everything is up to the latest versions. 

I do however also have 2 more sound sources:HDMI, which works.On the MB sound, did not try. 

I use the x-FI as it has true surround sound decoding, unlike the other on-board sound sources. 

Any help? 

Thanks in advance!

---

### Post by bcschmerker on 2016-07-24
I'm sorry, but as far as I am aware the Advanced LinUX Sound Architecture Project has abandoned development of the snd-ctxfi driver - Creative Technology, Ltd., proved of little to no help diagnosing the quirks of the E-MU® CA20K1 PCI 2.2 DSP and CA20K2 PCIe 2.0 x1 DSP used in the X-Fi® products.  ALSA does support some current (as of July 2016) Creative products; the E-MU® CA10300-IAT in the SB1550 Audigy 5 and RX is at least partially supported by snd-emu10k1 (originally developed for the E-MU® CA10K1, CA10K2, CA0100 and CA0102); and the Realtek® ALC-898 PCIe 3.0 x1 DSP in the SB1570 Audigy FX (which uses a Realtek® DSP) is fully supported, and the Creative Technology CA0132 SoundCore3D® PCIe 3.0 x1 DSP used in the Recon3D and Z/Zx/ZxR products at least partially supported, by snd-hda-intel.

---

