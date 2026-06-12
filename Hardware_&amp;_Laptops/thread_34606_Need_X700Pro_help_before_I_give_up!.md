---
title: "Need X700Pro help before I give up!"
date: 2005-05-15
forum: Hardware &amp; Laptops
---

### Post by GazaM on 2005-05-15
OK, for a start here's my exact system specs:

**Motherboard** MSI K8N Neo4 Platinum
**CPU** AMD Athlon64 3200+
**Graphics** Sapphire ATI Radeon X700Pro PCI-E
**Monitor** BenQ FP937s 19" LCD DVI

Ok, so I've been trying Ubuntu for a few weeks now as a first linux distro, mostly it's been a very hard fight to get everything working properly and it's still not 100%. I never expected it to be easy as my hardware is very new, but getting 3d acceleration has proven simply impossible! I have, without exaggerating, followed **every** single guide I could find on the internet to get the fglrx drivers working in ubuntu and linux in generel, with no succes other than getting the gui to startup using MESA coming up when I type 'fglrxinfo' in the command line, with no 3d acceleration and getting a measly 200-300fps in glx-gears. I'm 16 so gaming is obviously something I want to do sometimes, and since Enemy Territory is by far my most played Windows game I would love to switch to linux completely if I could just get my card working! I am trying to use the latest ATI drivers which I got by following a guide on these forums to overwrite the ones from the ubuntu repository. I need help! If anyone could post their working xorg.conf file (if youhave an X700 PCI-E of course :roll: ), or post the steps needed to make it work, or IM me or email me I would be very greatful!

---

### Post by GazaM on 2005-05-16
please, surely somebody has some type of advice?

---

### Post by guX on 2005-05-16
Come on! Somebody help this guy! I have very similar problems, only I have an x850xt PE.

---

### Post by GazaM on 2005-05-17
Still no answers! Surely somebody can help! I'll post my xorg.conf and xorg.log later, maybe that will help. One other thing, I have noticed that fglrxconfig can't autodetect my card, but normal 'dpkg-reconfigure xserver-xorg' can, although it still won't get fglrx working properly, so I figured that it probably can't detect the ChipID, which I think it needs to run the OpenGL accelleration specific to the card, so I went onto the sourceforge ATI ChipID page, but the only mention of an X700 was the mobility, so I booted Windows XP and went into the Catalyst Control Center and went to the details and got my ChipID for the X700Pro (5E4B if anyone wants to know). I then went back to the xorg.conf and put in the line:

ChipId     0x5E4B

That made things worse because when I rebooted it came up with some other error, I'll post that later as well. If the ChipId line syntax was wrong could someone please tell me the correct way of doing it?

---

### Post by guX on 2005-05-17
Anyone...?

---

### Post by Jarz Corp on 2005-05-19
Okay guys post some log files, there are no psycics in this forum, so to save U time and to help the helpers helping U, give us something to work with.

---

### Post by fargusmax on 2005-05-23
I managed to get my PCI-E X850XT to work with Ubuntu by adding a line to the device section of my xorg.conf.  I don't know if it'll work for anyone else, but it got me out of vesa hell on my desktop.

New Device Section:

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon X850 XT (R480)"
        Driver          "fglrx"
        BusID           "PCI:5:0:0"
        ChipId          0x5548
EndSection

Hope this might help some out there with PCI-E ATI cards!

Rob

edit:  After re-reading, it occurred to me that I did not specify what line I added.  I added the "ChipId" line in order to get X to start with the fglrx drivers.  Also, I used the fglrx drivers that "came" with 5.04, I ie, 8.8.something.

---

### Post by GazaM on 2005-05-26
Thanks, but I already new about the chipid line and have that in my xorg.conf. If anybody has a fully working xorg.conf for any of the X-series of radeon cards could you please post them. Here is a log file from my last black screen(minus pci scan as it takes up way too many characters making my post invalid).

> 
X Window System Version 6.8.2 (Ubuntu 6.8.2-10 20050405154308 [email]root@terranova.warthogs.hbd.com[/email])
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux ubuntu1 2.6.10-5-686 #1 Fri May 20 14:31:01 UTC 2005 i686
Build Date: 05 April 2005
	Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.10-5-686 (buildd@rothera) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Fri May 20 14:31:01 UTC 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu May 26 15:41:55 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "ATI Technologies, Inc. Radeon X700 Pro (RV410)"
(**) |-->Input Device "Generic Keyboard"
(**) Option "XkbRules" "xorg"
(**) XKB: rules: "xorg"
(**) Option "XkbModel" "pc105"
(**) XKB: model: "pc105"
(**) Option "XkbLayout" "gb"
(**) XKB: layout: "gb"
(==) Keyboard: CustomKeycode disabled
(**) |-->Input Device "Configured Mouse"
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "unix/:7100,/usr/lib/X11/fonts/misc,/usr/lib/X11/fonts/100dpi/:unscaled,/usr/lib/X11/fonts/75dpi/:unscaled,/usr/lib/X11/fonts/Type1,/usr/lib/X11/fonts/100dpi,/usr/lib/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.7
	X.Org XInput driver : 0.4
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(removed)

(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "dbe"
(II) Loading /usr/X11R6/lib/modules/extensions/libdbe.a
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "dri"
(II) Loading /usr/X11R6/lib/modules/extensions/libdri.a
(II) Module dri: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/X11R6/lib/modules/linux/libdrm.a
(II) Module drm: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension FontCache
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/X11R6/lib/modules/fonts/libfreetype.a
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 6.8.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.a
(II) Module glx: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/X11R6/lib/modules/extensions/libGLcore.a
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "record"
(II) Loading /usr/X11R6/lib/modules/extensions/librecord.a
(II) Module record: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension RECORD
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "fglrx"
(II) Loading /usr/X11R6/lib/modules/drivers/fglrx_drv.o
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 6.8.0, module version = 8.12.10
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "keyboard"
(II) Loading /usr/X11R6/lib/modules/input/keyboard_drv.o
(II) Module keyboard: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) ATI Radeon/FireGL: The following chipsets are supported:
	(removed)
(II) Primary Device is: PCI 05:00:0
(--) Assigning device section with no busID to primary device
(WW) fglrx: No matching Device section for instance (BusID PCI:5:0:1) found
(**) ChipID override: 0x5E4B
(**) Chipset RADEON X700 PRO (RV410 5E4B) found
(II) resource ranges after xf86ClaimFixedResources() call:
	(removed)
(II) Setting vga for screen 0.
(II) fglrx(0): === [R200PreInit] === begin, [s]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) fglrx(0): PCI bus 5 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "MonitorLayout" "AUTO, AUTO"
(**) fglrx(0): Option "UseInternalAGPGART" "no"
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) fglrx(0): initializing int10
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(**) fglrx(0): Chipset: "RADEON X700 PRO (RV410 5E4B)" (Chipset = 0x5e4b)
(**) fglrx(0): (PciSubVendor = 0x174b, PciSubDevice = 0x0530)
(**) fglrx(0): board vendor info: third party grafics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xfe2f0000
(--) fglrx(0): ChipExtRevID = 0x00
(--) fglrx(0): ChipIntRevID = 0x01
(--) fglrx(0): VideoRAM: 131072 kByte (64-bit SDR SDRAM)
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Loading /usr/X11R6/lib/modules/libi2c.a
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(II) fglrx(0): I2C bus "DDC" initialized.
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
(II) fglrx(0): Connector Layout from BIOS -------- 
(II) fglrx(0): Connector0: DDCType-1, DACType-0, TMDSType--1, ConnectorType-2
(II) fglrx(0): Connector1: DDCType-2, DACType-1, TMDSType-0, ConnectorType-3
(**) fglrx(0): MonitorLayout Option: 
	Monitor1--Type AUTO, Monitor2--Type AUTO

(II) fglrx(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) fglrx(0): I2C device "DDC:ddc2" removed.
(II) fglrx(0): DDC detected on DDCType 2 with Monitor Type 3
(II) fglrx(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) fglrx(0): I2C device "DDC:ddc2" removed.
(II) fglrx(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) fglrx(0): I2C device "DDC:ddc2" removed.

---

### Post by GazaM on 2005-05-26
By the way, that is the full Xorg.0.log (besides the bits I manually removed, all just pci scans and lots of numbers). It ends abrubtly at the ddc section. Other log files I have end abrubtly at loading the fb module 'libfb.a'.

---

### Post by dorris on 2005-06-27
Hey, I'm also having trouble getting it to start, Glad I'm not the only one
Acer Travelmate 8103, with X700 mobility (Pci-Express)
Standard kernel, with exception to install option acpi=off and vga=771 (which might be affecting me badly??

Attached is Xorg.conf
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"GLcore"
	Load	"glx"
	Load	"dri"
	SubSection "extmod"
		Option "omit xfree86-dga"
	EndSubSection
	Load	"freetype"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
	Option		"UseInternalAGPGART"	"no"
	Option		"NoDDC"
	BusID		"PCI:1:0:0"
	Option		"BusType" "PCIE"
	ChipID		0x3150
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-90
	VertRefresh	50-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI"
	Monitor		"Generic Monitor"
	DefaultDepth	24

	SubSection "Display"
		Depth		1
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```
Theres a lot of extras I've put in from all over the place to try get it to work, but none help

---

### Post by rachii on 2005-06-27
i had a problem with mesa taking over after i would try and install the drivers, and then try and REINSTALL ubuntu, but it kept using mesa after i would reboot, and not the fglrx.  
i got it fixed though, and i think that it was because under /etc/modules, mesa* was listed, so i just removed that and made sure fglrx was in /etc/modules, and i was all set?

---

### Post by dorris on 2005-06-27
my logs contain the following data, could this be the problem???
I also forgot to mention I have a widescreen display, could that be what this is all about?

I get is a black screen (which is of course better than the blue one I used to get, be4 I tweaked xorg.conf-that one had too much similiarity to windows :) )
```


DAC Type  -- Primary
 TMDS Type -- NONE
 DDC Type  -- MONID
(II) fglrx(0): 
(II) fglrx(0): DesktopSetup 0x0000
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Overlay disabled
(**) fglrx(0): Overlay disabled
(II) fglrx(0): PLL parameters: rf=2700 rd=27 min=20000 max=50000
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Generic Monitor: Using hsync range of 30.00-90.00 kHz
(II) fglrx(0): Generic Monitor: Using vrefresh range of 50.00-60.00 Hz
(II) fglrx(0): Clock range:  20.00 to 500.00 MHz
(II) fglrx(0): Not using default mode "640x350" (vrefresh out of range)
(II) fglrx(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "640x400" (vrefresh out of range)
(II) fglrx(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "720x400" (vrefresh out of range)
(II) fglrx(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "400x300" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "400x300" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "400x300" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "512x384" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "512x384" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "512x384" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "512x384" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "576x432" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x960" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x512" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x1024" (hsync out of range)
(II) fglrx(0): Not using default mode "640x512" (hsync out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (hsync out of range)
(II) fglrx(0): Not using default mode "800x600" (hsync out of range)
(II) fglrx(0): Not using default mode "1600x1200" (hsync out of range)
(II) fglrx(0): Not using default mode "800x600" (hsync out of range)
(II) fglrx(0): Not using default mode "1792x1344" (hsync out of range)
(II) fglrx(0): Not using default mode "896x672" (hsync out of range)
(II) fglrx(0): Not using default mode "1856x1392" (hsync out of range)
(II) fglrx(0): Not using default mode "928x696" (hsync out of range)
(II) fglrx(0): Not using default mode "1920x1440" (hsync out of range)
(II) fglrx(0): Not using default mode "960x720" (hsync out of range)
(II) fglrx(0): Not using default mode "832x624" (vrefresh out of range)
(II) fglrx(0): Not using default mode "416x312" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "576x432" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "700x525" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "700x525" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1400x1050" (hsync out of range)
(II) fglrx(0): Not using default mode "700x525" (hsync out of range)
(II) fglrx(0): Not using default mode "1920x1200" (hsync out of range)
(II) fglrx(0): Not using default mode "960x600" (hsync out of range)
(II) fglrx(0): Not using default mode "1920x1440" (hsync out of range)
(II) fglrx(0): Not using default mode "960x720" (hsync out of range)
(II) fglrx(0): Not using default mode "2048x1536" (hsync out of range)
(II) fglrx(0): Not using default mode "1024x768" (hsync out of range)
(II) fglrx(0): Not using default mode "2048x1536" (hsync out of range)
(II) fglrx(0): Not using default mode "1024x768" (hsync out of range)
(II) fglrx(0): Not using default mode "2048x1536" (hsync out of range)
(II) fglrx(0): Not using default mode "1024x768" (hsync out of range)
(II) fglrx(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) fglrx(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) fglrx(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) fglrx(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) fglrx(0): Not using default mode "1600x1200" (height too large for virtual size)
(--) fglrx(0): Virtual size is 1680x1050 (pitch 1728)
(**) fglrx(0): *Default mode "1680x1050": 147.1 MHz, 65.2 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1680x1050"  147.14  1680 1784 1968 2256  1050 1051 1054 1087
(**) fglrx(0):  Default mode "1400x1050": 122.0 MHz, 64.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1400x1050"  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(**) fglrx(0):  Default mode "1440x900": 108.8 MHz, 56.9 kHz, 60.2 Hz
(II) fglrx(0): Modeline "1440x900"  108.84  1440 1472 1880 1912  900 918 927 946 +hsync +vsync
(**) fglrx(0):  Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x960"  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync
(**) fglrx(0):  Default mode "1280x800": 83.5 MHz, 49.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"   83.46  1280 1344 1480 1680  800 801 804 828
(**) fglrx(0):  Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"   80.14  1280 1344 1480 1680  768 769 772 795
(**) fglrx(0):  Default mode "1152x768": 65.0 MHz, 44.2 kHz, 54.8 Hz
(II) fglrx(0): Modeline "1152x768"   65.00  1152 1178 1314 1472  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) fglrx(0):  Default mode "960x720": 117.0 MHz, 90.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "960x720"  117.00  960 1024 1128 1300  720 720 722 750 doublescan -hsync +vsync
(**) fglrx(0):  Default mode "928x696": 109.2 MHz, 86.4 kHz, 60.1 Hz (D)
(II) fglrx(0): Modeline "928x696"  109.15  928 976 1088 1264  696 696 698 719 doublescan -hsync +vsync
(**) fglrx(0):  Default mode "896x672": 102.4 MHz, 83.7 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "896x672"  102.40  896 960 1060 1224  672 672 674 697 doublescan -hsync +vsync
(**) fglrx(0):  Default mode "960x600": 96.6 MHz, 74.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "960x600"   96.58  960 1024 1128 1296  600 600 602 621 doublescan
(**) fglrx(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) fglrx(0):  Default mode "800x600": 81.0 MHz, 75.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "800x600"   81.00  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) fglrx(0):  Default mode "840x525": 73.6 MHz, 65.2 kHz, 60.1 Hz (D)
(II) fglrx(0): Modeline "840x525"   73.57  840 892 984 1128  525 525 527 543 doublescan
(**) fglrx(0):  Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "700x525"   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "640x512"   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "720x450": 54.4 MHz, 56.9 kHz, 60.2 Hz (D)
(II) fglrx(0): Modeline "720x450"   54.42  720 736 940 956  450 459 463 473 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) fglrx(0):  Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "640x480"   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "640x400"   41.73  640 672 740 840  400 400 402 414 doublescan
(**) fglrx(0):  Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(II) fglrx(0): Modeline "640x384"   40.07  640 672 740 840  384 384 386 397 doublescan
(**) fglrx(0):  Default mode "576x384": 32.5 MHz, 44.2 kHz, 54.8 Hz (D)
(II) fglrx(0): Modeline "576x384"   32.50  576 589 657 736  384 385 388 403 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "512x384"   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync
(**) fglrx(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) fglrx(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync
(==) fglrx(0): DPI set to (75, 75)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(

```

Any help would be appreciated

---

