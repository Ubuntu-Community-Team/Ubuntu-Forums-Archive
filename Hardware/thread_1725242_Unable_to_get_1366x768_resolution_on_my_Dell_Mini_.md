---
title: "Unable to get 1366x768 resolution on my Dell Mini 1012 - Ubuntu 10.10 (Maverick)"
date: 2011-04-09
forum: Hardware
---

### Post by JimLeek on 2011-04-09
Hi,

I have a Dell Mini 1012 running Ubuntu 10.10 (Maverick Meerkat). I've manually installed my wireless, and otherwise everything seems to work fine. However, my resolution is set at 1024x600, and I don't have the option under "system > preferences > monitors" to move up to 1366x768.

The monitor is designed to run at 1366x768 (HD) and my graphic chip is the Intel GMA 3150, so there should be no reason I can't get this resolution (see the system specs at [http://support.dell.com/support/edocs/systems/ins1012/en/cs/cs_en.pdf]("http://support.dell.com/support/edocs/systems/ins1012/en/cs/cs_en.pdf")).

From other posts I've read, there should be no problem with the Intel GMA 3150 driver. And from what I can see, I think the driver is fine, because I seem to have Compiz working (e.g. my Terminal window background is semi-transparent).

The first thing I did was to install ARandR (advice from some blog post), a GUI for XRandR, but this only lists resolutions up to 1024x600.

I then tried XRandR itself via the command line and tried to create a new modeline:

```
**jim@Inspiron-1012:~$** xrandr -q --verbose
Screen 0: minimum 320 x 200, current 1024 x 600, maximum 4096 x 4096
VGA1 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x41
	Timestamp:  61848
	Subpixel:   unknown
	Clones:    
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
LVDS1 connected 1024x600+0+0 (0x43) normal (normal left inverted right x axis y axis) 222mm x 125mm
	Identifier: 0x42
	Timestamp:  61848
	Subpixel:   horizontal rgb
	Gamma:      1.0:1.0:1.0
	Brightness: 1.0
	Clones:    
	CRTC:       1
	CRTCs:      1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	EDID:
		00ffffffffffff000daf041000000000
		0a13010390160c780acf459059579529
		1f505400000001010101010101010101
		0101010101019c1600af41583f208156
		8f00de7d0000001a0000000000000000
		00000000000000000000000000fe004a
		314a3933804e3130314c360a00000000
		00000000000000000001010a20200061
	BACKLIGHT: 7 (0x00000007)	range:  (0,15)
	Backlight: 7 (0x00000007)	range:  (0,15)
	scaling mode:	Full aspect
		supported: None         Full         Center       Full aspect 
  1024x600 (0x43)   57.9MHz +HSync -VSync *current +preferred
        h: width  1024 start 1153 end 1239 total 1455 skew    0 clock   39.8KHz
        v: height  600 start  608 end  623 total  663           clock   60.0Hz
  800x600 (0x44)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  800x600 (0x45)   36.0MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock   35.2KHz
        v: height  600 start  601 end  603 total  625           clock   56.2Hz
  640x480 (0x46)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz

**jim@Inspiron-1012:~$** gtf 1366 768 60

  # 1368x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 85.86 MHz
  Modeline "1368x768_60.00"  85.86  1368 1440 1584 1800  768 769 772 795  -HSync +Vsync

**jim@Inspiron-1012:~$** xrandr --newmode "1368x768_60.00"  85.86  1368 1440 1584 1800  768 769 772 795  -HSync +Vsync

**jim@Inspiron-1012:~$** xrandr --addmode LVDS1 1368x768_60.00
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  25
  Current serial number in output stream:  26
```

So far Google has failed me. I've seen lots of posts with this error for people trying to rotate their screens, and others using ATI drivers. I've even seen plenty of bug reports. Just no answers.

(Interestingly "xrandr --output LVDS1 --scale 1.5x1.5" works, and I get a very high resolution. However, this doesn't look great and also isn't the optimum resolution of 1366x768, and even if I could get 1366x768 by this method I have no idea how to automate it on boot up).

I then tried creating my own /etc/X11/xorg.conf. Ubuntu 10.10 does not come with one by default, so I had to create one manually:

  1. Whilst the machine is booting up, hold down shift and go into the recovery mode.
  2. Then drop into a root shell.
  3. sudo Xorg -configure
  4. sudo mv xorg.conf.new /etc/X11/xorg.conf
  5. Then edit and add my modeline:

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
	Load  "dbe"
	Load  "record"
	Load  "glx"
	Load  "dri2"
	Load  "dri"
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
        Modeline "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	BusID       "PCI:0:2:0"
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
                Modes "1360x768_60.00"
	EndSubSection
EndSection
```

However, this has had no effect on the machine at all! I restart the machine the new resolution is not listed in "system > preferences > monitors"!

I'm really stuck now, so if anyone has any ideas I'd be eternally grateful!

Cheers,  Jim

(More data):
```
**jim@Inspiron-1012:~$** lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
07:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
```

---

### Post by JimLeek on 2011-04-11
Bump.

---

### Post by JimLeek on 2011-04-13
Bump.

---

### Post by JimLeek on 2011-04-16
Bump!

---

### Post by Yellow Pasque on 2011-04-16
Note that your xorg.conf modeline uses 1360 instead of 1366/1368. It must be 1368 since generating a modeline with 1366 gives 1368.

EDIT: Also, cvt produces slightly different results than gtf. You may want to try that.

---

### Post by JimLeek on 2011-04-23
Hi Temüjin,

many thanks for your reply!

Have tried both gtf and cvt at 1368 (rather than 1360) but still no joy:

```
jim@Inspiron-1012:~$ cvt 1366x768 60
# 1368x60 50.19 Hz (CVT) hsync: 3.81 kHz; pclk: 6.50 MHz
Modeline "1368x60_60.00"    6.50  1368 1408 1536 1704  60 63 73 76 -hsync +vsync

jim@Inspiron-1012:~$ gtf 1366 768 60

  # 1368x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 85.86 MHz
  Modeline "1368x768_60.00"  85.86  1368 1440 1584 1800  768 769 772 795  -HSync +Vsync
```

Interestingly with these changes whilst I'm booting up my cursor changes from the 'normal' 1024x600 size to a smaller one (maybe the desired 1366x768?).

However, it's like something goes wrong and I briefly get an error flash up and then the login screen shows at 1024x600 resolution.

Once logged in, I still only have a maximum of 1024x600 when i check the available resolutions for my monitor.

Is there any way I can see the error message that flashed up in a logfile? Maybe that might tell me what's going wrong.

Cheers and many thanks,  Jim

---

### Post by JimLeek on 2011-04-23
Just to add, I've just tried looking at my boot log, but nothing:

```
jim@Inspiron-1012:~$ sudo cat /var/log/boot
(Nothing has been logged yet.)
```

Cheers,  Jim

---

### Post by realzippy on 2011-04-23
Change your xorg.conf's monitor section from:

```
Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
        Modeline "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
EndSection
```

to

```
Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
        HorizSync       30.0 - 83.0
        VertRefresh     56.0 - 75.0
        Modeline "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
EndSection
```

Modeline by "cvt",and **adding Vrefresh/Hsync values** should give you a few more resolutions.Delete your old *monitors.xml* before rebooting.

```
rm ~/.config/monitors.xml

```
[B]edit:
[/B]
forgot the *display subsection*:
```
SubSection "Display"
		Viewport   0 0
		Depth     24
                Modes "1360x768_60.00"
	EndSubSection
```

which also should be changed to :

```
SubSection "Display"
		Viewport   0 0
		Depth     24
                Modes "1368x768"
	EndSubSection
```

---

### Post by JimLeek on 2011-05-01
Thanks realzippy for your reply.

Unfortunately still no go. Still no sign of 1366x768 resolution.

Here is my xorg.conf:

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
	Load  "dbe"
	Load  "record"
	Load  "glx"
	Load  "dri2"
	Load  "dri"
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
        HorizSync       30.0 - 83.0
        VertRefresh     56.0 - 75.0
        Modeline "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	BusID       "PCI:0:2:0"
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
                Modes "1368x768"
	EndSubSection
EndSection
```

Thanks again.

Cheers,  Jim

---

### Post by realzippy on 2011-05-02
odd.Show us:

```
cat /var/log/Xorg.0.log
```

---

### Post by JimLeek on 2011-05-03
Hi realzippy,

Here we go:

```
jim@Inspiron-1012:~$ cat /var/log/Xorg.0.log
[    18.157] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    18.157] X Protocol Version 11, Revision 0
[    18.157] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    18.157] Current Operating System: Linux jim-Inspiron-1012 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[    18.157] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=5a875613-f2d3-4b46-aed6-9b3528ed9683 ro quiet splash vt.handoff=7
[    18.157] Build Date: 19 April 2011  03:33:17PM
[    18.157] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[    18.158] Current version of pixman: 0.20.2
[    18.158] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    18.158] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    18.158] (==) Log file: "/var/log/Xorg.0.log", Time: Tue May  3 20:11:30 2011
[    18.159] (==) Using config file: "/etc/X11/xorg.conf"
[    18.159] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    18.161] (==) ServerLayout "X.org Configured"
[    18.161] (**) |-->Screen "Screen0" (0)
[    18.161] (**) |   |-->Monitor "Monitor0"
[    18.162] (**) |   |-->Device "Card0"
[    18.162] (==) Automatically adding devices
[    18.162] (==) Automatically enabling devices
[    18.163] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    18.163] 	Entry deleted from font path.
[    18.163] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    18.163] 	Entry deleted from font path.
[    18.163] (**) FontPath set to:
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
[    18.163] (**) ModulePath set to "/usr/lib/xorg/modules"
[    18.163] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    18.163] (II) Loader magic: 0x81ffde0
[    18.163] (II) Module ABI versions:
[    18.164] 	X.Org ANSI C Emulation: 0.4
[    18.164] 	X.Org Video Driver: 10.0
[    18.164] 	X.Org XInput driver : 12.3
[    18.164] 	X.Org Server Extension : 5.0
[    18.169] (--) PCI:*(0:0:2:0) 8086:a011:1028:041a rev 0, Mem @ 0xf0200000/524288, 0xd0000000/268435456, 0xf0000000/1048576, I/O @ 0x000018d0/8
[    18.170] (--) PCI: (0:0:2:1) 8086:a012:1028:041a rev 0, Mem @ 0xf0280000/524288
[    18.171] (II) Open ACPI successful (/var/run/acpid.socket)
[    18.171] (II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
[    18.171] (II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
[    18.171] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    18.171] (II) "record" will be loaded. This was enabled by default and also specified in the config file.
[    18.171] (II) "dri" will be loaded. This was enabled by default and also specified in the config file.
[    18.171] (II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
[    18.171] (II) LoadModule: "dbe"
[    18.176] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    18.176] (II) Module dbe: vendor="X.Org Foundation"
[    18.176] 	compiled for 1.10.1, module version = 1.0.0
[    18.176] 	Module class: X.Org Server Extension
[    18.176] 	ABI class: X.Org Server Extension, version 5.0
[    18.177] (II) Loading extension DOUBLE-BUFFER
[    18.177] (II) LoadModule: "record"
[    18.179] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    18.179] (II) Module record: vendor="X.Org Foundation"
[    18.179] 	compiled for 1.10.1, module version = 1.13.0
[    18.179] 	Module class: X.Org Server Extension
[    18.179] 	ABI class: X.Org Server Extension, version 5.0
[    18.179] (II) Loading extension RECORD
[    18.179] (II) LoadModule: "glx"
[    18.180] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    18.181] (II) Module glx: vendor="X.Org Foundation"
[    18.181] 	compiled for 1.10.1, module version = 1.0.0
[    18.181] 	ABI class: X.Org Server Extension, version 5.0
[    18.181] (==) AIGLX enabled
[    18.181] (II) Loading extension GLX
[    18.181] (II) LoadModule: "dri2"
[    18.182] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    18.183] (II) Module dri2: vendor="X.Org Foundation"
[    18.183] 	compiled for 1.10.1, module version = 1.2.0
[    18.183] 	ABI class: X.Org Server Extension, version 5.0
[    18.183] (II) Loading extension DRI2
[    18.183] (II) LoadModule: "dri"
[    18.185] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    18.185] (II) Module dri: vendor="X.Org Foundation"
[    18.185] 	compiled for 1.10.1, module version = 1.0.0
[    18.185] 	ABI class: X.Org Server Extension, version 5.0
[    18.185] (II) Loading extension XFree86-DRI
[    18.186] (II) LoadModule: "extmod"
[    18.188] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    18.188] (II) Module extmod: vendor="X.Org Foundation"
[    18.188] 	compiled for 1.10.1, module version = 1.0.0
[    18.188] 	Module class: X.Org Server Extension
[    18.188] 	ABI class: X.Org Server Extension, version 5.0
[    18.189] (II) Loading extension MIT-SCREEN-SAVER
[    18.189] (II) Loading extension XFree86-VidModeExtension
[    18.189] (II) Loading extension XFree86-DGA
[    18.189] (II) Loading extension DPMS
[    18.189] (II) Loading extension XVideo
[    18.189] (II) Loading extension XVideo-MotionCompensation
[    18.189] (II) Loading extension X-Resource
[    18.189] (II) LoadModule: "intel"
[    18.189] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    18.190] (II) Module intel: vendor="X.Org Foundation"
[    18.190] 	compiled for 1.10.0.902, module version = 2.14.0
[    18.191] 	Module class: X.Org Video Driver
[    18.191] 	ABI class: X.Org Video Driver, version 10.0
[    18.191] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[    18.199] (++) using VT number 7

[    18.213] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    18.214] drmOpenDevice: node name is /dev/dri/card0
[    18.214] drmOpenDevice: open result is 9, (OK)
[    18.214] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    18.214] drmOpenDevice: node name is /dev/dri/card0
[    18.214] drmOpenDevice: open result is 9, (OK)
[    18.214] drmOpenByBusid: drmOpenMinor returns 9
[    18.214] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    18.214] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    18.214] (==) intel(0): RGB weight 888
[    18.214] (==) intel(0): Default visual is TrueColor
[    18.214] (II) intel(0): Integrated Graphics Chipset: Intel(R) Pineview GM
[    18.214] (--) intel(0): Chipset: "Pineview GM"
[    18.215] (**) intel(0): Tiling enabled
[    18.215] (**) intel(0): SwapBuffers wait enabled
[    18.215] (==) intel(0): video overlay key set to 0x101fe
[    18.215] (II) intel(0): Output LVDS1 using monitor section Monitor0
[    18.216] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    18.248] (II) intel(0): Output VGA1 has no monitor section
[    18.248] (II) intel(0): EDID for output LVDS1
[    18.248] (II) intel(0): Manufacturer: CMO  Model: 1004  Serial#: 0
[    18.248] (II) intel(0): Year: 2009  Week: 10
[    18.248] (II) intel(0): EDID Version: 1.3
[    18.248] (II) intel(0): Digital Display Input
[    18.248] (II) intel(0): Max Image Size [cm]: horiz.: 22  vert.: 12
[    18.248] (II) intel(0): Gamma: 2.20
[    18.249] (II) intel(0): No DPMS capabilities specified
[    18.249] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    18.249] (II) intel(0): First detailed timing is preferred mode
[    18.249] (II) intel(0): redX: 0.565 redY: 0.348   greenX: 0.343 greenY: 0.585
[    18.249] (II) intel(0): blueX: 0.161 blueY: 0.121   whiteX: 0.313 whiteY: 0.329
[    18.249] (II) intel(0): Manufacturer's mask: 0
[    18.249] (II) intel(0): Supported detailed timing:
[    18.249] (II) intel(0): clock: 57.9 MHz   Image Size:  222 x 125 mm
[    18.249] (II) intel(0): h_active: 1024  h_sync: 1153  h_sync_end 1239 h_blank_end 1455 h_border: 0
[    18.249] (II) intel(0): v_active: 600  v_sync: 608  v_sync_end 623 v_blanking: 663 v_border: 0
[    18.249] (II) intel(0):  J1J93&#65533;N101L6
[    18.249] (II) intel(0): Unknown vendor-specific block 0
[    18.249] (II) intel(0): EDID (in hex):
[    18.250] (II) intel(0): 	00ffffffffffff000daf041000000000
[    18.250] (II) intel(0): 	0a13010390160c780acf459059579529
[    18.250] (II) intel(0): 	1f505400000001010101010101010101
[    18.250] (II) intel(0): 	0101010101019c1600af41583f208156
[    18.250] (II) intel(0): 	8f00de7d0000001a0000000000000000
[    18.250] (II) intel(0): 	00000000000000000000000000fe004a
[    18.250] (II) intel(0): 	314a3933804e3130314c360a00000000
[    18.250] (II) intel(0): 	00000000000000000001010a20200061
[    18.250] (II) intel(0): EDID vendor "CMO", prod id 4100
[    18.250] (II) intel(0): Printing DDC gathered Modelines:
[    18.250] (II) intel(0): Modeline "1024x600"x0.0   57.88  1024 1153 1239 1455  600 608 623 663 +hsync -vsync (39.8 kHz)
[    18.251] (II) intel(0): Not using mode "1368x768_60.00" (exceeds panel dimensions)
[    18.251] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    18.251] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    18.251] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    18.251] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    18.251] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    18.251] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    18.252] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    18.252] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    18.252] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    18.252] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    18.252] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    18.252] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    18.252] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    18.252] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    18.252] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    18.252] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    18.252] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    18.252] (II) intel(0): Printing probed modes for output LVDS1
[    18.252] (II) intel(0): Modeline "1024x600"x60.0   57.88  1024 1153 1239 1455  600 608 623 663 +hsync -vsync (39.8 kHz)
[    18.252] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    18.253] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    18.253] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    18.284] (II) intel(0): EDID for output VGA1
[    18.284] (II) intel(0): Output LVDS1 connected
[    18.284] (II) intel(0): Output VGA1 disconnected
[    18.284] (II) intel(0): Using exact sizes for initial modes
[    18.284] (II) intel(0): Output LVDS1 using initial mode 1024x600
[    18.284] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    18.284] (II) intel(0): Kernel page flipping support detected, enabling
[    18.285] (**) intel(0): Display dimensions: (220, 120) mm
[    18.285] (**) intel(0): DPI set to (118, 126)
[    18.285] (II) Loading sub module "fb"
[    18.285] (II) LoadModule: "fb"
[    18.286] (II) Loading /usr/lib/xorg/modules/libfb.so
[    18.286] (II) Module fb: vendor="X.Org Foundation"
[    18.286] 	compiled for 1.10.1, module version = 1.0.0
[    18.286] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    18.286] (==) Depth 24 pixmap format is 32 bpp
[    18.286] (==) intel(0): VideoRam: 262144 KB
[    18.287] (II) intel(0): [DRI2] Setup complete
[    18.287] (II) intel(0): [DRI2]   DRI driver: i915
[    18.288] (II) intel(0): Allocated new frame buffer 1024x600 stride 4096, tiled
[    18.289] (II) UXA(0): Driver registered support for the following operations:
[    18.289] (II)         solid
[    18.289] (II)         copy
[    18.289] (II)         composite (RENDER acceleration)
[    18.289] (II)         put_image
[    18.289] (II)         get_image
[    18.289] (==) intel(0): Backing store disabled
[    18.289] (==) intel(0): Silken mouse enabled
[    18.289] (II) intel(0): Initializing HW Cursor
[    18.316] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    18.318] (==) intel(0): DPMS enabled
[    18.318] (==) intel(0): Intel XvMC decoder disabled
[    18.318] (II) intel(0): Set up textured video
[    18.318] (II) intel(0): Set up overlay video
[    18.318] (II) intel(0): direct rendering: DRI2 Enabled
[    18.319] (==) intel(0): hotplug detection: "enabled"
[    18.319] (--) RandR disabled
[    18.319] (II) Initializing built-in extension Generic Event Extension
[    18.319] (II) Initializing built-in extension SHAPE
[    18.319] (II) Initializing built-in extension MIT-SHM
[    18.319] (II) Initializing built-in extension XInputExtension
[    18.319] (II) Initializing built-in extension XTEST
[    18.319] (II) Initializing built-in extension BIG-REQUESTS
[    18.319] (II) Initializing built-in extension SYNC
[    18.319] (II) Initializing built-in extension XKEYBOARD
[    18.319] (II) Initializing built-in extension XC-MISC
[    18.319] (II) Initializing built-in extension SECURITY
[    18.319] (II) Initializing built-in extension XINERAMA
[    18.319] (II) Initializing built-in extension XFIXES
[    18.319] (II) Initializing built-in extension RENDER
[    18.320] (II) Initializing built-in extension RANDR
[    18.320] (II) Initializing built-in extension COMPOSITE
[    18.320] (II) Initializing built-in extension DAMAGE
[    18.320] (II) Initializing built-in extension GESTURE
[    18.435] (II) AIGLX: Trying DRI driver /usr/lib/dri/i915_dri.so
[    18.484] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    18.484] (II) AIGLX: enabled GLX_INTEL_swap_event
[    18.484] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    18.484] (II) AIGLX: enabled GLX_SGI_make_current_read
[    18.484] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    18.485] (II) AIGLX: Loaded and initialized i915
[    18.485] (II) GLX: Initialized DRI2 GL provider for screen 0
[    18.489] (II) intel(0): Setting screen physical size to 270 x 158
[    18.664] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    18.693] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    18.705] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.705] (II) LoadModule: "evdev"
[    18.706] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.706] (II) Module evdev: vendor="X.Org Foundation"
[    18.707] 	compiled for 1.10.0.902, module version = 2.6.0
[    18.707] 	Module class: X.Org XInput Driver
[    18.707] 	ABI class: X.Org XInput driver, version 12.3
[    18.707] (II) Using input driver 'evdev' for 'Power Button'
[    18.707] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.707] (**) Power Button: always reports core events
[    18.707] (**) Power Button: Device: "/dev/input/event2"
[    18.708] (--) Power Button: Found keys
[    18.708] (II) Power Button: Configuring as keyboard
[    18.708] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    18.708] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    18.708] (**) Option "xkb_rules" "evdev"
[    18.708] (**) Option "xkb_model" "pc105"
[    18.708] (**) Option "xkb_layout" "gb"
[    18.717] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[    18.720] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    18.721] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    18.721] (II) Using input driver 'evdev' for 'Video Bus'
[    18.721] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.721] (**) Video Bus: always reports core events
[    18.721] (**) Video Bus: Device: "/dev/input/event6"
[    18.721] (--) Video Bus: Found keys
[    18.721] (II) Video Bus: Configuring as keyboard
[    18.721] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6/event6"
[    18.721] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    18.721] (**) Option "xkb_rules" "evdev"
[    18.721] (**) Option "xkb_model" "pc105"
[    18.721] (**) Option "xkb_layout" "gb"
[    18.723] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    18.723] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.723] (II) Using input driver 'evdev' for 'Power Button'
[    18.723] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.723] (**) Power Button: always reports core events
[    18.723] (**) Power Button: Device: "/dev/input/event1"
[    18.724] (--) Power Button: Found keys
[    18.724] (II) Power Button: Configuring as keyboard
[    18.724] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0C:00/input/input1/event1"
[    18.724] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    18.724] (**) Option "xkb_rules" "evdev"
[    18.724] (**) Option "xkb_model" "pc105"
[    18.724] (**) Option "xkb_layout" "gb"
[    18.850] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    18.851] (II) No input driver/identifier specified (ignoring)
[    18.859] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event7)
[    18.859] (II) No input driver/identifier specified (ignoring)
[    18.860] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event8)
[    18.860] (II) No input driver/identifier specified (ignoring)
[    18.868] (II) config/udev: Adding input device Laptop_Integrated_Webcam_1.3M (/dev/input/event4)
[    18.868] (**) Laptop_Integrated_Webcam_1.3M: Applying InputClass "evdev keyboard catchall"
[    18.868] (II) Using input driver 'evdev' for 'Laptop_Integrated_Webcam_1.3M'
[    18.868] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.868] (**) Laptop_Integrated_Webcam_1.3M: always reports core events
[    18.868] (**) Laptop_Integrated_Webcam_1.3M: Device: "/dev/input/event4"
[    18.876] (--) Laptop_Integrated_Webcam_1.3M: Found keys
[    18.876] (II) Laptop_Integrated_Webcam_1.3M: Configuring as keyboard
[    18.876] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/input/input4/event4"
[    18.876] (II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_1.3M" (type: KEYBOARD)
[    18.876] (**) Option "xkb_rules" "evdev"
[    18.876] (**) Option "xkb_model" "pc105"
[    18.876] (**) Option "xkb_layout" "gb"
[    18.889] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    18.889] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    18.889] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    18.889] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.889] (**) AT Translated Set 2 keyboard: always reports core events
[    18.889] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    18.889] (--) AT Translated Set 2 keyboard: Found keys
[    18.889] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    18.889] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    18.890] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    18.890] (**) Option "xkb_rules" "evdev"
[    18.890] (**) Option "xkb_model" "pc105"
[    18.890] (**) Option "xkb_layout" "gb"
[    18.892] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[    18.892] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    18.892] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    18.892] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Dell Inspiron embedded buttons quirks"
[    18.892] (II) LoadModule: "synaptics"
[    18.893] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    18.893] (II) Module synaptics: vendor="X.Org Foundation"
[    18.893] 	compiled for 1.10.0.902, module version = 1.3.99
[    18.893] 	Module class: X.Org XInput Driver
[    18.893] 	ABI class: X.Org XInput driver, version 12.3
[    18.893] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    18.893] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    18.894] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    18.894] (**) Option "Device" "/dev/input/event5"
[    18.900] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5590
[    18.900] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4710
[    18.900] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    18.900] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    18.900] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    18.900] (**) Option "AreaBottomEdge" "4100"
[    18.900] (**) Option "JumpyCursorThreshold" "90"
[    18.908] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    18.908] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    18.916] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event5"
[    18.916] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    18.916] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    18.916] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    18.916] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.038
[    18.916] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    18.917] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    18.917] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    18.917] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    18.922] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    18.923] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    18.923] (II) No input driver/identifier specified (ignoring)
[    19.951] (II) intel(0): EDID vendor "CMO", prod id 4100
[    19.951] (II) intel(0): Printing DDC gathered Modelines:
[    19.951] (II) intel(0): Modeline "1024x600"x0.0   57.88  1024 1153 1239 1455  600 608 623 663 +hsync -vsync (39.8 kHz)
[    19.988] (II) intel(0): EDID vendor "CMO", prod id 4100
[    19.988] (II) intel(0): Printing DDC gathered Modelines:
[    19.988] (II) intel(0): Modeline "1024x600"x0.0   57.88  1024 1153 1239 1455  600 608 623 663 +hsync -vsync (39.8 kHz)
[    20.029] (II) intel(0): EDID vendor "CMO", prod id 4100
[    20.029] (II) intel(0): Printing DDC gathered Modelines:
[    20.029] (II) intel(0): Modeline "1024x600"x0.0   57.88  1024 1153 1239 1455  600 608 623 663 +hsync -vsync (39.8 kHz)
[    20.062] (II) intel(0): EDID vendor "CMO", prod id 4100
[    20.062] (II) intel(0): Printing DDC gathered Modelines:
[    20.063] (II) intel(0): Modeline "1024x600"x0.0   57.88  1024 1153 1239 1455  600 608 623 663 +hsync -vsync (39.8 kHz)
[    21.787] (II) intel(0): EDID vendor "CMO", prod id 4100
[    21.788] (II) intel(0): Printing DDC gathered Modelines:
[    21.788] (II) intel(0): Modeline "1024x600"x0.0   57.88  1024 1153 1239 1455  600 608 623 663 +hsync -vsync (39.8 kHz)
[    34.963] (II) intel(0): EDID vendor "CMO", prod id 4100
[    34.963] (II) intel(0): Printing DDC gathered Modelines:
[    34.963] (II) intel(0): Modeline "1024x600"x0.0   57.88  1024 1153 1239 1455  600 608 623 663 +hsync -vsync (39.8 kHz)
[    35.006] (II) intel(0): EDID vendor "CMO", prod id 4100
[    35.006] (II) intel(0): Printing DDC gathered Modelines:
[    35.006] (II) intel(0): Modeline "1024x600"x0.0   57.88  1024 1153 1239 1455  600 608 623 663 +hsync -vsync (39.8 kHz)
[    35.038] (II) intel(0): EDID vendor "CMO", prod id 4100
[    35.039] (II) intel(0): Printing DDC gathered Modelines:
[    35.039] (II) intel(0): Modeline "1024x600"x0.0   57.88  1024 1153 1239 1455  600 608 623 663 +hsync -vsync (39.8 kHz)
[    35.841] (II) intel(0): EDID vendor "CMO", prod id 4100
[    35.841] (II) intel(0): Printing DDC gathered Modelines:
[    35.841] (II) intel(0): Modeline "1024x600"x0.0   57.88  1024 1153 1239 1455  600 608 623 663 +hsync -vsync (39.8 kHz)
[    38.333] (II) intel(0): EDID vendor "CMO", prod id 4100
[    38.334] (II) intel(0): Printing DDC gathered Modelines:
[    38.334] (II) intel(0): Modeline "1024x600"x0.0   57.88  1024 1153 1239 1455  600 608 623 663 +hsync -vsync (39.8 kHz)
[    41.684] (II) intel(0): EDID vendor "CMO", prod id 4100
[    41.685] (II) intel(0): Printing DDC gathered Modelines:
[    41.685] (II) intel(0): Modeline "1024x600"x0.0   57.88  1024 1153 1239 1455  600 608 623 663 +hsync -vsync (39.8 kHz)
[   454.813] (II) intel(0): EDID vendor "CMO", prod id 4100
[   454.813] (II) intel(0): Printing DDC gathered Modelines:
[   454.813] (II) intel(0): Modeline "1024x600"x0.0   57.88  1024 1153 1239 1455  600 608 623 663 +hsync -vsync (39.8 kHz)
[   917.749] (II) intel(0): EDID vendor "CMO", prod id 4100
[   917.749] (II) intel(0): Printing DDC gathered Modelines:
[   917.749] (II) intel(0): Modeline "1024x600"x0.0   57.88  1024 1153 1239 1455  600 608 623 663 +hsync -vsync (39.8 kHz)
[   917.793] (II) intel(0): EDID vendor "CMO", prod id 4100
[   917.794] (II) intel(0): Printing DDC gathered Modelines:
[   917.794] (II) intel(0): Modeline "1024x600"x0.0   57.88  1024 1153 1239 1455  600 608 623 663 +hsync -vsync (39.8 kHz)
```

Cheers,  Jim

---

### Post by Yellow Pasque on 2011-05-03
Your display is only spec'd for 1024x600: [http://www.dell.com/us/p/inspiron-mini1012/pd.aspx?c=us&l=en&s=dhs&cs=19&redirect=1](http://www.dell.com/us/p/inspiron-mini1012/pd.aspx?c=us&l=en&s=dhs&cs=19&redirect=1)

---

### Post by JimLeek on 2011-05-12
You are right, just checked my dell service tag and got the following results for my machine spec:

Liquid Crystal Display,10.1WSVGA,Top Latch,V2,Industry Standard Panel/Display,Samsung

Amazing as Ubuntu is, it can't make a WSVGA monitor display HD!

Thanks everyone for all your help!

Jim

---

