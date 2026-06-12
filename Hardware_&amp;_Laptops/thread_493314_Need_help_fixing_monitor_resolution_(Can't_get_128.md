---
title: "Need help fixing monitor resolution (Can't get 1280x1024)"
date: 2007-07-05
forum: Hardware &amp; Laptops
---

### Post by estebanf on 2007-07-05
This is my first post here so let's hope I'm following the correct code of conduct... And thanks for reading and trying to help me solve my issue.

I need to make ubuntu work in 1280x1024@70hz. I know it has been asked several times, but I can't apply any of the solutions found in the forums, google or [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto).

I must admit I'm a really newbie. I applied the latest nvidia binaries drives as explained in [http://doc.gwos.org/index.php/Latest_nvidia_feisty#METHOD_2](http://doc.gwos.org/index.php/Latest_nvidia_feisty#METHOD_2). I couldn't use nv drives as my card is not supported and after two attempts I only got a not working xserver and I didn't know how to fix it without reinstalling. 

I've been trying to modify xorg.conf by hand, copy and paste, dpkg-reconfigure and nvidia-config for 2 days. With my current version I can see the 1280x1024 resolution in the /System/Preferences/Screen Resolution shortcut but only changes the virtual size and not the actual resolution. There's no option for 1280x1024 in nvidia-settings. This is my current xorg.conf:

> 
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "dbe"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "record"
    Load           "v4l"
    Load           "vbe"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "latam"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Monitor0"
  vendorname "Samsung"
  modelname "Samsung SyncMaster 910N/912N"
  HorizSync 30-81
  VertRefresh 56-85
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  gamma 1.0
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "UseEdidFreqs" "false"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024@75" "1280x1024@60" "1024x768@60" "1024x768@70" "1024x768@75" "800x600@60" "640x480@60"
        Virtual     1280 1024
    EndSubSection
EndSection


I have a mb ASUS M2N-SLI DELUXE Socket AM2 NVIDIA nForce 570 SLI, a gpu XFX GeFORCE 8500GT DDR2 (no SLI)  and 2gb Ddr2 800 Mhz. 

Thanks for any help. If you want to see any other log, please let me know. :p

Regards,

Esteban

---

### Post by estebanf on 2007-07-05
My xorg.0.log reads:

```
X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux esteban-desktop 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jul  5 16:46:54 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Videocard0"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
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
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "Xinerama" "0"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,0369 card 1043,8239 rev a1 class 05,00,00 hdr 00
(II) PCI: 00:01:0: chip 10de,0360 card 1043,8239 rev a2 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0368 card 1043,8239 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:01:2: chip 10de,036a card 1043,8239 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:02:0: chip 10de,036c card 1043,8239 rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,036d card 1043,8239 rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,036e card 1043,8239 rev a1 class 01,01,8a hdr 00
(II) PCI: 00:05:0: chip 10de,037f card 1043,8239 rev a2 class 01,04,85 hdr 80
(II) PCI: 00:05:1: chip 10de,037f card 1043,8239 rev a2 class 01,04,85 hdr 80
(II) PCI: 00:05:2: chip 10de,037f card 1043,8239 rev a2 class 01,04,85 hdr 80
(II) PCI: 00:06:0: chip 10de,0370 card 0000,0000 rev a2 class 06,04,01 hdr 81
(II) PCI: 00:06:1: chip 10de,0371 card 1043,81f6 rev a2 class 04,03,00 hdr 80
(II) PCI: 00:08:0: chip 10de,0373 card 1043,8239 rev a2 class 06,80,00 hdr 00
(II) PCI: 00:09:0: chip 10de,0373 card 1043,8239 rev a2 class 06,80,00 hdr 00
(II) PCI: 00:0a:0: chip 10de,0376 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0b:0: chip 10de,0374 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0c:0: chip 10de,0374 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0d:0: chip 10de,0378 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,0375 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0f:0: chip 10de,0377 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:0b:0: chip 104c,8023 card 1043,808b rev 00 class 0c,00,10 hdr 00
(II) PCI: 06:00:0: chip 197b,2363 card 1043,81e4 rev 03 class 01,06,01 hdr 80
(II) PCI: 06:00:1: chip 197b,2363 card 1043,81e4 rev 03 class 01,01,85 hdr 00
(II) PCI: 07:00:0: chip 10de,0421 card 1682,2305 rev a1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:6:0), (0,1,1), BCTRL: 0x0a04 (VGA_EN is cleared)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfde00000 - 0xfdefffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:10:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:11:0), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:12:0), (0,4,4), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:13:0), (0,5,5), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 6: bridge is at (0:14:0), (0,6,6), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 6 I/O range:
	[0] -1	0	0x00008000 - 0x000080ff (0x100) IX[B]
	[1] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[2] -1	0	0x00008800 - 0x000088ff (0x100) IX[B]
	[3] -1	0	0x00008c00 - 0x00008cff (0x100) IX[B]
	[4] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[5] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[6] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[7] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
(II) Bus 6 non-prefetchable memory range:
	[0] -1	0	0xfdd00000 - 0xfddfffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 7: bridge is at (0:15:0), (0,7,7), BCTRL: 0x001c (VGA_EN is set)
(II) Bus 7 I/O range:
	[0] -1	0	0x00007000 - 0x000070ff (0x100) IX[B]
	[1] -1	0	0x00007400 - 0x000074ff (0x100) IX[B]
	[2] -1	0	0x00007800 - 0x000078ff (0x100) IX[B]
	[3] -1	0	0x00007c00 - 0x00007cff (0x100) IX[B]
(II) Bus 7 non-prefetchable memory range:
	[0] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B]
(II) Bus 7 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,7), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(--) PCI:*(7:0:0) nVidia Corporation unknown chipset (0x0421) rev 161, Mem @ 0xfa000000/24, 0xe0000000/28, 0xf8000000/25, I/O @ 0x7c00/7, BIOS @ 0xfbfe0000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xfddfe000 - 0xfddfffff (0x2000) MX[B]
	[1] -1	0	0xfdef8000 - 0xfdefbfff (0x4000) MX[B]
	[2] -1	0	0xfdeff000 - 0xfdeff7ff (0x800) MX[B]
	[3] -1	0	0xfe025000 - 0xfe02500f (0x10) MX[B]
	[4] -1	0	0xfe026000 - 0xfe0260ff (0x100) MX[B]
	[5] -1	0	0xfe027000 - 0xfe027fff (0x1000) MX[B]
	[6] -1	0	0xfe028000 - 0xfe02800f (0x10) MX[B]
	[7] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[8] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[9] -1	0	0xfe020000 - 0xfe023fff (0x4000) MX[B]
	[10] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[11] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[12] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[13] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[14] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[15] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[16] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[17] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[18] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[19] -1	0	0x00008c00 - 0x00008c0f (0x10) IX[B]
	[20] -1	0	0x00009000 - 0x00009003 (0x4) IX[B]
	[21] -1	0	0x00009400 - 0x00009407 (0x8) IX[B]
	[22] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[23] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[24] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[25] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[26] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[27] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[28] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[29] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[30] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[31] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[32] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[33] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[34] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[35] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[36] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[37] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[38] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[39] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[40] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[41] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[42] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[43] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[44] -1	0	0x0000fc00 - 0x0000fc3f (0x40) IX[B]
	[45] -1	0	0x00007c00 - 0x00007c7f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfddfe000 - 0xfddfffff (0x2000) MX[B]
	[1] -1	0	0xfdef8000 - 0xfdefbfff (0x4000) MX[B]
	[2] -1	0	0xfdeff000 - 0xfdeff7ff (0x800) MX[B]
	[3] -1	0	0xfe025000 - 0xfe02500f (0x10) MX[B]
	[4] -1	0	0xfe026000 - 0xfe0260ff (0x100) MX[B]
	[5] -1	0	0xfe027000 - 0xfe027fff (0x1000) MX[B]
	[6] -1	0	0xfe028000 - 0xfe02800f (0x10) MX[B]
	[7] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[8] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[9] -1	0	0xfe020000 - 0xfe023fff (0x4000) MX[B]
	[10] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[11] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[12] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[13] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[14] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[15] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[16] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[17] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[18] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[19] -1	0	0x00008c00 - 0x00008c0f (0x10) IX[B]
	[20] -1	0	0x00009000 - 0x00009003 (0x4) IX[B]
	[21] -1	0	0x00009400 - 0x00009407 (0x8) IX[B]
	[22] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[23] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[24] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[25] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[26] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[27] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[28] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[29] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[30] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[31] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[32] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[33] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[34] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[35] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[36] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[37] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[38] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[39] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[40] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[41] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[42] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[43] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[44] -1	0	0x0000fc00 - 0x0000fc3f (0x40) IX[B]
	[45] -1	0	0x00007c00 - 0x00007c7f (0x80) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfddfe000 - 0xfddfffff (0x2000) MX[B]
	[5] -1	0	0xfdef8000 - 0xfdefbfff (0x4000) MX[B]
	[6] -1	0	0xfdeff000 - 0xfdeff7ff (0x800) MX[B]
	[7] -1	0	0xfe025000 - 0xfe02500f (0x10) MX[B]
	[8] -1	0	0xfe026000 - 0xfe0260ff (0x100) MX[B]
	[9] -1	0	0xfe027000 - 0xfe027fff (0x1000) MX[B]
	[10] -1	0	0xfe028000 - 0xfe02800f (0x10) MX[B]
	[11] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[12] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[13] -1	0	0xfe020000 - 0xfe023fff (0x4000) MX[B]
	[14] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[15] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[16] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[17] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[18] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[19] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[20] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[21] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[22] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x00008c00 - 0x00008c0f (0x10) IX[B]
	[26] -1	0	0x00009000 - 0x00009003 (0x4) IX[B]
	[27] -1	0	0x00009400 - 0x00009407 (0x8) IX[B]
	[28] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[29] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[30] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[31] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[32] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[33] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[34] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[35] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[36] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[37] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[38] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[39] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[40] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[41] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[42] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[43] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[44] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[45] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[46] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[47] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[48] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[49] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[50] -1	0	0x0000fc00 - 0x0000fc3f (0x40) IX[B]
	[51] -1	0	0x00007c00 - 0x00007c7f (0x80) IX[B](B)
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
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
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  100.14.11  Wed Jun 13 18:58:58 PDT 2007
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.1
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) v4l driver for Video4Linux
(II) NVIDIA dlloader X Driver  100.14.11  Wed Jun 13 18:23:34 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 07:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
	compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfddfe000 - 0xfddfffff (0x2000) MX[B]
	[5] -1	0	0xfdef8000 - 0xfdefbfff (0x4000) MX[B]
	[6] -1	0	0xfdeff000 - 0xfdeff7ff (0x800) MX[B]
	[7] -1	0	0xfe025000 - 0xfe02500f (0x10) MX[B]
	[8] -1	0	0xfe026000 - 0xfe0260ff (0x100) MX[B]
	[9] -1	0	0xfe027000 - 0xfe027fff (0x1000) MX[B]
	[10] -1	0	0xfe028000 - 0xfe02800f (0x10) MX[B]
	[11] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[12] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[13] -1	0	0xfe020000 - 0xfe023fff (0x4000) MX[B]
	[14] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[15] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[16] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[17] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[18] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[19] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[20] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[21] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[22] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x00008c00 - 0x00008c0f (0x10) IX[B]
	[26] -1	0	0x00009000 - 0x00009003 (0x4) IX[B]
	[27] -1	0	0x00009400 - 0x00009407 (0x8) IX[B]
	[28] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[29] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[30] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[31] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[32] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[33] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[34] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[35] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[36] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[37] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[38] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[39] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[40] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[41] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[42] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[43] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[44] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[45] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[46] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[47] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[48] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[49] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[50] -1	0	0x0000fc00 - 0x0000fc3f (0x40) IX[B]
	[51] -1	0	0x00007c00 - 0x00007c7f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfddfe000 - 0xfddfffff (0x2000) MX[B]
	[5] -1	0	0xfdef8000 - 0xfdefbfff (0x4000) MX[B]
	[6] -1	0	0xfdeff000 - 0xfdeff7ff (0x800) MX[B]
	[7] -1	0	0xfe025000 - 0xfe02500f (0x10) MX[B]
	[8] -1	0	0xfe026000 - 0xfe0260ff (0x100) MX[B]
	[9] -1	0	0xfe027000 - 0xfe027fff (0x1000) MX[B]
	[10] -1	0	0xfe028000 - 0xfe02800f (0x10) MX[B]
	[11] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[12] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[13] -1	0	0xfe020000 - 0xfe023fff (0x4000) MX[B]
	[14] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[15] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[16] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[17] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[18] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[19] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[20] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[21] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[22] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[23] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[24] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[25] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[28] -1	0	0x00008c00 - 0x00008c0f (0x10) IX[B]
	[29] -1	0	0x00009000 - 0x00009003 (0x4) IX[B]
	[30] -1	0	0x00009400 - 0x00009407 (0x8) IX[B]
	[31] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[32] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[33] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[34] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[35] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[36] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[37] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[38] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[39] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[40] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[41] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[42] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[43] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[44] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[45] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[46] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[47] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[48] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[49] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[50] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[51] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[52] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[53] -1	0	0x0000fc00 - 0x0000fc3f (0x40) IX[B]
	[54] -1	0	0x00007c00 - 0x00007c7f (0x80) IX[B](B)
	[55] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[56] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(**) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "UseEdidFreqs" "false"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
(**) NVIDIA(0):     disabled on all display devices.
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 8500 GT (G86) at PCI:7:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 60.86.34.00.81
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 8500 GT at PCI:7:0:0:
(--) NVIDIA(0):     Samsung (CRT-0)
(--) NVIDIA(0): Samsung (CRT-0): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "1280x1024@75"; removing.
(WW) NVIDIA(0): No valid modes for "1280x1024@60"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1024x768@60"
(II) NVIDIA(0):     "1024x768@70"
(II) NVIDIA(0):     "1024x768@75"
(II) NVIDIA(0):     "800x600@60"
(II) NVIDIA(0):     "640x480@60"
(**) NVIDIA(0): Virtual screen size configured to be 1280 x 1024
(--) NVIDIA(0): DPI set to (86, 84); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B]
	[1] 0	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
	[2] 0	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfddfe000 - 0xfddfffff (0x2000) MX[B]
	[8] -1	0	0xfdef8000 - 0xfdefbfff (0x4000) MX[B]
	[9] -1	0	0xfdeff000 - 0xfdeff7ff (0x800) MX[B]
	[10] -1	0	0xfe025000 - 0xfe02500f (0x10) MX[B]
	[11] -1	0	0xfe026000 - 0xfe0260ff (0x100) MX[B]
	[12] -1	0	0xfe027000 - 0xfe027fff (0x1000) MX[B]
	[13] -1	0	0xfe028000 - 0xfe02800f (0x10) MX[B]
	[14] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[15] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[16] -1	0	0xfe020000 - 0xfe023fff (0x4000) MX[B]
	[17] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[18] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[19] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[20] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[21] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[22] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[23] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[24] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[25] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[26] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[27] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[28] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[29] 0	0	0x00007c00 - 0x00007c7f (0x80) IX[B]
	[30] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[31] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[32] -1	0	0x00008c00 - 0x00008c0f (0x10) IX[B]
	[33] -1	0	0x00009000 - 0x00009003 (0x4) IX[B]
	[34] -1	0	0x00009400 - 0x00009407 (0x8) IX[B]
	[35] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[36] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[37] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[38] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[39] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[40] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[41] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[42] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[43] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[44] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[45] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[46] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[47] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[48] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[49] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[50] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[51] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[52] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[53] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[54] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[55] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[56] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[57] -1	0	0x0000fc00 - 0x0000fc3f (0x40) IX[B]
	[58] -1	0	0x00007c00 - 0x00007c7f (0x80) IX[B](B)
	[59] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[60] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1024x768@60"
(--) NVIDIA(0): No video decoder detected
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "latam"
(**) Generic Keyboard: XkbLayout: "latam"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!

```
Thanks

---

### Post by guru369 on 2007-07-05
> **estebanf said:**
> This is my first post here so let's hope I'm following the correct code of conduct... And thanks for reading and trying to help me solve my issue.

I need to make ubuntu work in 1280x1024@70hz. I know it has been asked several times, but I can't apply any of the solutions found in the forums, google or [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto).

I must admit I'm a really newbie. I applied the latest nvidia binaries drives as explained in [http://doc.gwos.org/index.php/Latest_nvidia_feisty#METHOD_2](http://doc.gwos.org/index.php/Latest_nvidia_feisty#METHOD_2). I couldn't use nv drives as my card is not supported and after two attempts I only got a not working xserver and I didn't know how to fix it without reinstalling. 

I've been trying to modify xorg.conf by hand, copy and paste, dpkg-reconfigure and nvidia-config for 2 days. With my current version I can see the 1280x1024 resolution in the /System/Preferences/Screen Resolution shortcut but only changes the virtual size and not the actual resolution. There's no option for 1280x1024 in nvidia-settings. This is my current xorg.conf:



I have a mb ASUS M2N-SLI DELUXE Socket AM2 NVIDIA nForce 570 SLI, a gpu XFX GeFORCE 8500GT DDR2 (no SLI)  and 2gb Ddr2 800 Mhz. 

Thanks for any help. If you want to see any other log, please let me know. :p

Regards,

Esteban

Remove the @60 and @75 and @70 parts from your modes under the Screen section and try.

---

### Post by leonelag on 2007-07-05
I see that the Monitor Section of your xorg.conf file has been nicely tailored for your display device.  Mine still uses "Generic Monitor", so I do not get the options for screen resolution.

How did you find those values for your Monitor ? Did you code them by hand or did you find them on the web ?

[]'s
Leonel

---

### Post by estebanf on 2007-07-05
I google them... "xorg.conf Syncmaster 910n" :)

---

### Post by estebanf on 2007-07-05
> **guru369 said:**
> Remove the @60 and @75 and @70 parts from your modes under the Screen section and try.

I tried with no sucess. No my screen section looks like this: 
```

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "UseEdidFreqs" "false"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
        Virtual     1280 1024
    EndSubSection
EndSection

```

---

### Post by estebanf on 2007-07-07
Any suggestion?.... I'm getting frustrated with this. I can't believe is so hard to get a correct resolution in linux. I never had this problem in windows....:(

---

### Post by estebanf on 2007-07-12
I'm still unable to solve this issue.... anybody with a fresh idea?

Thanks

---

### Post by dabl on 2007-07-12
You can try (in a console window) ```
sudo nvidia-settings
```

This will (hopefully) open the Nvidia driver utility.  The second menu item is "X Server Configuration" (approximately).  Click that.  On the panel that opens, click "detect display" first, then set your 1280 x 1024 resolution, then take a look at the refresh rate options -- you may get to pick 75 or 85 Hz, or you may have to leave it "auto".  When you've got it the way you want it, in the lower right corner click "Save to X Configuration File", then "save" on the little window that opens.

Now do Ctrl-Alt-Backspace, and do a new login, and it should come up at 1280 x 1024.

:)

---

### Post by atomicscissors on 2007-07-12
> **dabl said:**
> You can try (in a console window) ```
sudo nvidia-settings
```

This will (hopefully) open the Nvidia driver utility.  The second menu item is "X Server Configuration" (approximately).  Click that.  On the panel that opens, click "detect display" first, then set your 1280 x 1024 resolution, then take a look at the refresh rate options -- you may get to pick 75 or 85 Hz, or you may have to leave it "auto".  When you've got it the way you want it, in the lower right corner click "Save to X Configuration File", then "save" on the little window that opens.

Now do Ctrl-Alt-Backspace, and do a new login, and it should come up at 1280 x 1024.

:)

I'm having the same problem esteban is having.

I recently installed Ubuntu on a 4 year-old HP desktop that had been running XP Home in 1280x1024 on an even older generic Dell monitor.  I was bummed out after I installed Ubuntu that the highest resolution I could select was 1024x968.  I will try this and hope it works.

---

### Post by dabl on 2007-07-12
> **atomicscissors said:**
> I recently installed Ubuntu on a 4 year-old HP desktop that had been running XP Home in 1280x1024 on an even older generic Dell monitor.  I will try this and hope it works.

OK, but ya gotta have an Nvidia graphics card, and the Nvidia driver installed, for this to work .... :)

---

### Post by atomicscissors on 2007-07-12
> **dabl said:**
> OK, but ya gotta have an Nvidia graphics card, and the Nvidia driver installed, for this to work .... :)

The computer uses an integrated nVidia graphics processor and I've already installed the nVidia drivers.

I really want to run beryl and use Firefox in 1280x1024.  I'm crossing my fingers.  Will report back once I get home.  I'm at work!  :p

---

### Post by estebanf on 2007-07-12
I tried the sudo nvidia-settings suggestion, but when i click "Detect display" nothing happends. Any idea?

---

### Post by estebanf on 2007-07-12
I'm still stuck in this issue and very close to give up. I'm begging that anyones that have any clue how to solve this give me a hand.

Here's the info.

My xorg.conf

```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Wed Jun 13 18:40:26 PDT 2007

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
  identifier "SyncMaster"
  vendorname "Samsung"
  modelname "Samsung SyncMaster 910N/912N"
  HorizSync 30-81
  VertRefresh 56-85
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  gamma 1.0
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "SyncMaster"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1280x1024 +0+0;1024x768 +0+0; 800x600 +0+0; 640x480 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

My Xorg.0.log

```


X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux esteban-desktop 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jul 12 22:52:34 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "SyncMaster"
(**) |   |-->Device "Videocard0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(WW) The directory "/usr/X11R6/lib/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/X11R6/lib/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(**) RgbPath set to "/usr/lib/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "Xinerama" "0"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,0369 card 1043,8239 rev a1 class 05,00,00 hdr 00
(II) PCI: 00:01:0: chip 10de,0360 card 1043,8239 rev a2 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0368 card 1043,8239 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:01:2: chip 10de,036a card 1043,8239 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:02:0: chip 10de,036c card 1043,8239 rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,036d card 1043,8239 rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,036e card 1043,8239 rev a1 class 01,01,8a hdr 00
(II) PCI: 00:05:0: chip 10de,037f card 1043,8239 rev a2 class 01,04,85 hdr 80
(II) PCI: 00:05:1: chip 10de,037f card 1043,8239 rev a2 class 01,04,85 hdr 80
(II) PCI: 00:05:2: chip 10de,037f card 1043,8239 rev a2 class 01,04,85 hdr 80
(II) PCI: 00:06:0: chip 10de,0370 card 0000,0000 rev a2 class 06,04,01 hdr 81
(II) PCI: 00:06:1: chip 10de,0371 card 1043,81f6 rev a2 class 04,03,00 hdr 80
(II) PCI: 00:08:0: chip 10de,0373 card 1043,8239 rev a2 class 06,80,00 hdr 00
(II) PCI: 00:09:0: chip 10de,0373 card 1043,8239 rev a2 class 06,80,00 hdr 00
(II) PCI: 00:0a:0: chip 10de,0376 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0b:0: chip 10de,0374 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0c:0: chip 10de,0374 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0d:0: chip 10de,0378 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,0375 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0f:0: chip 10de,0377 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:0b:0: chip 104c,8023 card 1043,808b rev 00 class 0c,00,10 hdr 00
(II) PCI: 06:00:0: chip 197b,2363 card 1043,81e4 rev 03 class 01,06,01 hdr 80
(II) PCI: 06:00:1: chip 197b,2363 card 1043,81e4 rev 03 class 01,01,85 hdr 00
(II) PCI: 07:00:0: chip 10de,0421 card 1682,2305 rev a1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:6:0), (0,1,1), BCTRL: 0x0a04 (VGA_EN is cleared)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfde00000 - 0xfdefffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:10:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:11:0), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:12:0), (0,4,4), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:13:0), (0,5,5), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 6: bridge is at (0:14:0), (0,6,6), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 6 I/O range:
	[0] -1	0	0x00008000 - 0x000080ff (0x100) IX[B]
	[1] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[2] -1	0	0x00008800 - 0x000088ff (0x100) IX[B]
	[3] -1	0	0x00008c00 - 0x00008cff (0x100) IX[B]
	[4] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[5] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[6] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[7] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
(II) Bus 6 non-prefetchable memory range:
	[0] -1	0	0xfdd00000 - 0xfddfffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 7: bridge is at (0:15:0), (0,7,7), BCTRL: 0x001c (VGA_EN is set)
(II) Bus 7 I/O range:
	[0] -1	0	0x00007000 - 0x000070ff (0x100) IX[B]
	[1] -1	0	0x00007400 - 0x000074ff (0x100) IX[B]
	[2] -1	0	0x00007800 - 0x000078ff (0x100) IX[B]
	[3] -1	0	0x00007c00 - 0x00007cff (0x100) IX[B]
(II) Bus 7 non-prefetchable memory range:
	[0] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B]
(II) Bus 7 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,7), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(--) PCI:*(7:0:0) nVidia Corporation unknown chipset (0x0421) rev 161, Mem @ 0xfa000000/24, 0xe0000000/28, 0xf8000000/25, I/O @ 0x7c00/7, BIOS @ 0xfbfe0000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xfddfe000 - 0xfddfffff (0x2000) MX[B]
	[1] -1	0	0xfdef8000 - 0xfdefbfff (0x4000) MX[B]
	[2] -1	0	0xfdeff000 - 0xfdeff7ff (0x800) MX[B]
	[3] -1	0	0xfe025000 - 0xfe02500f (0x10) MX[B]
	[4] -1	0	0xfe026000 - 0xfe0260ff (0x100) MX[B]
	[5] -1	0	0xfe027000 - 0xfe027fff (0x1000) MX[B]
	[6] -1	0	0xfe028000 - 0xfe02800f (0x10) MX[B]
	[7] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[8] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[9] -1	0	0xfe020000 - 0xfe023fff (0x4000) MX[B]
	[10] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[11] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[12] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[13] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[14] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[15] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[16] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[17] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[18] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[19] -1	0	0x00008c00 - 0x00008c0f (0x10) IX[B]
	[20] -1	0	0x00009000 - 0x00009003 (0x4) IX[B]
	[21] -1	0	0x00009400 - 0x00009407 (0x8) IX[B]
	[22] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[23] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[24] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[25] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[26] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[27] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[28] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[29] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[30] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[31] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[32] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[33] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[34] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[35] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[36] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[37] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[38] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[39] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[40] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[41] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[42] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[43] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[44] -1	0	0x0000fc00 - 0x0000fc3f (0x40) IX[B]
	[45] -1	0	0x00007c00 - 0x00007c7f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfddfe000 - 0xfddfffff (0x2000) MX[B]
	[1] -1	0	0xfdef8000 - 0xfdefbfff (0x4000) MX[B]
	[2] -1	0	0xfdeff000 - 0xfdeff7ff (0x800) MX[B]
	[3] -1	0	0xfe025000 - 0xfe02500f (0x10) MX[B]
	[4] -1	0	0xfe026000 - 0xfe0260ff (0x100) MX[B]
	[5] -1	0	0xfe027000 - 0xfe027fff (0x1000) MX[B]
	[6] -1	0	0xfe028000 - 0xfe02800f (0x10) MX[B]
	[7] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[8] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[9] -1	0	0xfe020000 - 0xfe023fff (0x4000) MX[B]
	[10] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[11] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[12] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[13] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[14] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[15] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[16] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[17] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[18] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[19] -1	0	0x00008c00 - 0x00008c0f (0x10) IX[B]
	[20] -1	0	0x00009000 - 0x00009003 (0x4) IX[B]
	[21] -1	0	0x00009400 - 0x00009407 (0x8) IX[B]
	[22] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[23] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[24] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[25] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[26] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[27] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[28] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[29] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[30] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[31] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[32] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[33] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[34] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[35] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[36] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[37] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[38] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[39] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[40] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[41] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[42] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[43] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[44] -1	0	0x0000fc00 - 0x0000fc3f (0x40) IX[B]
	[45] -1	0	0x00007c00 - 0x00007c7f (0x80) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfddfe000 - 0xfddfffff (0x2000) MX[B]
	[5] -1	0	0xfdef8000 - 0xfdefbfff (0x4000) MX[B]
	[6] -1	0	0xfdeff000 - 0xfdeff7ff (0x800) MX[B]
	[7] -1	0	0xfe025000 - 0xfe02500f (0x10) MX[B]
	[8] -1	0	0xfe026000 - 0xfe0260ff (0x100) MX[B]
	[9] -1	0	0xfe027000 - 0xfe027fff (0x1000) MX[B]
	[10] -1	0	0xfe028000 - 0xfe02800f (0x10) MX[B]
	[11] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[12] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[13] -1	0	0xfe020000 - 0xfe023fff (0x4000) MX[B]
	[14] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[15] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[16] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[17] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[18] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[19] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[20] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[21] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[22] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x00008c00 - 0x00008c0f (0x10) IX[B]
	[26] -1	0	0x00009000 - 0x00009003 (0x4) IX[B]
	[27] -1	0	0x00009400 - 0x00009407 (0x8) IX[B]
	[28] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[29] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[30] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[31] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[32] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[33] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[34] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[35] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[36] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[37] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[38] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[39] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[40] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[41] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[42] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[43] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[44] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[45] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[46] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[47] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[48] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[49] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[50] -1	0	0x0000fc00 - 0x0000fc3f (0x40) IX[B]
	[51] -1	0	0x00007c00 - 0x00007c7f (0x80) IX[B](B)
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
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
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules//fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  100.14.11  Wed Jun 13 18:58:58 PDT 2007
(II) Loading extension GLX
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) NVIDIA dlloader X Driver  100.14.11  Wed Jun 13 18:23:34 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 07:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
	compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfddfe000 - 0xfddfffff (0x2000) MX[B]
	[5] -1	0	0xfdef8000 - 0xfdefbfff (0x4000) MX[B]
	[6] -1	0	0xfdeff000 - 0xfdeff7ff (0x800) MX[B]
	[7] -1	0	0xfe025000 - 0xfe02500f (0x10) MX[B]
	[8] -1	0	0xfe026000 - 0xfe0260ff (0x100) MX[B]
	[9] -1	0	0xfe027000 - 0xfe027fff (0x1000) MX[B]
	[10] -1	0	0xfe028000 - 0xfe02800f (0x10) MX[B]
	[11] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[12] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[13] -1	0	0xfe020000 - 0xfe023fff (0x4000) MX[B]
	[14] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[15] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[16] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[17] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[18] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[19] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[20] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[21] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[22] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x00008c00 - 0x00008c0f (0x10) IX[B]
	[26] -1	0	0x00009000 - 0x00009003 (0x4) IX[B]
	[27] -1	0	0x00009400 - 0x00009407 (0x8) IX[B]
	[28] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[29] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[30] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[31] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[32] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[33] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[34] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[35] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[36] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[37] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[38] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[39] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[40] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[41] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[42] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[43] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[44] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[45] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[46] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[47] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[48] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[49] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[50] -1	0	0x0000fc00 - 0x0000fc3f (0x40) IX[B]
	[51] -1	0	0x00007c00 - 0x00007c7f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfddfe000 - 0xfddfffff (0x2000) MX[B]
	[5] -1	0	0xfdef8000 - 0xfdefbfff (0x4000) MX[B]
	[6] -1	0	0xfdeff000 - 0xfdeff7ff (0x800) MX[B]
	[7] -1	0	0xfe025000 - 0xfe02500f (0x10) MX[B]
	[8] -1	0	0xfe026000 - 0xfe0260ff (0x100) MX[B]
	[9] -1	0	0xfe027000 - 0xfe027fff (0x1000) MX[B]
	[10] -1	0	0xfe028000 - 0xfe02800f (0x10) MX[B]
	[11] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[12] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[13] -1	0	0xfe020000 - 0xfe023fff (0x4000) MX[B]
	[14] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[15] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[16] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[17] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[18] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[19] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[20] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[21] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[22] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[23] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[24] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[25] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[28] -1	0	0x00008c00 - 0x00008c0f (0x10) IX[B]
	[29] -1	0	0x00009000 - 0x00009003 (0x4) IX[B]
	[30] -1	0	0x00009400 - 0x00009407 (0x8) IX[B]
	[31] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[32] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[33] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[34] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[35] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[36] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[37] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[38] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[39] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[40] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[41] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[42] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[43] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[44] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[45] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[46] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[47] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[48] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[49] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[50] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[51] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[52] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[53] -1	0	0x0000fc00 - 0x0000fc3f (0x40) IX[B]
	[54] -1	0	0x00007c00 - 0x00007c7f (0x80) IX[B](B)
	[55] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[56] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(**) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "1280x1024 +0+0;1024x768 +0+0; 800x600 +0+0; 640x480 +0+0"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 8500 GT (G86) at PCI:7:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 60.86.34.00.81
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 8500 GT at PCI:7:0:0:
(--) NVIDIA(0):     Samsung (CRT-0)
(--) NVIDIA(0): Samsung (CRT-0): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "1280x1024+0+0"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1024x768+0+0"
(II) NVIDIA(0):     "800x600+0+0"
(II) NVIDIA(0):     "640x480+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(--) NVIDIA(0): DPI set to (86, 84); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B]
	[1] 0	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
	[2] 0	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfddfe000 - 0xfddfffff (0x2000) MX[B]
	[8] -1	0	0xfdef8000 - 0xfdefbfff (0x4000) MX[B]
	[9] -1	0	0xfdeff000 - 0xfdeff7ff (0x800) MX[B]
	[10] -1	0	0xfe025000 - 0xfe02500f (0x10) MX[B]
	[11] -1	0	0xfe026000 - 0xfe0260ff (0x100) MX[B]
	[12] -1	0	0xfe027000 - 0xfe027fff (0x1000) MX[B]
	[13] -1	0	0xfe028000 - 0xfe02800f (0x10) MX[B]
	[14] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[15] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[16] -1	0	0xfe020000 - 0xfe023fff (0x4000) MX[B]
	[17] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[18] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[19] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[20] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[21] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[22] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[23] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[24] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[25] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[26] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[27] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[28] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[29] 0	0	0x00007c00 - 0x00007c7f (0x80) IX[B]
	[30] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[31] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[32] -1	0	0x00008c00 - 0x00008c0f (0x10) IX[B]
	[33] -1	0	0x00009000 - 0x00009003 (0x4) IX[B]
	[34] -1	0	0x00009400 - 0x00009407 (0x8) IX[B]
	[35] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[36] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[37] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[38] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[39] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[40] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[41] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[42] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[43] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[44] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[45] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[46] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[47] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[48] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[49] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[50] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[51] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[52] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[53] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[54] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[55] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[56] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[57] -1	0	0x0000fc00 - 0x0000fc3f (0x40) IX[B]
	[58] -1	0	0x00007c00 - 0x00007c7f (0x80) IX[B](B)
	[59] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[60] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1024x768+0+0"
(--) NVIDIA(0): No video decoder detected
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Keyboard0: Core Keyboard
(**) Option "Protocol" "standard"
(**) Keyboard0: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Keyboard0: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Keyboard0: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Keyboard0: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Keyboard0: CustomKeycodes disabled
(**) Option "Protocol" "auto"
(**) Mouse0: Device: "/dev/psaux"
(**) Mouse0: Protocol: "auto"
(**) Option "CorePointer"
(**) Mouse0: Core Pointer
(**) Option "Device" "/dev/psaux"
(**) Option "Emulate3Buttons" "no"
(**) Option "ZAxisMapping" "4 5"
(**) Mouse0: ZAxisMapping: buttons 4 and 5
(**) Mouse0: Buttons: 9
(II) XINPUT: Adding extended input device "Mouse0" (type: MOUSE)
(II) XINPUT: Adding extended input device "Keyboard0" (type: KEYBOARD)
(--) Mouse0: PnP-detected protocol: "ExplorerPS/2"
(II) Mouse0: ps2EnableDataReporting: succeeded

```

Please, help :confused:

---

### Post by atomicscissors on 2007-07-13
> **dabl said:**
> You can try (in a console window) ```
sudo nvidia-settings
```


Haha!  It worked!  Thanks dabl!

---

### Post by yakkeh on 2007-07-13
Since you've edited your xorg.conf with something you found on google.... 
did you ever try replacing those modelines and generate a single new modeline with the modeline generator?
The link is [http://www.sh.nu/nvidia/gtf.php](http://www.sh.nu/nvidia/gtf.php)

This worked for me, I was stuck on 1280x1024 and couldn't get my 1440x990.
Even if you don't have an nvidia card for graphics, this tool should work. These are "general" settings and work for most people who try it

---

### Post by estebanf on 2007-07-13
> **yakkeh said:**
> Since you've edited your xorg.conf with something you found on google.... 
did you ever try replacing those modelines and generate a single new modeline with the modeline generator?
The link is [http://www.sh.nu/nvidia/gtf.php](http://www.sh.nu/nvidia/gtf.php)

This worked for me, I was stuck on 1280x1024 and couldn't get my 1440x990.
Even if you don't have an nvidia card for graphics, this tool should work. These are "general" settings and work for most people who try it

Yes, I did... I tried setting the modlines for my common resolutions (640*480, 800*600,1024*768,1280*1024). Also tried setting just 1280*1024... No sucess....

I tried yesterday with "envy", but same results... 

there must be something really weird as the screen resolution applet (ubuntu default under preference menu) not only shows resolution up to 1024*768, but the refresh rate are 50,54 or 58... I have no idea where to look to find out from where it is getting those values.

Regards,

---

