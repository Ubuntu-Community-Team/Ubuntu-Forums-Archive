---
title: "Intuos4 in Ubuntu 11.10 modprobe not working"
date: 2011-10-29
forum: Hardware
---

### Post by mike2046 on 2011-10-29
Hi,

I have a Wacom Intuos4 tablet installed on Ubuntu 11.10. I have found a website that gives a way of setting the LEDs on the buttons (see [http://braindump.kargulus.de/?p=432](http://braindump.kargulus.de/?p=432) for details). However to use this method I need to do the following

a) use rmmod to unload wacom, 

b) set the LEDs on the tablet

c) run modprobe -v wacom 

However when I do this the tablet, stylus etc are not found.  The wacom module is loaded, but it looks like I need to run something else to get it to pick up the tablet. Incidentally I get the same result if I just run rmmod and modprobe - so I know that it isn't a problem caused by the process that sets the LEDs.

Any advice would be appreciated.

Thank you.

---

### Post by boxcorner on 2011-12-03
Sorry I cannot solve your problem, but this looks like it might be helpful:

[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Main_Page]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Main_Page")

---

