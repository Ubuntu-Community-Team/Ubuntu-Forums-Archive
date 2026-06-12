---
title: "mose pad doesn't work after istallation of 9.10 on laptop"
date: 2009-11-03
forum: Hardware
---

### Post by tryf_u on 2009-11-03
Hey all,

i have a Dell latitude d820 laptop.
after upgrading from 9,04 to 9.10 th touch pad has stopped responding.

this is my xorg.conf file:


Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection


it seems quite empty to me .... ????

what should i do?

thanks,

Uri

---

### Post by Sctmon on 2010-01-24
Did you ever get your mouse pad working? I couldn't get 9.10 to install on my laptop as it wouldn't recognize the hard drive but after installing 9.04 and upgrading to 9.10, the touch pad has stopped working.

---

