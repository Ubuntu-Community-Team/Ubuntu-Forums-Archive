---
title: "Microphone not working (Thinkpad X301 + Conexant CX20561 (Hermosa) codec)"
date: 2010-10-17
forum: Hardware
---

### Post by maxigas on 2010-10-17
After updating to 10.10 (Meerkat) the microphone stopped working on my Thinkpad X301. There is an internal microphone and a minijack input for microphone, both worked before and neither works now. Skype doesn't work plus running "record -vv -fdat foo.wav" shows 00% and the resulting file is silent. I used alsamixer to unmute and amplify all input channels. I tried the process described on the following page and also looked for relevant bugs on launchpad: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) I tried to play around with parameters in /etc/modprobe.d/alsa-base.conf, like "options snd-hda-intel model=laptop", and now I have "options snd-hda-intel model=lenovo-x200" but it doesn't make a difference.

I attached the results of alsa-info.sh which I hope provides enough background. I am running the stock kernel now (although I started with Ubuntu Studio, 9.04 Jaunty Jackalope but I think this problem is not Studio-specific), "uname -a" returns:

Linux chaar 2.6.35-22-generic #34-Ubuntu SMP Sun Oct 10 09:26:05 UTC 2010 x86_64 GNU/Linux

Hope somebody has a tip,

---

