---
title: "Can't change screen resolution on an Asus 1000HE"
date: 2009-11-18
forum: Hardware
---

### Post by b.lindahl on 2009-11-18
I've read and tried all solution I have found but with no success. 

As topic says, I have a Asus 1000HE and in Ubuntu 9.04 I used a script to toggle between 1024x600 and 1024x768 since some user interfaces in applications need bigger height than 600px if everything in the GUI should be visible. The script i used looked like this: 
> #!/bin/bash

res=$(xrandr | grep LVDS | cut -b21)

if [ $res = 7 ]; then
exec xrandr --output LVDS --panning 1024x600
elif [ $res = 6 ]; then
exec xrandr --output LVDS --panning 1024x768
fi


I print some output here that I've seen other requesting when people asked similar questions
> $ xrandr -q
Screen 0: minimum 320 x 200, current 1024 x 600, maximum 4096 x 4096
VGA1 disconnected (normal left inverted right x axis y axis)
   1024x768_60.00   59.9  
LVDS1 connected 1024x600+0+0 (normal left inverted right x axis y axis) 220mm x 129mm
   1024x600       60.0*+
   640x480        59.9
> $  cvt 1024 768
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync 
But when I tried doing newmode I get the following output:
> $ xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  23
  Current serial number in output stream:  23

I guess it could be because I have defined 1024x768_60.00 already for VGA1, right? Anyway, I guess I want to modify LVDS since that's what my script was switching resolution for in 9.04, even though I don't really understand what LVDS and VGA1 is.

Anyway, if I do addmode I get the following output:
> $ xrandr --addmode LVDS1 1024x768_60.00
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  23
  Current serial number in output stream:  24

and the output switch gives:
> $ xrandr --output VGA1 --mode 1024x768_60.00

$ xrandr --output LVDS1 --mode 1024x768_60.00
xrandr: cannot find mode 1024x768_60.00

If I do lspci -v, I get the following output that seem to be relevant to this issue:
> $ lspci -v

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 8340
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 8340
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f7f00000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at dc00 [size=8]
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Memory at f7ec0000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 8340
	Flags: bus master, fast devsel, latency 0
	Memory at f7f80000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>


I've tried to remove xorg.conf and do a sudo dpkg-reconfigure xserver-xorg followed with restart of xwindows with ctrl+alt+backspace as well as trying to add the Modeline above to the Monitor as well adding wanted resolutions to the file like this:
> Section "Monitor"
	Identifier	"Generic Monitor"
	Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "1024x600" "800x600"
	EndSubSection
EndSection


Last note, when I run my script, i.e run
xrandr --output LVDS --panning 1024x768
I get the following in dmesg:
integrated sync not supported

Alright, long post but I tried to give as much background information as possible in order to know what could causing my problem. Please let me know if you need some additional information. Thanks in advance!

---

