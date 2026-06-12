---
title: "Trident Cyberblade 3d and Xorg bug?"
date: 2006-10-12
forum: Hardware &amp; Laptops
---

### Post by cius on 2006-10-12
I have a Toshiba te2000 laptop computer running Dapper with all the latest updates.  The laptop has a Trident Cyberblade Ai1 graphics chipset.  I'm using the "trident" driver for xorg (ubuntu used it by default).

This chipset is supposed to have rudimentary 3d capabilities, and I know that it does because of one of the symptoms of my problem.  When I start glxgears, the window pops up and it runs just fine for a few seconds, the gears are turning away at what appears to be a fairly decent framerate.  Then, they stop dead and only chug along at about .15 frames per second or something after that.  Naturally, I thought this behavior odd (it works, then suddenly it doesn't) and rightly assumed that my resources were being suddenly taxed by something that would slow it down.  I opened a terminal, checked top, and low and behold, Xorg is taking 96% of my CPU time, leaving other processes to fight for the remaining 5%, including glxgears.

So, the 3d acceleration obviously works, because I get that brief moment of nicely turning gears, but then suddenly Xorg becomes a CPU hog and slow everything down.  I assume this is a bug somewhere (xorg or driver, I dunno).  Anyone know anything about this?

---

### Post by tical2756 on 2007-04-17
I'm having the same problem.  Anyone??

---

### Post by jepong on 2008-03-25
I believe my ThinkPad R30 has the same problem as well.

---

### Post by gmasters on 2008-03-27
This seems to be a problm with the Cyberblade that I have noted from 7.04 through 7.10. My Cyberblade-based laptop's CD-ROM drive died so I am not able to test it with 8.04 beta. Has anyone tried it with the beta as I had reported a similar bug with the Cyberblade over a year ago? The developers did trace it to the xorg server.

---

### Post by jepong on 2008-03-27
Has anyone on this thread tried openSuSe 11 Alpha 3 (Gnome)? 

I tried it last weekend and it was able to detect my ThinkPad R30 and I believe the other hardware Ubuntu haven't supported to date. 

For the record, I'm still using Ubuntu and hoping not to change distro forever. :guitar:

---

### Post by rockachu2 on 2008-07-06
My laptop is also having a problem with it. The solution I found was to go to knoppix.com and download a live cd of the latest version. Then I copied the xorg.conf file from the ramdisk and saved it. The xorg.conf file is the same on some linux systems, so it works to increase resolution and fix bugs.

---

