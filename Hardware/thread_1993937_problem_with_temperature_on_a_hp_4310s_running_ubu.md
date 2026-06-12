---
title: "problem with temperature on a hp 4310s running ubuntu 12.04"
date: 2012-06-02
forum: Hardware
---

### Post by izrafel on 2012-06-02
the laptop is a hp 4310s with : 
GPU : Radeon HD 4300 Series card (this goes up to 72-73 C)
CPU : Intel(R) Core(TM)2 Duo CPU T6670 @ 2.20GHz
Running ubuntu 12.04 32 bit with gnome shell
the problem is that the gpu goes 72-73 C on startup which i think i too high.
i have tried the proprietary drivers but the problem is that when i install it the cpu usage and temp goes up. 
Today i found out that my processor is 64 bit, the question is if i install the 64 bit will the temperature go down?
any other fix for this temperature problem?
i love ubuntu and i don't want to change the os.
P.S not sure which prefix to choose...

---

### Post by Redblade20XX on 2012-06-02
72-73 degrees isn't something to really worry about for a laptop. But if it still concerns you, check out your bios to see if there is an option for fan control (if your laptop has a fan, I assume). The 64 bit thing only deals with memory addresses that the computer uses. It shouldn't effect the temp of your laptop though.

-Red

---

### Post by izrafel on 2012-06-02
> **Redblade20XX said:**
> 72-73 degrees isn't something to really worry about for a laptop. But if it still concerns you, check out your bios to see if there is an option for fan control (if your laptop has a fan, I assume). The 64 bit thing only deals with memory addresses that the computer uses. It shouldn't effect the temp of your laptop though.

-Red

yeah i know, but i was kinda hopping for some optimization for graphics drivers, guess not. 
just found out jupiter applet, works great, now my gpu temp  is 55 :), and my processor core0 31 core1 35 :)

---

