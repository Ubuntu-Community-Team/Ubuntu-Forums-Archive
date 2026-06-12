---
title: "display problems hardy- intel 945GME - xorg.log gives a clue?"
date: 2009-07-16
forum: Hardware
---

### Post by zholistic on 2009-07-16
[FONT="Arial"]Diligently updating as always, at some time this week my xorg.conf file was reset to its plain state, resulting in my external display running at 1280x960 rather than its potential 1680x1050. System>Preferences>Screen Resolution does not show any other option than 1280x960 or 'off'. Clicking on the display icons in the box above results in my screen getting split and I can't find the windows title bars etc so I can't use them. I edited the xorg.conf file after the reset to the same state it was in, but although I no longer have a fuzzy screen I have a stretched out and less than sharp display.
My display is candela cplv20wdg1. Japanese maker, can't find any info on google than who's selling it.


To give a little history, I couldn't get my external display working properly on my Avertac 1000 (same as MSI Wind just a different name).
I edited the xorg.conf file as per various posts here and elsewhere, so it contained the following before the reset:[/FONT]

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"intel"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Horizsync	30.0	-	65.0
	Vertrefresh	60
	Displaysize	1680	1050
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
		Modes		"1680x1050"	"1280x1024"	"1024x768"	"800x600"	"640x480"
		#"1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

[FONT="Arial"]These modes are those detailed in the monitor manual.
When my xorg.conf was reset I added these back in, plus a little bit more so it looks like this (now):[/FONT]

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"intel"
	Option		"AccelMethod" "UXA"
	Option		"Tiling" "false"
	VideoRam 261632
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync     30.0 - 65.0 
        VertRefresh   60   
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth 24
SubSection "Display"
		Viewport    0 0
		Depth       24
		Modes "1680x1050"	"1280x1024"	"1024x768"	"800x600"	"640x480"
EndSubSection

[FONT="Arial"]
These modes are those specified in the manual.

lshw output shows:[/FONT]
 *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile 945GME Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0

[FONT="Arial"]lspci | grep VGA shows:[/FONT]

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)

[FONT="Arial"]lspci -vv shows:[/FONT]

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 0110
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at dfe80000 (32-bit, non-prefetchable) [size=512K]
	Region 1: I/O ports at d0f0 [size=8]
	Region 2: Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Region 3: Memory at dff00000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 0110
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Region 0: Memory at dfe00000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

[FONT="Arial"]So when my xorg.conf was reset, I followed advice to run
sudo gksu displayconfig-gtk
which I did. Despite the selected configurations not testing properly, it appears they were saved to the xorg.conf file as below. This completely screwed my display, both onboard and external, so I had to reset xorg.conf manually. The following is the stuff added through displayconfig-gtk and listed below the info I gave above.[/FONT]

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" #   
	Identifier	"device1"
	Boardname	"VESA driver (generic)"
	Busid		"PCI:0:2:0"
	Driver		"vesa"
	Screen	1
EndSection
Section "screen" #   
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"800x600@60"	"1024x768@60"	"800x600@56"	"1280x960@60"	"640x480@60"	"1280x1024@60"
	EndSubSection
EndSection
Section "monitor" #   
	Identifier	"monitor1"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x1024"
	Horizsync	31.5-64.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	Gamma	1.0
EndSection
Section "device" #   
	Identifier	"device2"
	Boardname	"VESA driver (generic)"
	Busid		"PCI:0:2:1"
	Driver		"vesa"
	Screen	0
EndSection
Section "screen" #   
	Identifier	"screen2"
	Device		"device2"
	Defaultdepth	24
	Monitor		"monitor2"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"
	EndSubSection
EndSection
Section "monitor" #   
	Identifier	"monitor2"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
Section "device" #  
	Identifier	"device3"
	Boardname	"VESA driver (generic)"
	Busid		"PCI:0:2:0"
	Driver		"vesa"
	Screen	0
EndSection
Section "screen" #  
	Identifier	"screen3"
	Device		"device3"
	Defaultdepth	24
	Monitor		"monitor3"
	SubSection "Display"
		Depth	24
		Virtual	1280	1024
		Modes		"1024x768@60"	"1280x960@60"	"800x600@60"	"1280x1024@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection
Section "monitor" #  
	Identifier	"monitor3"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x1024"
	Horizsync	31.5-64.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	Gamma	1.0
EndSection

[FONT="Arial"]Now, that bit's all gone. I had a look at  /var/log/Xorg.O.log:
[/FONT]

drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) intel(0): Setting screen physical size to 277 x 208
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event7
(**) Option "Device" "/dev/input/event7"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event7
(**) Option "Device" "/dev/input/event7"
(--) Synaptics Touchpad touchpad found
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): EDID vendor "DIC", prod id 8369
(II) intel(0): EDID vendor "CPT", prod id 1220
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1072 1104 1200  600 603 609 625 -hsync -vsync (37.5 kHz)
(II) intel(0): EDID vendor "CPT", prod id 1220
(II) intel(0): EDID vendor "DIC", prod id 8369
(II) intel(0): EDID vendor "CPT", prod id 1220
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1072 1104 1200  600 603 609 625 -hsync -vsync (37.5 kHz)
(II) intel(0): EDID vendor "CPT", prod id 1220
(II) intel(0): EDID vendor "DIC", prod id 8369
(II) intel(0): EDID vendor "CPT", prod id 1220
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1072 1104 1200  600 603 609 625 -hsync -vsync (37.5 kHz)
(II) intel(0): EDID vendor "CPT", prod id 1220
(II) intel(0): EDID vendor "DIC", prod id 8369
(II) intel(0): EDID vendor "CPT", prod id 1220
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1072 1104 1200  600 603 609 625 -hsync -vsync (37.5 kHz)
(II) intel(0): EDID vendor "CPT", prod id 1220
(II) intel(0): EDID vendor "DIC", prod id 8369
(II) intel(0): EDID vendor "CPT", prod id 1220
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1072 1104 1200  600 603 609 625 -hsync -vsync (37.5 kHz)
(II) intel(0): EDID vendor "CPT", prod id 1220
SetClientVersion: 0 9
(II) intel(0): EDID vendor "DIC", prod id 8369
(II) intel(0): EDID vendor "CPT", prod id 1220
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1072 1104 1200  600 603 609 625 -hsync -vsync (37.5 kHz)
(II) intel(0): EDID vendor "CPT", prod id 1220
(II) intel(0): EDID vendor "DIC", prod id 8369
(II) intel(0): EDID vendor "CPT", prod id 1220
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1072 1104 1200  600 603 609 625 -hsync -vsync (37.5 kHz)
(II) intel(0): EDID vendor "CPT", prod id 1220
(II) intel(0): EDID vendor "DIC", prod id 8369
(II) intel(0): EDID vendor "CPT", prod id 1220
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1072 1104 1200  600 603 609 625 -hsync -vsync (37.5 kHz)
(II) intel(0): EDID vendor "CPT", prod id 1220
(II) intel(0): EDID vendor "DIC", prod id 8369
(II) intel(0): EDID vendor "CPT", prod id 1220
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1072 1104 1200  600 603 609 625 -hsync -vsync (37.5 kHz)
(II) intel(0): EDID vendor "CPT", prod id 1220
(II) intel(0): EDID vendor "DIC", prod id 8369
(II) intel(0): EDID vendor "CPT", prod id 1220
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1072 1104 1200  600 603 609 625 -hsync -vsync (37.5 kHz)
(II) intel(0): EDID vendor "CPT", prod id 1220
SetClientVersion: 0 9
(II) intel(0): EDID vendor "DIC", prod id 8369
(II) intel(0): EDID vendor "CPT", prod id 1220
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1072 1104 1200  600 603 609 625 -hsync -vsync (37.5 kHz)
(II) intel(0): EDID vendor "CPT", prod id 1220
(II) intel(0): EDID vendor "DIC", prod id 8369
(II) intel(0): EDID vendor "CPT", prod id 1220
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1072 1104 1200  600 603 609 625 -hsync -vsync (37.5 kHz)
(II) intel(0): EDID vendor "CPT", prod id 1220


[FONT="Arial"]Are the bits about (WW) AIGLX: 3D driver claims to not support visual 0x23 to do with the ULX setting I edited in? (I don't claim to understand what that's about but it made sense on the walkthrough).

Also, the last lines about Modelines seem to be restricting the display, this looks something like the onboard display resolution, but doesn't correspond to the 1280x960 'default' setting I'm getting. Also, I noticed that these modelines give/set(?) information similar to that when I used displayconfig-gtk. 

So how come I don't have the options for resolution set in xorg.conf available in the screen resolution panel? 
Any ideas on how to get my display back to the best resolution again?

Many thanks.[/FONT]

---

