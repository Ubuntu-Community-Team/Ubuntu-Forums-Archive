---
title: "Display problem after upgrade: (EE) No devices detected"
date: 2009-04-01
forum: Installation &amp; Upgrades
---

### Post by paul_rubin on 2009-04-01
Hardware is a Dell Optiplex GX620 (Intel integrated graphics) + Dell 1908fp monitor, with no proprietary drivers installed.  It was working fine until I downloaded a system update today that required a reboot.  After the reboot, I got into the Gnome but with a goofy resolution (wrong aspect ratio among other things).  When I changed the screen resolution and logged out/in, I started getting the "no devices detected" error.

If I accept the "running low graphics mode" option, I get into X and the Gnome desktop ok, but at a higher resolution (1280x1024) than what I want.  When I use System > Preferences > Screen Resolution to reset the resolution, it lists the display as "unknown" with 0 Hz the only listed refresh rate, and "Detect Displays" does nothing.  The xorg.conf file shows the adapter and correct monitor (as best I can tell).  If I set a different resolution and then reboot, I'm back to low graphics mode, and when I get back to the desktop it is once again back to 1280x1024.

FWIW, here's the relevant part of xorg.conf:

```
Section "Device"
	Identifier	"Intel Corporation 82945G/GZ Integrated Graphics Controller"
	Driver		"i810"
#	BusID		"PCI:0:2:0"
#	BusID		"PCI:1:2:0"
	BusID		"PCI:0:2:1"
EndSection

Section "Monitor"
	Identifier	"DELL 1908FP"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82945G/GZ Integrated Graphics Controller"
	Monitor		"DELL 1908FP"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

```

Here's what lspci -v had to say:

```
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
	Subsystem: Dell Device 01ad
	Flags: fast devsel, IRQ 11
	Memory at feb00000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at e898 [size=8]
	Memory at e0000000 (32-bit, prefetchable) [size=256M]
	Memory at feac0000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [d0] Power Management version 2
	Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
	Subsystem: Dell Device 01ad
	Flags: bus master, fast devsel, latency 0
	Memory at feb80000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: [d0] Power Management version 2

```

The commented BusID lines in xorg.conf are me shooting from the hip trying to tell if a wrong id is what's causing the problem.

One last wrinkle:  a while back, I switched my monitor from the analog VGA connector to the digital connector.  I'm pretty sure but not positive that I rebooted the system after that and before today's adventures.

Can anybody point me to a possible fix?  I'm massively confused here.

TIA,
Paul

---

