---
title: "CPU Frequency Scaling Misbeheaving"
date: 2010-04-30
forum: Hardware
---

### Post by sdm_cacto on 2010-04-30
Hi, I'm using Ubuntu Lucid right now with a Dell Inspiron 1521,  CPU is an "AMD Athlon 64 X2 Dual Core Processor TK-55".

The problem has existed since Ubuntu Karmic at least, but I havent noticed it in older versions of Ubuntu.

CPU Frequency Scaling changes itself to the lowest, even if I'm using Performance Mode, I the CPUFreq Applet indicator's bar goes to the lowest. If I switch it to 1800mhz (the highest) it automatically goes down to 800 Mhz. 

This happens specially while I'm watching movies (specially 720p movies or h264 compressed videos) and while I'm watching flash videos. Sometimes the bar goes up for a while, but then it goes down again.

The effect is that the problem affects general system performance heavily and causes severe frame drops while playing videos.

Thanks

---

### Post by sdm_cacto on 2010-05-01
Update: it also happens while playing MP3 tracks on rhythmbox. Te CPU frequency just steps down to the lowest, causing the song to stop for a couple of seconds.

That means that it happens in Lucid worst than in karmic

Plase help.

---

### Post by sdm_cacto on 2010-05-01
Another update: when playing any MP3 on totem, the problem occurs. Might be a pulseaudio bug.

---

### Post by Yellow Pasque on 2010-05-01
Perhaps there is a setting in the BIOS which is interfering.

---

### Post by sdm_cacto on 2010-05-01
Just resetted Bios configuration to default, theres wasn't a lot of options and they didn't sound like they had anything to do with the problem, except AMD powernow, which is necessary. The problem persists

---

### Post by sdm_cacto on 2010-05-02
I think this should be moved to Multimedai & Video.

---

### Post by mk4umha on 2010-05-18
I have this same problem on my Dell E6400 after doing a clean install of 10.04 from 9.10. The CPU autoscales until I run totem streaming internet radio, then it stays stuck at 800mhz until I kill Totem.

---

### Post by sdm_cacto on 2010-05-18
I've just solved the problem, it was not a bug afterwards.

What happened was that the laptop was overheating, so I had use a usb fan tray for a while (I borrowed it for a friend).
Patiently I opened up my laptop using a manual I've found online, at dells official website (for parts replacement and stuff, not really intended for the owner).
There was a lot of dirt blocking the heatsink that was it.

You should first try xsensors (you can find it on synaptic) to monitor your system's temperature while you watch an HD movie, or listen to music or all together... my laptop was somewhere around 75ºC or more.

---

### Post by mk4umha on 2010-05-18
I have the lm-sensors running and processor temp is around 60C so I don't see how that's overheating but I'll see if there are any dust bunnies.

---

