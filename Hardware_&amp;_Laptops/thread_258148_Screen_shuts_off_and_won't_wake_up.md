---
title: "Screen shuts off and won't wake up"
date: 2006-09-15
forum: Hardware &amp; Laptops
---

### Post by dasteve2 on 2006-09-15
I just built a new system with specs as follows:
ASUS M2NPV-VM
AMD Athlon 64 x2 3800+
1GB RAM (i forget what kind, kingston maybe but it was on the mobo's QVL list)
250GB SATA Hard Drive

Sometimes I'll come home and the computer will be on but the screen is shut off and won't wake up from mouse or keyboard input.  I can ssh into the box from another computer and it seems to run fine, cpu is basically at idle, no processes hogging resources.  Under Power Management in System > Preferences, I have the display set to go to sleep after 10 minutes and the computer set to go to sleep never.  Are there other power management settings in ubuntu that could cause this problem?  Any ideas at all would be appreciated, for now I'm going to set the display to never sleep but I'd rather it shut off when im not here.

---

### Post by cracker on 2006-09-16
Here are a couple things I'd check. What is your video card, and which drivers do you use? Have you entered your monitor's sync fequencies into your xorg.conf file?

---

### Post by gn2 on 2006-09-17
set the screen to never go off, then when you want it off, use the switch/power button/unplug it?

---

