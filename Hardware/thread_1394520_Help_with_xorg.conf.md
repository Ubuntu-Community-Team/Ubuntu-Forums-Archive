---
title: "Help with xorg.conf"
date: 2010-01-30
forum: Hardware
---

### Post by mcgeek on 2010-01-30
I have an old Dell Inspiron 5000e laptop I just intalled KK on. I was going to use this for a digital picture frame. The only thing is the video is messed up. The native display resolution is 1400x1050 and the best I can get is 800x600. From what I can glean I need to use a vesa driver for this chip set and display. Looking at other posts I have created a new xorg.conf file by running X -configure. I'm just not sure how to edit this file to get the display to work properly. See xorg.conf below.

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dri2"
	Load  "glx"
	Load  "dri"
	Load  "record"
	Load  "dbe"
	Load  "extmod"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "Dac8Bit"            	# [<bool>]
        #Option     "DMAForXv"           	# [<bool>]
        #Option     "ForcePCIMode"       	# [<bool>]
        #Option     "CCEPIOMode"         	# [<bool>]
        #Option     "CCENoSecurity"      	# [<bool>]
        #Option     "CCEusecTimeout"     	# <i>
        #Option     "AGPMode"            	# <i>
        #Option     "AGPSize"            	# <i>
        #Option     "RingSize"           	# <i>
        #Option     "BufferSize"         	# <i>
        #Option     "EnablePageFlip"     	# [<bool>]
        #Option     "Display"            	# <str>
        #Option     "PanelWidth"         	# <i>
        #Option     "PanelHeight"        	# <i>
        #Option     "ProgramFPRegs"      	# [<bool>]
        #Option     "UseFBDev"           	# [<bool>]
        #Option     "VideoKey"           	# <i>
        #Option     "ShowCache"          	# [<bool>]
        #Option     "VGAAccess"          	# [<bool>]
	Identifier  "Card0"
	Driver      "r128"
	VendorName  "ATI Technologies Inc"
	BoardName   "Rage Mobility M3 AGP 2x"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

Thanks in advance for any advice.

---

### Post by Yellow Pasque on 2010-01-31
Can you post/pastebin your /var/log/Xorg.0.log?

---

### Post by mcgeek on 2010-01-31
Here you go.

/var/log/xorg.0.log

```
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux xxxxxxxx 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-17-generic root=UUID=xxxxxxxxxxxxxx ro quiet splash
Build Date: 14 November 2009  05:48:26PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jan 31 08:52:48 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "X.org Configured"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Card0"
(**) |-->Input Device "Mouse0"
(**) |-->Input Device "Keyboard0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(**) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Mouse0
(WW) Disabling Keyboard0
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:1:0:0) 1002:4c46:1028:00cc ATI Technologies Inc Rage Mobility M3 AGP 2x rev 2, Mem @ 0xf8000000/67108864, 0xf4100000/16384, I/O @ 0x00002000/256, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "r128"
(II) Loading /usr/lib/xorg/modules/drivers//r128_drv.so
(II) Module r128: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 6.8.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) R128: Driver for ATI Rage 128 chipsets:
	ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
	ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
	ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
	ATI Rage 128 Pro GL PC (PCI/AGP), ATI Rage 128 Pro GL PD (PCI),
	ATI Rage 128 Pro GL PE (PCI/AGP), ATI Rage 128 Pro GL PF (AGP),
	ATI Rage 128 Pro VR PG (PCI/AGP), ATI Rage 128 Pro VR PH (PCI/AGP),
	ATI Rage 128 Pro VR PI (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
	ATI Rage 128 Pro VR PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
	ATI Rage 128 Pro VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
	ATI Rage 128 Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
	ATI Rage 128 Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
	ATI Rage 128 Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
	ATI Rage 128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
	ATI Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
	ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
	ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
	ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (PCI/AGP),
	ATI Rage 128 4X SF (PCI/AGP), ATI Rage 128 4X SG (PCI/AGP),
	ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128 4X SK (PCI/AGP),
	ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM (AGP),
	ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
	ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
	ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
	ATI Rage 128 Pro ULTRA TU (AGP?)
(II) Primary Device is: PCI 01@00:00:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) R128(0): PCI bus 1 card 0 func 0
(==) R128(0): Depth 24, (--) framebuffer bpp 32
(II) R128(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) R128(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) R128(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) R128(0): RGB weight 888
(II) R128(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) R128(0): initializing int10
(II) R128(0): Primary V_BIOS segment is: 0xc000
(--) R128(0): Chipset: "ATI Rage 128 Mobility M3 LF (AGP)" (ChipID = 0x4c46)
(--) R128(0): Linear framebuffer at 0xf8000000
(--) R128(0): MMIO registers at 0xf4100000
(--) R128(0): VideoRAM: 16384 kByte (128-bit SDR SGRAM 1:1)
(**) R128(0): Using flat panel for display
(II) R128(0): Primary Display == Type 2
(II) R128(0): Panel size: 1400x1050
(II) R128(0): Panel ID: IBM ITSX93              
(II) R128(0): Panel Type: Color, Single, TFT
(II) R128(0): Panel Interface: LVDS
(II) R128(0): PLL parameters: rf=2700 rd=60 min=12500 max=25000; xclk=10500
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) R128(0): VESA BIOS detected
(II) R128(0): VESA VBE Version 2.0
(II) R128(0): VESA VBE Total Mem: 16384 kB
(II) R128(0): VESA VBE OEM: ATI MOBILE M3
(II) R128(0): VESA VBE OEM Software Rev: 1.0
(II) R128(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) R128(0): VESA VBE OEM Product: M3  
(II) R128(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) R128(0): VESA VBE DDC supported
(II) R128(0): VESA VBE DDC Level none
(II) R128(0): VESA VBE DDC transfer in appr. 2 sec.
(II) R128(0): VESA VBE DDC read failed
(==) R128(0): Using gamma correction (1.0, 1.0, 1.0)
(II) R128(0): Monitor0: Using default hsync range of 31.50-37.90 kHz
(II) R128(0): Monitor0: Using default vrefresh range of 50.00-70.00 Hz
(WW) R128(0): Unable to estimate virtual size
(II) R128(0): Clock range:  12.50 to 250.00 MHz
(II) R128(0): Not using default mode "640x350" (vrefresh out of range)
(II) R128(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "640x400" (vrefresh out of range)
(II) R128(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "720x400" (no mode of this name)
(II) R128(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "640x480" (vrefresh out of range)
(II) R128(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "640x480" (vrefresh out of range)
(II) R128(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "640x480" (hsync out of range)
(II) R128(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1152x864" (no mode of this name)
(II) R128(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1280x960" (no mode of this name)
(II) R128(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1280x960" (no mode of this name)
(II) R128(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1280x1024" (hsync out of range)
(II) R128(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1280x1024" (hsync out of range)
(II) R128(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1280x1024" (hsync out of range)
(II) R128(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1600x1200" (no mode of this name)
(II) R128(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1600x1200" (no mode of this name)
(II) R128(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1600x1200" (no mode of this name)
(II) R128(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1600x1200" (no mode of this name)
(II) R128(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1600x1200" (no mode of this name)
(II) R128(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1792x1344" (no mode of this name)
(II) R128(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1856x1392" (no mode of this name)
(II) R128(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1920x1440" (no mode of this name)
(II) R128(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "832x624" (no mode of this name)
(II) R128(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1152x864" (no mode of this name)
(II) R128(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1152x864" (no mode of this name)
(II) R128(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1152x864" (no mode of this name)
(II) R128(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1152x864" (no mode of this name)
(II) R128(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1152x864" (no mode of this name)
(II) R128(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1152x864" (no mode of this name)
(II) R128(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1360x768" (no mode of this name)
(II) R128(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1360x768" (no mode of this name)
(II) R128(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1400x1050" (hsync out of range)
(II) R128(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1400x1050" (hsync out of range)
(II) R128(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1400x1050" (hsync out of range)
(II) R128(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1400x1050" (hsync out of range)
(II) R128(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1440x900" (no mode of this name)
(II) R128(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1600x1024" (no mode of this name)
(II) R128(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1680x1050" (no mode of this name)
(II) R128(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1680x1050" (no mode of this name)
(II) R128(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1680x1050" (no mode of this name)
(II) R128(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1680x1050" (no mode of this name)
(II) R128(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1680x1050" (no mode of this name)
(II) R128(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1920x1080" (no mode of this name)
(II) R128(0): Not using default mode "960x540" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1920x1200" (no mode of this name)
(II) R128(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) R128(0): Modifying mode according to VBIOS: 800x600 [pclk 40.0 MHz] for FP to: 800x600 [pclk 108.0 MHz]
(II) R128(0): Modifying mode according to VBIOS: 800x600 [pclk 36.0 MHz] for FP to: 800x600 [pclk 108.0 MHz]
(II) R128(0): Modifying mode according to VBIOS: 640x480 [pclk 25.2 MHz] for FP to: 640x480 [pclk 108.0 MHz]
(--) R128(0): Virtual size is 800x600 (pitch 800)
(**) R128(0): *Default mode "800x600": 108.0 MHz (scaled from 40.0 MHz), 37.9 kHz, 60.3 Hz
(II) R128(0): Modeline "800x600"x60.3  108.00  800 848 862 1088  600 600 603 616 +hsync +vsync (37.9 kHz)
(**) R128(0): *Default mode "800x600": 108.0 MHz (scaled from 36.0 MHz), 35.2 kHz, 56.2 Hz
(II) R128(0): Modeline "800x600"x56.2  108.00  800 848 862 1088  600 600 603 616 +hsync +vsync (35.2 kHz)
(**) R128(0): *Default mode "640x480": 108.0 MHz (scaled from 25.2 MHz), 31.5 kHz, 59.9 Hz
(II) R128(0): Modeline "640x480"x59.9  108.00  640 688 702 928  480 480 483 496 -hsync -vsync (31.5 kHz)
(==) R128(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.2.1
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "shadowfb"
(II) LoadModule: "shadowfb"
(II) Loading /usr/lib/xorg/modules//libshadowfb.so
(II) Module shadowfb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) R128(0): Page flipping disabled
(!!) R128(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] loaded kernel module for "r128" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) R128(0): [drm] Using the DRM lock SAREA also for drawables.
(II) R128(0): [drm] framebuffer handle = 0xf8000000
(II) R128(0): [drm] added 1 reserved context for kernel
(II) R128(0): X context handle = 0x1
(II) R128(0): [drm] installed DRM signal handler
(II) R128(0): [agp] Mode 0x1f000201 [AGP 0x8086/0x7190; Card 0x1002/0x4c46]
(II) R128(0): [agp] 8192 kB allocated with handle 0x00000001
(II) R128(0): [agp] ring handle = 0xe0000000
(II) R128(0): [agp] Ring mapped at 0xb7772000
(II) R128(0): [agp] ring read ptr handle = 0xe0101000
(II) R128(0): [agp] Ring read ptr mapped at 0xb7887000
(II) R128(0): [agp] vertex/indirect buffers handle = 0xe0102000
(II) R128(0): [agp] Vertex/indirect buffers mapped at 0xb6526000
(II) R128(0): [agp] AGP texture map handle = 0xe0302000
(II) R128(0): [agp] AGP Texture map mapped at 0xb6046000
(II) R128(0): [drm] register handle = 0xf4100000
(II) R128(0): [dri] Visual configs initialized
(II) R128(0): CCE in BM mode
(II) R128(0): Using 8 MB AGP aperture
(II) R128(0): Using 1 MB for the ring buffer
(II) R128(0): Using 2 MB for vertex/indirect buffers
(II) R128(0): Using 5 MB for AGP textures
(II) R128(0): Memory manager initialized to (0,0) (800,2457)
(II) R128(0): Reserved area from (0,600) to (800,602)
(II) R128(0): Largest offscreen area available: 800 x 1855
(II) R128(0): Reserved back buffer from (0,602) to (800,1202)
(II) R128(0): Reserved depth buffer from (0,1202) to (800,1803)
(II) R128(0): Reserved depth span from (0,1802) offset 0x57fd00
(II) R128(0): Reserved 8704 kb for textures at offset 0x77f880
(II) R128(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Dashed Lines
	Setting up tile and stipple cache:
		30 128x128 slots
(II) R128(0): Acceleration enabled
(==) R128(0): Backing store disabled
(==) R128(0): Silken mouse enabled
(II) R128(0): Using hardware cursor (scanline 7212)
(II) R128(0): Largest offscreen area available: 800 x 651
(II) R128(0): DPMS enabled
(II) R128(0): [DRI] installation complete
(II) R128(0): [drm] Added 128 16384 byte vertex/indirect buffers
(II) R128(0): [drm] Mapped 128 vertex/indirect buffers
(II) R128(0): [drm] dma control initialized, using IRQ 11
(II) R128(0): Direct rendering enabled
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: Loaded and initialized /usr/lib/dri/r128_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) config/hal: Adding input device Sleep Button
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event2"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event6"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/hal: Adding input device B16_b_02 USB-PS/2 Optical Mouse
(**) B16_b_02 USB-PS/2 Optical Mouse: always reports core events
(**) B16_b_02 USB-PS/2 Optical Mouse: Device: "/dev/input/event5"
(II) B16_b_02 USB-PS/2 Optical Mouse: Found 12 mouse buttons
(II) B16_b_02 USB-PS/2 Optical Mouse: Found x and y relative axes
(II) B16_b_02 USB-PS/2 Optical Mouse: Found scroll wheel(s)
(II) B16_b_02 USB-PS/2 Optical Mouse: Configuring as mouse
(**) B16_b_02 USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
(**) B16_b_02 USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "B16_b_02 USB-PS/2 Optical Mouse" (type: MOUSE)
(**) B16_b_02 USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1
(**) B16_b_02 USB-PS/2 Optical Mouse: (accel) filter chain progression: 2.00
(**) B16_b_02 USB-PS/2 Optical Mouse: (accel) filter stage 0: 20.00 ms
(**) B16_b_02 USB-PS/2 Optical Mouse: (accel) set acceleration profile 0
(II) B16_b_02 USB-PS/2 Optical Mouse: initialized for relative axes.
```

---

### Post by JonFen on 2010-05-31
I have the same laptop and the same problems with 10.04.  :(

JonFen

---

### Post by efflandt on 2010-05-31
What does **xrandr** show, and have you tried using xrandr to temporarily set your native resolution?  Note that is not permanent, it reverts to defaults when you log out of X.

You could find a modeline with **cvt 1400 1050** or **gtf 1400 1050 60**.

See [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

