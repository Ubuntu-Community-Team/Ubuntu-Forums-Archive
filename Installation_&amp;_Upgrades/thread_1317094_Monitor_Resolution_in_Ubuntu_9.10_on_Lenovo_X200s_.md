---
title: "Monitor Resolution in Ubuntu 9.10 on Lenovo X200s - multiple monitors"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by Jabz.biz on 2009-11-06
Hi, I have just upgraded from 9.04 to 9.10 and have trouble getting a higher resolution on both of my screens. When the laptop is not docked on the docking-station the resolution is fine.
When both monitors are active my resolution on both screens is 1152x864

Under system>Admin>Hardware Drivers are no drivers available.

Some more infos:

### lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)


### cat /etc/X11/xorg.conf
Section "Monitor"
Identifier	"Configured Monitor"
EndSection
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	3360 1200
	EndSubSection
EndSection
Section "Device"
	Identifier	"Configured Video Device"
EndSection
(My 9.04 setup had an empty xorg.conf)


### sudo Xorg -configure
Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.



Any ideas to fix this?
Thanks.

---

### Post by jwmuelle on 2009-11-06
First, try adjusting the resolutions using the display app (system > preferences > display).  That's worked for me and is retained across boots.

Additionally/alternatively, you can look at the xrandr command to change display resolutions and positions.  Changes made with xrandr are lost and need to be re-executed with each log-in (or cycle of the X server).  If you need to go this route, consider setting the commands in a script that runs when you log in (system > preferences > startup applications).  When I've needed this, I included a "sleep 10" or "sleep 20" command in the script before the xrandr commands.  This slight delay ensures the default graphics setup has completed and my xrandr commands are the last executed.  "xrandr" by itself from a terminal CLI will display current settings (note the monitor/display names).  In it's most basic form, "xrandr --output LVDS1 --auto --output VGA1 --auto --right-of LVDS1"   (without quotes, and I'm using integrated intel graphic cards) will set both to native resolution and position the external monitor to the right of the laptop display.

hth.

jw.

---

### Post by Jabz.biz on 2009-11-06
> **jwmuelle said:**
> First, try adjusting the resolutions using the display app (system > preferences > display).  That's worked for me and is retained across boots.

I should put more trust in the GUI. Worked for me. Thanks.

---

