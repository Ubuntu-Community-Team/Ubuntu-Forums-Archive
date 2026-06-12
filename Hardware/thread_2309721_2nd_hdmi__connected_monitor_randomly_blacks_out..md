---
title: "2nd hdmi  connected monitor randomly blacks out."
date: 2016-01-12
forum: Hardware
---

### Post by ravimannan2002 on 2016-01-12
I attach my laptop to a 2nd monitor via HDMI. This monitor blacks out randomly. I think it's random, at least. I'm not sure if it's going into sleep mode or not. I went into my laptop and monitor settings and turned off any power saving and sleep modes.  I
tried the nouveau driver, nvidia "proprietary,tested driver" and  the nvidia "proprietary" driver and I still have the same problem. I checked my cables and they are not loose. I even used a different hdmi port.
Later, I switched to the Intel graphics card. I'm pretty sure now nvidia is disabled. I'm still having the same effing problem!!!!!!!!!!!!!!!!!!!!

I'm not sure what type of log would help diagnose the problem. I did do a dmesg and this is what I got:

Another thing is that when I am playing music through the hdmi cable (the monitor has speakers) and the screen blacks out, the audio shuts off as well. So that's why I thought it was the cable, but the cable is on their tight.

The monitor blacks out even when I am typing, so it's not going into any power save mode, from what I can tell. I disabled every power saving feature I could find in  ubuntu and in the monitor preferences.

Somebody help. :popcorn:

---

### Post by ravimannan2002 on 2016-01-25
I tried this with windows 10 and it works ok. This mean the monitor and cable are fine. So what do I do for linux?

---

### Post by ravimannan2002 on 2016-01-26
It doesn't seem to be happening at a lower resolution of    2560x1080:

HDMI1 connected 2560x1080+1920+0 800mm x 335mm
   3440x1440      50.0 +   30.0  
   2560x1080      60.0*

---

### Post by ravimannan2002 on 2016-08-14
it was the refresh rate. it was too high for the 3440x1440 rez. use xrandr to 30

---

