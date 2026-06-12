---
title: "White line on right edge of the sceen"
date: 2017-05-29
forum: Hardware
---

### Post by bl4ckbl00d on 2017-05-29
I just installed Ubuntu 17.04 Desktop and there's a white line of 1 pixel width all across the right edge of the screen every time there's an unmaximized window focused. If I maximize the window or click outside of it (window loses focus) the line disappears.
[ATTACH=CONFIG]275347[/ATTACH]

---

### Post by kc1di on 2017-05-29
Hello bl4ckbl00d and Welcome to Ubuntu,

It would be helpful to know what your video card is and which driver your using?

---

### Post by bl4ckbl00d on 2017-05-29
Hi thanks for replying, I'm running Ubuntu on an Acer V5 laptop, CPU Intel Celeron 847, Graphics Card Integrated Intel HD, drivers are the proprietary default ones.

---

### Post by kc1di on 2017-05-30
Please go to a terminal and type this command and post the output here.```
inxi -G
```
If it does not report anything or if it says inxi is not installed install it ```
sudo apt-get install inxi
``` Then run the command again.

---

### Post by bl4ckbl00d on 2017-05-30
Graphics:  Card: Intel 2nd Generation Core Processor Family Integrated Graphics Controller
           Display Server: X.Org 1.19.3 drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1366x768@60.07hz
           GLX Renderer: Mesa DRI Intel Sandybridge Mobile GLX Version: 3.0 Mesa 17.0.3

---

### Post by bl4ckbl00d on 2017-05-30
The problem could be related to this [https://github.com/linuxmint/Cinnamon/issues/5228](https://github.com/linuxmint/Cinnamon/issues/5228) since I'm also using cinnamon, I will try the proposed fix and report back.

---

### Post by bl4ckbl00d on 2017-05-30
Didn't work, also I went back to 16.04 and the problem persists

---

### Post by bl4ckbl00d on 2017-05-30
Fixed it somehow, I changed the controls theme from Ambiance to any other option (Numix daily) and the line disappeared for good.

---

