---
title: "Multiple monitors with compositing"
date: 2010-05-27
forum: Hardware
---

### Post by exoren22 on 2010-05-27
OK, I am running Xubuntu Lucid on a Dell Latitude D630 with an Nvidia Quadro NVS 135M. I wanted multiple monitor support so I installed the restricted Nvidia drivers and went into the Nvidia X Server Settings application. 

I first tried twinview, but since the laptop moonitor is 1440x900 and the external monitor is 1280x1024 there was vertical space that was unused by the monitors, but the mouse could travel down there all it wanted. 

Then I did Xinerama, which did exactly what I wanted, but does not support compositing, which just plain sucks. I love the xfwm compositor, so Xinerama just doesn't cut it. 

I finally tried using them as separate X screens without Xinerama, but the non primary screen has an unchangable desktop picture and I cannot figure out how to get windows to go to the other screen.

So I really just want to know if there is a way to get it to behave like xinerama but with compositing. Thanks in advance.

---

