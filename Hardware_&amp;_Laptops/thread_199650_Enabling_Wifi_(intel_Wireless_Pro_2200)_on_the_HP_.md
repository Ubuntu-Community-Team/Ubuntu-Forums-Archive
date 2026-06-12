---
title: "Enabling Wifi (intel Wireless Pro 2200) on the HP nc6000?"
date: 2006-06-19
forum: Hardware &amp; Laptops
---

### Post by remi_2 on 2006-06-19
Hi everybody,

I can't make my Wifi work so far with Ubuntu 6.06 desktop on my 2 years old HP nc6000 (P-M 1.4 Ghz, intel Wifi chip).

Symptoms with Ubuntu : 
Wifi controller shows up active in the Network pannel, 

I edit the parameters of the Wifi card (eSSID and hexadecimal WEP key), clik the "apply" button, the gnome progress bar stays on screen for 2-3 minutes and then disapears, and Wifi does not work.

Same problem with Kubuntu, the KDE network config tool lets me enter SSID and WEP parameters, and stays stuck during the "restarting network" phase, I have to kill the window by hand and network connection does not work.


Perhaps I need to install a specific driver for the intel wifi controller, if so how do I do that !?


Thanks alot!

---

### Post by gm__ on 2006-06-19
I have the same card with Dapper on an Acer laptop.
First it seemed to work then it not, then again yes, then again no.
I saw that everybody's having problem with that card so i gave up,
and ordered a Netgear card.

---

### Post by zba78 on 2006-06-20
Try using NetworkManager.

If using Gnome you'll need to use nm-applet

If using KDE you'll need to use KNetworkManager

---

### Post by hashstat on 2006-06-20
I have a Intel Wireless Pro 2200BG working on a Dell laptop.  I downloaded and installed the latest driver from [ipw2200.sourceforge.net]("http://ipw2200.sourceforge.net/#downloads") and also the latest [firmware]("http://ipw2200.sourceforge.net/firmware.php").  I actually made the module by replacing ipw2200.h and ipw2200.c in my linux source tree with the downloaded version so that it compiles with my kernel.  Then I extracted and copied the firmware files to */lib/firmware/$(uname -r)*.  This should be enough to get wifi working with WEP.

Be sure to reload the ipw2200 module or reboot after installing the new module.

By the way, NetworkManager is a pretty slick utility 8-).

---

