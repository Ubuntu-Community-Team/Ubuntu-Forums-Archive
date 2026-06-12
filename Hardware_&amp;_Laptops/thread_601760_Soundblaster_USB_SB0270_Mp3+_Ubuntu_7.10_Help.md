---
title: "Soundblaster USB SB0270 Mp3+ Ubuntu 7.10 Help"
date: 2007-11-03
forum: Hardware &amp; Laptops
---

### Post by mr_manson on 2007-11-03
Hi

I' ve installed on my Ubuntu 7.10 this external soundcard 

I naturallt deactivate from bios the soundmax onboard at my pc

The Card is recognized cause i can see it on Mixer and when i see something on youtube i can hear sound correctly but when i try to listen a video or mp3 no sound 

What can I try to do ?

Thanks

---

### Post by mr_manson on 2007-11-03
...then...

I try to update with synaptic package manager some alsa packet 

alsa-firmware-loaders    ALSA software loaders for specific hardware

alsamixergui                 graphical soundcard mixer for ALSA soundcard driver

alsaplayer-alsa               PCM player designed for ALSA (ALSA output module)

aconnectgui                    graphical ALSA sequencer connection manager

and now is all ok ! :) (I think the first alsa-firmware-loaders is the necessart upgrade packet):-D

---

### Post by Snire on 2007-11-03
Thank you for this. I have a Soundblaster USB soundcard and the same problems. I will try your advise tomorrow.
BTW, my first post here at the forum.

I bought an Acer TM4230 with Vista preinstalled. And that made me look for an alternative os. Vista is not good. I think now after trying Ubuntu for some weeks, I will never return to Vista.

---

### Post by mr_manson on 2007-11-04
Eheheheh 

I know what you mean about Vista....

I'm not so expert about Ubuntu but is very easy to serach update and many other software with the update package manager 

Good Luck

:)

---

### Post by rklauco on 2007-11-10
Go to sound control panel and select USB audio as default sound device.
I had to do more hacking with mplayer (edit the gui.conf and insert ao_driver = "alsa:device=hw=1.0" and edit the mplayer.conf and add ao=alsa:noblock:device=hw=1.0 and softvol=yes).
Using this I can play videos, mp3 and everything using the USB card.

---

### Post by Odisej on 2007-11-29
I have Soundblaster USB and it generally works. But I still have some problems with it. First of all, did anybody succeed in  enabling Optical Out to work properly? That is, i would like to use AC3 output but could not do it. There is also a peculiar problem with mixer-applet2. Sometimes it just locks up using 100% of processor power saying that USB soundblaster is not connected. I cannot figure it out why as it sometimes appears in half an hour sometimes not at all. Anybody having the same problems? 

Thanx,

Odisej

---

