---
title: "My touchpad is not working at all"
date: 2010-05-26
forum: Hardware
---

### Post by fedemw on 2010-05-26
Hello people,


Running version 10 Lucid, I'm getting this error when opening synaptic touchpad control screen on the menu:

[b]
GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics[/b]

The device is completely death.

xorg.conf IS COPIED at /ETC/X11/

```
more xorg.conf 
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
	Load  "dri"
	Load  "record"
	Load  "glx"
	Load  "extmod"
	Load  "dri2"
	Load  "dbe"
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

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "SHMConfig"             "True"
        Option          "HorizScrollDelta"      "0"
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
	VendorName  "Intel Corporation"
	BoardName   "Mobile GM965/GL960 Integrated Graphics Controller"
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
	EndSubSection
EndSection

```

BOOT LOG FILE

```
   1.
      more /var/log/Xorg.0.log
   2.
       
   3.
      X.Org X Server 1.7.6
   4.
      Release Date: 2010-03-17
   5.
      X Protocol Version 11, Revision 0
   6.
      Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
   7.
      Current Operating System: Linux trainspotting 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686
   8.
      Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=c5a4b223-3c15-4882-a9db-1581fede72fd ro quiet splash
   9.
      Build Date: 23 April 2010  05:11:50PM
  10.
      xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>)
  11.
      Current version of pixman: 0.16.4
  12.
              Before reporting problems, check http://wiki.x.org
  13.
              to make sure that you have the latest version.
  14.
      Markers: (--) probed, (**) from config file, (==) default setting,
  15.
              (++) from command line, (!!) notice, (II) informational,
  16.
              (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
  17.
      (==) Log file: "/var/log/Xorg.0.log", Time: Tue May 25 17:21:57 2010
  18.
      (==) Using config file: "/etc/X11/xorg.conf"
  19.
      (==) Using config directory: "/usr/lib/X11/xorg.conf.d"
  20.
      (==) ServerLayout "X.org Configured"
  21.
      (**) |-->Screen "Screen0" (0)
  22.
      (**) |   |-->Monitor "Monitor0"
  23.
      (**) |   |-->Device "Card0"
  24.
      (**) |-->Input Device "Mouse0"
  25.
      (**) |-->Input Device "Keyboard0"
  26.
      (==) Automatically adding devices
  27.
      (==) Automatically enabling devices
  28.
      (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
  29.
              Entry deleted from font path.
  30.
      (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
  31.
              Entry deleted from font path.
  32.
      (**) FontPath set to:
  33.
              /usr/share/fonts/X11/misc,
  34.
              /usr/share/fonts/X11/100dpi/:unscaled,
  35.
              /usr/share/fonts/X11/75dpi/:unscaled,
  36.
              /usr/share/fonts/X11/Type1,
  37.
              /usr/share/fonts/X11/100dpi,
  38.
              /usr/share/fonts/X11/75dpi,
  39.
              /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
  40.
              built-ins,
  41.
              /usr/share/fonts/X11/misc,
  42.
              /usr/share/fonts/X11/100dpi/:unscaled,
  43.
              /usr/share/fonts/X11/75dpi/:unscaled,
  44.
              /usr/share/fonts/X11/Type1,
  45.
              /usr/share/fonts/X11/100dpi,
  46.
              /usr/share/fonts/X11/75dpi,
  47.
              /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
  48.
              built-ins
  49.
      (**) ModulePath set to "/usr/lib/xorg/modules"
  50.
      (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
  51.
      (WW) Disabling Mouse0
  52.
      (WW) Disabling Keyboard0
  53.
      (II) Loader magic: 0x81f0e80
  54.
      (II) Module ABI versions:
  55.
              X.Org ANSI C Emulation: 0.4
  56.
              X.Org Video Driver: 6.0
  57.
              X.Org XInput driver : 7.0
  58.
              X.Org Server Extension : 2.0
  59.
      (++) using VT number 7
  60.
       
  61.
      (--) PCI:*(0:0:2:0) 8086:2a02:1179:ff50 Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller rev 3, Mem @ 0xf0000000/1048576, 0xd0000000/26843
  62.
      5456, I/O @ 0x00001800/8
  63.
      (--) PCI: (0:0:2:1) 8086:2a03:1179:ff50 Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller rev 3, Mem @ 0xf0100000/1048576
  64.
      (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
  65.
      (II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
  66.
      (II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
  67.
      (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
  68.
      (II) "record" will be loaded. This was enabled by default and also specified in the config file.
  69.
      (II) "dri" will be loaded. This was enabled by default and also specified in the config file.
  70.
      (II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
  71.
      (II) LoadModule: "dri"
  72.
      (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
  73.
      (II) Module dri: vendor="X.Org Foundation"
  74.
              compiled for 1.7.6, module version = 1.0.0
  75.
              ABI class: X.Org Server Extension, version 2.0
  76.
      (II) Loading extension XFree86-DRI
  77.
      (II) LoadModule: "record"
  78.
      (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
  79.
      (II) Module record: vendor="X.Org Foundation"
  80.
              compiled for 1.7.6, module version = 1.13.0
  81.
              Module class: X.Org Server Extension
  82.
              ABI class: X.Org Server Extension, version 2.0
  83.
      (II) Loading extension RECORD
  84.
      (II) LoadModule: "glx"
  85.
      (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
  86.
      (II) Module glx: vendor="X.Org Foundation"
  87.
              compiled for 1.7.6, module version = 1.0.0
  88.
              ABI class: X.Org Server Extension, version 2.0
  89.
      (==) AIGLX enabled
  90.
      (II) Loading extension GLX
  91.
      (II) LoadModule: "extmod"
  92.
      (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
  93.
      (II) Module extmod: vendor="X.Org Foundation"
  94.
              compiled for 1.7.6, module version = 1.0.0
  95.
              Module class: X.Org Server Extension
  96.
              ABI class: X.Org Server Extension, version 2.0
  97.
      (II) Loading extension MIT-SCREEN-SAVER
  98.
      (II) Loading extension XFree86-VidModeExtension
  99.
      (II) Loading extension XFree86-DGA
 100.
      (II) Loading extension DPMS
 101.
      (II) Loading extension XVideo
 102.
      (II) Loading extension XVideo-MotionCompensation
 103.
      (II) Loading extension X-Resource
 104.
      (II) LoadModule: "dri2"
 105.
      (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
 106.
      (II) Module dri2: vendor="X.Org Foundation"
 107.
              compiled for 1.7.6, module version = 1.1.0
 108.
              ABI class: X.Org Server Extension, version 2.0
 109.
      (II) Loading extension DRI2
 110.
      (II) LoadModule: "dbe"
 111.
      (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
 112.
      (II) Module dbe: vendor="X.Org Foundation"
 113.
              compiled for 1.7.6, module version = 1.0.0
 114.
              Module class: X.Org Server Extension
 115.
              ABI class: X.Org Server Extension, version 2.0
 116.
      (II) Loading extension DOUBLE-BUFFER
 117.
      (II) LoadModule: "intel"
 118.
      (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
 119.
      (II) Module intel: vendor="X.Org Foundation"
 120.
              compiled for 1.7.6, module version = 2.9.1
 121.
              Module class: X.Org Video Driver
 122.
              ABI class: X.Org Video Driver, version 6.0
 123.
      (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
 124.
              i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
 125.
              E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
 126.
              965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
 127.
              4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
 128.
      (II) Primary Device is: PCI 00@00:02:0
 129.
      drmOpenDevice: node name is /dev/dri/card0
 130.
      drmOpenDevice: open result is 8, (OK)
 131.
      drmOpenByBusid: Searching for BusID pci:0000:00:02.0
 132.
      drmOpenDevice: node name is /dev/dri/card0
 133.
      drmOpenDevice: open result is 8, (OK)
 134.
      drmOpenByBusid: drmOpenMinor returns 8
 135.
      drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
 136.
      (==) intel(0): Depth 24, (--) framebuffer bpp 32
 137.
      (==) intel(0): RGB weight 888
 138.
      (==) intel(0): Default visual is TrueColor
 139.
      (II) intel(0): Integrated Graphics Chipset: Intel(R) 965GM
 140.
      (--) intel(0): Chipset: "965GM"
 141.
      (II) intel(0): Output VGA1 using monitor section Monitor0
 142.
      (II) intel(0): Output LVDS1 has no monitor section
 143.
      (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
 144.
      (II) intel(0): EDID for output VGA1
 145.
      (II) intel(0): EDID for output LVDS1
 146.
      (II) intel(0): Manufacturer: SEC  Model: 3741  Serial#: 0
 147.
      (II) intel(0): Year: 2007  Week: 0
 148.
      (II) intel(0): EDID Version: 1.3
 149.
      (II) intel(0): Digital Display Input
 150.
      (II) intel(0): Max Image Size [cm]: horiz.: 29  vert.: 18
 151.
      (II) intel(0): Gamma: 2.20
 152.
      (II) intel(0): No DPMS capabilities specified
 153.
      (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4
 154.
      (II) intel(0): First detailed timing is preferred mode
 155.
      (II) intel(0): redX: 0.580 redY: 0.340   greenX: 0.320 greenY: 0.540
 156.
      (II) intel(0): blueX: 0.155 blueY: 0.125   whiteX: 0.313 whiteY: 0.329
 157.
      (II) intel(0): Manufacturer's mask: 0
 158.
      (II) intel(0): Supported detailed timing:
 159.
      (II) intel(0): clock: 71.0 MHz   Image Size:  286 x 179 mm
 160.
      (II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
 161.
      (II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
 162.
      (II) intel(0): Unknown vendor-specific block f
 163.
      (II) intel(0):  SAMSUNG
 164.
      (II) intel(0):  LTN133AT07001
 165.
      (II) intel(0): EDID (in hex):
 166.
      (II) intel(0):  00ffffffffffff004ca3413700000000
 167.
      (II) intel(0):  00110103801d12780a81c59457528a27
 168.
      (II) intel(0):  20505400000001010101010101010101
 169.
      (II) intel(0):  010101010101bc1b00a0502017303020
 170.
      (II) intel(0):  36001eb3100000190000000f00000000
 171.
      (II) intel(0):  00000000002387026400000000fe0053
 172.
      (II) intel(0):  414d53554e470a2020202020000000fe
 173.
      (II) intel(0):  004c544e3133334154303730303100ae
 174.
      (II) intel(0): Not using default mode "320x175" (doublescan mode not supported)
 175.
      (II) intel(0): Not using default mode "320x200" (doublescan mode not supported)
 176.
      (II) intel(0): Not using default mode "360x200" (doublescan mode not supported)
 177.
      (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
 178.
      (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
 179.
      (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
 180.
      (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
 181.
      (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
 182.
      (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
 183.
      (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
 184.
      (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
 185.
      (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
 186.
      (II) intel(0): Not using default mode "1024x768" (interlace mode not supported)
 187.
      (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
 188.
      (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
 189.
      (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
 190.
      (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
 191.
      (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
 192.
      (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
 193.
      (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
 194.
      (II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
 195.
      (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
 196.
      (II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
 197.
      (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
 198.
      (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
 199.
      (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
 200.
      (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
 201.
      (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
 202.
      (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
 203.
      (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
 204.
      (II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
 205.
      (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
 206.
      (II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
 207.
      (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
 208.
      (II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
 209.
      (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
 210.
      (II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
 211.
      (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
 212.
      (II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
 213.
      (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
 214.
      (II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
 215.
      (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
 216.
      (II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
 217.
      (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
 218.
      (II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
 219.
      (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
 220.
      (II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
 221.
      (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
 222.
      (II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
 223.
      (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
 224.
      (II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
 225.
      (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
 226.
      (II) intel(0): Not using default mode "416x312" (doublescan mode not supported)
 227.
      (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
 228.
      (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
 229.
      (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
 230.
      (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
 231.
      (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
 232.
      (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
 233.
      (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
 234.
      (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
 235.
      (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
 236.
      (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
 237.
      (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
 238.
      (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
 239.
      (II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
 240.
      (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
 241.
      (II) intel(0): Not using default mode "1360x768" (exceeds panel dimensions)
 242.
      (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
 243.
      (II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
 244.
      (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
 245.
      (II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
 246.
      (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
 247.
      (II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
 248.
      (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
 249.
      (II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
 250.
      (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
 251.
      (II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
 252.
      (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
 253.
      (II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
 254.
      (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
 255.
      (II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
 256.
      (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
 257.
      (II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
 258.
      (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
 259.
      (II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
 260.
      (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
 261.
      (II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
 262.
      (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
 263.
      (II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
 264.
      (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
 265.
      (II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
 266.
      (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
 267.
      (II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
 268.
      (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
 269.
      (II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
 270.
      (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
 271.
      (II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
 272.
      (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
 273.
      (II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
 274.
      (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
 275.
      (II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
 276.
      (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
 277.
      (II) intel(0): Printing probed modes for output LVDS1
 278.
      (II) intel(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
 279.
      (II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
 280.
      (II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
 281.
      (II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
 282.
      (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
 283.
      (II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
 284.
      (II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
 285.
      (II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
 286.
      (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
 287.
      (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
 288.
      (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
 289.
      (II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
 290.
      (II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
 291.
      (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
 292.
      (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
 293.
      (II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
 294.
      (II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
 295.
      (II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
 296.
      (II) intel(0): Output VGA1 disconnected
 297.
      (II) intel(0): Output LVDS1 connected
 298.
      (II) intel(0): Using exact sizes for initial modes
 299.
      (II) intel(0): Output LVDS1 using initial mode 1280x800
 300.
      (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
 301.
      (==) intel(0): video overlay key set to 0x101fe
 302.
      (==) intel(0): DPI set to (96, 96)
 303.
      (II) Loading sub module "fb"
 304.
      (II) LoadModule: "fb"
 305.
      (II) Loading /usr/lib/xorg/modules/libfb.so
 306.
      (II) Module fb: vendor="X.Org Foundation"
 307.
              compiled for 1.7.6, module version = 1.0.0
 308.
              ABI class: X.Org ANSI C Emulation, version 0.4
 309.
      (==) Depth 24 pixmap format is 32 bpp
 310.
      (II) intel(0): [DRI2] Setup complete
 311.
      (**) intel(0): Framebuffer compression disabled
 312.
      (**) intel(0): Tiling enabled
 313.
      (**) intel(0): SwapBuffers wait enabled
 314.
      (==) intel(0): VideoRam: 262144 KB
 315.
      (II) intel(0): Attempting memory allocation with tiled buffers.
 316.
      (II) intel(0): Tiled allocation successful.
 317.
      (II) UXA(0): Driver registered support for the following operations:
 318.
      (II)         solid
 319.
      (II)         copy
 320.
      (II)         composite (RENDER acceleration)
 321.
      (==) intel(0): Backing store disabled
 322.
      (==) intel(0): Silken mouse enabled
 323.
      (II) intel(0): Initializing HW Cursor
 324.
      (II) intel(0): No memory allocations
 325.
      (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
 326.
      (==) intel(0): DPMS enabled
 327.
      (==) intel(0): Intel XvMC decoder disabled
 328.
      (II) intel(0): Set up textured video
 329.
      (II) intel(0): Set up overlay video
 330.
      (II) intel(0): direct rendering: DRI2 Enabled
 331.
      (--) RandR disabled
 332.
      (II) Initializing built-in extension Generic Event Extension
 333.
      (II) Initializing built-in extension SHAPE
 334.
      (II) Initializing built-in extension MIT-SHM
 335.
      (II) Initializing built-in extension XInputExtension
 336.
      (II) Initializing built-in extension XTEST
 337.
      (II) Initializing built-in extension BIG-REQUESTS
 338.
      (II) Initializing built-in extension SYNC
 339.
      (II) Initializing built-in extension XKEYBOARD
 340.
      (II) Initializing built-in extension XC-MISC
 341.
      (II) Initializing built-in extension SECURITY
 342.
      (II) Initializing built-in extension XINERAMA
 343.
      (II) Initializing built-in extension XFIXES
 344.
      (II) Initializing built-in extension RENDER
 345.
      (II) Initializing built-in extension RANDR
 346.
      (II) Initializing built-in extension COMPOSITE
 347.
      (II) Initializing built-in extension DAMAGE
 348.
      (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
 349.
      (II) AIGLX: enabled GLX_SGI_make_current_read
 350.
      (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
 351.
      (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
 352.
      (II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
 353.
      (II) GLX: Initialized DRI2 GL provider for screen 0
 354.
      (II) intel(0): Setting screen physical size to 338 x 211
 355.
      (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
 356.
      (II) config/udev: Adding input device Power Button (/dev/input/event2)
 357.
      (**) Power Button: Applying InputClass "evdev keyboard catchall"
 358.
      (II) LoadModule: "evdev"
 359.
      (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
 360.
      (II) Module evdev: vendor="X.Org Foundation"
 361.
              compiled for 1.7.6, module version = 2.3.2
 362.
              Module class: X.Org XInput Driver
 363.
              ABI class: X.Org XInput driver, version 7.0
 364.
      (**) Power Button: always reports core events
 365.
      (**) Power Button: Device: "/dev/input/event2"
 366.
      (II) Power Button: Found keys
 367.
      (II) Power Button: Configuring as keyboard
 368.
      (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
 369.
      (**) Option "xkb_rules" "evdev"
 370.
      (**) Option "xkb_model" "pc105"
 371.
      (**) Option "xkb_layout" "es"
 372.
      (II) XKB: reuse xkmfile /var/lib/xkb/server-FFBD4FDC8093CCB415CD73029FDA64F4B077A3E7.xkm
 373.
      (II) config/udev: Adding input device Video Bus (/dev/input/event6)
 374.
      (**) Video Bus: Applying InputClass "evdev keyboard catchall"
 375.
      (**) Video Bus: always reports core events
 376.
      (**) Video Bus: Device: "/dev/input/event6"
 377.
      (II) Video Bus: Found keys
 378.
      (II) Video Bus: Configuring as keyboard
 379.
      (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
 380.
      (**) Option "xkb_rules" "evdev"
 381.
      (**) Option "xkb_model" "pc105"
 382.
      (**) Option "xkb_layout" "es"
 383.
      (II) config/udev: Adding input device Power Button (/dev/input/event1)
 384.
      (**) Power Button: Applying InputClass "evdev keyboard catchall"
 385.
      (**) Power Button: always reports core events
 386.
      (**) Power Button: Device: "/dev/input/event1"
 387.
      (II) Power Button: Found keys
 388.
      (II) Power Button: Configuring as keyboard
 389.
      (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
 390.
      (**) Option "xkb_rules" "evdev"
 391.
      (**) Option "xkb_model" "pc105"
 392.
      (**) Option "xkb_layout" "es"
 393.
      (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
 394.
      (II) No input driver/identifier specified (ignoring)
 395.
      (II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event8)
 396.
      (II) No input driver/identifier specified (ignoring)
 397.
      (II) config/udev: Adding input device PIXART USB OPTICAL MOUSE (/dev/input/event5)
 398.
      (**) PIXART USB OPTICAL MOUSE: Applying InputClass "evdev pointer catchall"
 399.
      (**) PIXART USB OPTICAL MOUSE: always reports core events
 400.
      (**) PIXART USB OPTICAL MOUSE: Device: "/dev/input/event5"
 401.
      (II) PIXART USB OPTICAL MOUSE: Found 3 mouse buttons
 402.
      (II) PIXART USB OPTICAL MOUSE: Found scroll wheel(s)
 403.
      (II) PIXART USB OPTICAL MOUSE: Found relative axes
 404.
      (II) PIXART USB OPTICAL MOUSE: Found x and y relative axes
 405.
      (II) PIXART USB OPTICAL MOUSE: Configuring as mouse
 406.
      (**) PIXART USB OPTICAL MOUSE: YAxisMapping: buttons 4 and 5
 407.
      (**) PIXART USB OPTICAL MOUSE: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
 408.
      (II) XINPUT: Adding extended input device "PIXART USB OPTICAL MOUSE" (type: MOUSE)
 409.
      (II) PIXART USB OPTICAL MOUSE: initialized for relative axes.
 410.
      (II) config/udev: Adding input device PIXART USB OPTICAL MOUSE (/dev/input/mouse1)
 411.
      (II) No input driver/identifier specified (ignoring)
 412.
      (II) config/udev: Adding input device Chicony USB 2.0 Camera (/dev/input/event7)
 413.
      (**) Chicony USB 2.0 Camera: Applying InputClass "evdev keyboard catchall"
 414.
      (**) Chicony USB 2.0 Camera: always reports core events
 415.
      (**) Chicony USB 2.0 Camera: Device: "/dev/input/event7"
 416.
      (II) Chicony USB 2.0 Camera: Found keys
 417.
      (II) Chicony USB 2.0 Camera: Configuring as keyboard
 418.
      (II) XINPUT: Adding extended input device "Chicony USB 2.0 Camera" (type: KEYBOARD)
 419.
      (**) Option "xkb_rules" "evdev"
 420.
      (**) Option "xkb_model" "pc105"
 421.
      (**) Option "xkb_layout" "es"
 422.
      (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
 423.
      (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
 424.
      (**) AT Translated Set 2 keyboard: always reports core events
 425.
      (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
 426.
      (II) AT Translated Set 2 keyboard: Found keys
 427.
      (II) AT Translated Set 2 keyboard: Configuring as keyboard
 428.
      (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
 429.
      (**) Option "xkb_rules" "evdev"
 430.
      (**) Option "xkb_model" "pc105"
 431.
      (**) Option "xkb_layout" "es"
 432.
      (II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event3)
 433.
      (**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
 434.
      (**) Macintosh mouse button emulation: always reports core events
 435.
      (**) Macintosh mouse button emulation: Device: "/dev/input/event3"
 436.
      (II) Macintosh mouse button emulation: Found 3 mouse buttons
 437.
      (II) Macintosh mouse button emulation: Found relative axes
 438.
      (II) Macintosh mouse button emulation: Found x and y relative axes
 439.
      (II) Macintosh mouse button emulation: Configuring as mouse
 440.
      (**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
 441.
      (**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
 442.
      (II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
 443.
      (II) Macintosh mouse button emulation: initialized for relative axes.
 444.
      (II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
 445.
      (II) No input driver/identifier specified (ignoring)
 446.
      (II) intel(0): EDID vendor "SEC", prod id 14145
 447.
      (II) intel(0): Printing DDC gathered Modelines:
 448.
      (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
 449.
      (II) intel(0): EDID vendor "SEC", prod id 14145
 450.
      (II) intel(0): Printing DDC gathered Modelines:
 451.
      (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
 452.
      (II) intel(0): EDID vendor "SEC", prod id 14145
 453.
      (II) intel(0): Printing DDC gathered Modelines:
 454.
      (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
 455.
      (II) intel(0): EDID vendor "SEC", prod id 14145
 456.
      (II) intel(0): Printing DDC gathered Modelines:
 457.
      (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
 458.
      (II) intel(0): EDID vendor "SEC", prod id 14145
 459.
      (II) intel(0): Printing DDC gathered Modelines:
 460.
      (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
 461.
      (II) intel(0): EDID vendor "SEC", prod id 14145
 462.
      (II) intel(0): Printing DDC gathered Modelines:
 463.
      (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
 464.
      (II) intel(0): EDID vendor "SEC", prod id 14145
 465.
      (II) intel(0): Printing DDC gathered Modelines:
 466.
      (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
 467.
      (II) intel(0): EDID vendor "SEC", prod id 14145
 468.
      (II) intel(0): Printing DDC gathered Modelines:
 469.
      (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
 470.
      (II) intel(0): EDID vendor "SEC", prod id 14145
 471.
      (II) intel(0): Printing DDC gathered Modelines:
 472.
      (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
```


Could you help me please? I'm driving crazy without touchpad :(

Thanks for your help team,

Best regards,

---

