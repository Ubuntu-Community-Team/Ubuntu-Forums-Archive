---
title: "Does xorg.conf work differently in 8.10?"
date: 2008-10-30
forum: General Help
---

### Post by wilberfan on 2008-10-30
I'm generally impressed with Intrepid so far, but I'm confused by my xorg.conf file:   There's almost nothing in it!  8-[

I'm used to a rather extensive number of entries in it, but when I opened the latest all I saw was this:

> Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

That's the *entire* file!  I was thinking of putting in my monitor's resolution numbers...but now I'm not so sure where they would go...

Is all of the info I'm used to seeing in this file now being stored somewhere else?  Where WOULD I put my HorizSync & VertRefresh numbers?  Where is all the information kept when all of the above devices were "configured"?

---

### Post by dmizer on 2008-10-30
xorg.conf has been removed from Intrepid. It currently exists only as a stub.

Here's more information about configuring your hardware in Intrepid: [https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)

---

