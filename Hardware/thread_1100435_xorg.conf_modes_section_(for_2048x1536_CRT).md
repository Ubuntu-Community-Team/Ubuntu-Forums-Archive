---
title: "xorg.conf modes section? (for 2048x1536 CRT)"
date: 2009-03-19
forum: Hardware
---

### Post by dh003i on 2009-03-19
Hi all,

I have a Sony GDM-F520, which supports 2048x1536 at 75Hz; and 1920x1440, 1800x1440, 1600x1200 at 85Hz. 

How do I set these in the modes section? What about all that blanking stuff, doublescan, hsync, etc?

---

### Post by ebharv on 2009-03-19
Hit Alt+F2 or open terminal enter
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```This backs up you current .conf file just in case things get messed up even more.
Then do 
```
gksu gedit /etc/X11/xorg.conf
```Open you .conf file in gedit with administrative rights. Do a find for 'Section "Screen"' without single quotes. 
On the line before EndSection do this.
```

SubSection "Display"
        Depth        24
        Modes       "2048x1536" "1920x1440" "1800x1440" "1600x1200"
EndSubSection

```Save and restart X server  logging out or Ctrl+Alt+Backspace.

As of late I have been having problems with Ubuntu keeping the changes on my xorg.conf file after a manual edit, so I don't know if the file will remain intact for you after a reboot. 

I'm not sure but I think running this command:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```after editing the xorg.conf file should make ubuntu use it after a reboot. I'm not at my machine right now so I can't test it. There is more about the command in the .conf file. just do a find for "dpkg -reconfigure".

---

### Post by dh003i on 2009-03-19
Thanks, I'll try that...but what about setting the refresh rates? (this is a CRT, so getting the highest refresh rate without going beyond specs is important).

---

### Post by dh003i on 2009-03-20
> **ebharv said:**
> As of late I have been having problems with Ubuntu keeping the changes on my xorg.conf file after a manual edit, so I don't know if the file will remain intact for you after a reboot. 

I'm not sure but I think running this command:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```after editing the xorg.conf file should make ubuntu use it after a reboot. I'm not at my machine right now so I can't test it. There is more about the command in the .conf file. just do a find for "dpkg -reconfigure".

Ok, I have the same problem. After a reboot, Kubuntu replaces the new xorg.conf I made with an almost empty one! (presumably for that autodetect junk). Typing [COLOR="Lime"][COLOR="DarkRed"]sudo dpkg -reconfigure -phigh xserver-xorg[/COLOR][/COLOR] does the same thing (replaces my current xorg.conf file with whatever Kubuntu thinks it should be). 

How do I get the changes to stick?

Btw, here's my xorg.conf, does this look good?

```
Section	"Device"
	Identifier	"ATI Radeon HD4670"
	Driver		"radeonhd"
	Option		"AccelMethod" "exa"	# default shadowfb ; turn off if cause problems; experimental in HEAD radeonhd
	Option		"DRI" "on"		# turn off if cause problems; experimental in HEAD radeonhd
EndSection

Section	"Monitor"
	Identifier	"Sony GDM-F520"
	VendorName	"Sony"
	ModelName	"GDM-F520"
	HorizSync	30-137kHz					# units in kHz by default
	VertRefresh	48-170Hz					# units in Hz by default
	DisplaySize	406 303 					# specified in x y millimeters
	# Gamma		1.0						# specifies gamma
	# Gamma		1.0 1.0 1.0					# red green blue gammas
	UseModes	"Modes GDM-F520"				# make modes listed in Mode : modesection-id available for this monitor
	# Mode name							# provide definitions for video modes for monitor
		# DotClock	clock					# dot (pixel) clock rate to be used for mode
		# HTimings	hdisp hsyncstart hsyncend htotal	# horizontal timings for mode
		# VTimings	vdisp vsyncstart vcyncend vtotal	# vertical timings for mode
		# Flags		flag					# optional set of mode flags, each with a separate string in double-quotes
		# HSkew		hskew					# number of pixels towards right edge of screen by which display enable signal is to be skewed
		# VScan		vsacn					# number times each scanline is painted on the screen; 1 is default; DoubleScan Flag doubles this value
	# Option	TargetRefresh rate				# target vertical refresh rate when selecting video modes
	# Option	Position x y					# position of monitor within X screen
	# Option	LeftOf output					# monitor should be positioned to the left of the output (not monitor) of a given name
	Option		MinClock 23.86					# minimum dot clock (kHz) supported by monitor
	Option		MaxClock 388.04					# maximum dot clock (kHz) supported by monitor
	Option		Rotate normal					# valid values normal, left, right, inverted
	Option		PreferredMode "2048x1536_75.00"			# specifies a mode to be marked as the preferred initial mode of the monitor
EndSection

Section	"Modes"
      Identifier	"Modes for GDM-F520"
	#					Dotclock; hdisp, hsyncstart, hsyncend, htotal; vdisp, vsyncstart, vsyncend, vtotal
	# 9:5 ASPECT RATIO SETTINGS (slightly longer than 16:9)
	# Modlin 	"XxY_Refresh"		Dotclc	hdsp hsys hsye htot  vdsp vsys vsye vtot
	Modeline	"720x400_70.00"		26.15   720  736  808  896   400  401  404  417   -HSync +Vsync	# 720x400 @ 70.00 Hz (GTF) hsync: 29.19 kHz; pclk: 26.15 MHz
	Modeline	"720x400_85.00"		32.64   720  744  816  912   400  401  404  421   -HSync +Vsync	# 720x400 @ 85.00 Hz (GTF) hsync: 35.78 kHz; pclk: 32.64 MHz
	# 5:4 ASPECT RATIO SETTINGS
	# Modlin 	"XxY_Refresh"		Dotclc	hdsp hsys hsye htot  vdsp vsys vsye vtot
	Modeline	"1280x1024_60.00"	108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync	# 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
	Modeline	"1280x1024_75.00"	138.54  1280 1368 1504 1728  1024 1025 1028 1069  -HSync +Vsync	# 1280x1024 @ 75.00 Hz (GTF) hsync: 80.17 kHz; pclk: 138.54 MHz
	Modeline	"1280x1024_85.00"	159.36  1280 1376 1512 1744  1024 1025 1028 1075  -HSync +Vsync	# 1280x1024 @ 85.00 Hz (GTF) hsync: 91.38 kHz; pclk: 159.36 MHz
	# 4:3 ASPECT RATIO SETTINGS
	# Modlin 	"XxY_Refresh"		Dotclc	hdsp hsys hsye htot  vdsp vsys vsye vtot
	Modeline	"640x480_60.00"		23.86   640  656  720  800   480  481  484  497   -HSync +Vsync	# 640x480 @ 60.00 Hz (GTF) hsync: 29.82 kHz; pclk: 23.86 MHz
	Modeline	"640x480_75.00"		30.72   640  664  728  816   480  481  484  502   -HSync +Vsync	# 640x480 @ 75.00 Hz (GTF) hsync: 37.65 kHz; pclk: 30.72 MHz
	Modeline	"640x480_85.00"		35.71   640  672  736  832   480  481  484  505   -HSync +Vsync	# 640x480 @ 85.00 Hz (GTF) hsync: 42.92 kHz; pclk: 35.71 MHz
	Modeline	"800x600_60.00"		38.22   800  832  912  1024  600  601  604  622   -HSync +Vsync	# 800x600 @ 60.00 Hz (GTF) hsync: 37.32 kHz; pclk: 38.22 MHz
	Modeline	"800x600_75.00"		48.91   800  840  920  1040  600  601  604  627   -HSync +Vsync	# 800x600 @ 75.00 Hz (GTF) hsync: 47.03 kHz; pclk: 48.91 MHz
	Modeline	"800x600_85.00"		56.55   800  840  928  1056  600  601  604  630   -HSync +Vsync	# 800x600 @ 85.00 Hz (GTF) hsync: 53.55 kHz; pclk: 56.55 MHz
	Modeline	"832x624_75.00"		53.20   832  872  960  1088  624  625  628  652   -HSync +Vsync	# 832x624 @ 75.00 Hz (GTF) hsync: 48.90 kHz; pclk: 53.20 MHz
	Modeline	"1024x768_60.00"	64.11   1024 1080 1184 1344  768  769  772  795   -HSync +Vsync	# 1024x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 64.11 MHz
	Modeline	"1024x768_70.00"	76.16   1024 1080 1192 1360  768  769  772  800   -HSync +Vsync	# 1024x768 @ 70.00 Hz (GTF) hsync: 56.00 kHz; pclk: 76.16 MHz
	Modeline	"1024x768_75.00"	81.80   1024 1080 1192 1360  768  769  772  802   -HSync +Vsync	# 1024x768 @ 75.00 Hz (GTF) hsync: 60.15 kHz; pclk: 81.80 MHz
	Modeline	"1024x768_85.00"	94.39   1024 1088 1200 1376  768  769  772  807   -HSync +Vsync	# 1024x768 @ 85.00 Hz (GTF) hsync: 68.60 kHz; pclk: 94.39 MHz
	Modeline	"1152x864_75.00"	104.99  1152 1224 1352 1552  864  865  868  902   -HSync +Vsync	# 1152x864 @ 75.00 Hz (GTF) hsync: 67.65 kHz; pclk: 104.99 MHz
	Modeline	"1152x864_85.00"	119.65  1152 1224 1352 1552  864  865  868  907   -HSync +Vsync	# 1152x864 @ 85.00 Hz (GTF) hsync: 77.10 kHz; pclk: 119.65 MHz
	Modeline	"1600x1200_60.00"	160.96  1600 1704 1880 2160  1200 1201 1204 1242  -HSync +Vsync	# 1600x1200 @ 60.00 Hz (GTF) hsync: 74.52 kHz; pclk: 160.96 MHz
	Modeline	"1600x1200_65.00"	176.23  1600 1712 1888 2176  1200 1201 1204 1246  -HSync +Vsync	# 1600x1200 @ 65.00 Hz (GTF) hsync: 80.99 kHz; pclk: 176.23 MHz
	Modeline	"1600x1200_70.00"	190.25  1600 1712 1888 2176  1200 1201 1204 1249  -HSync +Vsync	# 1600x1200 @ 70.00 Hz (GTF) hsync: 87.43 kHz; pclk: 190.25 MHz
	Modeline	"1600x1200_75.00"	205.99  1600 1720 1896 2192  1200 1201 1204 1253  -HSync +Vsync	# 1600x1200 @ 75.00 Hz (GTF) hsync: 93.97 kHz; pclk: 205.99 MHz
	Modeline	"1600x1200_85.00"	234.76  1600 1720 1896 2192  1200 1201 1204 1260  -HSync +Vsync	# 1600x1200 @ 85.00 Hz (GTF) hsync: 107.10 kHz; pclk: 234.76 MHz
	Modeline	"1920x1440_75.00"	297.59  1920 2072 2280 2640  1440 1441 1444 1503  -HSync +Vsyn	# 1920x1440 @ 75.00 Hz (GTF) hsync: 112.73 kHz; pclk: 297.59 MHz
	Modeline	"1920x1440_85.00"	341.35  1920 2072 2288 2656  1440 1441 1444 1512  -HSync +Vsync	# 1920x1440 @ 85.00 Hz (GTF) hsync: 128.52 kHz; pclk: 341.35 MHz
	Modeline	"2048x1536_60.00"	266.95  2048 2200 2424 2800  1536 1537 1540 1589  -HSync +Vsync	# 2048x1536 @ 60.00 Hz (GTF) hsync: 95.34 kHz; pclk: 266.95 MHz
	Modeline	"2048x1536_75.00"	340.48  2048 2216 2440 2832  1536 1537 1540 1603  -HSync +Vsync	# 2048x1536 @ 75.00 Hz (GTF) hsync: 120.22 kHz; pclk: 340.48 MHz
#	Modeline	"2048x1536_85.00"	388.04  2048 2216 2440 2832  1536 1537 1540 1612  -HSync +Vsync	# 2048x1536 @ 85.00 Hz (GTF) hsync: 137.02 kHz; pclk: 388.04 MHz
EndSection

Section	"Screen"
	Identifier	"Default Screen"
	Device		"ATI Radeon HD4670"
	Monitor		"Sony GDM-F520"
	DefaultDepth	24
	SubSection	"Display"
		Depth	24
		Modes	"2048x1536_75.00" "2048x1536_60.00" "1920x1440_85.00" "1920x1440_75.00" "1600x1200_85.00" "1600x1200_75.00" "1600x1200_65.00" "1600x1200_60.00" "1152x864_85.00" "1152x864_75.00" "1024x768_85.00" "1024x768_75.00" "1024x768_75.00" "1024x768_70.00" "1024x768_60.00" "832x624_75.00" "800x600_85.00" "800x600_75.00" "800x600_60.00" "640x480_85.00" "640x480_75.00" "640x480_60.00" "1280x1024_85.00" "1280x1024_75.00" "1280x1024_60.00" "720x400_85.00" "720x400_70.00"
		Virtual	2048 1536					# specifies the virtual screen resolution to be used; 5888 2400 for GDM-F520 + VP2290B
	EndSubSection
	SubSection	"Display"
		Depth	16
		Modes	"2048x1536_75.00" "2048x1536_60.00" "1920x1440_85.00" "1920x1440_75.00" "1600x1200_85.00" "1600x1200_75.00" "1600x1200_65.00" "1600x1200_60.00" "1152x864_85.00" "1152x864_75.00" "1024x768_85.00" "1024x768_75.00" "1024x768_75.00" "1024x768_70.00" "1024x768_60.00" "832x624_75.00" "800x600_85.00" "800x600_75.00" "800x600_60.00" "640x480_85.00" "640x480_75.00" "640x480_60.00" "1280x1024_85.00" "1280x1024_75.00" "1280x1024_60.00" "720x400_85.00" "720x400_70.00"
		Virtual	2048 1536					# specifies the virtual screen resolution to be used; 5888 2400 for GDM-F520 + VP2290B
	EndSubSection
	SubSection	"Display"
		Depth	24
		Modes	"2048x1536_75.00" "2048x1536_60.00" "1920x1440_85.00" "1920x1440_75.00" "1600x1200_85.00" "1600x1200_75.00" "1600x1200_65.00" "1600x1200_60.00" "1152x864_85.00" "1152x864_75.00" "1024x768_85.00" "1024x768_75.00" "1024x768_75.00" "1024x768_70.00" "1024x768_60.00" "832x624_75.00" "800x600_85.00" "800x600_75.00" "800x600_60.00" "640x480_85.00" "640x480_75.00" "640x480_60.00" "1280x1024_85.00" "1280x1024_75.00" "1280x1024_60.00" "720x400_85.00" "720x400_70.00"
		Virtual	2048 1536					# specifies the virtual screen resolution to be used; 5888 2400 for GDM-F520 + VP2290B
	EndSubSection
EndSection
```

---

### Post by ebharv on 2009-03-20
> **dh003i said:**
> How do I get the changes to stick?

Ok when I got home and fired up my tuxbox, my modified xorg.conf file was loaded. This time it hadn't been replaced. I don't know why but here's my guess:

When you dpkg-reconfigure -phigh xserver-xorg is creates a backup of your xorg.conf renaming it something like xorg.conf.XXXXXXXXX where the X's are some number (possibly the date or a timestamp haven't paid much attention to it). I'm guessing that this lets Ubuntu know how to backup your xorg.conf file if its manually edited and doesn't work right. 

Again this is just a guess as mine was working fine when I got home last night (03.19.2009), but wasn't the night before (03.18.2009). 

I also had the same problem with my Mint box (based on Ubuntu) and fixed it this morning to test my theory. When I rebooted it this morning, it loaded the edited xorg.conf file. Here's what I did.

Since the Ubuntu and Mint are on the same monitor and both have nvidia cards I copied  Ubuntu's xorg.conf file to usb. I booted the Mint and did ```
sudo dpgk-reconfigure -phigh xserver-xorg
``` That created the backup xorg.conf file then  I did a ```
sudo cp /media/myUSBdrive/xorg.conf /etc/X11/xorg.conf
```After that I rebooted the machine instead of restarting X (Ctrl+Alt+Backspace) like I was doing the night before, and my resolution came out fine.

So you should try this:
I'm assuming you have a backup of the .conf file you want to use. 
Type this into a terminal:
```
sudo dpkg-reconfigure -phigh xorg.conf
sudo cp /path/to/the/xorg/conf/file/you/want/to/use /etc/X11/xorg.conf
```Then reboot the machine. If it doesn't boot with the max resolution then there's a change it did work, to be sure, go System->Preferences->Screen Resolution to make sure it just didn't use a different resolution.

As far as the refresh rates go, I just let Ubuntu handle them. I've got an LCD. You should be able to choose your refresh rate in System->Preferences->Screen Resolution though.

---

### Post by dh003i on 2009-03-20
I tried what you said, it still doesn't work. Now, I modified my xorg.conf file (there were a few errors detected in /var/log/Xorg.conf.0.log), and it will load KDE, but still at this awful low resolution. Here is my /var/log/Xorg.conf.0.log file NOW (when I can start X, but get low resolution), and my Xorg.conf file.

It is like it is ignoring all of my settings for 2048x1536! I don't like xrandr. 

**/var/log/Xorg.conf.0.log**
```

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server x86_64 Ubuntu
Current Operating System: Linux davidjheinrich 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64
Build Date: 24 October 2008  09:06:49AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@crested.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Mar 20 17:29:32 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Sony GDM-F520"
(**) |   |-->Device "ATI Radeon HD4670"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7b7320
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0@1:0:0) ATI Technologies Inc RV730XT [Radeon HD 4670] rev 0, Mem @ 0xd0000000/268435456, 0xfe8e0000/65536, I/O @ 0x0000b000/256, BIOS @ 0x????????/131072
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
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
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "radeonhd"

(II) Loading /usr/lib/xorg/modules/drivers//radeonhd_drv.so
(II) Module radeonhd: vendor="AMD GPG"
	compiled for 1.5.2, module version = 1.2.4
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) RADEONHD: X driver for the following AMD GPG (ATI) graphics devices:
	RV505 : Radeon X1550, X1550 64bit.
	RV515 : Radeon X1300, X1550, X1600; FireGL V3300, V3350.
	RV516 : Radeon X1300, X1550, X1550 64-bit, X1600; FireMV 2250.
	R520  : Radeon X1800; FireGL V5300, V7200, V7300, V7350.
	RV530 : Radeon X1300 XT, X1600, X1600 Pro, X1650; FireGL V3400, V5200.
	RV535 : Radeon X1300, X1650.
	RV550 : Radeon X2300 HD.
	RV560 : Radeon X1650.
	RV570 : Radeon X1950, X1950 GT; FireGL V7400.
	R580  : Radeon X1900, X1950; AMD Stream Processor.
	R600  : Radeon HD 2900 GT/Pro/XT; FireGL V7600/V8600/V8650.
	RV610 : Radeon HD 2350, HD 2400 Pro/XT, HD 2400 Pro AGP; FireGL V4000.
	RV620 : Radeon HD 3450, HD 3470.
	RV630 : Radeon HD 2600 LE/Pro/XT, HD 2600 Pro/XT AGP; Gemini RV630;
		FireGL V3600/V5600.
	RV635 : Radeon HD 3650, HD 3670.
	RV670 : Radeon HD 3690, 3850, HD 3870, FireGL V7700, FireStream 9170.
	R680  : Radeon HD 3870 X2.
	M52   : Mobility Radeon X1300.
	M54   : Mobility Radeon X1400; M54-GL.
	M56   : Mobility Radeon X1600; Mobility FireGL V5200.
	M58   : Mobility Radeon X1800, X1800 XT; Mobility FireGL V7100, V7200.
	M62   : Mobility Radeon X1350.
	M64   : Mobility Radeon X1450, X2300.
	M66   : Mobility Radeon X1700, X1700 XT; FireGL V5250.
	M68   : Mobility Radeon X1900.
	M71   : Mobility Radeon HD 2300.
	M72   : Mobility Radeon HD 2400; Radeon E2400.
	M74   : Mobility Radeon HD 2400 XT.
	M76   : Mobility Radeon HD 2600;
		(Gemini ATI) Mobility Radeon HD 2600 XT.
	M82   : Mobility Radeon HD 3400.
	M86   : Mobility Radeon HD 3650, HD 3670, Mobility FireGL V5700.
	M88   : Mobility Radeon HD 3850, HD 3850 X2, HD 3870, HD3870 X2.
	RS600 : Radeon Xpress 1200, Xpress 1250.
	RS690 : Radeon X1200, X1250, X1270.
	RS740 : RS740, RS740M.
	RS780 : Radeon HD 3100/3200/3300 Series.
	RV770 : Radeon HD 4800 Series; Everest, K2, Denali ATI FirePro.
	R700  : Radeon R700.
	M98   : Radeon M98 Mobility.
	RV730 : Radeon HD4670, HD4650.
	M96   : Radeon M96 Mobility.
	RV710 : Radeon HD4570, HD4350.

(II) RADEONHD: version 1.2.4, built from git branch master, commit d9c8f9ce

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
(**) RADEONHD(0): Depth 24, (--) framebuffer bpp 32
(**) RADEONHD(0): Option "AccelMethod" "exa"
(**) RADEONHD(0): Option "DRI" "on"
(**) RADEONHD(0): Selected EXA 2D acceleration.
(II) RADEONHD(0): Unknown card detected: 0x9490:0x1462:0x1590.
	If - and only if - your card does not work or does not work optimally
	please contact radeonhd@opensuse.org to help rectify this.
	Use the subject: 0x9490:0x1462:0x1590: <name of board>
	and *please* describe the problems you are seeing
	in your message.
(--) RADEONHD(0): Detected an RV730 on an unidentified card
(II) RADEONHD(0): Mapped IO @ 0xfe8e0000 to 0x7f613b562000 (size 0x00010000)
(II) RADEONHD(0): PCIE Card Detected
(II) RADEONHD(0): Getting BIOS copy from legacy VBIOS location
(II) RADEONHD(0): ATOM BIOS Rom: 
	SubsystemVendorID: 0x1462 SubsystemID: 0x1590
	IOBaseAddress: 0xb000
	Filename: Test.bin    
	BIOS Bootup Message: 
113-MSITV159MS.100-AB73100-100-MI RV730 GDDR3 128BIT 750E/1000M               
(II) RADEONHD(0): Analog TV Default Mode: 1
(II) RADEONHD(0): Found default TV Mode NTSC
(II) RADEONHD(0): The detected amount of videoram exceeds the PCI BAR aperture.
(II) RADEONHD(0): Using only 262144kB of the total 524288kB.
(--) RADEONHD(0): VideoRAM: 262144 kByte
(II) RADEONHD(0): Framebuffer space used by Firmware (kb): 20
(II) RADEONHD(0): Start of VRAM area used by Firmware: 0x7ffec
(II) RADEONHD(0): AtomBIOS requests 20kB of VRAM scratch space
(II) RADEONHD(0): AtomBIOS VRAM scratch base: 0x7ffec
(WW) RADEONHD(0): rhdAtomAllocateFbScratch: FW FB scratch area not located at the end of VRAM. Scratch End: 0x84fec VRAM End: 0x10000000
(II) RADEONHD(0): Cannot get VRAM scratch space. Allocating in main memory instead
(II) RADEONHD(0): Default Engine Clock: 750000
(II) RADEONHD(0): Default Memory Clock: 1000000
(II) RADEONHD(0): Maximum Pixel ClockPLL Frequency Output: 1200000
(II) RADEONHD(0): Minimum Pixel ClockPLL Frequency Output: 0
(II) RADEONHD(0): Maximum Pixel ClockPLL Frequency Input: 16000
(II) RADEONHD(0): Minimum Pixel ClockPLL Frequency Input: 6000
(II) RADEONHD(0): Maximum Pixel Clock: 400000
(II) RADEONHD(0): Reference Clock: 27000
(WW) RADEONHD(0): Direct rendering for R600 and up forced on - This is NOT officially supported yet and may cause instability or lockups
(II) RADEONHD(0): Found libdri 5.4.0.
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) RADEONHD(0): Found libdrm 1.3.0.
(II) RADEONHD(0): Found radeon drm 1.29.0.
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) RADEONHD(0): Reference Clock: 27000
(II) RADEONHD(0): GPIO_I2C_Clk_Mask: 0x1f90
(II) RADEONHD(0): GPIO_I2C_Clk_Mask_Shift: 0x0
(II) RADEONHD(0): GPIO_I2C_Data_Mask: 0x1f90
(II) RADEONHD(0): GPIO_I2C_Data_Mask_Shift: 0x8
(II) RADEONHD(0): I2C bus "RHD I2C line 0" initialized.
(II) RADEONHD(0): GPIO_I2C_Clk_Mask: 0x1f94
(II) RADEONHD(0): GPIO_I2C_Clk_Mask_Shift: 0x0
(II) RADEONHD(0): GPIO_I2C_Data_Mask: 0x1f94
(II) RADEONHD(0): GPIO_I2C_Data_Mask_Shift: 0x8
(II) RADEONHD(0): I2C bus "RHD I2C line 1" initialized.
(II) RADEONHD(0): GPIO_I2C_Clk_Mask: 0x1f98
(II) RADEONHD(0): GPIO_I2C_Clk_Mask_Shift: 0x0
(II) RADEONHD(0): GPIO_I2C_Data_Mask: 0x1f98
(II) RADEONHD(0): GPIO_I2C_Data_Mask_Shift: 0x8
(II) RADEONHD(0): I2C bus "RHD I2C line 2" initialized.
(II) RADEONHD(0): GPIO_I2C_Clk_Mask: 0x1f88
(II) RADEONHD(0): GPIO_I2C_Clk_Mask_Shift: 0x0
(II) RADEONHD(0): GPIO_I2C_Data_Mask: 0x1f88
(II) RADEONHD(0): GPIO_I2C_Data_Mask_Shift: 0x8
(II) RADEONHD(0): I2C bus "RHD I2C line 3" initialized.
(II) RADEONHD(0): GPIO_I2C_Clk_Mask: 0x1fc4
(II) RADEONHD(0): GPIO_I2C_Clk_Mask_Shift: 0x0
(II) RADEONHD(0): GPIO_I2C_Data_Mask: 0x1fc4
(II) RADEONHD(0): GPIO_I2C_Data_Mask_Shift: 0x8
(II) RADEONHD(0): I2C bus "RHD I2C line 4" initialized.
(II) RADEONHD(0): GPIO_I2C_Clk_Mask: 0x1fe8
(II) RADEONHD(0): GPIO_I2C_Clk_Mask_Shift: 0x0
(II) RADEONHD(0): GPIO_I2C_Data_Mask: 0x1fe8
(II) RADEONHD(0): GPIO_I2C_Data_Mask_Shift: 0x8
(II) RADEONHD(0): I2C bus "RHD I2C line 5" initialized.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) RADEONHD(0): Detected VGA mode.
(**) RADEONHD(0): Using AtomBIOS for Crtcs
(**) RADEONHD(0): Using AtomBIOS for PLLs
(II) RADEONHD(0): Minimum Pixel ClockPLL Frequency Output: 0
(II) RADEONHD(0): Maximum Pixel ClockPLL Frequency Output: 1200000
(II) RADEONHD(0): Maximum Pixel Clock: 400000
(II) RADEONHD(0): Reference Clock: 27000
(II) RADEONHD(0): rhdAtomSetPixelClockVersion returned version 3 for index 0xc
(II) RADEONHD(0): rhdAtomSetPixelClockVersion returned version 3 for index 0xc
(II) RADEONHD(0): FB: Allocated Cursor Image at offset 0x00000000 (size = 0x00004000)
(II) RADEONHD(0): FB: Allocated Cursor Image at offset 0x00004000 (size = 0x00004000)
(II) RADEONHD(0): Connector[0] {RHD_CONNECTOR_DVI, "DUAL_LINK_DVI_I CRT2 DFP2", RHD_DDC_4, RHD_HPD_1, { RHD_OUTPUT_UNIPHYC, RHD_OUTPUT_DACB } }
(II) RADEONHD(0): Connector[1] {RHD_CONNECTOR_DVI, "DUAL_LINK_DVI_I CRT1 DFP1", RHD_DDC_3, RHD_HPD_0, { RHD_OUTPUT_UNIPHYA, RHD_OUTPUT_DACA } }
(**) RADEONHD(0): Using AtomBIOS for Outputs
(EE) RADEONHD(0): RHDHdmiInit: unknown HDMI output type
(II) RADEONHD(0): rhdAtomSelectCrtcSourceVersion returned version 2 for index 0x2a
(--) RADEONHD(0): Attaching Output AtomOutputUniphyC to Connector DVI-I 1
(**) RADEONHD(0): Using AtomBIOS for Outputs
(II) RADEONHD(0): rhdAtomSelectCrtcSourceVersion returned version 2 for index 0x2a
(--) RADEONHD(0): Attaching Output AtomOutputDACB to Connector DVI-I 1
(**) RADEONHD(0): Using AtomBIOS for Outputs
(II) RADEONHD(0): rhdAtomSelectCrtcSourceVersion returned version 2 for index 0x2a
(--) RADEONHD(0): Attaching Output AtomOutputUniphyA to Connector DVI-I 2
(**) RADEONHD(0): Using AtomBIOS for Outputs
(II) RADEONHD(0): rhdAtomSelectCrtcSourceVersion returned version 2 for index 0x2a
(--) RADEONHD(0): Attaching Output AtomOutputDACA to Connector DVI-I 2
(II) RADEONHD(0): RandR: Adding RRoutput DVI-I_1/digital for Output AtomOutputUniphyC
(II) RADEONHD(0): RandR: Adding RRoutput DVI-I_1/analog for Output AtomOutputDACB
(II) RADEONHD(0): RandR: Adding RRoutput DVI-I_2/digital for Output AtomOutputUniphyA
(II) RADEONHD(0): RandR: Adding RRoutput DVI-I_2/analog for Output AtomOutputDACA
(II) RADEONHD(0): Output DVI-I_1/digital using monitor section Sony GDM-F520
(II) RADEONHD(0): Output DVI-I_1/digital has no monitor section
(II) RADEONHD(0): Output DVI-I_1/analog has no monitor section
(II) RADEONHD(0): Output DVI-I_2/digital has no monitor section
(II) RADEONHD(0): Output DVI-I_2/analog has no monitor section
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: none
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Setting AtomOutputDACA to incoherent
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" removed.
(II) RADEONHD(0): Output DVI-I_1/digital disconnected
(II) RADEONHD(0): Output DVI-I_1/analog disconnected
(II) RADEONHD(0): Output DVI-I_2/digital disconnected
(II) RADEONHD(0): Output DVI-I_2/analog connected
(II) RADEONHD(0): Using fuzzy aspect match for initial modes
(II) RADEONHD(0): Output DVI-I_2/analog using initial mode 1152x864
(II) RADEONHD(0): RandR 1.2 support enabled
(==) RADEONHD(0): RGB weight 888
(==) RADEONHD(0): Default visual is TrueColor
(==) RADEONHD(0): Using gamma correction (1.0, 1.0, 1.0)
(II) RADEONHD(0): Using 2048x1536 Framebuffer with 2048 pitch
(II) RADEONHD(0): FB: Allocated ScanoutBuffer at offset 0x00008000 (size = 0x00C00000)
(**) RADEONHD(0): Display dimensions: (406, 303) mm
(**) RADEONHD(0): DPI set to (128, 128)
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) Loading sub module "exa"
(II) LoadModule: "exa"

(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.4.0
	ABI class: X.Org Video Driver, version 4.1
(II) RADEONHD(0): FB: Allocated Offscreen Buffer at offset 0x00C08000 (size = 0x01998000)
(II) RADEONHD(0): FB: Allocated DRI Back Buffer at offset 0x025A0000 (size = 0x00C00000)
(II) RADEONHD(0): FB: Allocated DRI Depth Buffer at offset 0x031A0000 (size = 0x00C00000)
(II) RADEONHD(0): FB: Allocated GART table at offset 0x0FFF0000 (size = 0x00010000, end of FB)
(II) RADEONHD(0): FB: Allocated DRI Textures at offset 0x03DA0000 (size = 0x0C000000)
(II) RADEONHD(0): Using 16 MB GART aperture
(II) RADEONHD(0): Using 2 MB for the ring buffer
(II) RADEONHD(0): Using 2 MB for vertex/indirect buffers
(II) RADEONHD(0): Using 12 MB for GART textures
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
(II) RADEONHD(0): Mapped IO @ 0xfe8e0000 to 0x7f613b562000 (size 0x00010000)
(II) RADEONHD(0): Mapped FB @ 0xd0000000 to 0x7f61278c3000 (size 0x10000000)
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) RADEONHD(0): [drm] Using the DRM lock SAREA also for drawables.
(II) RADEONHD(0): [drm] framebuffer handle = 0xd0000000
(II) RADEONHD(0): [drm] added 1 reserved context for kernel
(II) RADEONHD(0): X context handle = 0x1
(II) RADEONHD(0): [drm] installed DRM signal handler
(II) RADEONHD(0): [pci] 16384 kB allocated with handle 0x1256d200
(II) RADEONHD(0): [pci] ring handle = 0x1effe000
(II) RADEONHD(0): [pci] Ring mapped at 0x7f61276c2000
(II) RADEONHD(0): [pci] Ring contents 0x00000000
(II) RADEONHD(0): [pci] ring read ptr handle = 0x2efff000
(II) RADEONHD(0): [pci] Ring read ptr mapped at 0x7f613b517000
(II) RADEONHD(0): [pci] Ring read ptr contents 0x00000000
(II) RADEONHD(0): [pci] vertex/indirect buffers handle = 0x1efff000
(II) RADEONHD(0): [pci] Vertex/indirect buffers mapped at 0x7f61274c2000
(II) RADEONHD(0): [pci] Vertex/indirect buffers contents 0x00000000
(II) RADEONHD(0): [pci] GART texture map handle = 0x1f000000
(II) RADEONHD(0): [pci] GART Texture map mapped at 0x7f6126902000
(II) RADEONHD(0): [drm] register handle = 0xfe8e0000
(II) RADEONHD(0): [dri] Visual configs initialized
(II) RADEONHD(0): [DRI] installation complete
(II) RADEONHD(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEONHD(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEONHD(0): [drm] dma control initialized, using IRQ 16
(II) RADEONHD(0): [drm] Initialized kernel GART heap manager, 12320768
(II) RADEONHD(0): Direct rendering enabled
(II) RADEONHD(0): Using DRM Command Processor (indirect) for acceleration.
(II) EXA(0): Offscreen pixmap area of 26836992 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(II)         UploadToScreen
(II)         DownloadFromScreen
(==) RADEONHD(0): Backing store disabled
(==) RADEONHD(0): Silken mouse enabled
(II) RADEONHD(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling DAC2OutputControl
(II) RADEONHD(0): DAC2OutputControl Successful
(II) RADEONHD(0): Calling DACBEncoderControl
(II) RADEONHD(0): DACBEncoderControl Successful
(II) RADEONHD(0): Calling DAC1OutputControl
(II) RADEONHD(0): DAC1OutputControl Successful
(II) RADEONHD(0): Calling DACAEncoderControl
(II) RADEONHD(0): DACAEncoderControl Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): Calling DAC1OutputControl
(II) RADEONHD(0): DAC1OutputControl Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): On Crtc 0 Setting 60.0 Hz Mode: Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync
(II) RADEONHD(0): Calling SetCRTC_Timing
(II) RADEONHD(0): SetCRTC_Timing Successful
(II) RADEONHD(0): CallingSetCRTC_OverScan
(II) RADEONHD(0): Set CRTC_OverScan Successful
(II) RADEONHD(0): Calling EnableScaler
(II) RADEONHD(0): EnableScaler Successful
(II) RADEONHD(0): Calling SetPixelClock
(II) RADEONHD(0): SetPixelClock Successful
(II) RADEONHD(0): Calling SelectCRTCSource
(II) RADEONHD(0): SelectCRTCSource Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling DACAEncoderControl
(II) RADEONHD(0): DACAEncoderControl Successful
(II) RADEONHD(0): Calling DAC1OutputControl
(II) RADEONHD(0): DAC1OutputControl Successful
(II) RADEONHD(0): Calling DAC2OutputControl
(II) RADEONHD(0): DAC2OutputControl Successful
(II) RADEONHD(0): Calling DACBEncoderControl
(II) RADEONHD(0): DACBEncoderControl Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): RHDAudioSetSupported: config 0x60040 codec 0x1
(II) RADEONHD(0): DPMS enabled
(II) RADEONHD(0): Xv: Textured Video initialised.
(--) RandR disabled
(II) Setting vga for screen 0.
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
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(EE) AIGLX error: dlopen of /usr/lib/dri/r600_dri.so failed (/usr/lib/dri/r600_dri.so: cannot open shared object file: No such file or directory)
(EE) AIGLX: reverting to software rendering
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) RADEONHD(0): Setting screen physical size to 304 x 228
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.0.99
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event5"
(II) Logitech USB Receiver: Found 1 mouse buttons
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Logitech USB Receiver: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Logitech USB Receiver: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Logitech USB Receiver: xkb_layout: "us"
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event4"
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Found 16 mouse buttons
(II) Logitech USB Receiver: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Wacom Bamboo
(II) LoadModule: "wacom"

(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) Wacom driver level: 47-0.8.1-4 $
(**) Wacom Bamboo: always reports core events
(**) Wacom Bamboo device is /dev/input/event8
(**) Wacom Bamboo is in absolute mode
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) Wacom Bamboo: serial speed 9600
(II) XINPUT: Adding extended input device "Wacom Bamboo" (type: Wacom Stylus)
(**) Option "Device" "/dev/input/event8"
Wacom Bamboo Wacom X driver grabbed event device
(==) Wacom using pressure threshold of 30 for button 1
(==) Wacom USB Bamboo tablet speed=9600 (38400) maxX=14760 maxY=9225 maxZ=511 resX=2540 resY=2540  tilt=disabled
(==) Wacom device "Wacom Bamboo" top X=0 top Y=0 bottom X=14760 bottom Y=9225 resol X=2540 resol Y=2540
(II) config/hal: Adding input device Composite USB PS2 Converter USB to PS2 Adaptor  V3.10
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: always reports core events
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Device: "/dev/input/event3"
(II) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Found x and y relative axes
(II) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Found 10 mouse buttons
(II) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Found keys
(II) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Configuring as mouse
(II) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Configuring as keyboard
(II) XINPUT: Adding extended input device "Composite USB PS2 Converter USB to PS2 Adaptor  V3.10" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: xkb_layout: "us"
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: YAxisMapping: buttons 4 and 5
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Composite USB PS2 Converter USB to PS2 Adaptor  V3.10
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: always reports core events
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Device: "/dev/input/event2"
(II) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Found keys
(II) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Configuring as keyboard
(II) XINPUT: Adding extended input device "Composite USB PS2 Converter USB to PS2 Adaptor  V3.10" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: xkb_layout: "us"
(II) RADEONHD(0): RHDHdmiUpdateAudioSettings: stoped with 1 channels, 48000 Hz sampling rate, 8 bits per sample,
(II) RADEONHD(0): RHDHdmiUpdateAudioSettings: 0x00 IEC60958 status bits and 0x00 category code
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" removed.
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" removed.
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" removed.
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" removed.
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling DACAEncoderControl
(II) RADEONHD(0): DACAEncoderControl Successful
(II) RADEONHD(0): Calling DAC1OutputControl
(II) RADEONHD(0): DAC1OutputControl Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" removed.
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" removed.
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
```

The only time the **/var/X11/Xorg.conf.0.log** even mentions 2048 and 1536 is here. Why is it saying "analog using initial mode 1152x864"!? And I set it prefer "2048x1536_85.00". 

```
(II) RADEONHD(0): Using fuzzy aspect match for initial modes
(II) RADEONHD(0): Output DVI-I_2/analog using initial mode 1152x864
(II) RADEONHD(0): RandR 1.2 support enabled
(==) RADEONHD(0): RGB weight 888
(==) RADEONHD(0): Default visual is TrueColor
(==) RADEONHD(0): Using gamma correction (1.0, 1.0, 1.0)
(II) RADEONHD(0): Using 2048x1536 Framebuffer with 2048 pitch
(II) RADEONHD(0): FB: Allocated ScanoutBuffer at offset 0x00008000 (size = 0x00C00000)
(**) RADEONHD(0): Display dimensions: (406, 303) mm
(**) RADEONHD(0): DPI set to (128, 128)
```

**/etc/Xorg.conf**
```
Section	"Device"
	Identifier	"ATI Radeon HD4670"
	Driver		"radeonhd"
	Option		"AccelMethod" "exa"	# default shadowfb ; turn off if cause problems; experimental in HEAD radeonhd
	Option		"DRI" "on"		# turn off if cause problems; experimental in HEAD radeonhd
EndSection

Section	"Monitor"
	Identifier	"Sony GDM-F520"
	VendorName	"Sony"
	ModelName	"GDM-F520"
	HorizSync	30-137   					# units in kHz by default
	VertRefresh	48-170  					# units in Hz by default
	DisplaySize	406 303 					# specified in x y millimeters
	# Gamma		1.0						# specifies gamma
	# Gamma		1.0 1.0 1.0					# red green blue gammas
	UseModes	"Modes GDM-F520"				# make modes listed in Mode : modesection-id available for this monitor
	# Mode name							# provide definitions for video modes for monitor
		# DotClock	clock					# dot (pixel) clock rate to be used for mode
		# HTimings	hdisp hsyncstart hsyncend htotal	# horizontal timings for mode
		# VTimings	vdisp vsyncstart vcyncend vtotal	# vertical timings for mode
		# Flags		flag					# optional set of mode flags, each with a separate string in double-quotes
		# HSkew		hskew					# number of pixels towards right edge of screen by which display enable signal is to be skewed
		# VScan		vsacn					# number times each scanline is painted on the screen; 1 is default; DoubleScan Flag doubles this value
	# Option	TargetRefresh rate				# target vertical refresh rate when selecting video modes
	# Option	Position x y					# position of monitor within X screen
	# Option	LeftOf output					# monitor should be positioned to the left of the output (not monitor) of a given name
	# Option	MinClock 23.86					# minimum dot clock (kHz) supported by monitor
	# Option	MaxClock 388.04					# maximum dot clock (kHz) supported by monitor
	# Option	Rotate normal					# valid values normal, left, right, inverted
# 	Option		"PreferredMode" "2048x1536_85.00"		# specifies a mode to be marked as the preferred initial mode of the monitor
EndSection

Section	"Modes"
      Identifier	"Modes GDM-F520"
	#					Dotclock; hdisp, hsyncstart, hsyncend, htotal; vdisp, vsyncstart, vsyncend, vtotal
	# 9:5 ASPECT RATIO SETTINGS (slightly longer than 16:9)
	# Modlin 	"XxY_Refresh"		Dotclc	hdsp hsys hsye htot  vdsp vsys vsye vtot
	Modeline	"720x400_70.00"		26.15   720  736  808  896   400  401  404  417   -HSync +Vsync	# 720x400 @ 70.00 Hz (GTF) hsync: 29.19 kHz; pclk: 26.15 MHz
	Modeline	"720x400_85.00"		32.64   720  744  816  912   400  401  404  421   -HSync +Vsync	# 720x400 @ 85.00 Hz (GTF) hsync: 35.78 kHz; pclk: 32.64 MHz
	# 5:4 ASPECT RATIO SETTINGS
	# Modlin 	"XxY_Refresh"		Dotclc	hdsp hsys hsye htot  vdsp vsys vsye vtot
	Modeline	"1280x1024_60.00"	108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync	# 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
	Modeline	"1280x1024_75.00"	138.54  1280 1368 1504 1728  1024 1025 1028 1069  -HSync +Vsync	# 1280x1024 @ 75.00 Hz (GTF) hsync: 80.17 kHz; pclk: 138.54 MHz
	Modeline	"1280x1024_85.00"	159.36  1280 1376 1512 1744  1024 1025 1028 1075  -HSync +Vsync	# 1280x1024 @ 85.00 Hz (GTF) hsync: 91.38 kHz; pclk: 159.36 MHz
	# 4:3 ASPECT RATIO SETTINGS
	# Modlin 	"XxY_Refresh"		Dotclc	hdsp hsys hsye htot  vdsp vsys vsye vtot
	Modeline	"640x480_60.00"		23.86   640  656  720  800   480  481  484  497   -HSync +Vsync	# 640x480 @ 60.00 Hz (GTF) hsync: 29.82 kHz; pclk: 23.86 MHz
	Modeline	"640x480_75.00"		30.72   640  664  728  816   480  481  484  502   -HSync +Vsync	# 640x480 @ 75.00 Hz (GTF) hsync: 37.65 kHz; pclk: 30.72 MHz
	Modeline	"640x480_85.00"		35.71   640  672  736  832   480  481  484  505   -HSync +Vsync	# 640x480 @ 85.00 Hz (GTF) hsync: 42.92 kHz; pclk: 35.71 MHz
	Modeline	"800x600_60.00"		38.22   800  832  912  1024  600  601  604  622   -HSync +Vsync	# 800x600 @ 60.00 Hz (GTF) hsync: 37.32 kHz; pclk: 38.22 MHz
	Modeline	"800x600_75.00"		48.91   800  840  920  1040  600  601  604  627   -HSync +Vsync	# 800x600 @ 75.00 Hz (GTF) hsync: 47.03 kHz; pclk: 48.91 MHz
	Modeline	"800x600_85.00"		56.55   800  840  928  1056  600  601  604  630   -HSync +Vsync	# 800x600 @ 85.00 Hz (GTF) hsync: 53.55 kHz; pclk: 56.55 MHz
	Modeline	"832x624_75.00"		53.20   832  872  960  1088  624  625  628  652   -HSync +Vsync	# 832x624 @ 75.00 Hz (GTF) hsync: 48.90 kHz; pclk: 53.20 MHz
	Modeline	"1024x768_60.00"	64.11   1024 1080 1184 1344  768  769  772  795   -HSync +Vsync	# 1024x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 64.11 MHz
	Modeline	"1024x768_70.00"	76.16   1024 1080 1192 1360  768  769  772  800   -HSync +Vsync	# 1024x768 @ 70.00 Hz (GTF) hsync: 56.00 kHz; pclk: 76.16 MHz
	Modeline	"1024x768_75.00"	81.80   1024 1080 1192 1360  768  769  772  802   -HSync +Vsync	# 1024x768 @ 75.00 Hz (GTF) hsync: 60.15 kHz; pclk: 81.80 MHz
	Modeline	"1024x768_85.00"	94.39   1024 1088 1200 1376  768  769  772  807   -HSync +Vsync	# 1024x768 @ 85.00 Hz (GTF) hsync: 68.60 kHz; pclk: 94.39 MHz
	Modeline	"1152x864_75.00"	104.99  1152 1224 1352 1552  864  865  868  902   -HSync +Vsync	# 1152x864 @ 75.00 Hz (GTF) hsync: 67.65 kHz; pclk: 104.99 MHz
	Modeline	"1152x864_85.00"	119.65  1152 1224 1352 1552  864  865  868  907   -HSync +Vsync	# 1152x864 @ 85.00 Hz (GTF) hsync: 77.10 kHz; pclk: 119.65 MHz
	Modeline	"1600x1200_60.00"	160.96  1600 1704 1880 2160  1200 1201 1204 1242  -HSync +Vsync	# 1600x1200 @ 60.00 Hz (GTF) hsync: 74.52 kHz; pclk: 160.96 MHz
	Modeline	"1600x1200_65.00"	176.23  1600 1712 1888 2176  1200 1201 1204 1246  -HSync +Vsync	# 1600x1200 @ 65.00 Hz (GTF) hsync: 80.99 kHz; pclk: 176.23 MHz
	Modeline	"1600x1200_70.00"	190.25  1600 1712 1888 2176  1200 1201 1204 1249  -HSync +Vsync	# 1600x1200 @ 70.00 Hz (GTF) hsync: 87.43 kHz; pclk: 190.25 MHz
	Modeline	"1600x1200_75.00"	205.99  1600 1720 1896 2192  1200 1201 1204 1253  -HSync +Vsync	# 1600x1200 @ 75.00 Hz (GTF) hsync: 93.97 kHz; pclk: 205.99 MHz
	Modeline	"1600x1200_85.00"	234.76  1600 1720 1896 2192  1200 1201 1204 1260  -HSync +Vsync	# 1600x1200 @ 85.00 Hz (GTF) hsync: 107.10 kHz; pclk: 234.76 MHz
	Modeline	"1920x1440_75.00"	297.59  1920 2072 2280 2640  1440 1441 1444 1503  -HSync +Vsync	# 1920x1440 @ 75.00 Hz (GTF) hsync: 112.73 kHz; pclk: 297.59 MHz
	Modeline	"1920x1440_85.00"	341.35  1920 2072 2288 2656  1440 1441 1444 1512  -HSync +Vsync	# 1920x1440 @ 85.00 Hz (GTF) hsync: 128.52 kHz; pclk: 341.35 MHz
	Modeline	"2048x1536_60.00"	266.95  2048 2200 2424 2800  1536 1537 1540 1589  -HSync +Vsync	# 2048x1536 @ 60.00 Hz (GTF) hsync: 95.34 kHz; pclk: 266.95 MHz
	Modeline	"2048x1536_75.00"	340.48  2048 2216 2440 2832  1536 1537 1540 1603  -HSync +Vsync	# 2048x1536 @ 75.00 Hz (GTF) hsync: 120.22 kHz; pclk: 340.48 MHz
	Modeline	"2048x1536_85.00"	388.04  2048 2216 2440 2832  1536 1537 1540 1612  -HSync +Vsync	# 2048x1536 @ 85.00 Hz (GTF) hsync: 137.02 kHz; pclk: 388.04 MHz
EndSection

Section	"Screen"
	Identifier	"Default Screen"
	Device		"ATI Radeon HD4670"
	Monitor		"Sony GDM-F520"
	DefaultDepth	24
	SubSection	"Display"
		Depth	24
		Modes	"2048x1536_75.00" "2048x1536_60.00" "1920x1440_85.00" "1920x1440_75.00" "1600x1200_85.00" "1600x1200_75.00" "1600x1200_65.00" "1600x1200_60.00" "1152x864_85.00" "1152x864_75.00" "1024x768_85.00" "1024x768_75.00" "1024x768_75.00" "1024x768_70.00" "1024x768_60.00" "832x624_75.00" "800x600_85.00" "800x600_75.00" "800x600_60.00" "640x480_85.00" "640x480_75.00" "640x480_60.00" "1280x1024_85.00" "1280x1024_75.00" "1280x1024_60.00" "720x400_85.00" "720x400_70.00"
		Virtual	2048 1536					# specifies the virtual screen resolution to be used; 5888 2400 for GDM-F520 + VP2290B
	EndSubSection
	SubSection	"Display"
		Depth	16
		Modes	"2048x1536_75.00" "2048x1536_60.00" "1920x1440_85.00" "1920x1440_75.00" "1600x1200_85.00" "1600x1200_75.00" "1600x1200_65.00" "1600x1200_60.00" "1152x864_85.00" "1152x864_75.00" "1024x768_85.00" "1024x768_75.00" "1024x768_75.00" "1024x768_70.00" "1024x768_60.00" "832x624_75.00" "800x600_85.00" "800x600_75.00" "800x600_60.00" "640x480_85.00" "640x480_75.00" "640x480_60.00" "1280x1024_85.00" "1280x1024_75.00" "1280x1024_60.00" "720x400_85.00" "720x400_70.00"
		Virtual	2048 1536					# specifies the virtual screen resolution to be used; 5888 2400 for GDM-F520 + VP2290B
	EndSubSection
	SubSection	"Display"
		Depth	8
		Modes	"2048x1536_75.00" "2048x1536_60.00" "1920x1440_85.00" "1920x1440_75.00" "1600x1200_85.00" "1600x1200_75.00" "1600x1200_65.00" "1600x1200_60.00" "1152x864_85.00" "1152x864_75.00" "1024x768_85.00" "1024x768_75.00" "1024x768_75.00" "1024x768_70.00" "1024x768_60.00" "832x624_75.00" "800x600_85.00" "800x600_75.00" "800x600_60.00" "640x480_85.00" "640x480_75.00" "640x480_60.00" "1280x1024_85.00" "1280x1024_75.00" "1280x1024_60.00" "720x400_85.00" "720x400_70.00"
		Virtual	2048 1536					# specifies the virtual screen resolution to be used; 5888 2400 for GDM-F520 + VP2290B
	EndSubSection
EndSection
```

---

### Post by ebharv on 2009-03-23
In Your "Monitor Section" where you specified the "PreferredMode" is reads ```
#     Option        "PreferredMode" "2048x1536_85.00"        # specifies a mode to be marked as the preferred initial mode of the monitor
```It should read ```
Option        "PreferredMode" "2048x1536_85.00"        # specifies a mode to be marked as the preferred initial mode of the monitor
```The hash/sharp/pound sign (#) is used for comments. Anything after the first hash/sharp/pound on the line is ignored. You have this line (and many others) commented out!!! Delete the hash/sharp/pound character at the begining of the Option  "PreferredMode" line if you want that to be your default resolution. 

Also, your .conf file is wwwaaaaayyy more detailed than mine.  And I'm wondering if you need all of those options. I'll post my .conf file when I can so you can see what I mean but for now......

Delete the hash/sharp/pound character at the begining of the Option  "PreferredMode" line if you want that to be your default resolution.

Got my .conf file. Here's what it looks like
```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "nvidia"
    Option        "NoLogo"    "True"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor       "Configured Monitor"
    Device        "Configured Video Device"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        Modes    "1680x1050"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen       "Default Screen"
EndSection

Section "Module"
    Load        "glx"
EndSection

```I run GNOME on my machine.

---

### Post by dh003i on 2009-03-23
> **ebharv said:**
> In Your "Monitor Section" where you specified the "PreferredMode" is reads ```
#     Option        "PreferredMode" "2048x1536_85.00"        # specifies a mode to be marked as the preferred initial mode of the monitor
```It should read ```
Option        "PreferredMode" "2048x1536_85.00"        # specifies a mode to be marked as the preferred initial mode of the monitor
```

I did this. It makes no difference. [See this thread I started]("http://ubuntuforums.org/showthread.php?t=1102551"). It's like the xserver isn't even seeing my modeline settings. I added a 2048x1500 modeline (non-standard) to my xorg.conf file; that doesn't show up anywhere in the /var/log/Xorg.0.log file.

---

