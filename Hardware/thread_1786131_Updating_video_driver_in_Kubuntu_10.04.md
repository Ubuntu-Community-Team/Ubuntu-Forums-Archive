---
title: "Updating video driver in Kubuntu 10.04"
date: 2011-06-19
forum: Hardware
---

### Post by hikinthru on 2011-06-19
I have an Intel 945GM Graphics Controller on a Dell D620. I'm trying to install the proprietary drivers, I want to play WoW and the video is too choppy to play.

I've downloaded the drivers, but don't know what to do next. I've read all of the documentation (README, INSTALL, etc) that came with the driver download. I've downloaded xf86-video-intel-2.15.0.tar.bz2 with the drivers for my card, but don't know what to next. 

These are the files:
aclocal.m4  compile       config.sub    depcomp     m4           missing  uxa
AUTHORS     config.guess  configure     INSTALL     Makefile.am  NEWS
build-aux   config.h.in   configure.ac  install-sh  Makefile.in  README
ChangeLog   config.log    COPYING       ltmain.sh   man          src
 
How do I upgrade the card drivers?

Any advice is gratefully appreciated.

Sherrie

---

### Post by foresthill on 2011-06-19
Where did you get the drivers? I would be interested in trying them too.

There should be instructions on the site where you downloaded them. Are these drivers from the official Intel site or somewhere else?

---

### Post by hikinthru on 2011-06-19
I got the drivers for Linux from here:
[http://intellinuxgraphics.org/2011Q1.html](http://intellinuxgraphics.org/2011Q1.html)

I read the instructions, essentially all of the text files included with the drivers, but those that include how to install the drivers simply say to "follow the instructions" with the driver. It's a bit circular.

Best,
Sherrie

---

### Post by foresthill on 2011-06-19
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

> Adding this PPA to your system

You can update your system with unsupported packages from this untrusted PPA by adding ppa:xorg-edgers/ppa to your system's Software Sources. 

I did see this. ^^^

Apparently you have to add their site to your software sources, and then I imagine that the files will show up in Synaptic or whatever software update program Kubuntu uses.

As far as your original question, it looks like you will need to build the driver yourself, which is something I have tried doing a few times, but never had much luck with. 

I myself am gonna pass on this and wait for a stable version to show up in the regular software updates. I have been burned too many times with beta pre-release drivers, kernels, etc.

---

