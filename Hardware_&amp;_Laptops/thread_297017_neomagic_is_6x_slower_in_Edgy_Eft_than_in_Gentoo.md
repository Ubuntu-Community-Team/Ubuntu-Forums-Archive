---
title: "neomagic is 6x slower in Edgy Eft than in Gentoo"
date: 2006-11-10
forum: Hardware &amp; Laptops
---

### Post by damiencc on 2006-11-10
Hello,

I would love to switch to Edgy Eft from Gentoo, but the graphical performance is not acceptable on my Thinkpad 600E. Under Gentoo, I enjoy good graphical performance (full window moving is fine). On the other hand, Edgy Eft (xubuntu) is _very_ slow. Here is the beginning of the benchmarks:

$ x11perfcomp x11perf-gentoo.txt x11perf-ubuntu.txt

1: x11perf-gentoo.txt
2: x11perf-ubuntu.txt

     1         2    Operation
--------  --------  ---------
5470000.0  4650000.0  Dot
892000.0  1520000.0  1x1 rectangle
385000.0  219000.0  10x10 rectangle
 29000.0    5710.0  100x100 rectangle
  1830.0     331.0  500x500 rectangle

16 bit modes in both cases.

I have even recompiled xserver-xorg-core and xserver-xorg-video-neomagic for pentiumIII (there is one in my laptop) and without the -g flag, but with great difference.

Could anyone shed light on this matter?

Thanks

Damien

---

### Post by TuxCrafter on 2007-03-09
I don't have a clue if it works but maybe there is a framebuffer loaded on ubuntu thats slows things down? You can check it with lsmod as a gentoo user you probably know the rest :-D

---

### Post by drratchet on 2007-03-10
Edgy sets up xorg at 24 bits, which is un-accelerated and very slow with the Neomagic driver... Set DefaultDepth to 16 in the "screen" section of /etc/X11/xorg.conf file, and restart X and all should be fine (at least, it was for me when I had the same problem!)

---

