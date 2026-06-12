---
title: "Ubuntu killed my graphics card?"
date: 2010-04-20
forum: Hardware
---

### Post by UncleChicken on 2010-04-20
Hey all,

 I'm running Ubuntu 9.04 on my desktop, which is basically a custom build made up of inexpensive parts that I am slowly upgrading. My latest purchase was a Radeon 4350 512 mb Video card, which was an upgrade from the generic ATI 128 mb I had installed.

 My mobo is an Nforce6m-A 2.0 with a PC-Ie port. (4gb RAM and AMD dual core 1.8 64-bit, and a 550W PSU, if more specs matter). When I switched out the cards, everything was gravy. After I futzed around with the drivers, I had the dual monitors functioning perfectly and running apps no problem. Then, all of a sudden (I was working on my other computer at the time, and nothing was running on my desktop), the right screen (VGA port) shut off completely, and the left screen (Digital) went completely out of adjustment. After checking the cables and whatnot, I restarted the computer, and got absolutely nothing. There is absolutely no signal getting back to the monitors.

 I left it for a few hours, and put the old card back in, which worked fine.

 But this is not all - a while ago I had a GeForce 8400GS 512 mb card that sort of did the same thing, except only the digital port stopped working and the VGA worked great. At the time I thought I had been had by the ebay seller, but now I am thinking it's something to do with my hardware configuration (I know, my powers of deduction are astounding)

 So, any suggestions? Did I get a bad unit, do I have an insufficient PSU, or is my mobo killing my graphics cards? I'm pretty new to this whole computer modifying thing, so there's probably a simple (but probably not cheap) solution to this.

---

### Post by Sin@Sin-Sacrifice on 2010-04-21
[http://manpages.ubuntu.com/manpages/jaunty/man4/radeon.4.html](http://manpages.ubuntu.com/manpages/jaunty/man4/radeon.4.html)

---

### Post by Fir3chi3f on 2010-04-21
Were you also running dual monitor with the GeForce 8400GS?
To my knowledge linux has some problems with dual monitors some times, although I myself have never had an issue (infact it works better than windows but thats beside the point ;) )

Any rate, I don't think that ubuntu would do such a thing. Have you tried a live CD? I've had better luck with nvidia cards being supported. I sounds more likely to me that the configuration for the dual monitor just got messed up some how. 

can you post xorg?

```
gksudo gedit /etc/X11/xorg.conf
``` (can't believe I have that memorized)

---

### Post by UncleChicken on 2010-04-21
I will try to post my xorg.conf later, but the issue right now is that right from boot-up, I get no display. Not even the boot-up screen or BIOS options. I tried running dual screen with the 8400GS as well, and it did the weird adjustment thing as well, and when I restarted it, only the digital port worked (even in windows.)

 I guess that my title is not exactly appropriate, since it's probably a hardware issue, rather than a software one. I just can't think for the life of me what hardware issue would cause this problem on two video cards!

---

