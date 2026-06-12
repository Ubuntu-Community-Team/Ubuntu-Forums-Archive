---
title: "Realtek ALC887-VD missing driver (Front panel audio &amp; microphone not working)"
date: 2020-04-20
forum: Hardware
---

### Post by norbi095 on 2020-04-20
Hello Everyone!
I could use some help finding a way to set up the front-panel audio ports on my new PC,  (green, and pink) since none of them work under Ubuntu as of now.
I"ve been trying to find a solution since months, hopefully someone can provide some info, or has had a same config as I do, with the same ALC887-VD Chipset, to get the audio & microphone working.

So If I plug in my headphones to the front ports, I cant hear anything.
(Under Windows 10, it works fine, it even has a notification when I plug in the headphones to the front port, allowing me to choose the type of the sound device in the realtek audio console).

The back audio ports on my motherboard IO work fine though, its the front panel that does not seem to be recognized. I"ve messed around in alsamixer, pulseaudio for months, without any luck. Someone also suggested hdajackretask on Reddit when I posted about my problem there too, but since its no longer available for 19.10 or newer, it cannot be installed.
Is there even anyone who had success with this chipset? Is it even supported on Linux? It has to be.. 

Thanks for the infos, if anyone has anything...

---

### Post by Yellow Pasque on 2020-04-21
Start here:
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

> Someone also suggested hdajackretask on Reddit when I posted about my problem there too, but since its no longer available for 19.10 or newer, it cannot be installed.
Sure it can. It's part of alsa-tools-gui:
```
sudo apt-get install alsa-tools-gui
```

---

### Post by sebastienserre on 2021-01-19
Hello,

I'm occurring the same problem, here's my Alsa Log:
[http://alsa-project.org/db/?f=1a01ce2148dfd57d938709f372a8d0b568d658cc](http://alsa-project.org/db/?f=1a01ce2148dfd57d938709f372a8d0b568d658cc)

Hope someone could help me.

---

