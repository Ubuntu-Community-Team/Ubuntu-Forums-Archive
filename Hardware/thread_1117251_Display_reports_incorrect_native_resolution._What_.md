---
title: "Display reports incorrect native resolution. What can I do?"
date: 2009-04-05
forum: Hardware
---

### Post by mikehattingh on 2009-04-05
I have a 1080p HDTV. Wen I set the resolution to 1920x1080 the TV shows that it is getting a 1080p signal but the X display is larger than the screen.
If we look at System > Administration > Nvidia X server settings under GPU 0 > DFP 1 we see that the native resolution is 1680x1050 witch is incorrect.
The System > Administration > Sytem log > xorg.0.log says:
```

(**) NVIDIA(0): Option "MetaModes" "1920x1080 +0+0; 1680x1050 +0+0; nvidia-auto-select +0+0"
(**) NVIDIA(0): Enabling RENDER acceleration
(WW) NVIDIA(0): The EDID for ViewSonic N4285p (DFP-1) contradicts itself: mode
(WW) NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
(WW) NVIDIA(0):     valid HorizSync range (30.000-82.000 kHz) would exclude
(WW) NVIDIA(0):     this mode's HorizSync (28.1 kHz); ignoring HorizSync check
(WW) NVIDIA(0):     for mode "1920x1080".
(II) NVIDIA(0): Assigned Display Device: DFP-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1920x1080+0+0"
(II) NVIDIA(0):     "1680x1050+0+0"
(II) NVIDIA(0):     "nvidia-auto-select+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
(--) NVIDIA(0): DPI set to (52, 51); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): 
(II) NVIDIA(0): Setting mode "1920x1080+0+0"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
AUDIT: Sun Apr  5 13:44:16 2009: 16174 X: client 4 rejected from local host ( uid=0 gid=0 pid=16196 )
(II) NVIDIA(0): Setting mode "1920x1080_50i"

```

I have no idea why nvidia is setting the mode to 1080_i_ after a restart of X but I'll worry about that later.

get-edid | parse-edid says:
```

get-edid: get-edid version 1.4.1

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
	Function supported
	Call successful

	VBE version 300
	VBE string at 0x11110 "NVIDIA"

VBE/DDC service about to be called
	Report DDC capabilities

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
	Function supported
	Call successful

	Monitor and video card combination does not support DDC1 transfers
	Monitor and video card combination does not support DDC2 transfers
	0 seconds per 128 byte EDID block transfer
	Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
	Read EDID

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
	Function supported
	Call failed

The EDID data should not be trusted as the VBE call failed
Error: output block unchanged
parse-edid: IO error reading EDID

```

If I use parse-edid on the edid file obtained from Nvidia X server settings > DFP1, it says:
```

mike@mike-AV:~$ sudo parse-edid //home/mike/Desktop/edid.bin 
parse-edid: parse-edid version 1.4.1
parse-edid: EDID checksum passed.

	# EDID version 1 revision 3
Section "Monitor"
	# Block type: 2:0 3:ff
	# Block type: 2:0 3:fd
	# Block type: 2:0 3:fc
	Identifier "N4285p"
	VendorName "VSC"
	ModelName "N4285p"
	# Block type: 2:0 3:ff
	# Block type: 2:0 3:fd
	HorizSync 30-82
	VertRefresh 50-75
	# Max dot clock (video bandwidth) 170 MHz
	# Block type: 2:0 3:fc
	# DPMS capabilities: Active off:yes  Suspend:no  Standby:no

	Mode 	"1680x1050"	# vfreq 59.954Hz, hfreq 65.290kHz
		DotClock	146.250000
		HTimings	1680 1784 1960 2240
		VTimings	1050 1053 1059 1089
		Flags	"+HSync" "-VSync"
	EndMode
	# Block type: 2:0 3:ff
	# Block type: 2:0 3:fd
	# Block type: 2:0 3:fc
EndSection

```

From What I can tell the display is reporting, incorrectly, that it is a 1680x1050. There is the option of referring to a saved edid file with the correct information in it, but I don't know what that information would look like, and I don't know how to generate that file. On the other hand maybe I'm on the wrong track, is there a better way to deal with this problem?

---

