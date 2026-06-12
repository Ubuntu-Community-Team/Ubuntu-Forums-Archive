---
title: "Gutsy video problems on toshiba tecra M1"
date: 2008-03-17
forum: Hardware &amp; Laptops
---

### Post by Tim from Tang on 2008-03-17
Hi all,
I have just installed Gutsy on a toshiba Tecra M1 laptop for my eight year old daughter. I have most everything working well enough excepting two problems.
the first is that on closing the screen the display zooms to the top left corner displaying only about a quarter of the desktop. This is currently easily enough got out of by switching to tty1 and then back to tty7 ctrl+alt+F1then ctrl+alt+F7.
The other issue is a thorny one however.
I can not get the machine to display video (dvd's and the like) The only video that works is flash (you tube etc). I have all the correct codecs installed libdvdcss2 etc, as I installed them on my own thinkpad T40 at the same time and it is playing dvd's etc fine.
I have (I hope) attached the xorg config file from the tecra. below are the relevant bits in case it did not make it.

Section "Device"
	Identifier	"Trident Microsystems CyberBlade XP4m32"
	Driver		"trident"
	BusID		"PCI:1:0:0"
        
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Trident Microsystems CyberBlade XP4m32"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"


hoping somebody can help
Tim

---

### Post by ghartl1 on 2008-07-16
i think you have had the same problem with the same hardware..

here is my solution..hopefully you can exploit it

greets günter

[http://www.slackforum.de/forum/index.php?t=rview&goto=19384#msg_19384](http://www.slackforum.de/forum/index.php?t=rview&goto=19384#msg_19384)

---

