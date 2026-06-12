---
title: "Laptop HP DV4000 - can't get VGA out"
date: 2005-11-11
forum: Hardware &amp; Laptops
---

### Post by guano on 2005-11-11
Hello all. I'm new to Ubuntu, but not to Linux, and I must say i I'm very impressed. As a former Slackware-Gentoo user, I first tried to install Gento on my new laptop, an HP dv 4170us (dv4000). After three day compiling stuff, the system was almost ok, but I spend about three hours in google to find how to make the 1280x800 resolution to work and so on. Then I decided for Ubuntu 5.10. Wow! The install proccess was very fast and it auto detected all my hardware! 1280x800 automatically! Wireless, everything. I'm just with a small problem with the keyboard layout, but no big deal.

My real problem is that I can't get a decent VGA out! I gave up trying to make the FnF4 hotkey to work after I found i810switch, but the output is real flickerring... then I found i855crt, which seem to be good, but I can'e get it to work!

This is how my device is in xorg.conf
(the videoboard is a Intel 915)

>Section "Device"
>	Identifier	"Intel Corporation Intel Default Card"
>	Driver		"i810"
>	Option		"SWCursor"	"1"
>	BusID		"PCI:0:2:0"
>EndSection

and this is what I get with i855crt:

#guano@Event_Horizon:~$ i855crt swcursor overlaycrt on 1024x768@85
#
#Intel 855GM CRT out driver V0.4
#Copyright (C) Merello Andrea 2004
#
#found mode 1024x768@85
#No know videocard has been found.

If I try it with sudo, same thing...

Anyone?

---

