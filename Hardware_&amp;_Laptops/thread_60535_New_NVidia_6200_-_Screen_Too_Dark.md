---
title: "New NVidia 6200 - Screen Too Dark"
date: 2005-08-28
forum: Hardware &amp; Laptops
---

### Post by watchitman on 2005-08-28
I've got a wierd problem. I just installed a brand new Gigabyte NVidia GeForce 6200 (AGP). When the driver loads, the screen is so dark, it's nearly impossible to see anything. I reinstalled the official driver and it didn't make any difference, it looks exactly the same. Btw, I dual boot and everything works fine under Windows so it's not the monitor. Anyone have this problem and/or a solution?

---

### Post by watchitman on 2005-08-28
*bump*

---

### Post by Parkotron on 2005-08-29
The problem *could* be a really dark gamma setting.

I know that the system tray interface of the nVidia driver for Windows allows you to adjust the gamma levels of the video card output. Maybe there's a similiar setting of Linux? The last time I recompiled the nVidia kernel module, I remember finding a whole slew of configurable options hidden away in the documentation that came with the source.

I'm sorry I couldn't be of more help. Really the gamma setting is just a shot in the dark.

---

### Post by mctavish on 2005-08-29
You are not alone. There is alot of information on the nvidia linux forums.

In a nutshell, the problem is that hoary's nvidia drivers are too old to support this card.

The solution is to download nvidia's installer and install it yourself. Pretty sure I am using version 7664, and it works fine.

---

### Post by dysprosium on 2005-09-05
The 7667 definitely is the driver to go with over the newer one.  I have an NVID 6200, and started off with the 7676, and had major problems.  I installed the 7667 and that driver works so far.  This was, of course, after struggling with the NVIDIA drivers from ubuntu... don't even bother...save yourself the headache.

---

