---
title: "Nvidia/Compiz - Transparent terminals and window decorators refresh problem"
date: 2008-11-25
forum: General Help
---

### Post by Aviopene on 2008-11-25
Hi everybody,

I'm new to this forum, but I'm not new to compiz oddities.

My problem is shown here:

[IMG]http://i36.tinypic.com/2l8822c.png[/IMG]

and here...

[IMG]http://i37.tinypic.com/2mh9168.png[/IMG]

In practice, my transparent terminals (every kind of transparent terminal) sometimes refresh this way. And so my window decorators do.

But every other "normal" window (even if made transparent with «opacity» compiz plugin) doesn't. All of this with nvidia drivers 177.80 or 173.14, and with hardy or intrepid without distinction.

I don't think that this strange behaviour can be due to hardware problems, but I didn't try any video stress test program for linux.

Any ideas?

My lspci:

```
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 248 (1250ns min, 250ns max)
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at de000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at e0000000 (32-bit, prefetchable) [size=256M]
	Region 2: Memory at dd000000 (32-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at dffe0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidiafb, nvidia

```

My xorg.conf:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon RV200 QW [Radeon 7500]"
	Monitor		"SyncMaster"
	SubSection "Display"
		Depth	1
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	#Option		"AddARGBGLXVisuals"		"True"
	Option		"RenderAccel"	"true"
	Option		"XAANoOffscreenPixmaps"	"1"
	Option		"AllowGLXWithComposite"	"true"
	Option		"BackingStore"	"true"
	Option		"TripleBuffer"	"true"
	Option		"Coolbits"	"1"
	Option		"DisableGLXRootClipping"	"True"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon RV200 QW [Radeon 7500]"
	Driver		"nvidia"
	Option		"XAANoOffscreenPixmaps"	"1"
	Busid		"PCI:1:0:0"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"it"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/wacom"# Change to 
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
	# /dev/input/event
	# for USB
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/wacom"# Change to 
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
	# /dev/input/event
	# for USB
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/wacom"# Change to 
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
	# /dev/input/event
	# for USB
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	#Option		"AIGLX"	"true"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	#Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"type1"
	Load		"vbe"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

Section "Files"
	Fontpath	"/usr/share/X11/fonts/misc"
	Fontpath	"/usr/share/X11/fonts/cyrillic"
	Fontpath	"/usr/share/X11/fonts/100dpi/:unscaled"
	Fontpath	"/usr/share/X11/fonts/75dpi/:unscaled"
	Fontpath	"/usr/share/X11/fonts/Type1"
	Fontpath	"/usr/share/X11/fonts/100dpi"
	Fontpath	"/usr/share/X11/fonts/75dpi"
	Fontpath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

```

Sorry for that «ATI Technologies bla bla»... I had a radeon until a few months ago, and I'm quite lazy :P

Thanks to all
Avio

---

