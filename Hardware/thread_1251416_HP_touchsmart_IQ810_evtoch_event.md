---
title: "HP touchsmart IQ810 evtoch event"
date: 2009-08-27
forum: Hardware
---

### Post by brunom9 on 2009-08-27
Hi,

I've managed to install jaunty 9.04 amd64 on a HP Touchsmart IQ810.

Fixed the problem with the sound card following this guide [https://wiki.cse.unsw.edu.au/~jlennox/cgi-bin/moin.cgi/powmri/touchsmart](https://wiki.cse.unsw.edu.au/~jlennox/cgi-bin/moin.cgi/powmri/touchsmart)

Managed to get the touchscreen working following both of these guides, installing evtouch driver for NextWindow and configuring X.

[http://www.conan.de/touchscreen/evtouch.html](http://www.conan.de/touchscreen/evtouch.html)
[https://wiki.cse.unsw.edu.au/~jlennox/cgi-bin/moin.cgi/powmri/nextwindow](https://wiki.cse.unsw.edu.au/~jlennox/cgi-bin/moin.cgi/powmri/nextwindow)

So far, my xorg.conf is well configured and touching the screen as an alternative to mouse input works great, except for a "right click", can't seem to get it to work.

However, (and this is random) from time to time my computer will boot and there's no touchscreen working. Seems that evtouch and the NextWindow touchscreen gets assigned a different input event. Have to go thru the different inputs reported by evtouch as /dev/input/eventX till I find the right one and then change the xorg.conf accordingly.  

     Option "Device" "/dev/input/eventX"

Is there any way to assign the same HAL event to the Nextwindow touchscreen so everytime it boots it uses the same input event?

Thanx for your help

Bruno Carcamo
Otro amante del open source en MX
Another open source lover in MX

---

