---
title: "ALSA settings don't affect mic capture level."
date: 2008-11-20
forum: Hardware
---

### Post by vandalay on 2008-11-20
Hi,

I have an HP Pavillion dv6000 running an AMD64 version of Intrepid.

Everything works brilliantly except for the microphone capture level - I want to record some guitar tracks using Ardour, however the mic capture level is constantly peaking so the resulting recording is clipped and sounds horrible. 

:guitar:

I have tried changing settings in the volume applet and using alsamixer... the sliders all seem to be there but have no effect on the capture levels. Running just 'alsamixer' at the command line lets me set levels at Pulseaudio level, and running 'alsamixer -c 0' lets me set them for the "Conexant CX20549 (Venice)" card directly, but neither of these have any effect. The relevant input seems to be "IntMic" even though it is an external mic.

Does anyone know if mic capture levels are supported for this sound card using ALSA?

---

### Post by ireneshusband on 2009-07-27
Did you ever find a solution to this? I have an identical situation on the same sound card (including the anomaly with the internal and external mic being confused). However in my case the problem just suddenly appeared. In other words it was working fine, and then all of a sudden I couldn't adjust the capture level any more.

---

### Post by lhtown on 2009-08-10
Check this out:
[https://launchpad.net/~c4pp4/+archive/cx20549](https://launchpad.net/~c4pp4/+archive/cx20549)

---

