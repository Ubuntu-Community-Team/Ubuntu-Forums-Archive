---
title: "Broken boot splash problem"
date: 2008-05-03
forum: Hardware
---

### Post by materthron on 2008-05-03
Hi all!
I've been trying hard for the last two hours to figure out the number for the vga parameter in order to get a usable boot splash.

It seems as if only 800x600 resolution does it as 771, 787 and 788 are the only modes in which I don't end up in a black screen. The problem is that in these modes the boot splash is shifted somewhat to the left giving a weird look.

So what shall I do now? Are there any more params I need to know about?

BTW: I'm on a Toshiba M30X with an ATI Mobility Radeon 9600 M10 (RV350) using ATI's proprietary drivers. I already disabled the BIOS' stretch pic feature, not yielding any effect on the problem.

Sources: [http://www.gelato.unsw.edu.au/lxr/source/Documentation/svga.txt?a=i386](http://www.gelato.unsw.edu.au/lxr/source/Documentation/svga.txt?a=i386)
[http://www.linuxquestions.org/questions/debian-26/lilo-vga-modes-152575/](http://www.linuxquestions.org/questions/debian-26/lilo-vga-modes-152575/)

Thanks in advance
Philipp

---

### Post by BorisDBlade on 2008-05-04
do a search for usplash in synaptic, it makes adding a boot splash easier. How did you get your 9600 to work? I've got a mobility 9700 and no drivers will install.

---

