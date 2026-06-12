---
title: "Acer aspire 4736z sound issue with headphone jack"
date: 2009-07-26
forum: Hardware
---

### Post by vaib on 2009-07-26
I have recently bought this new laptop Acer aspire 4736z. It gives sound from laptop speakers fine. But no matter what i do headphone doesn't get any voice. When i connect headphone sound still keeps cming from laptop speakers. I have already tried 
*options* snd-*hda*-intel model=*acer*-aspire/acer and 10s of models, but it remains same. Any help would be really great.

Kernel : 2.6.30-1-686
alsa version : 1.0.20


# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #


# amixer info
Card default 'Intel'/'HDA Intel at 0x98800000 irq 22'
  Mixer name    : 'Intel G45 DEVCTG'
  Components    : 'HDA:10ec0888,10250260,00100202 HDA:11c11040,10250260,00100200 HDA:80862802,80860101,00100000'
  Controls      : 37
  Simple ctrls  : 21


Alsa-info output:
[http://www.alsa-project.org/db/?f=bb60bf477ec553cb250b12b7f9e7d77e9b9219cd](http://www.alsa-project.org/db/?f=bb60bf477ec553cb250b12b7f9e7d77e9b9219cd)

---

### Post by Shanison on 2009-09-28
hi, i also have the same problem. However, my computer is Aspire 6930Z and the problem is exactly the same as you. Any help from here?

---

### Post by vaib on 2009-09-28
You may need to give correct model name. "acer-aspire-4930g", I used this option and its working fine for me. List of models you can find on the following link.

[http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.31.y.git;a=blob;f=Documentation/sound/alsa/HD-Audio-Models.txt;h=939a3dd5814817d222ff64c8ce4489a16f8d9930;hb=2147b209180701193e4a154896494aeeeab9d268](http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.31.y.git;a=blob;f=Documentation/sound/alsa/HD-Audio-Models.txt;h=939a3dd5814817d222ff64c8ce4489a16f8d9930;hb=2147b209180701193e4a154896494aeeeab9d268)

---

### Post by Shanison on 2009-09-28
Hi, sorry that I am a newbie to ubuntu. I don't quite get you. My Acer model is ASPIRE 6930Z. What should I edit in order to make the sound jack working? Can you give me a bit more details. I would really appreciate that. Thank you! Quite sad without sound from the earphone

---

### Post by vaib on 2009-09-28
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

A quick search gave this link. You can go through it.



In short you need to modify file :[FONT=monospace] [/FONT]/etc/modprobe.d/alsa-base
make a entry : options snd-hda-intel model=MODEL

for example in my case as u can see from my first post i have model ALC888.
From 2nd post's link you can see all options for ALC888:

ALC883/888 [ 133]("http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.31.y.git;a=blob;f=Documentation/sound/alsa/HD-Audio-Models.txt;h=939a3dd5814817d222ff64c8ce4489a16f8d9930;hb=2147b209180701193e4a154896494aeeeab9d268#l133") ==========
 [ 134]("http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.31.y.git;a=blob;f=Documentation/sound/alsa/HD-Audio-Models.txt;h=939a3dd5814817d222ff64c8ce4489a16f8d9930;hb=2147b209180701193e4a154896494aeeeab9d268#l134")   3stack-dig    3-jack with SPDIF I/O
 [ 135]("http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.31.y.git;a=blob;f=Documentation/sound/alsa/HD-Audio-Models.txt;h=939a3dd5814817d222ff64c8ce4489a16f8d9930;hb=2147b209180701193e4a154896494aeeeab9d268#l135")   6stack-dig    6-jack digital with SPDIF I/O
 [ 136]("http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.31.y.git;a=blob;f=Documentation/sound/alsa/HD-Audio-Models.txt;h=939a3dd5814817d222ff64c8ce4489a16f8d9930;hb=2147b209180701193e4a154896494aeeeab9d268#l136")   3stack-6ch    3-jack 6-channel
 [ 137]("http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.31.y.git;a=blob;f=Documentation/sound/alsa/HD-Audio-Models.txt;h=939a3dd5814817d222ff64c8ce4489a16f8d9930;hb=2147b209180701193e4a154896494aeeeab9d268#l137")   3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
 [ 138]("http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.31.y.git;a=blob;f=Documentation/sound/alsa/HD-Audio-Models.txt;h=939a3dd5814817d222ff64c8ce4489a16f8d9930;hb=2147b209180701193e4a154896494aeeeab9d268#l138")   6stack-dig-demo  6-jack digital for Intel demo board
 [ 139]("http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.31.y.git;a=blob;f=Documentation/sound/alsa/HD-Audio-Models.txt;h=939a3dd5814817d222ff64c8ce4489a16f8d9930;hb=2147b209180701193e4a154896494aeeeab9d268#l139")   acer          Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
 [ 140]("http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.31.y.git;a=blob;f=Documentation/sound/alsa/HD-Audio-Models.txt;h=939a3dd5814817d222ff64c8ce4489a16f8d9930;hb=2147b209180701193e4a154896494aeeeab9d268#l140")   acer-aspire   Acer Aspire 9810
 [ 141]("http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.31.y.git;a=blob;f=Documentation/sound/alsa/HD-Audio-Models.txt;h=939a3dd5814817d222ff64c8ce4489a16f8d9930;hb=2147b209180701193e4a154896494aeeeab9d268#l141")   acer-aspire-4930g Acer Aspire 4930G
 [ 142]("http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.31.y.git;a=blob;f=Documentation/sound/alsa/HD-Audio-Models.txt;h=939a3dd5814817d222ff64c8ce4489a16f8d9930;hb=2147b209180701193e4a154896494aeeeab9d268#l142")   acer-aspire-6530g Acer Aspire 6530G
 [ 143]("http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.31.y.git;a=blob;f=Documentation/sound/alsa/HD-Audio-Models.txt;h=939a3dd5814817d222ff64c8ce4489a16f8d9930;hb=2147b209180701193e4a154896494aeeeab9d268#l143")   acer-aspire-8930g Acer Aspire 8930G
.....
.....

So its basically hit and trial which of above model for ALC888 would work for me.
You need to give model name and reboot your machine.

i made entry : "options snd-hda-intel model=acer-aspire-4930g" which worked fine for me.

---

