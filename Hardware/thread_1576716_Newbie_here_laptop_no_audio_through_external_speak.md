---
title: "Newbie here: laptop: no audio through external speakers"
date: 2010-09-17
forum: Hardware
---

### Post by allenwhoa on 2010-09-17
Hey what's up everyone. I've recently jumped on the Ubuntu bandwagon and did a successful install of 10.04 Desktop Edition on my laptop (Toshiba A135-S4407). I'm satisfied with everything I've experienced so far, except one small hiccup:

I like using my external speakers. For some reason every time I reboot my laptop, the audio decides it wants to play through the laptop's internal speakers. In order for me to get the sound to the external speakers I have to unplug the plug (laptop audio out --> speaker input plug) and plug it right back in.

By the way, I'm very new to Ubuntu and this is my first experience with it. If anyone can help me out with some simple or step by step instructions on how to fix this, or if I need to install anything, please help a newbie out! Thanks

---

### Post by lidex on 2010-09-17
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

### Post by allenwhoa on 2010-09-17
Thanks lidex. Here's the link: [http://www.alsa-project.org/db/?f=4d040158d68e8a464fbf2d6279d91f45a1bb2f5b](http://www.alsa-project.org/db/?f=4d040158d68e8a464fbf2d6279d91f45a1bb2f5b)

---

### Post by lidex on 2010-09-17
How about this output:
```
dpkg -l | grep "alsa"
```

---

### Post by allenwhoa on 2010-09-17
This is what showed up in terminal:

ii  alsa-base                                 1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                        0.10.28-1                                       GStreamer plugin for ALSA

---

### Post by lidex on 2010-09-17
A bit of a conflict with version numbers here:
```
!!ALSA Version
!!------------

Driver version:     1.0.21
Library version:    1.0.22
Utilities version:  1.0.22



```
I would suggest following the link in my sig to get alsa v.1.0.23
These newer codecs work better, for the most part, with latest driver.

---

### Post by allenwhoa on 2010-09-18
Thanks a ton. I'll give it a shot

---

