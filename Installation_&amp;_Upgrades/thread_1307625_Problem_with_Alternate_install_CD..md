---
title: "Problem with Alternate install CD."
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by zebala on 2009-10-31
Hey guys!

I'm trying to install Ubuntu 9.10 on HP laptop with an Alternate install CD to get a much more leaner install of Ubuntu. I wan't to be able to choose which packages to install and so on. For some weird reason, though, after I either try to check the disk integrity or install, the screen says something like "Starting system log daemon" and flickers and turns off. Nothing happens after that. The screen just stays off and pressing anything doesn't help.

I'm trying to install only a command line install but even the normal didn't help. Tried a few different boot parameters, too, but to no avail. I used Virtualbox to try this out before and everything went fine then.

Is it possible to do a minimal install with the normal cd by writing 'custom' or 'server' in the boot parameter? Or any other way?

Oh yeah and I tried like two different CD:s plus a USB stick so I don't think that's the problem. Help appreciated! I would like to get back to buntu soon! Thanks!

EDIT: Did some digging and found out it could be that the monitor frequency is out of range..

---

### Post by zebala on 2009-10-31
Writing vga=771 as a boot parameter solved everything. Sorry for a quite useless thread...

---

