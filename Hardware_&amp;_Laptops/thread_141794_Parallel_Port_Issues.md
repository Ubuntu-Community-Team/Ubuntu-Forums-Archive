---
title: "Parallel Port Issues"
date: 2006-03-09
forum: Hardware &amp; Laptops
---

### Post by exp(x) on 2006-03-09
I aquired a free Billy Bass (those stupid singing fish), so I decided to follow the instructions [here](http://bigmouth.here-n-there.com/) for connecting it to a computer and using linux to control it. I'm pretty sure I got all the wiring correct, and the software compiled after some minor changes, but I think the problem is the program isn't able to access the parallel port. Whenever I plug in the fish, its head turns and stays there. I decided to test the pins that it uses and discovered that pin 4 has a constant 5 volts going through it. The only way to turn off pin 4 is to remove the parport_pc module (and anything that depends on it). Even after I do this, the software doesn't do anything with the parallel port. Pin 2 should be going on and off while the program is running, but it doesn't. Any suggestions?

If anyone wants to try compiling the program, I uploaded fixed versions of the source and the qpthread prerequisite here:
[bmbb-linux.tar.gz](http://brandon.conglacia.com/files/bmbb-linux.tar.gz)
[qpthread-1.3.0.tar.gz](http://brandon.conglacia.com/files/qpthread-1.3.0.tar.gz)
You'll also need [OSALP](http://osalp.sourceforge.net/), which compiles fine.

Update: I got everything working fine on my desktop. It runs 64-bit Breezy instead of 32-bit like my laptop, but I compiled the program in my 32-bit chroot. I still can't figure out why it won't work with my laptop.

---

### Post by exp(x) on 2006-03-10
I figured out what the problem was; my Thinkpad uses 0x3bc instead of 0x378 for the parallel port. Changing this in bmbbcontrol.h fixed it.

---

