---
title: "Badger locks while detecting hardware"
date: 2007-04-19
forum: Hardware &amp; Laptops
---

### Post by prcormier on 2007-04-19
I am confused as to why breazy can detect my hardware and install, when Dapper won't.  That seems like things are going backwards.  Why would that be?
I am curious because I would like to try a lighter version of Ubuntu, but if they are based on badger, I don't think that they will install.

I was looking for a distro that would work on my Sager 9820 laptop (K6-2 400MHz processor, 256MB ram, 4GB hard drive, CDROM & Floppy) and handle my Belkin f5d7010 v5000 wlan pcmcia card.

I have tried numerous distros and about half of them lock while detecting hardware, especially around the IDE devices (even when I use ide=nodma and a few other options that I don't currently remember).

:( So far, none of the distro's that worked with my system accepted my wireless card (even using ndiswrapper).

:)      I have been able to install breazy, then, using a pcmcia ethernet card, update all of the packages and add the netcard configuration tool and, voila, everything works.  Unfortunately, the system is a bit taxed and I would like to try xubuntu or ubuntu lite, but I don't want to screw up what already works.

Any suggestions?

---

### Post by bloodniece on 2007-04-19
Damn Small Linux would be your best bet. Or Puppy Linux.

You could install ubuntu server using the alternative image and then istall blackbox window manager.

fluxbuntu works pretty well on legacy systems too.

I have xubuntu 6.06 running on a 450mhz Dell Uninspiron craptop using a cheapy PCMCIA ethernet card and ralink USB wifi dongle.   

Good luck

---

### Post by prcormier on 2007-04-19
Damn Small Linux installs, but I can't seem to get the wireless card working.
puppy and fluxbuntu lock up during hardware detection.

Oh, sorry, but I said badger, but meant Dapper (version 6.06).

I don't know about the server edition, I have never explored those possibilities.

Thanks.

---

