---
title: "ATI Dual-Monitors, ATI Control, Big Desktop Horizontal Problems"
date: 2007-02-05
forum: Hardware &amp; Laptops
---

### Post by myXtakenheart on 2007-02-05
First, here are specs to refer to.

Ubuntu 6.10 i386
Intel P4, 3.00GHZ, w/ HT. EM64T
2.00GB of DDR-400 Dual Channel RAM
(1) SAPHIRE ATI Radeon X1600XT 256mb, 128-bit, PCI-E, 16x Graphics Card.

Heres whats happening.

I have the program ATI Control installed, and there is a option for Dual-Monitors to run in a Big Desktop Horizontal Mode, and thats what I want. Right now, its set on clone.
So,
I go into ATI Control.
Go into "Desktop Setup" and choose "Big Desktop Horizontal."
I click Apply, and it tells me to restart the X server for setting to take effect.
Now, no matter what I do, no matter how many times I restart the X server, the setup is still set as clone, and still appears as clone.

I've tried Alt+Ctrl+Backspace and reboot multiple times, having it changed back into Clone each time, and just trying to change it again, and it tells me to restart the X server, but it never works.

I'm very frustrated. Because I'm used to a Dual Monitor setup, with a stretched/Extended Desktop.
One screen at 1280x1024 is not enough for me!

Thanks,
myXtakenheart

---

### Post by myXtakenheart on 2007-02-07
I'm still having problems with this..

BUMP..
Please, if you have any input, it would be great.

---

### Post by theonlyandy on 2007-02-07
Perhaps this post helps?
[http://www.ubuntuforums.org/showthread.php?t=301941&highlight=ati+big+desktop](http://www.ubuntuforums.org/showthread.php?t=301941&highlight=ati+big+desktop)

---

### Post by Priit Tamboom on 2007-02-19
Hi!

I was looking the same thing for some time. Actually the answer is very simple, just change the resolution and you are back in one screen mode :-) 

System -> Preferences -> Screen Resolution

I have installed also Resolution Switcher under Add/Remove Applications and it works really well with ATI x1400 and their fglrx driver,

So you don't have to use this ATI Control (becaus it's doesn't change resolution on the fly), Even if you wish do use it then you have to use with sudo, so the ati control has power to change. 

sudo /usr/bin/fireglcontrolpanel

just in case I will add part of my xorg.conf

Section "Device"
	Identifier  "ATI Technologies (Primary)"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
        Option	    "DesktopSetup" "horizontal"
        Option      "Mode2" "1680x1050"
        Option "VideoOverlay" "on"
        Option "OpenGLOverlay" "off" 
        Option      "DesktopSetup" "LVDS, LCD" #the types of monitors LVDS = LCD, CRT, AUTO
EndSection


Section "Monitor"
	Identifier   "Laptop LCD"
	Option	    "DPMS" "true"
EndSection

Section "Screen"
	Identifier "Internal Screen"
	Device     "ATI Technologies (Primary)"
	Monitor    "Laptop LCD"
	DefaultDepth     24
	SubSection "Display"
         #       Viewport 0 0
		Depth     24
		Modes    "1280x800"
	EndSubSection
EndSection

Section "Monitor"
	Identifier   "External Monitor"
	VendorName   "Samsung"
        ModelName    "SyncMaster 205BW"
        Option       "dpms"
EndSection

Section "Screen"
	Identifier "External Screen"
	Device     "ATI Technologies (Primary)"
	Monitor    "External Monitor"
	DefaultDepth     24
	SubSection "Display"
	#	Viewport 0 0
                Depth     24
		Modes     "1680x1050" "1280x800"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

---

