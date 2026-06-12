---
title: "How to control GPU's fan (strange behavior)?"
date: 2018-12-30
forum: Hardware
---

### Post by dowoshek on 2018-12-30
Hi,
I'm looking for application that can control graphics card's fans speed depending on the current temperature. My GeForce 1060 Expedition fans keep turning on and off. It literally turns on for half a second and stops, about 60 times in a single minute. It starts acting this way when temperature is 57 and stops below 50. Silent but really annoying sounds and I'm worried about its lifespan. Is there any solution for Linux users or can it be modified by firmware or Windows application?

---

### Post by CatKiller on 2018-12-30
They're designed to turn off and on: it won't adversely affect their lifespan.

The fan curve is stored in the firmware of the graphics card. There's nothing available for Linux that will let you edit it, but there are some enthusiast Windows applications that will. Once you've changed the fan curve in Windows it will apply in Linux too, since it's stored on the card.

---

### Post by dowoshek on 2018-12-30
> **CatKiller said:**
> They're designed to turn off and on: it won't adversely affect their lifespan.
But it literally turns on and off about 40-60 times in 1 minute. Why can't it run until it goes down to 50 temperature? Is it really normal? It's actually not the speed making noise - it's the start and stop sounds.

---

### Post by CatKiller on 2018-12-30
> **dowoshek said:**
> But it literally turns on and off about 40-60 times in 1 minute. Why can't it run until it goes down to 50 temperature? Is it really normal? It's actually not the speed making noise - it's the start and stop sounds.

[This](https://www.ekwb.com/blog/what-is-pwm-and-how-does-it-work/) is how PWM works.

The zone you're talking about is where the duty cycle is high enough to make the fan start to spin, but not high enough to overcome the inertia of the fan itself. So it throbs.

You control the duty cycle at a given temperature with the fan curve.

---

### Post by QIII on 2018-12-30
This is exactly why I prefer voltage regulation over PWM and use the former when I can.

Voltage regulation changes over a smoother curve.  Those changes, and the attendant fan noise, are nearly imperceptible.

The impulse with PWM is on/off, so there is a sharp noise at each "on kick".  The fan is actually stuttering.  If your temp happens to be hovering slightly back and forth across some minimal horizon, that chatter can happen rapidly.  The average rpms will be low, but the pulses may be very quick.

If the level of noise is not disturbing, then don't worry about it -- unless the electrical noise throughout the system, over your speakers for instance, is a problem.

---

### Post by dowoshek on 2018-12-31
Thx for all replies.
I guess I'd need to set higher the lowest speed of fan using Asus GPU Tweak. Do you know if it'd be against the typical warranty rules?

---

### Post by Yellow Pasque on 2018-12-31
> But it literally turns on and off about 40-60 times in 1 minute. Why can't it run until it goes down to 50 temperature?

Yeah, that's how it should work to prevent rapid switching (the fancy word for this is "hysteresis"). It seems to be normal (poor) behavior with the Asus GTX 1000 cards if your system load keeps the card around 55C. There's a good discussion here: [https://www.reddit.com/r/nvidia/comments/671i1k/warning_asus_strix_1080ti_lacking_fan_hysteresis/](https://www.reddit.com/r/nvidia/comments/671i1k/warning_asus_strix_1080ti_lacking_fan_hysteresis/)
Check under the PowerMizer Settings in your Nvidia control panel and make sure you are in Adaptive Mode. 

If all else fails, you may be able to get manual control of the fan using Coolbits (and restarting the system):
```
sudo nvidia-xconfig --cool-bits=4
```
Then you may have a fan setting in your Nvidia control panel in the Thermal Settings section.

---

