---
title: "[SOLVED] earphone jack not functioning (vaio)"
date: 2007-11-05
forum: Hardware &amp; Laptops
---

### Post by astarem on 2007-11-05
Hi,

I'm a first time linux/ubuntu user and  using gutsy on a dual boot vaio fz160e laptop.

My problem is that although I have no problem about the sound output from the built in speakers, there is no output from the earphone jack. Sound keeps coming from the speakers when the earphones are plugged in and there is no sound coming from the latter. The earphones and the jack are both functional under vista. So, I need to find out how to enable the earphone jack and also how to disable sound output from the speakers when earphones are plugged in under ubuntu. 

I would welcome if anyone able to assist me on this could indicate the commands that I should run in the terminal to provide more information if needed. 

Thanks in advance!

astarem

---

### Post by astarem on 2007-11-05
I forgot mentioning in the first message, the default device in the "Volume Control" is SigmaTel STAC9872AK (OSS Mixer) and there is nothing but the volume ticker in the its preferences dialogue...Also even if I change the device to HDA Intel (Alsa Mixer), there are only the master, PCM and digital tickers under the preferences dialogue.

thanks again...

---

### Post by astarem on 2007-11-06
Apparently I did not conduct proper research before posting...

My problem is solved after following the how to at the following address:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

