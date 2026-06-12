---
title: "Video Drivers for Intel Chipsets"
date: 2008-11-06
forum: General Help
---

### Post by geubank on 2008-11-06
How could I determine which video driver is being used on my system.  It uses the i810 chip set and I am trying to install intrepid.  Also how can you force a particular driver(i810,intel,vesa)

---

### Post by blue13130 on 2008-11-06
To see what driver you are using run this command:
```
cat /etc/X11/xorg.conf | grep Driver
```

You can also just run:
```
cat /etc/X11/xorg.conf
``` 
and then look for the line that says "Driver"

If you want to force a driver, edit the /etc/X11/xorg.conf file and change the name of the driver to intel, or vesa.

I recommend making a copy of a working xorg.conf prior to changing it.

---

### Post by geubank on 2008-11-06
The xorg.conf in intrepid is basically empty as compared to the older ones.  No driver section.

---

### Post by blue13130 on 2008-11-07
You can try searching the Xorg log to see what driver is being used:
```
cat /var/log/Xorg.0.log | grep -i driver
```

---

### Post by ramaswamyps on 2008-11-07
root@ramaswamy-desktop:~# cat /var/log/Xorg.0.log | grep -i driver |more
        X.Org Video Driver: 2.0
        X.Org XInput driver : 2.0
        ABI class: X.Org Video Driver, version 2.0
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 2.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 2.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 2.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
        ABI class: X.Org Video Driver, version 2.0
        ABI class: X.Org Video Driver, version 2.0
        ABI class: X.Org Video Driver, version 2.0
(II) Loading /usr/lib/xorg/modules/drivers//sil164.so
        ABI class: X.Org Video Driver, version 2.0
(II) Loading /usr/lib/xorg/modules/drivers//ch7xxx.so
        ABI class: X.Org Video Driver, version 2.0
(II) Loading /usr/lib/xorg/modules/drivers//ivch.so
        ABI class: X.Org Video Driver, version 2.0
(II) Loading /usr/lib/xorg/modules/drivers//tfp410.so
        ABI class: X.Org Video Driver, version 2.0
(II) Loading /usr/lib/xorg/modules/drivers//ch7017.so
        ABI class: X.Org Video Driver, version 2.0
        ABI class: X.Org Video Driver, version 2.0
(II) [drm] loaded kernel module for "i915" driver.
(II) intel(0): [drm] framebuffer mapped by ddx driver
(II) EXA(0): Driver registered support for the following operations:
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
root@ramaswamy-desktop:~#  


this my xorg log part.in ubuntu-8.04


in 8.10 only vesa is being used. i could not make it use like this intel.
i have 845 p4 mother board


root@ramaswamy-desktop:~# cat /mnt/hda1/var/log/Xorg.0.log | grep -i driver |more
        X.Org Video Driver: 4.1
        X.Org XInput driver : 2.1
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 4.1
(II) VESA: driver for VESA chipsets: vesa
        ABI class: X.Org Video Driver, version 4.1
        ABI class: X.Org Video Driver, version 4.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 2.1
root@ramaswamy-desktop:~#                               

this is the log for 8.10

how do i make it use the first configuration???

---

### Post by blue13130 on 2008-11-07
You could try forcing xorg in 8.10 to use the intel driver.  Add this to your xorg.conf file (after backing up the original!).

```
Section "Device"
	Identifier	"Default Device"
	Driver	"intel"
EndSection
```

**This is only a suggestion!  I don't have a machine that I tested this on.  My 8.10 has an Nvidia card.  Be prepared to know how to boot to the shell and restore the original xorg.conf if this really messes things up to prevent you from having a GUI.**

---

### Post by geirha on 2008-11-07
This should display which video driver is being used I think.
```
grep -C2 'Module class: X.Org Video Driver' /var/log/Xorg.0.log
```

---

### Post by ramaswamyps on 2008-11-07
once i add something like devices section driver screen size and other dri glx or any one of them X starts with blank screen.
this cannot be done in xorg.conf. it looks for preconfigured X the file is elsewhere i could not find it yet.

modprobe shows the intel i810 vga modues are present .
but i cant make it load any of them.

the kernel forces the X to use vesa. if say something else in xorg.conf it has to take both actions and blank screen and getting stuck there.

the root cause has to be found out.

i tried fglrx server also no dice!
i have to try and compile kernel modules and new bzImage and things like that.

xorg is already configured and it just does not accept any more change in xorg.conf.


root@ramaswamy-desktop:~# grep -C2 'Module class: X.Org Video Driver' /var/log/Xorg.0.log
(II) Module intel: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 2.2.1
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "mouse"
root@ramaswamy-desktop:~#
this is log in ubuntu-8.04  and works really nice with Xrender and opengl transaprency shadows etc.


i will post the 8.10 log in a minute

this xorg module is distro given. is there a way i can install the versions used in 8.04???

------------------------------------------

root@ramaswamy-desktop:~# grep -C2 'Module class: X.Org Video Driver' /mnt/hda1/var/log/Xorg.0.log
(II) Module vesa: vendor="X.Org Foundation"
        compiled for 1.5.0, module version = 1.3.0
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 4.1
(II) VESA: driver for VESA chipsets: vesa
root@ramaswamy-desktop:~#

this is log of 8.10 Xorg

unless we change the compiled module it may not be possible to get other video drivers work here.

any suggestions??

---

### Post by geirha on 2008-11-08
Open 8.10's Xorg.0.log file in an editor, then browse down to the spot where it loads the video module and see if it attempts to load the intel driver. It might have some error messages that explains why it is unable to load the intel driver.

---

### Post by ramaswamyps on 2008-11-10
i was able to make the vga module loaded with intel driver.
now th desktop effects and 1024x768 screen resolution comesup .occationally system gets stuck. then that problem is there with ubuntu-8.10
now my xorg.conf is like this

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
Section "Monitor"
	#DisplaySize	  280   210	# mm
	Identifier   "Monitor0"
	VendorName   "GSM"
	ModelName    "20Si"
	HorizSync    20.0 - 54.0
	VertRefresh  60 - 80
ModeLine "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
   ModeLine "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
   ModeLine "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync 
	Option	    "DPMS"
EndSection

Section "Extensions"
    Option  "Composite"  "Enable"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
        #DefaultDepth 24 
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
        Modes "1024x768" "800x600" "640x480"
		Depth    4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
Modes "1024x768" "800x600" "640x480"
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
Modes "1024x768" "800x600" "640x480"
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
Modes "1024x768" "800x600" "640x480"
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
Modes "1024x768" "800x600" "640x480"
		Depth     24
	EndSubSection
EndSection

---

