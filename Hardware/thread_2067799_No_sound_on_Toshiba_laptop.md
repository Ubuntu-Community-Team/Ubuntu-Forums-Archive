---
title: "No sound on Toshiba laptop"
date: 2012-10-07
forum: Hardware
---

### Post by gibbyoxley on 2012-10-07
**No sound on Toshiba Satellite P105-S6114 laptop** 			
 			 			 		   		 		 		I was hoping  someone might be able to help my no sound problem. I just finished  installing Ubuntu 12.04 LTS Desktop on my Toshiba Satellite P105-S6114

I get the following info from 
sudo lspci |more:

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio C
ontroller (rev 02)
    Subsystem: Toshiba America Info Systems AC97 Data Fax SoftModem with Sma
rtCP
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at b0000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
  
I've also double check in alsa mixer to make sure it was not muted. As I suspected it was not muted.

I'm getting no sound through the built in speakers, headphone jack, or  the speaker jack. Any help would be much appreciated!!! Thank you in  advance!

---

### Post by ajgreeny on 2012-10-07
Check also in pulseaudio-volume-control.

---

### Post by jalirious on 2012-10-11
What worked for me was..

->system settings -> sound

Select 

LFE on Separate Mono Output / Amplifier

---

