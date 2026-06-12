---
title: "laptop no widescreen.."
date: 2006-04-13
forum: Hardware &amp; Laptops
---

### Post by mengqing on 2006-04-13
I have the Asus W5A laptop and it is a intel 915GML Express ingrated card..

i installed breezy b4 and i got 1280x768 working..

but this time i failed..

basically i've tried everything that i tried from last time..

my xorg.conf is as follow

> Section "Monitor"
	Identifier	"Generic Monitor"
	#Option		"DPMS"
	HorizSync	30-101
	VertRefresh	50-101
	#Modeline	"1280x768@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Intel Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		16
		Modes		"1280x768" 
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x768" 
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection



as you can see I only have the 1280x768 entered...

however after running under X, i found out that I am running 1024x768, at 75Hz, I can only switch to lower resolutions eg 800x600, 640x480.. however 1024x768 is the highest available

I also tried 915resolution and it didnt work the way Those tutorials said will either...

SOmebody help me thx...



PS: I also tried installing the driver from Intel's website, however following error came up

Compiling new agpgart module...

ERROR: AGPGART module did not compile

Compiling DRM module...

ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.

---

### Post by McLogic on 2006-04-13
I can only say that 855res/915res works fine for me.

You do need to fill in the options, and call it from the right places.

```
Edit /etc/default/855resolution as follows :

# 
# 855resolution default
#
# find free modes by  /usr/sbin/855resolution -l
# and set it to MODE
#
MODE=5c
#
# and set resolutions for the mode.
#
XRESO=1280
YRESO=800

To work hibernation, add 855resolution line to head of /etc/acpi/resume.sh.

#!/bin/bash (-)

invoke-rc.d --quiet 855resolution start

*snip*

To work mem suspend, uncomment follow line of /etc/default/acpi-support.

ACPI_SLEEP=true 

```

I hope this helps. :confused:

---

### Post by snipe122 on 2006-05-06
if you havnt solved the problem left try to reconfigure your xserver...

dpkg-reconfigure xserver-xorg

greetz
snipe

---

### Post by masooga on 2006-05-06
I have this same problem.  I've tried dpkg-reconfigure xserver-xorg but that doesn't work either.

---

### Post by snipe122 on 2006-05-07
somewhere in the reconfiguratin-process, theres a point where you can choose the possible resolutions... does it not help just to mark the right one and unmark all others?

---

### Post by barbarian on 2006-05-07
sorry for interrupting, but maybe this website would be usefull:
[http://www.linux-on-laptops.com/asus.html](http://www.linux-on-laptops.com/asus.html)

---

