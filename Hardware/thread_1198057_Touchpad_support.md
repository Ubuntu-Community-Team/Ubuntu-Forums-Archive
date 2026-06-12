---
title: "Touchpad support"
date: 2009-06-26
forum: Hardware
---

### Post by Samnsparky on 2009-06-26
Hello! I am working on a project that involves multi-touch gestures on Synaptics touch pads. I am aware of the information provided by synclient but I am curious to see if there is any additional information provided by the device that is not reported in that application. Specifically I am curious to see if the touchpad is aware of the location of individual fingers or even more specific readings that might be useful in gesture recognition. The information will be run through Python scripts for analysis.

I know I am taking a shot in the dark but thanks for your help in advance,
Sam

---

### Post by Rhubarb on 2009-06-26
Sounds like a great idea.

I remember using the synaptics touchpad driver in windows years ago, it could should you a little pressure map of the touchpad, which could indeed indicate multiple fingers, and the pressures of each finger.

Would be good to integrate this in to MPX (Multi-Pointer X) which I think is / has been merged into Xorg recently.

---

### Post by Samnsparky on 2009-06-26
Sounds like a great idea! Hopefully the support is there. Thanks for the quick response!

---

