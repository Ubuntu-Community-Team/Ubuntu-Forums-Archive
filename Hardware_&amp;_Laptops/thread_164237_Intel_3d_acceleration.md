---
title: "Intel 3d acceleration"
date: 2006-04-22
forum: Hardware &amp; Laptops
---

### Post by [Knuckles] on 2006-04-22
I'm currently looking for a new laptop, and most laptops I like (and that are in my price range and available in Portugal) use embedded Intel graphics.
I've always been a desktop guy, and I have "populated" all my computers with nvidia graphics cards to get good 3d support on linux, and I've been googling and searching everywere, and I can't find an answer that suits me.

My question is:
How good (or bad) are Intel graphics on laptops on linux? Can I run Xgl/aiglx with 24/32 bits color? Do they run well? Can I play opengl games? What problems do they generally have? Should I choose a 8xx or a 9xx? Are drivers as-easy-as or easier to install than nvidia's?

If anyone has a laptop with some intel graphics I would appreciate your input so I can get a good idea what i'm up against.

Thanks.

---

### Post by al-yazir on 2006-04-22
Hi,

[here](http://www.notebookcheck.com/Mobile_Grafikkarten_Benchmarklist.735.0.html) is a benchmark-site for mobile GPU's. It's german, but you should be able to understand it though.
I own a 7300 Go with XGL working pretty good.
But it is definitely too slow for gaming, maybe older games work. But don't expect Doom3 or something running with it.

I hope, i could help you a bit.

Al-Yazir

---

### Post by [Knuckles] on 2006-04-22
Hey!

Thanks for your answer, I'm not really that demanding (and I can tell you from personal experience that it's possible to run Doom3, Half-life 2, Halo, Unreal 2 and Ut 2004 even on a geforce 2 mx with a good overclock and some extra cooling), but as I the first thing I'm doing when I get the laptop is get windows off it (if I can't get one that's clean already), I'm looking for linux feedback / benchmarks, as unfortunately most vendors still dont give a crap about linux and for example ati X1800 under linux has little more perfornance than a X800. Also, I'm searching more for a ultra-portable, and those don't have ati or nvidia parts.

---

### Post by [Knuckles] on 2006-04-23
Ok, thanks for all the help, but I really give up on intel, the more I search the more people I see struggling with intel graphics on linux, so I decided to consider nvidia chips as must-have on my new laptop.

Anyways, here's what I found out, if someone bumps into this thread sometime in the future and is looking for the same thing I was:

Intel graphics on linux:
o Intel GMA 950: i945G, i945GM, i945Gx, 950, 955x
o Intel GMA 900: i910G, i915G, i915Gx
o Intel Extreme Graphics 2: 855GM, 855GME, 852GME
o Intel Extreme Graphics: 852GM, 845G/GE/GL/GV
o Intel Graphics Technology: 830MG
o Intel® 82810 and 82815 graphics controllers (really old?)
*GMA: Graphics Media Accelerator

Most 8xx and 9xx use the same X driver (i810) and a kernel module. For GMA 950 latest 2.6.16 or 2.6.15 with backports kernel is needed.

From what I saw, for 3d acceleration to work, you have to be running 16 bits color, composite is still pretty crappy, Xgl is slow and has problems with playing video, opengl stuff and transparency, and aiglx works a bit better, it seems, but doesn't provide all that xgl does.

Good luck!

---

