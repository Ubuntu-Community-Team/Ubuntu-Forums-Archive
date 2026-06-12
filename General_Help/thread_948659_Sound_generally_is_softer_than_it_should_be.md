---
title: "Sound generally is softer than it should be"
date: 2008-10-15
forum: General Help
---

### Post by macaholic on 2008-10-15
For some reason on Ubuntu my sound is always softer than it should be, and I am forced to amplify the software equalizer (gnome) to it's highest mode to just hear normal stuff. Flash is especially bad. I am running 64-bit Hardy Heron, and use ALSA for Pulse to interface with my sound card. 
Ready and willing to post any further information or command outputs.
Any suggestion, insight, or input is always greatly appreciated.

---

### Post by Yellow Pasque on 2008-10-15
Pulse Audio has a volume control too. The easiest way to control it is with:
```
sudo apt-get install pavolumecontrol
```
I believe this will install a mixer-app under Sound and Video.

---

### Post by shawnrgr on 2008-10-15
Check your PCM volume, not just the Master volume. If pcm is low thats your problem

---

### Post by macaholic on 2008-10-18
<I apologize for late response>
> **Temüjin said:**
> Pulse Audio has a volume control too. The easiest way to control it is with:
```
sudo apt-get install pavolumecontrol
```
I believe this will install a mixer-app under Sound and Video.
Ya I've had that, but it only allows me to lower it past 0.00 db, I can't make it any louder.
Also, how would I increase my pcm volume if I'm using Pulse?

---

### Post by macaholic on 2008-10-22
Any ideas?

---

