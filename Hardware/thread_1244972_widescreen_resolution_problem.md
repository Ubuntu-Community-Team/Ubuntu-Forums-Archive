---
title: "widescreen resolution problem"
date: 2009-08-20
forum: Hardware
---

### Post by faust99 on 2009-08-20
Can somebody please assist? I have Ubuntu 8.10 installed. On original installation the widescreen resolution for my Dell Inspiron 710m was right, without having to make any modifications to the Xorg file. 

Today I connected an external monitor which resulted in some kind of problem with my screen (i.e. the monitor stopped working entirely). I therefore booted up in recovery mode and attempted to fix the Xserver. It worked to the extent that the screen now works, but the resolution is wrong, and I've not been able to set it up properly. 

Considering that upon initial installation the hardware was detected properly, is there any way to reset?

---

### Post by faust99 on 2009-08-20
Resetting via rm ~/.config/monitors.xml and rebooting has seemingly fixed the problem.

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

