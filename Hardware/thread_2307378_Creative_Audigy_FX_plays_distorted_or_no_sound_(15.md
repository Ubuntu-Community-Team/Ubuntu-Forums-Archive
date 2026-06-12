---
title: "Creative Audigy FX plays distorted or no sound (15.10)"
date: 2015-12-24
forum: Hardware
---

### Post by kaffelars on 2015-12-24
I have a Creative Audigy FX sound card that is behaving strange in Ubuntu 15.10 64-bit.
Sometimes I get sound when I log in, and then it suddenly stops. Other times I get only static noise at login, and only static for a while - then nothing.
The card works fine in Windows 10. I have also tried reinstalling Ubuntu, but this didn't help.

I have an Nvidia GTX 960 and it appears that both the Audigy and the nvidia HDMI output use the snd_hda_intel driver, this may be a part of the problem - but I can't find any working solutions.

Any suggestions?

---

### Post by bcschmerker on 2015-12-25
The Creative Laboratories® SB1570 low-profile audio card uses a Realtek® ALC889 audio chip (ALSA driver: snd-hda-intel), rather than a Creative® chip such as the CA10300-IAT (ALSA driver: snd-emu10k1; CA10200, CA10300 partially supported) in the SB1550 PCIe 2.0 x1 card that I've been testing in my own rig.  Otoh, the nVIDIA® GM206 with its HDMI output is currently supported only by nVIDIA Corporation, which has a long history of frenemyhood with the open-source community; the Maxwells all require closed-source firmware as of 24 December 2015.  Don't know whether the GeForce® Maxwell modules (packages: nvidia-current, nvidia-settings-current) will even tie into ALSA.

---

### Post by Yellow Pasque on 2015-12-25
I'm pretty sure I've seen very similar reports about this card. Every time someone thinks they've found the solution, it's back to spewing static at the next reboot.
If you want to try disabling the nvidia audio to see if it helps, you can use a line like this in /etc/modprobe.d/alsa-base.conf:
```
options snd-hda-intel enable="1,0"
```
(If this disables the Audigy, switch to 0,1

> Realtek® ALC889
It's actually 8**98**

---

