---
title: "Ubuntu runs hotter than Windows"
date: 2012-02-02
forum: Hardware
---

### Post by teacherjeff on 2012-02-02
Dual Boot Ubuntu Oneiric and Windows 7 64-bit Home Premium on HP Pavilion laptop.  CPU temperature runs 8-10 degrees hotter under Ubuntu than under Windows while doing similar simple tasks (like browsing the web).  Typically 58C or so for Windows versus 68C or so for Ubuntu.  And the laptop is in fact perceptibly hotter under Ubuntu, and the fan runs more and faster.

Is this normal?  Is it a problem?  (The Windows CoreTemp utility gives TJ max for my processor as 115 degrees C.  So even the Ubuntu number is a long way from that.  Still, something doesn't seem right.)

Thanks for any information.

---

### Post by Gregory Lee on 2012-02-06
The AMD proprietary graphics driver for ATI cards for Linux called Catalyst, I have heard has some power saving features that let it run cooler than the free Linux driver..  Maybe that's what's going on.  I don't actually have my Pavilion yet, so please treat this as a rumor. I did run across some instructions for installing the AMD proprietary driver here: [http://mygeekopinions.blogspot.com/2011/08/how-to-install-atiamd-catalyst-117.html](http://mygeekopinions.blogspot.com/2011/08/how-to-install-atiamd-catalyst-117.html).

---

### Post by Yellow Pasque on 2012-02-07
All of those numbers seem high. Even 58C as a typical temp is high (that should be the load temp)). Has this laptop been dusted out recently? Is the heatsink attached properly?

---

### Post by Mark Phelps on 2012-02-08
Ubuntu running hotter is a known problem with kernel bugs. 

Maybe the workaround listed below will help:

[http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html]("http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html")

---

