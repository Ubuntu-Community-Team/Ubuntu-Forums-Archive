---
title: "HDMI connected monitor no longer detected"
date: 2021-07-29
forum: Hardware
---

### Post by moylando on 2021-07-29
I upgraded to 21.04 and now external HDMI connected monitor is not detected.  I'm using both Intel and Nvidia 470 drivers.  Can run with either successfully on main laptop monitor, but the external monitor is no longer detected.  It was previously working flawlessly.  I've tried with monitor connected at boot and hot plugging.  

xrandr shows:
HDMI-1-1 disconnected (normal left inverted right x axis y axis)

Any help debugging is appreciated.

---

### Post by moylando on 2021-07-29
Some more info, I manually activated the HDMI port via grub video option, then I can manually fetch edid information from the monitor

>get-edid | parse-edid
This is read-edid version 3.0.2. Prepare for some fun.
Attempting to use i2c interface
No EDID on bus 0
Problem requesting slave address: Device or resource busy
No EDID on bus 2
No EDID on bus 4
No EDID on bus 6
2 potential busses found: 3 5
Will scan through until the first EDID is found.
Pass a bus number as an option to this program to go only for that one.
256-byte EDID successfully retrieved from i2c bus 3
Looks like i2c was successful. Have a good day.
Checksum Correct


Section "Monitor"
	Identifier "PA278QV"
	ModelName "PA278QV"
	VendorName "AUS"
	# Monitor Manufactured week 47 of 2020
	# EDID version 1.3
	# Digital Display
	DisplaySize 600 340
	Gamma 2.20
	Option "DPMS" "true"
	Horizsync 30-112
	VertRefresh 46-75
	# Maximum pixel clock is 300MHz
	#Not giving standard mode: 1152x864, 75Hz
	#Not giving standard mode: 1280x1024, 60Hz
	#Not giving standard mode: 1280x960, 60Hz
	#Not giving standard mode: 1440x900, 60Hz
	#Not giving standard mode: 1600x1200, 60Hz
	#Not giving standard mode: 1680x1050, 60Hz
	#Not giving standard mode: 1920x1200, 60Hz
	#Not giving standard mode: 2048x1152, 60Hz


	#Extension block found. Parsing...
	Modeline 	"Mode 11" 79.50 1280 1344 1472 1664 768 771 778 798 -hsync +vsync 
	Modeline 	"Mode 0" 241.50 2560 2608 2640 2720 1440 1443 1448 1481 +hsync -vsync 
	Modeline 	"Mode 1" 148.500 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
	Modeline 	"Mode 2" 74.250 1280 1390 1420 1650 720 725 730 750 +hsync +vsync
	Modeline 	"Mode 3" 27.027 720 736 798 858 480 489 495 525 -hsync -vsync
	Modeline 	"Mode 4" 27.027 720 736 798 858 480 489 495 525 -hsync -vsync
	Modeline 	"Mode 5" 27.000 720 732 796 864 576 581 586 625 -hsync -vsync
	Modeline 	"Mode 6" 27.000 720 732 796 864 576 581 586 625 -hsync -vsync
	Modeline 	"Mode 7" 74.250 1280 1720 1760 1980 720 725 730 750 +hsync +vsync
	Modeline 	"Mode 8" 148.500 1920 2448 2492 2640 1080 1084 1089 1125 +hsync +vsync
	Modeline 	"Mode 9" 74.250 1920 2008 2052 2200 1080 1082 1087 1125 +hsync +vsync interlace
	Modeline 	"Mode 10" 74.250 1920 2448 2492 2640 1080 1082 1089 1125 +hsync +vsync interlace
	Modeline 	"Mode 12" 298.47 2560 2583 2615 2670 1440 1478 1486 1492 +hsync -vsync 
	Modeline 	"Mode 13" 83.50 1280 1352 1480 1680 800 803 809 831 -hsync +vsync 
	Modeline 	"Mode 14" 181.25 2560 2608 2640 2720 1080 1083 1093 1111 +hsync -vsync 
	Option "PreferredMode" "Mode 11"
EndSection

However, 

>cat /sys/class/drm/card0-HDMI-A-1/edid

returns empty and 

xrandr doesn't reflect these options:

HDMI-1 connected 1024x768+1920+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00* 
   800x600       60.32    56.25  
   848x480       60.00  
   640x480       59.94  

So, there seems to be an issue recognizing a monitor when connected, reading the edid and configuring things appropriately.  Odd, given that I can read that information manually.

---

