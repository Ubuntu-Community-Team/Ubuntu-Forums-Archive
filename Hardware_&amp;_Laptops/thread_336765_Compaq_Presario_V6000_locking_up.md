---
title: "Compaq Presario V6000 locking up"
date: 2007-01-12
forum: Hardware &amp; Laptops
---

### Post by crthomas on 2007-01-12
I bought a compaq laptop recently, and it is locking up.  First it was after about two days of uptime, then a day, now its anywhere between 2 and 24 hours.  I am running 64bit version.  The problem is that I can't tell if its a hardware or software problem.  I have never used the 64bit version, so I don't know how stable it should be.  The other issue is that I got it open-box.  It is still under warranty, but that is the reason I think it might be hardware.

I don't know if this helps diagnose the problem, but I happened to be watching a video during one crash, and the sound kept repeating the same one second.

When it happens, nothing works.  I can't control-alt-backspace, control-alt-f1, f2, etc.  The mouse doesn't move at all.  The only thing I can do is cold reboot.

---

### Post by greg.hagen on 2007-01-12
I had a similar problem with a Thinkpad x24. It turned out to be a video driver problem, and reducing my default color depth in xorg.conf from 24 to 16 stopped the random crashing.

---

### Post by crthomas on 2007-01-19
No luck.  I have the official nvidia drivers installed, and I changed the bit depth to 16, and it is still locking up.

---

