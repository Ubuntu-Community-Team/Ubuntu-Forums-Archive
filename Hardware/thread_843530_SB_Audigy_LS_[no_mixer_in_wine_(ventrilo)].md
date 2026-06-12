---
title: "SB Audigy LS [no mixer in wine (ventrilo)]"
date: 2008-06-28
forum: Hardware
---

### Post by aer0nz on 2008-06-28
Okay guys, I have a Creative Labs SB Audigy LS.

my problem is that WINE, does not recognize my sound card as an input device, i have my microphone plugged in, and i can hear it just fine in the
sound options and such. but ventrilo does not detect a mixer, which means i can't talk. neither ALSA or OSS work. CA0106

help is appreciated. i can hear voices in ventrilo, i can hear sounds in CS and WoW. its just really annoying not being able
to talk to my guild during raids and having to type my responses, they are sick of it, and i'm sick of it. but, i'm not getting rid of my trusty ubuntu, its been kind to me so far.

>_<

---

### Post by webbed on 2008-11-04
I have the same issue, I have tried enabling both the Alsa and OSS drivers for Wine but still get not mixer in Ventrilo.

System Information:
Ubuntu 8.10 x64
Wine 1.01 Stable
Ventrillo 3.03

Am able to record sound in Sound Recorder using the OSS driver.

Any help would be appreciated.

---

### Post by webbed on 2008-11-06
Was able to figure out the cause of my issue, the ALSA drivers to not support the Analog/Digital source for my sound card.

[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs")

OSS Mixer support for Wine is also not supported for my card.

Wasn't sure sure which card was yours aer0nz but you can check all the Alsa details there.

From my understanding you need working ALSA for both input and output to be able to easily use Ventrilo as you would in Windows.

---

