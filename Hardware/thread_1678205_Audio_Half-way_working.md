---
title: "Audio Half-way working"
date: 2011-01-29
forum: Hardware
---

### Post by computerman0219 on 2011-01-29
Hello everyone,

I am fairly new to Ubuntu and I have to say I really like it! The only real issue I have is that my audio is not working properly. If I plug in headphone it works great! However when I unplug the headphone I dont hear anything coming out of my speakers. I did notice if I turn them all the way up I can hear it but it is real quite. I tried searching for this issue but no luck so far. Here is some info I can give you...
```
Intel [HDA Intel], device 1: ALC889 Digital [ALC889 Digital]

```Also the speakers are logitech X-540 
I believe I have the gold, black, and green cables plugged into my MB

I am using the default software/driver for audio and I have tried Pulse Audio.
If I select analog output thats how I can bearly hear the music on speakers other settings I dont get anything.

I know this sounds to simple to hopefully I am missing something and someone can help me out please?!?

Thanks in advance!

---

### Post by lidex on 2011-01-30
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

