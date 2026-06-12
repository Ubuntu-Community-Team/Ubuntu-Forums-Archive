---
title: "dual monitor (VGA + DVI)  intel 945GM help"
date: 2008-05-06
forum: Hardware
---

### Post by guisep on 2008-05-06
I'm attempting to get both of my external monitors working on my D620 with Intel 945GM.  Looks like 8.04 sees both but only puts out to VGA.
Here's my xorg.conf. (see below)  Unfortunately I don't have enough expertise to know what to modify to get this to work.  On a side note I'll still need my LCD working when I work at home.
TIA..

Joe

# xorg.conf (X.Org X Window System server configuration file)

Section "InputDevice"
..."
EndSection

Section "InputDevice"
...
EndSection

Section "InputDevice"
...
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by chewearn on 2008-05-07
Just to confirm, you are referring to Dell Latitude D620?  And with a dock, which has VGA and DVI ports?

As far as I can tell, you can get any two out of three output working at one time (counting the internal LCD as well); not all three.

---

### Post by guisep on 2008-05-07
Yes correct I'm attempting to get two working at a time.  When docked I would prefer the VGA and DVI to function when standalone the LCD.  I've seen several posts from people with similar problems, looks like the graphics detector is overlaying all output on top of each other rather then being separate monitors.  I'm sure if I knew how to modify the xorg.conf I would fix it but I have little experience with it and from my old 6.x system things have changed on what it finds.. Anyone know of a good tutorial that could help with 8.04s xorg.conf?

---

