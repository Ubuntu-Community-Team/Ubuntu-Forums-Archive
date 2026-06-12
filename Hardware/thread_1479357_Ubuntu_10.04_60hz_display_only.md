---
title: "Ubuntu 10.04 60hz display only"
date: 2010-05-10
forum: Hardware
---

### Post by Thomasasz on 2010-05-10
Hello, 
I am newby to Linux. By far I adore this OS, however, my eyes are hurt by 60hz display refresh rate :( I cannot choose any other rates. I did some research on Google and I found out that I need to configure something in xorg.conf but I do not know what. Can someone tell me what to do? :)

These are the contents of the xorg.conf:
> 
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"fglrx"
EndSection


My graphics card is ATI Radeon Mobility 3400HD. 

Thank you for your help!

---

### Post by Thomasasz on 2010-05-11
Anyone? :D

---

### Post by Mike BFD on 2010-05-11
It seems to me, the "fglrx" driver is that used for failsafe mode. So it's no surprise it supports only "minimal", "basic" functionality.

Here in the Forums I saw many threads about ATI driver problems (mostly solved problems), try this:
[http://ubuntuforums.org/search.php?searchid=72887534](http://ubuntuforums.org/search.php?searchid=72887534)

---

