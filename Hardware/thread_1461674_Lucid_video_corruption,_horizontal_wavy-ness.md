---
title: "Lucid video corruption, horizontal wavy-ness"
date: 2010-04-24
forum: Hardware
---

### Post by oryan_dunn on 2010-04-24
ATI Radeon 9700 with Proview 19" 1440x900 monitor.

Karmic detected and booted just fine with the correct resolution, refresh rate, and no corruption.
Lucid detected and booted just fine with the correct resolution and refresh rate, but there are horizontal wavy corruption.  I also reported this issue with Fedora 12 [here]("http://forums.fedoraforum.org/showthread.php?t=241365").  I posted a [video]("http://www.youtube.com/watch?v=pBFE2UgCDGU") because words can't really describe it.  My monitor accepts two refresh rates 60Hz and 75Hz.  If I use the Monitor applet to switch to 75Hz, there is no problem.  But the boot screen and gdm still are wavy (plus there were no issue in Karmic, so the 60Hz should work).

Here is the output of xrandr:
```
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 4096 x 4096
VGA-0 connected 1440x900+0+0 (normal left inverted right x axis y axis) 410mm x 256mm
   1440x900       59.9*+   75.0     59.9  
   1280x1024      75.0     60.0  
   1024x768       75.1     70.1     60.0  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     60.0  
   720x400        70.1  
DVI-0 disconnected (normal left inverted right x axis y axis)
S-video disconnected (normal left inverted right x axis y axis)
```

and here is the output of sudo get-edid|parse-edid:
```
ryan@ryan-desktop:~$ sudo get-edid|parse-edid 
parse-edid: parse-edid version 2.0.0
get-edid: get-edid version 2.0.0

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
	Function supported
	Call successful

	VBE version 200
	VBE string at 0x2110 "ATI R300"

VBE/DDC service about to be called
	Report DDC capabilities

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
	Function supported
	Call successful

	Monitor and video card combination does not support DDC1 transfers
	Monitor and video card combination supports DDC2 transfers
	0 seconds per 128 byte EDID block transfer
	Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
	Read EDID

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
	Function supported
	Call successful

parse-edid: EDID checksum passed.

	# EDID version 1 revision 3
Section "Monitor"
	# Block type: 2:0 3:fd
	# Block type: 2:0 3:ff
	Identifier "PTS:7007"
	VendorName "PTS"
	ModelName "PTS:7007"
	# Block type: 2:0 3:fd
	HorizSync 30-80
	VertRefresh 60-75
	# Max dot clock (video bandwidth) 140 MHz
	# Block type: 2:0 3:ff
	# DPMS capabilities: Active off:yes  Suspend:yes  Standby:yes

	Mode 	"1440x900"	# vfreq 59.901Hz, hfreq 55.469kHz
		DotClock	88.750000
		HTimings	1440 1488 1520 1600
		VTimings	900 903 909 926
		Flags	"-HSync" "+VSync"
	EndMode
	Mode 	"1280x1024"	# vfreq 60.020Hz, hfreq 63.981kHz
		DotClock	108.000000
		HTimings	1280 1328 1440 1688
		VTimings	1024 1025 1028 1066
		Flags	"+HSync" "+VSync"
	EndMode
	# Block type: 2:0 3:fd
	# Block type: 2:0 3:ff
EndSection

```

In all cases (F12, Karmic, Lucid), the radeon driver was used. I have a feeling it's the boot process (Plymouth? KMS?) that is causing the issue.  Any ideas?  If need be, I can take a video of the corruption in lucid, but it's identical to that in fedora (which certainly narrows the problem down to an upstream issue somewhere, and I'll go bother that upstream project if I can pinpoint which one it is).

Thanks,
Ryan

Edit: I tried switching out monitors and VGA cables and neither had trouble, though it was a completely different monitor and resolution.  I then swapped my 9700 Pro with a spare Radeon 9600, and this card seems to work just fine with my 1440x900 monitor.  Now I need to figure out why my monitor and the 9700 don't seem to get along at the 60Hz refresh rate in these latest linux releases.

Edit 2: After putting the old card back in (the 9700Pro), there was no wavyness.  It seems to work just fine for a while, then it starts to get worse, so it looks like it is a hardware problem with that card (probably heat related).  So it doesn't look like any kind of bug, but some code changes between software in karmic to lucid bring out this problem.  So, now I need to figure out how to specify modelines manually to work around this issue.

---

### Post by artursm on 2010-04-30
I'm having this problem as well. I'm running a notebook with ATI Radeon x1270, and the notebook's screen is fine, but the screen on my second monitor gets very wavy. It happens on the login screen (very smooth slow waves) and happens on the desktop to (very quick, choppy, and random waves).

---

### Post by artursm on 2010-04-30
I tested 2 different drivers and both produced the waviness, only different.
This:

sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri

Produced the very choppy wavyness on the desktop (like I mentioned earlier).

While this:

sudo apt-get install xorg-driver-fglrx

Produced smoother waves. The point is, the software is likely the issue with me, since it's a brand new notebook.

---

### Post by oryan_dunn on 2010-04-30
Well, it turns out it is a hardware failure.  My 9700Pro that has served me well for the past 7 years finally gave up.

As for the issue of the wavyness, I got it to go away by disabling KMS.  The 60Hz res that x picked worked, whereas the 60Hz res that the kernel picked had issues.  It's all a moot point now.  I just orderded a Radeon HD4650 to replace it.  Should be quite a nice upgrade.

---

