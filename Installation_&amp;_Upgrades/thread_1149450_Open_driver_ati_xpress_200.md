---
title: "Open driver ati xpress 200"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by max246 on 2009-05-05
I have upgraded my ubuntu from 8.10 to 9.04 but My card is not support on driver 9.4 but driver open not work.

Glx return:

glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Segmentation fault

xorg:

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "ati"
        BusID           "PCI:1:5:0"
        Option          "DRI" "true"
        Option          "GARTSize" "64"

EndSection


Why not work?

---

### Post by Mark Phelps on 2009-05-05
Did you have ATI restricted drivers installed before the upgrade? If so, it's likely that they didn't get removed properly.

---

### Post by Kryzzalid on 2009-10-04
I have also an ATI Radeon Xpress 200M (128/256mb) and with the help of "man radeon" and [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) i got it to work with the open drivers kinda well. But I'm just wandering what options i could add to get it to work better. I added in the xorg.conf:

Section "Device"
        Identifier      "Xpress 200"
        Driver          "ati"
        BusID           "PCI:1:5:0"
        Option          "XAANoOffscreenPixmaps"
	Option          "AccelMethod"    "EXA"
	Option          "TripleBuffer"   "true"
	Option		"AGPMode" "8"
	Option		"AGPMode" "PCIE"

EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Xpress 200"
	DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
		Virtual         1280 800
        EndSubSection
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection

Is there anything else i could add? My goal is to get Half Life 2 to work faster. Because it pretty slow.

---

### Post by StuartN on 2009-10-04
It seems the update process is very badly handled for users with the proprietary drivers installed with the (now) unsupported cards. Only a clean install is assured to work.

---

### Post by Mark Phelps on 2009-10-04
This has been a standard problem with updates ever since I started out using Ubuntu back in the version 7.x days.  If you have any restricted drivers installed, you have to remove them before doing an upgrade or run the risk of the system not working properly afterward.  If the drivers are network or wireless, that's generally a simple fix.  But if the drivers are video, you often get a black screen with a blinking cursor.

Why the update SW can't check for the presence of restricted drivers and alter the upgrader to remove them -- is beyond me.

---

### Post by StuartN on 2009-10-04
> **Mark Phelps said:**
> If you have any restricted drivers installed, you have to remove them before doing an upgrade or run the risk of the system not working properly afterward.

In the many, many threads on the ATI upgrade woes, it seems that uninstalling the proprietary driver was not enough because of various other configuration changes that had been introduced and the only way to be sure of a functioning "legacy" ATI device was a clean install. The steps I saw described would tax the upgrade process.

---

### Post by Mark Phelps on 2009-10-05
> **StuartN said:**
> In the many, many threads on the ATI upgrade woes, it seems that uninstalling the proprietary driver was not enough because of various other configuration changes that had been introduced and the only way to be sure of a functioning "legacy" ATI device was a clean install. The steps I saw described would tax the upgrade process.

Can't speak to other folks' problems, but I had restricted drivers installed, removed them following the instructions in the ATI Open Source drivers Wiki, upgraded to 9.04 -- and have had no problems at all.  I'm still running the ATI open source drivers.

The steps I saw in the Wiki were a few simple commands -- something a script should easily be able to handle as part of an upgrade process.

---

