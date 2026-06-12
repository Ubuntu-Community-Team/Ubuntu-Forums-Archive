---
title: "NVIDIA Quadro 880: Slow performance and CPU leaks"
date: 2014-04-20
forum: Hardware
---

### Post by dcrooke on 2014-04-20
[ I'm aware of [http://ubuntuforums.org/showthread.php?t=2182627](http://ubuntuforums.org/showthread.php?t=2182627) but it didn't seem like a good place for this ] 

My laptop (Lenovo ThinkPad W510) has the following video card as reported by lspci: 01:00.0 VGA compatible controller: NVIDIA Corporation GT216GLM [Quadro FX 880M] (rev a2)

I got the machine about 3 years ago, and installed Ubuntu 11.04 desktop amd64 ... the video performance has always been below par, an order of magnitude slower than Windows driver at best, and nowhere close to the speed of other NVIDIA cards with the proprietary Linux driver, but about a year ago it went into the toilet. Everything that uses X11 video seems to leak extraordinary amounts of **user space** CPU. As I type this, Firefox is literally unable to keep up, and is redlining a whole CPU, which it does more or less continuously. Any page which uses AJAX will slow it down to the point where the X server greys out its window. compiz is using 1.3GB of RAM, surely that's a leak too?

Command line stuff that uses a lot of CPU runs fine, and both memory bandwidth (16+ GB/sec per memtest86) and CPU speed seem to be normal (I have aftermarket RAM which is faster than the factory stuff)

[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 3191.84 BogoMIPS (lpj=6383692)
[    0.332806] smpboot: Total of 4 processors activated (12767.38 BogoMIPS)

I had been running 12.10 LTS for a while, and recently went up to 13.10 to see if it would improve ... it did a little, but it's still slower than it was in 2011 and perhaps 96% slower than Windows (factor of 25). This is the 304 driver, I'm going to try the new 319 one and report back in this thread.

- what's the best way to report this as a bug to NVIDA - via Canonical?
- is there any diagnostics I can grab that will help, and if so what should I use - truss? gdb?
- is the easiest solution to simply buy another video card from a different manufacturer?

---

### Post by dcrooke on 2014-04-20
Confirmed that 319 still has the problem. Words With Friends on Facebook on Firefox still absolutely kills it. I should also mention that it seems to start at a livable speed on a fresh login and get slowly worse.

---

### Post by mörgæs on 2014-04-20
How does it work in a fresh install of X/Lubuntu 14.04?

---

### Post by johan18 on 2014-08-04
I have a w510 with a dual boot of 14.04 and Win 7. I had major crashing problems with the Nouveau driver. the screen would freeze and then time out to the log in screen that looked like like a purple mess. Even Ctrl+Alt+Del didn't work. I had to do a hard restart. After that happend countless times and I sent a report every time. I got sick of it and installed the NVIDIA vr. 331.38 and it works pretty well. A few hiccups with Firefox load times and the like, also I havent really tested it with some rendering or heavy game play but It does an okay job with Chromium and open GL/Web GL like skycraft .io. Well I hope that helps and that you have a better experience cause the W510 is pretty GREAT.

---

