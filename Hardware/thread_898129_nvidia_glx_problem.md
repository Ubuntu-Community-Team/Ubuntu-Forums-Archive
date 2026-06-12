---
title: "nvidia glx problem"
date: 2008-08-22
forum: Hardware
---

### Post by shamgar03 on 2008-08-22
For some reason when I start X with glx enable X completely freezes after a few seconds and if I ssh in at that point (the keyboard stops working so I cant move using CTRL-ALT-F1) the CPU usage is at 99% for xorg. I have looked all over for a solution, I have added "UseEvents" and that didn't work. I have used the envy nvidia driver and that does it. I can't figure this out. I am using Ubuntu 8.04 and have apt-get update and apt-get dist-upgrade so it isn't an 
old version problem....

my video card is old but not ancient, FX-5200 which is supposedly supported in the nvidia-glx-new package. Anyone have an idea on this, its really killing me.

---

