---
title: "Question about Software Fan Speed Controllers"
date: 2014-02-13
forum: Hardware
---

### Post by NickKourpias on 2014-02-13
I'm about to install Ubuntu again as a side OS on my computer, and my computer's fans are very loud. To counter this on Windows I use a program called SpeedFan which a fan speed controller in software. However the last time I was on Linux I could not find a program that was like this (having a nice GUI and all). 

So, my question is: do any of you know of a nice, highly preferably easy to use, software fan speed controller for Linux?

Your help is much appreciated. And thanks in advance.

---

### Post by Yellow Pasque on 2014-02-13
The pwmconfig and fancontrol scripts (part of lm-sensors package) are fairly easy to use, so I don't think anyone ever bothered to make a GUI.

---

### Post by tgalati4 on 2014-02-14
*thinkfan* has a gui.  I don't know if it requires the ibm_acpi to function, but you can try to load it and see.  It works well and is quite customizable.  Nothing will fix bad engineering.  If the fans are loud because the heat sink is too small, then turning them down will just cause the CPU to heat up to the point of thermal shutdown.

---

