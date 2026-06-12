---
title: "How to obtain mouse driver source"
date: 2012-09-14
forum: Hardware
---

### Post by Beacon11 on 2012-09-14
Hello all. I have a Dell XPS 13, but this isn't necessarily a computer-specific question.

First, a little background: I'm an experienced C/C++ developer, but my experience is limited to bare-metal or application-level. I don't really have experience delving into Linux modules or device drivers.

The driver for my XPS 13's Cypress touchpad was just recently released (see this blog post: [http://bartongeorge.net/2012/06/20/sputnik-update-touchpad-driver-now-available/](http://bartongeorge.net/2012/06/20/sputnik-update-touchpad-driver-now-available/)). The PPA for it is here: [https://launchpad.net/~canonical-hwe-team/+archive/sputnik-kernel](https://launchpad.net/~canonical-hwe-team/+archive/sputnik-kernel) . It's still in beta, and it needs some love. I'd like to take a crack at the issues I have with it, but I don't really know what I need to obtain. 

Where do I get the source code for a touchpad driver? I was sort of hoping it would be a .deb for which I could grab the source, but it doesn't look like it's that easy. If it's a module distributed with the kernel, do I need to get the source for the whole kernel and the source for the driver comes with it?

Thanks for your help!

---

### Post by Beacon11 on 2012-09-16
I've made some progress on this: The driver source code is indeed included with the kernel. Now I just need to figure out how to build it and test it without messing up my install.

---

