---
title: "Seeting the refresh rate and detecting unknown monitor (18.04)"
date: 2019-01-09
forum: Hardware
---

### Post by Mongoose088 on 2019-01-09
Hello all,

I just put a fresh install of Ubuntu Mate 18.04 on this machine. GFX Card is ATI Radeon RX 580. Monitor is Acer XG 270HU.

This is the output of inxi -G:
```
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Ellesmere [Radeon RX 470/480/570/570X/580/580X/590]
           Display Server: x11 (X.Org 1.19.6 )
           drivers: fbdev,ati (unloaded: modesetting,vesa,radeon,amdgpu)
           Resolution: 2560x1440@93.00hz
           OpenGL: renderer: llvmpipe (LLVM 7.0, 128 bits)
           version: 3.3 Mesa 19.0.0-devel (git-0cc01f4 2019-01-07 bionic-oibaf-ppa)

```
And here's the output of xrandr:
```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 2560 x 1440, current 2560 x 1440, maximum 2560 x 1440
default connected primary 2560x1440+0+0 0mm x 0mm
   2560x1440     93.00*
```

My monitor is an Acer XG270HU, capable of 2560x1440 @ 144hz. However, under my displays window, it appears that my monitor is not properly detected, see attached.

[ATTACH=CONFIG]282155[/ATTACH]

I am not able to pick any other resolutions or refresh rates. I tried modifying "monitors.xml" but the changes didn't appear to take and were overwritten on the next reboot!

Can you help me to get my monitor correctly identified in the displays app so I can pick the right refresh rate? From the google searching I've done, I know the gamma error on xrandr is part of why the detection fails.Thanks!

---

### Post by Autodave on 2019-01-09
How is the monitor connected to the PC?

---

### Post by Mongoose088 on 2019-01-09
I have one montior connected to the RX 580 via a display port cable. My tweak setting is on compiz, but it is not on HiDPI. When i switched to HiDPI parts of my screen were cut off (overscan?) And i still couldn't  pick a better refresh rate.

EDIT: I tried to connect via HDMI to see if I could populate EDID info. No luck, it still shows as an unknown monitor. However, I do have the output of reading my edid:

```

sudo get-edid|parse-edid
This is read-edid version 3.0.2. Prepare for some fun.
Attempting to use i2c interface
No EDID on bus 0
No EDID on bus 1
No EDID on bus 2
No EDID on bus 3
Looks like no busses have an EDID. Sorry!
Attempting to use the classical VBE interface

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
	Function supported
	Call successful

	VBE version 300
	VBE string at 0xc0268 "AMD ATOMBIOS"

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

EDID claims 1 more blocks left


*********** Something special has happened!
This happens a lot with TV's, and other devices
with extension blocks. If you have a TV, don't bother.
Odds are good that I2C will work for you. Try 'modprobe i2c-dev'.
Otherwise, please contact the author, Matthew Kern
E-mail: pyrophobicman@gmail.com
Please include full output from this program (especially that to stderr)



Reading next EDID block

VBE/DDC service about to be called
	Read EDID

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
	Function supported
	Call successful

EDID claims 1 more blocks left
EDID blocks left is wrong.
Your EDID is probably invalid.
Looks like VBE was successful. Have a good day.
Checksum Correct

Section "Monitor"
	Identifier "XF270HU"
	ModelName "XF270HU"
	VendorName "ACR"
	# Monitor Manufactured week 51 of 2016
	# EDID version 1.4
	# Digital Display
	DisplaySize 600 340
	Gamma 2.20
	Option "DPMS" "true"
	Horizsync 222-222
	VertRefresh 40-144
	# Maximum pixel clock is 600MHz
	#Not giving standard mode: 1152x864, 75Hz
	#Not giving standard mode: 1280x960, 60Hz
	#Not giving standard mode: 1280x1024, 60Hz
	#Not giving standard mode: 1280x720, 60Hz
	#Not giving standard mode: 1280x800, 60Hz
	#Not giving standard mode: 1440x900, 60Hz
	#Not giving standard mode: 1680x1050, 60Hz
	#Not giving standard mode: 1920x1080, 60Hz

	#Extension block found. Parsing...
I only know about extension blocks of type 02h. PLEASE email me!
Something strange happened. Please contact the author,
Matthew Kern at <pyrophobicman@gmail.com>

```

My apologizes as well, the monitor is actually an XF270HU. By the VBE method, it clearly detects an Acer with a capability of 144 hz! How can I get Mate to understand this as well?

---

