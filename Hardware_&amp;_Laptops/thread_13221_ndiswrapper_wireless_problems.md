---
title: "ndiswrapper wireless problems"
date: 2005-01-29
forum: Hardware &amp; Laptops
---

### Post by NaughtyusMaximus on 2005-01-29
I have a compaq laptop with ubuntu hoary installed.  It has a broadcom based wireless card built in, and for the life of me, I can't figure out how to get ndiswrapper working properly.  I have had it working properly under Gentoo, so I do know that it works.

In order to install the drivers, I followed the directions in the support section, and have yet to be able to get the card's 'power' light to come on (as it usually does when the drivers are loaded).

When I do a 'modprobe ndiswrapper', I see the following line appear in my dmesg, but of course actually connecting to a network doesn't work. :(

ndiswrapper: using irq 17
wlan0: ndiswrapper ethernet device 00:90:4b:5a:df:4b using driver bcmwl5
wlan0: encryption modes supported: WEP
ndiswrapper: driver bcmwl5 (Broadcom,10/28/2003, 3.40.25.3) added


Any suggestions?

EDIT: Fixed.  For some reason downgrading to .10 and then upgrading (without uninstalling .10) to 1.0 seems to have worked.  I don't understand why, but I'm happy about it. :D

---

### Post by grj on 2005-01-29
I do not recognize the problem, but have you tried it with WEP off on the access point to help take some complexity out until you get it working. Also, what is the model of your card?

---

### Post by NaughtyusMaximus on 2005-01-29
The problem is that I can't get far enough to be able to start the networking configuration.  When the driver loads, normally the light on the network card will come on, but that is not happening.

The same thing happens when I put a Belkin F5D7010 into the PCMCIA slot - the card just never comes to life (they both take the same driver - bcmw5l.inf )

---

### Post by NaughtyusMaximus on 2005-01-29
Hrmm.. I actually seem to remember having the same problems with ndiswrapper 1.0 on Gentoo - when 0.12 still worked fine.  Is there any way I can get a debian package for ndiswrapper 0.12 ?

I've tried downloading from source, and haven't been able to get that install to work at all (even with kernel-headers installed, and kernel-source, I can't find the kernel source on the computer at all).

---

### Post by NaughtyusMaximus on 2005-01-29
If I install the 0.10 debian package (the most recent version other than 1.0 that I can find in a .deb), I get this message when I do a modprobe:

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-2-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

---

