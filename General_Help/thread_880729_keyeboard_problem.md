---
title: "keyeboard problem"
date: 2008-08-05
forum: General Help
---

### Post by PIPI on 2008-08-05
I installed latest ubuntu and everything looked just fine. Now when I log in it seams my keyboard doesn't work. At the beginning works now and then but later it doesn't work at all. I have PS2 and usb keyboard and none of them work. I tried just with one and every time the same thing happens. I login and after that everything goes to hell. Please help.

---

### Post by cmnorton on 2008-08-05
Check where the keyboard and mouse plug into your computer. If you have to, force the system down with the power off button, or do so if the mouse works. Then see if it comes back. This sounds like loose keyboard/mouse cables or a hardware problem. 

Another thing to try is to boot into recovery mode, and enter dpkg-reconfigure xserver-xorg. Change no settings other than to let the keyboard and mouse be re-detected. That is take defaults for everything. Then type exit, and see if your keyboard and mouse work. If you boot into recovery mode and the keyboard does not work; your mouse and keyboard are plugged in; you have tried another mouse and keyboard; and finally you have tried to boot with a live cd and your keyboard still does not work, then I would say something is wrong with your hardware.

---

### Post by PIPI on 2008-08-06
i fixed it. when I was installing ubuntu two keyboard were pluged. I think that was a problem. I installed ubuntu again with just one pluged and everything works fine. thx anyway

---

