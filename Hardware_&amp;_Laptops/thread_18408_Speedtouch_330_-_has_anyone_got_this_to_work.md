---
title: "Speedtouch 330 - has anyone got this to work?"
date: 2005-03-06
forum: Hardware &amp; Laptops
---

### Post by Arrondor on 2005-03-06
I am aware there has been several posts on this subject - including one from me - but I have yet to find or hear of a solution that actually gets the Speedtouch 330 USB modem working with Ubuntu (or most distros of Linux for that matter)

Is there anyone out there who could post a clear guide to installing this modem before I abandon Ubuntu and Linux forever.

---

### Post by poofyhairguy on 2005-03-06
[QUOTE=Arrondor]I am aware there has been several posts on this subject - including one from me - but I have yet to find or hear of a solution that actually gets the Speedtouch 330 USB modem working with Ubuntu (or most distros of Linux for that matter)

Is there anyone out there who could post a clear guide to installing this modem before I abandon Ubuntu and Linux forever.[/QUOTE]


Aww....don't abandon linux forever. Lets just see what Google says. When I searched for "Speedtouch 330 USB linux" I got a howto:

[http://www.xs4all.nl/~pschram/english.html](http://www.xs4all.nl/~pschram/english.html)

A script for Debian:

[http://christophe.delord.free.fr/en/adsl/debian.html](http://christophe.delord.free.fr/en/adsl/debian.html)

Advice to get it to work in MEPIS (very close to Ubuntu, should work):

[http://www.mepis.org/node/view/4893](http://www.mepis.org/node/view/4893)


I will admit that looking at the links shows me that IT IS POSSIBLE, but it is not really easy. Thats just the breaks for some hardware and Linux. You can get it to work though. Me, well... I'm a lazy ass. If a piece of hardware doesn't work in Linux, I buy a new one. Tell myself "well, thats how much I would have spend upgrading my virus scanner on XP this year!"

But it seems to be quite possible for you to work with what you have. In fact, looking at the last link it seems easier to do than to get the ATI drivers to work (the most work I ever did to not just replace a piece of hardware.)

Good luck.

---

### Post by MrFunster on 2005-03-06
[QUOTE=Arrondor]I am aware there has been several posts on this subject - including one from me - but I have yet to find or hear of a solution that actually gets the Speedtouch 330 USB modem working with Ubuntu (or most distros of Linux for that matter)

Is there anyone out there who could post a clear guide to installing this modem before I abandon Ubuntu and Linux forever.[/QUOTE]


I am postin this using warty and a speedtouch 330 V2 (the burgundy model)
I used the kernel drivers and it worked a charm.
I think I posted a link to it in the previous thread of yours, but if not go to :

[http://linux-usb.sourceforge.net/SpeedTouch/](http://linux-usb.sourceforge.net/SpeedTouch/)

navigate to ubuntu

and follow these instructions. 
The connection should be established at boot, just before the logon screen, so you will need to rebootafter installing the drivers.

If you can't get it going repost with the error messages generated and I'll let you know if I've come accross the problem when I installed.

You should find out your modem version using:
cat /proc/bus/usb/devices | grep -B 1 ALCATEL
which returns Rev = X.00 in the 1st line, where X is the version
Mine is V2 so I used the KQD6_3.012 as my mgmt.o

---

