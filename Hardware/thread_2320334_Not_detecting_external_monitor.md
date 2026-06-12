---
title: "Not detecting external monitor"
date: 2016-04-13
forum: Hardware
---

### Post by Vencislav_Popov on 2016-04-13
I have a really weird issue. I'm using an Acer laptop running Ubuntu 15.10 and a Dell laptop running Windows 8. I have two monitors. The first one works fine with both my windows and my Ubuntu 15.10 machines. The second one works with my windows machine, but not with my Ubuntu machine. It is outputing a DVI signal through a DVI-HDMI adapter cable to the hdmi port of the laptop. I am using nvidia proprietary drivers. When I run xrandr it says that HDMI-1-0 is disconnected, even though the cable is connected. I've tried it both when running the NVIDIA card, and the intel card, doesn't work. I've tried manually adding a new mode with xrandr for the HDMI output, and it does appear, but when I then try to use xrandr --output HDMI-1-0 --mode 1920x1080 --right-of eDP-1-0, but the laptop screen just flickers and goes back to normal. I've tried several different nvidia drivers (now using 361), I've also tried the noveau drivers as well, same story. I know the cable and the monitor work fine, because they do on the windows machine, and I know that the port on the Ubuntu machine works fine, because it does with a different monitor. 

I've spent 5 hours trying to solve this to no avail. Here's my Xorg log: 

[http://paste.ubuntu.com/15803798/](http://paste.ubuntu.com/15803798/)

And here's the output of get-edid | parse-edid:

```
This is read-edid version 3.0.2. Prepare for some fun.
Attempting to use i2c interface
No EDID on bus 0
No EDID on bus 1
No EDID on bus 3
No EDID on bus 5
2 potential busses found: 2 4
Will scan through until the first EDID is found.
Pass a bus number as an option to this program to go only for that one.
128-byte EDID successfully retrieved from i2c bus 2
Looks like i2c was successful. Have a good day.
WARNING: Checksum failed
Trying to continue...
Section "Monitor"
	Identifier "VA2448 SERIES"
	ModelName "VA2448 SERIES"
	VendorName "VSC"
	# Monitor Manufactured week 41 of 2011
	# EDID version 1.3
	# Digital Display
	DisplaySize 520 290
	Gamma 2.20
	Option "DPMS" "true"
	Horizsync 24-82
	VertRefresh 50-75
	# Maximum pixel clock is 170MHz
	#Not giving standard mode: 1680x1050, 60Hz
	#Not giving standard mode: 1600x1200, 60Hz
	#Not giving standard mode: 1440x900, 60Hz
	#Not giving standard mode: 1280x1024, 60Hz
	#Not giving standard mode: 1280x960, 60Hz
	#Not giving standard mode: 1280x800, 75Hz
	#Not giving standard mode: 1280x800, 60Hz
	#Not giving standard mode: 1152x864, 75Hz
	Modeline 	"Mode 0" 148.50 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync 
EndSection

```

So some information does reach the laptop, because the edid shows the correct model of the monitor. But the hdmi port still shows as disconnected in xrandr, and both the "Display" settings in Ubuntu, and the nvidia-settings panel cannot detect the second screen. Any ideas? This is driving me crazy.

---

