---
title: "Strange Freeze on Vaio Laptop"
date: 2006-11-15
forum: Hardware &amp; Laptops
---

### Post by cayamara on 2006-11-15
Hello!

I've been experiencing strange freezes on my Vaio Laptop recently. These occur completely random (at least from what I can see). The screen just freezes and doesn't respond to either mouse nor keyboard input, so that I have to power down the laptop to reboot.

I am running edgy with the latest X, Gnome and Beryl (version 0.1.3 svn) with the NVIDIA beta 9742. My kernel is 2.6.17-10-generic #2 SMP. I have a celeron duo T2300 (2 x 1.66 GHz) processor and a GeForce Go 7400 graphics card.

This is the /var/log/kern.log passage related to the crash:
```
Nov 15 20:23:58 henning-laptop kernel: [17180406.600000] NVRM: Xid (0001:00): 6, PE0000 0480 00ffffff 0000fabc 00000000 00ffffff
Nov 15 20:23:58 henning-laptop kernel: [17180406.616000] NVRM: Xid (0001:00): 30,  L1 -> L0

```

I have been looking through other log files, but found nothing else related to that. Maybe some one of you can point me to the right direction to where the problem may be. And maybe I'm just running too much beta software (oh, beryl is fun!).

Thanks in advance!

---

### Post by eznet on 2008-06-18
Its always funny (not 'funny - ha, ha', but the other funny) when you find a two year old post that is talking about the exact same error that you are looking for info on in a later release - Hardy in my case.  Same freezing, same log error, different notebook (HP DV6000t)

---

### Post by eznet on 2008-06-24
Installing xserver-xgl has stopped my freezing and black flashing, though my processor does seem to be under a heavier load now...  It is nice to have the black flickering and locking up gone - for now at least..

---

### Post by eznet on 2008-06-25
Ok, so heres an update - uninstalled xserver-xgl.  The processor consumption did increase, no if ands or buts about it.  Although my system no longer randomly 'froze', it did become so bogged down when attempting to perform processor intensive tasks and using any of the 'big' compiz effects - such as rotating the cube.  Next, some gxl applications seeming slowed down significantly and xgl screensavers would not work at all.  
Furthermore, something with the xserver-xgl prevented my screen from going to sleep, so not only could screen savers not come on, but the LCD would stay 'on' at all times - it would go black, but the backlight remained on.  Often, while the screen was black (when it was supposed to be in power saving mode) the processor would be doing some heavy activity (I assume as the fans were going full speed).  So, despite the flickering and random lock ups, I feel this (no xserver-xgl) to be the better of the two alternatives.  I wish I knew what the problem's root was because the flickering is definitely back :( .
Also, the [gnome System Monitor memory issue]("http://ubuntuforums.org/showthread.php?t=769757") seemed to be tied to the xserver-xgl as now my memory readings are correct.  Odd.

---

### Post by lexus on 2008-06-26
Friend sees the date of publication
**November 15th, 2006 **

---

