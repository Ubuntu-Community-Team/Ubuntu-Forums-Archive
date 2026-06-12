---
title: "Samtron 4Bni Resolution problem"
date: 2009-06-07
forum: Hardware
---

### Post by warez on 2009-06-07
Hi.. I am having a problem with setting up resolution on my old system. I just installed Ubuntu 9.04. But the highest resolution I receive is 800 X 600 only.

My system uses a Asus Motherboard with nVidia chipset and nVidia GeForce2 MX Integrated graphics controller.

I tried installing and activating the nVidia drivers, but as soon as I reboot the system, the pixels are very much into each other ;). If I move a window, it leaves traces on the screen.

Earlier I remember with the older version I used 'displayconfig-gtk' to configure my Monitor, and everything worked great, but now that package seems to be discontinued.

I also followed some documentation on modifying my monitor settings in the /etc/X11/xorg.conf file however maybe I don't know the correct refresh rates of my monitor, or I am doing something wrong. After every reboot, the screen just comes up blank.

The /etc/X11/xorg.conf file on my system is pretty much with the default entries like it did not detect anything. Here is my xorg.conf file....

********************
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
EndSection
********************

Please provide me with some leads with getting my monitor's screen resolution increased... Thanks

---

### Post by warez on 2009-06-15
Guys.. please help me on this one !!!

---

### Post by jaiseh1306 on 2010-10-11
**Samtron 4Bni Resolution problem** 			
 			 			 		   		 		 		Hi.. I am  having a problem with setting up resolution on my old system. I just  installed Ubuntu 9.04. But the highest resolution I receive is 800 X 600  only.

My system uses a Asus Motherboard with nVidia chipset and nVidia GeForce2 MX Integrated graphics controller.

I tried installing and activating the nVidia drivers, but as soon as I  reboot the system, the pixels are very much into each other :wink:. If I move a window, it leaves traces on the screen.

Earlier I remember with the older version I used 'displayconfig-gtk' to configure my Monitor, and everything worked great, but now that package seems to be discontinued.

I also followed some documentation on modifying my monitor settings in the /etc/X11/xorg.conf file however maybe I don't know the correct refresh rates of my monitor, or I am doing something wrong. After every reboot, the screen just comes up blank.

The /etc/X11/xorg.conf file on my system is pretty much with the default entries like it did not detect anything. Here is my xorg.conf file....

********************
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
EndSection
********************

Please provide me with some leads with getting my monitor's screen resolution increased... Thanks

---

