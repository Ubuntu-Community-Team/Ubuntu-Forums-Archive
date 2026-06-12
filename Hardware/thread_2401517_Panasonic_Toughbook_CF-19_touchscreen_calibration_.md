---
title: "Panasonic Toughbook CF-19 touchscreen calibration issue"
date: 2018-09-19
forum: Hardware
---

### Post by ant-tv on 2018-09-19
Hello everyone.

I have an issue with calibration of touchscreen panel on my old good Toughbook CF-19 laptop.

Until last update everything works perfectly. When I taped some point on a screen, even with a finger, it just pressed, without any calibration.

So, how I have tried to fix this calibration?

1) Installed [I]xinput_calibrator


[/I]2) launch it:
> 
$ xinput_calibrator -v
DEBUG: XInputExtension version is 2.3
DEBUG: Skipping virtual master devices and devices without axis valuators.
DEBUG: Skipping device 'Virtual core XTEST pointer' id=4, does not report Absolute events.
DEBUG: Skipping device 'PS/2 Generic Mouse' id=11, does not report Absolute events.
DEBUG: Selected device: Fujitsu Component USB Touch Panel
DEBUG: Not usbtouchscreen calibrator: Not a usbtouchscreen device
DEBUG: Not evdev calibrator: Evdev: invalid "Evdev Axis Calibration" property format
Calibrating standard Xorg driver "Fujitsu Component USB Touch Panel"
	current calibration values: min_x=0, max_x=65535 and min_y=0, max_y=65535
	If these values are estimated wrong, either supply it manually with the --precalib option, or run the 'get_precalib.sh' script to automatically get it (through HAL).
DEBUG: Found that 'Fujitsu Component USB Touch Panel' is a sysfs name.
DEBUG: Adding click 0 (X=181, Y=103)
DEBUG: Adding click 1 (X=887, Y=101)
DEBUG: Adding click 2 (X=186, Y=589)
DEBUG: Adding click 3 (X=882, Y=590)
	--> Making the calibration permanent <--
DEBUG: Found that 'Fujitsu Component USB Touch Panel' is a sysfs name.
  copy the snippet below into '/etc/X11/xorg.conf.d/99-calibration.conf' (/usr/share/X11/xorg.conf.d/ in some distro's)
Section "InputClass"
	Identifier	"calibration"
	MatchProduct	"Fujitsu Component USB Touch Panel"
	Option	"MinX"	"4267"
	Option	"MaxX"	"64084"
	Option	"MinY"	"1771"
	Option	"MaxY"	"57236"
	Option	"SwapXY"	"0" # unless it was already set to 1
	Option	"InvertX"	"0"  # unless it was already set
	Option	"InvertY"	"0"  # unless it was already set
EndSection



3) Copied this snippet into '/etc/X11/xorg.conf.d/99-calibration.conf'
/xorg.conf.d as well as 99.calibration.conf does not existed, so I have created them.

after rebooting the system nothing changed. So I have made 

4) created directory and file in /usr/share/X11/xorg.conf.d/

5)rebooted the system. 

Again, touchscreen does not worked. In lower half of the screen the mouse cursor occured up to 3 cm from the point of the tap.

How to activate the calibration data?
Help me please!

---

