---
title: "Asus F5SL: eth0 frame errors, web sites unavailable; driver problem?"
date: 2008-09-24
forum: Hardware
---

### Post by pusisaul on 2008-09-24
Hello,

I have been trying to configure interpid (first alpha 5 from September 5, then alpha6 from September 18) so that the wired connection works properly. No luck.

Windows Vista on same notebook have no problems with the frame errors whatsoever, neither problems with accessing web sites.

An old PC (Compaq ENS/P800/10E/6/128CV) had alpha6 installed, connected to same router - no problems with frame errors, worked fine. 

First started with disabling of IPv6 - no success.
Then tried reducing the w_mem and r_mem for tcp - no success.

Sites such as [www.google.com](www.google.com) open, while [www.ubuntu.org](www.ubuntu.org) time out (error: connection timed out while negotiating).

---

### Post by pusisaul on 2008-09-27
The problem solution has been proposed a while ago:

How To Create The Sis191 Gigabit Ethernet Driver On Linux 2.6
[http://www.howtoforge.com/creating-the-sis191-gigabit-ethernet-driver-on-linux-2.6](http://www.howtoforge.com/creating-the-sis191-gigabit-ethernet-driver-on-linux-2.6)

However, the drivers file /drivers/net/sis190.c has been changed since and seems to incorporate some changes. 

The problem with some web sites inaccessible persists though.

---

### Post by stratofarmer on 2009-02-23
Hi I'm using Intrepid Ibex and I ran into this issue with my Asus laptop having a SiS191 Gigabit Ethernet card.
I installed the kernel from Jaunty which solved the issue for me. Kernel version 2.6.28-8 to be precise. It needs a few dependencies (eg: wireless-crda).

I downloaded these on a different pc to get a working connection:
[http://launchpadlibrarian.net/22746997/linux-image-generic_2.6.28.8.8_i386.deb](http://launchpadlibrarian.net/22746997/linux-image-generic_2.6.28.8.8_i386.deb)
[http://launchpadlibrarian.net/22555021/wireless-crda_1.5_i386.deb](http://launchpadlibrarian.net/22555021/wireless-crda_1.5_i386.deb)

Even then there's still a bug in the sis190 driver itself, it needs a workaround to work properly by setting the MTU to 1024. Don't know exactly why but it works for me.
Something like: sudo ifconfig eth0 mtu 1024 up

I hope this helps someone.

P.S. Incidently, the new kernel also fixed my Atheros wireless card connection.

You can get all necessary packages here:
[http://packages.ubuntu.com/jaunty/linux-image-2.6.28-8-generic](http://packages.ubuntu.com/jaunty/linux-image-2.6.28-8-generic)

The MTU workaround can be set automatically upon connection by NetworkManager by adding a script to /etc/network/if-up/

---

