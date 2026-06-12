---
title: "Keyboard and Mouse problems"
date: 2009-08-02
forum: Installation &amp; Upgrades
---

### Post by smaller on 2009-08-02
I just did a fresh install of Jaunty 64 bit on my PC and ran into trouble with my mouse and keyboard, they don't seem to be responsive at all in:

1) The installer
2) The login screen (normal boot)
3) The options menu (recovery boot)

They only seem to work:

1) If I boot the live cd (This also how I managed to install it)
2) On the boot loader screen

Any tips on where to start looking? All I could find are posts indicating to look in the X logs, but if that were the case surely i'd be able to boot in recovery mode?

Completely lost, all help appreciated

---

### Post by smaller on 2009-08-03
Ok, after some googling I found this:
[http://www.linux-usb.org/USB-guide/x194.html](http://www.linux-usb.org/USB-guide/x194.html)

Does anyone know if this applies to the latest Ubuntu version? And if so how do I do the kernel configuration things they are describing?

---

### Post by Sef on 2009-08-03
What are your system specs, including your keyboard and mouse?

---

### Post by smaller on 2009-08-03
> **Sef said:**
> What are your system specs, including your keyboard and mouse?

It's a dual processor machine (2 x AMD Opteron 64 bit) with 2 GB RAM and an NVIDIA Quadro NVS280. If you need more specs they are listed here: [W2100z]("http://www.sun.com/desktop/workstation/w2100z/specs.jsp")

As for the mouse/keyboard, it's a logitec Cordless Desktop Optical. But I also tried it by plugging in the wired mouse/keyboard (both USB) that came with the PC and they didn't work either.

---

### Post by smaller on 2009-08-19
This a shameless bump as it's now 2 weeks on and I'm still completely stuck on this problem. :confused:

---

### Post by Cheesemill on 2009-08-19
You need to go into your BIOS and enable 'USB Legacy Mode'
It might be named differently on your BIOS but you should be able to find it.

---

