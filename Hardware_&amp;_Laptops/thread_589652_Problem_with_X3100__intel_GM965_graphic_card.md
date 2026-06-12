---
title: "Problem with X3100  intel GM965 graphic card"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by sigveh on 2007-10-24
After installation of gutsy gibbon, the screen goes blank after the login procedure. It works in failsafe mode.

The laptop is a Gateway M-6816. 

Pootential interesting info from xorg.conf is listed at the bottom.
On an early try it worked with a vesa drver, but the screen was really dim. Now I can not reproduce that either.Also I have got it to work with the intel 965 driver, but now the rsolution was only 680x480. The laptop is really 1280x800.

I love kubuntu when it works, ...

Cheers


Section "Device"
	Identifier	"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection

---

### Post by ettore85a on 2007-11-03
same problem...

any suggestion?^?

please help!!

---

### Post by PJSingh5000 on 2007-11-28
Have you tried running "sudo dpkg-reconfigure xserver-xorg" ?

---

### Post by PJSingh5000 on 2007-11-29
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/151311](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/151311) [br].[/br] ---------------------------- [br].[/br] [br].[/br]

After running  "sudo dpkg-reconfigure xserver-xorg" your KDM/GDM resolution may be off.  If so, as per  anespor ([https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/151311](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/151311)), add the following two lines to the "Monitor" section of xorg.conf:

	DisplaySize	<Display  WIDTH in mm> <Display HEIGHT in mm>
	Option		"Monitor-LVDS" "<Monitor Identifier>"
	# Replace the <> with your own values

Here is the full "Monitor" section from my updated xorg.conf for your reference...

Section "Monitor"
	Identifier	        "DCLCD"
	Option		"DPMS" "true"
	HorizSync	        64.7-65.29
	VertRefresh	59.883-59.954
	DisplaySize	433 271
	Option		"Monitor-LVDS" "DCLCD"
EndSection

Let me know if this helps.

---

