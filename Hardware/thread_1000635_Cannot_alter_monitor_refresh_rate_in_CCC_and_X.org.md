---
title: "Cannot alter monitor refresh rate in CCC and X.org"
date: 2008-12-03
forum: Hardware
---

### Post by AuronGrande on 2008-12-03
This is a big problem that I am having, and one that causes great headaches, literally.

I know nothing about using the Konsole, apart from knowing that sudo allows higher access. So I need the help to be simple enough to understand.

I have an ATI X1950 Pro card, using the fglrx drivers through the repository.

In the Catalyst Control Centre it detects the monitor fine, no problem there, but I can only alter the resolution. The refresh rate is fixed at 60hz. It says in the CCC that the monitor can do 75hz max, which is what I need it at.

However, going into System->Preferences->Screen Resolution. It doesn't even detect the monitor. It will let me choose a resolution, but yet again, it only allows 60hz. Clicking "Detect Monitor" does nothing.

In the xorg.conf file is the following;

Section "Monitor"
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
	Driver	"fglrx"
EndSection

I have search the internet, but to no avail.

I am using Ubuntu 8.10.

---

