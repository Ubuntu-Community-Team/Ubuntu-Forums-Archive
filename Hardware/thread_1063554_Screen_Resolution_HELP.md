---
title: "Screen Resolution HELP"
date: 2009-02-08
forum: Hardware
---

### Post by Dr Belka on 2009-02-08
Yes, I am aware this has been asked 1000 times (Please dont kill me :sad:).  I have been working on this for a week, to no avail, so I thought that I should just ask for myself.  I have successfully installed and used ubuntu 8.10 alongside windows xp on my dell B130 for awhile now, and I decided to put it on my desktop computer.  It works fine except for the screen resolution is at 800x600 at 60hz.  It looks TERRIBLE!  In under the screen resolution thing in preferences, it has only four options (800x600, 640x480, 400x300 and 320x240) all of which look progressively worse.  I have tried as many things as I could off these forums to get this working, but nothing I have tried has worked so far.  

The computer is several years old.  It has an AMD Athlon 3200+2.20GHZ xp processor, 512mb RAM, and, something I am assuming to be useful to mention, a NVIDIA GeForce4 MX card with 64mb.

Thanks in advance for helping me out

---

### Post by ajmorris on 2009-02-09
> **Dr Belka said:**
> Yes, I am aware this has been asked 1000 times (Please dont kill me :sad:).  I have been working on this for a week, to no avail, so I thought that I should just ask for myself.  I have successfully installed and used ubuntu 8.10 alongside windows xp on my dell B130 for awhile now, and I decided to put it on my desktop computer.  It works fine except for the screen resolution is at 800x600 at 60hz.  It looks TERRIBLE!  In under the screen resolution thing in preferences, it has only four options (800x600, 640x480, 400x300 and 320x240) all of which look progressively worse.  I have tried as many things as I could off these forums to get this working, but nothing I have tried has worked so far.  

The computer is several years old.  It has an AMD Athlon 3200+2.20GHZ xp processor, 512mb RAM, and, something I am assuming to be useful to mention, a NVIDIA GeForce4 MX card with 64mb.

Thanks in advance for helping me out

hi there,
unfortunately this can be an issue with using HAL auto-detection. First, lets check that your accelerated graphics drivers are in use.
Paste the output of:
```
sudo glxinfo
```

After i know if your driver is in use, then we can go about rectifying your resolution issue :)

AJ

---

