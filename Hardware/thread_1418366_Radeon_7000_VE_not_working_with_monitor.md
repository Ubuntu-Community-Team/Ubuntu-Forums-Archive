---
title: "Radeon 7000 VE not working with monitor"
date: 2010-02-28
forum: Hardware
---

### Post by IanVonSpeedfreak on 2010-02-28
I just installed an ATI Radeon 7000 video card on my desktop.  I can see the card when I run lspci, I can also see that the open-source radeon driver is installed. Though for some reason, when I try to start the computer with my monitor plugged into the card's VGA slot, it doesn't work. My monitor acts like it isn't plugged into anything.  Right now, I have my monitor plugged in the normal VGA slot and it works just fine, but I have no idea if the video card is being used.  So my question is, how would I get my monitor to work while plugged in the video card's VGA slot?  More importantly, how can I tell if my video card is being used or if it's just my onboard memory?  I'm using a fresh install of Xubuntu Hardy Heron btw.

Thanks in advance.

---

### Post by IanVonSpeedfreak on 2010-03-01
bump

---

### Post by IanVonSpeedfreak on 2010-03-02
This is the output of glxinfo | grep vendor:
```
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc
```
I have the right driver installed, so why is it not being detected?

If I'm not providing enough info for anyone to help me, please let me know, and I'll post whatever is needed.

---

