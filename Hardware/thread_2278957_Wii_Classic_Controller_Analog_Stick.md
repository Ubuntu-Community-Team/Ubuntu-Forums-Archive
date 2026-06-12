---
title: "Wii Classic Controller Analog Stick"
date: 2015-05-20
forum: Hardware
---

### Post by jrdobelmann on 2015-05-20
I'm using "Wiican" in order to use my Wii's classic controller on my computer.  It works pretty well for the most part, but I'm having some serious issues with the analog sticks.  When I use jstest, it's able to recognize the analog sticks' behaviour just fine, but when I try to setup the controls for any game, it doesn't want to work.  Most of the time, when I try to move the stick up or to the right, it will either do nothing or register it as moving it down or to the left.  I'm using Ubuntu Studio Unity 14.04 64 bit.  Please help.
```
jstest /dev/input/js1
Driver version is 2.1.0.
Joystick (Nintendo Wiimote) has 6 axes (X, Y, Hat0X, Hat0Y, Hat1X, Hat1Y)
and 11 buttons (BtnX, BtnY, BtnTL, BtnTR, BtnTR2, BtnSelect, BtnStart, BtnMode, BtnThumbL, BtnThumbR, ?).
Testing ... (interrupt to exit)
Axes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10:off 


```

The first two axises are for my d-pad, 2 and 3 are for my left stick, and 4 and 5 are for my right stick.  Like I said, jstest is able to detect the analog sticks just fine, but none of the games I try to set up will work.  Let me know if you need anymore information.  Thanks.

---

### Post by Vladlenin5000 on 2015-05-20
Wiican hasn't been updated in more than 3 years. I wouldn't expect it to work in newer Ubuntu releases.

---

### Post by jrdobelmann on 2015-05-20
Thanks for the reply.  Do you have any other suggestions for programs I can use instead of Wiican?

---

### Post by Vladlenin5000 on 2015-05-20
No, not really. I don't use such devices. 
Please note, I didn't say it doesn't work - it may need tweaks, adaptations, dependencies but otherwise it's - just that I wouldn't expect it to...

---

