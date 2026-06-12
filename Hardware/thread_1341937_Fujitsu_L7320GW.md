---
title: "Fujitsu L7320GW"
date: 2009-11-30
forum: Hardware
---

### Post by Phillip Hutchinson on 2009-11-30
I Have an Fujitsu Seimens Amilo l7320GW. With Ubuntu 9.04 running. However I have a problem in that my LCD not recognised, so I ended up with just the top left 1280x800 of a 1600x1200 virtual screen. Any sollution I am scratching my head.

---

### Post by SpearZ on 2009-12-08
Hi,
Previously in Jaunty I solved this by using the below in /etc/X11/xorg.conf

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
	DefaultDepth	16
	Subsection "Display"
		Viewport	 0 0
		Depth		16
		Modes		"1280x800" "1024x768" "800x600"
	EndSubSection
EndSection

Hope it helps ;)

---

### Post by nzmark on 2010-03-23
Many thanks for this great post!

My hard drive died in my Amilo L7320GW after years being a XP user and discovered I could install ubuntu on a usb caddy I had lying around, It seemed to run great but for the over sized screen resolution. 

I'm a total noob 1st timer and set on a hellbent mission to get it fixed! 

I'm running ubuntu 9.10 and couldn't find xorg.conf in the suggested place, so I opened a terminal (Applications/Accessories/Terminal) 

Cut and pasted the command line "sudo nano /etc/X11/xorg.conf" 

A blank xorg.conf editor will open, now back to this page to cut and paste in the comand lines above, You also got to press Ctrl+x to save your new xorg.conf, making sure to press Y and then Enter at the prompts, now reboot.

It took my hours of google but well worth it, thanks a million mate!  


nz

---

### Post by wh00ps on 2011-01-06
thanks so much, I'm doing exactly the same thing (running ubuntu 9 from usb - actually from the 8GB memory of my old Samsung Omnia on my wife's laptop) and i was all morning looking for drivers and typing random things into synaptic :D

---

