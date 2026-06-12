---
title: "Xorg not probing correct PCI address for second video card..."
date: 2007-07-26
forum: Hardware &amp; Laptops
---

### Post by myk.dinis on 2007-07-26
Here's my problem...Actually...it's in the title...

I hope I don't get in trouble but I'm gonna post my poop that will help...

Actually...I just looked at my Xorg.0.log and it seemed to find the right address...but it had no idea what was there...and it didn't load it right...

I am so lost now...

Begin xorg.conf (just the good stuff)----------------------------------------

Section "Module"
  Load "i2c"
  Load "bitmap"
  Load "ddc"
  Load "extmod"
  Load "freetype"
  Load "int10"
  Load "vbe"
  load "glx"
  load "GLcore"
  load "dri"
  load "v4l"
EndSection


#########################################################
############# Start nVidia Section ######################
#########################################################
Section "Device" # "nVidia Corporation NV6 [Vanta/Vanta LT]"
        Identifier      "VidCardnVidia"
        Boardname       "RIVA TNT2"
        Driver          "nvidia"
        #Screen 0
        Busid           "PCI:1:0:0"
        Vendorname      "nVidia"
        VideoRam        16384
        Option          "NoLogo"        "False"
        Option          "AllowGLXWithComposite" "False"
EndSection

Section "Monitor"
        Identifier      "Dell-P990"
        Vendorname      "Dell"
        Modelname       "Dell Ultrascan P990"
        Option          "DPMS"
        Horizsync       30.0-96.0
        Vertrefresh     48.0-120.0
        #modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
        #modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
        #modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
        #modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
        #modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
        #modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
        #modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
        #modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
        #modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
        #modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
        #modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
        #modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
        #modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
        #modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
        #modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
        #modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
        #modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
        #modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
        #modeline  "1280x960@85" 148.5 1280 1344 1504 1728 960 961 964 1011 +hsync +vsync
        #modeline  "1280x1024@85" 157.5 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
        #modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
        #modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
        #modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
        #modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
        #modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
        #modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
        #modeline  "1600x1200@75" 202.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
        #modeline  "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
        #modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
        #modeline  "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
        #modeline  "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
        #modeline  "2048x1536@60" 266.95 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync
        #gamma 1.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "VidCardnVidia"
        Monitor         "Dell-P990"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Modes   "1280x1024" 
        EndSubSection
EndSection
#########################################################
########### Commented Out Modes #########################
#########################################################
# "1792x1344@60" "1856x1392@60" "1920x1440@60" "2048x1536@60"
# "1400x1050@75" "1400x1050@60" "1600x1200@75" "1600x1200@70"
# "1600x1200@65" "1600x1200@60" "1280x960@60" "1152x864@75" 
#"1280x960@85" "1024x768@43" #"1280x1024@85" "1024x768@60" 
#"1280x1024@60" "1024x768@70" "1280x960@75" "1024x768@75"  
#"1024x768@85"  "832x624@75"  "800x600@60"  "800x600@85"  
#"800x600@75"  "800x600@72"  #"800x600@56"  "640x480@85"  
#"640x480@75"  "640x480@72" "640x480@60"
#########################################################



#########################################################
########### End nVidia Section ##########################
#########################################################
Section "ServerLayout"
        Identifier      "Default Layout"
  Screen 0 "Default Screen" 0 0
  Screen 1 "Screen1" rightof "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
EndSection
Section "DRI"
        Mode    0666
EndSection
#########################################################
########### Start ATI Section ###########################
#########################################################
Section "Device"
        Identifier      "VidCardATI"
        Boardname       "ATI Rage 128"
        Driver          "ati"
        #Screen 1
        Busid           "PCI:2:oa:0"
        VideoRam        16384
        Vendorname      "ATI"
        #Option         "MergedFB"      "off"
EndSection

Section "Monitor"
        Identifier      "Gateway2000"
        Vendorname      "Gateway"
        Modelname       "Gateway Vivitron 17"
        Horizsync       31.5-64
        Vertrefresh     50-120
        #Option         "DPMS"
EndSection

Section "Screen"
        Identifier      "Screen1"
        Device          "VidCardATI"
        Monitor         "Gateway2000"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Modes   "1280x1024" 
        EndSubSection
EndSection

#       modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
#       modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
#       modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
#       modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
#       modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
#       modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
#       modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
#       modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
#       modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
#       modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
#       modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
#       modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
#       modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
#       modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
#       modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
#       modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync


#########################################################
#"1280x960@60" "1024x768@43" "1024x768@60" "1024x768@70" 
#"1024x768@75" "832x624@75" "800x600@60" "800x600@85" 
#"800x600@75" "800x600@72" "800x600@56" "640x480@85" "640x480@75" 
#"640x480@72" "640x480@60"
#########################################################
#########################################################
################ End ATI Section ########################
#########################################################



#########################################################
################ The next bit is commented ##############
################ out for testing purposes ###############
#########################################################
#Section "ServerLayout"
#       Identifier      "Default Layout"
#       Screen          "Screen0"
#       InputDevice     "Generic KeyBoard"
#       InputDevice     "Configured Mouse"
#EndSection
#########################################################

#########################################################
############### Start Dual-Head Section #################
#########################################################
Section "ServerFlags"
        Option          "Xinerama"      "true"
EndSection


##########################################################
############# End Dual-Head Section ######################
##########################################################

End-----------------------------------------------------------------------------------

Next comes the line from lspci
---------------------------------------------
01:00.0 VGA compatible controller: nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15)
02:08.0 VGA compatible controller: ATI Technologies Inc Rage 128 RE/SG
-----------------------------------------------

And of course...my Xorg.0.log -------------------------

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux Abel 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jul 26 16:45:24 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Dell-P990"
(**) |   |-->Device "VidCardnVidia"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "Gateway2000"
(**) |   |-->Device "VidCardATI"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
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
(**) Option "Xinerama" "true"
(**) Xinerama: enabled
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
(II) PCI: 00:00:0: chip 8086,1130 card 0000,0000 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,1131 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1e:0: chip 8086,2418 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,2410 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,2411 card 8086,2411 rev 02 class 01,01,80 hdr 00
(II) PCI: 00:1f:2: chip 8086,2412 card 8086,2412 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,2415 card 0e11,b1bf rev 02 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 10de,002c card 1048,0c25 rev 15 class 03,00,00 hdr 00
(II) PCI: 02:08:0: chip 1002,5245 card 1002,0008 rev 00 class 03,00,00 hdr 00
(II) PCI: 02:09:0: chip 10b7,9055 card 10b7,9055 rev 64 class 02,00,00 hdr 00
(II) PCI: 02:0a:0: chip 10b7,9055 card 10b7,9055 rev 24 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0x41000000 - 0x421fffff (0x1200000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0x48000000 - 0x49ffffff (0x2000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[1] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[2] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[3] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0x40000000 - 0x404fffff (0x500000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x44000000 - 0x47ffffff (0x4000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV6 [Vanta/Vanta LT] rev 21, Mem @ 0x41000000/24, 0x48000000/25
(--) PCI: (2:8:0) ATI Technologies Inc Rage 128 RE/SG rev 0, Mem @ 0x44000000/26, 0x40000000/14, I/O @ 0x1000/8
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
(II) PCI Memory resource overlap reduced 0x4c000000 from 0x4fffffff to 0x4bffffff
(II) Active PCI resource ranges:
	[0] -1	0	0x40200000 - 0x4020007f (0x80) MX[B]
	[1] -1	0	0x40100000 - 0x4010007f (0x80) MX[B]
	[2] -1	0	0x4c000000 - 0x4bffffff (0x0) MX[B]O
	[3] -1	0	0x48000000 - 0x49ffffff (0x2000000) MX[B](B)
	[4] -1	0	0x41000000 - 0x41ffffff (0x1000000) MX[B](B)
	[5] -1	0	0x00001480 - 0x000014ff (0x80) IX[B]
	[6] -1	0	0x00001400 - 0x0000147f (0x80) IX[B]
	[7] -1	0	0x00002400 - 0x0000243f (0x40) IX[B]
	[8] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[9] -1	0	0x00002440 - 0x0000245f (0x20) IX[B]
	[10] -1	0	0x00002460 - 0x0000246f (0x10) IX[B]
(II) Inactive PCI resource ranges:
	[0] -1	0	0x40000000 - 0x40003fff (0x4000) MX[B](B)
	[1] -1	0	0x44000000 - 0x47ffffff (0x4000000) MX[B](B)
	[2] -1	0	0x00001000 - 0x000010ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0x40200000 - 0x4020007f (0x80) MX[B]
	[1] -1	0	0x40100000 - 0x4010007f (0x80) MX[B]
	[2] -1	0	0x4c000000 - 0x4bffffff (0x0) MX[B]O
	[3] -1	0	0x48000000 - 0x49ffffff (0x2000000) MX[B](B)
	[4] -1	0	0x41000000 - 0x41ffffff (0x1000000) MX[B](B)
	[5] -1	0	0x00001480 - 0x000014ff (0x80) IX[B]
	[6] -1	0	0x00001400 - 0x0000147f (0x80) IX[B]
	[7] -1	0	0x00002400 - 0x0000243f (0x40) IX[B]
	[8] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[9] -1	0	0x00002440 - 0x0000245f (0x20) IX[B]
	[10] -1	0	0x00002460 - 0x0000246f (0x10) IX[B]
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0x40000000 - 0x40003fff (0x4000) MX[B](B)
	[1] -1	0	0x44000000 - 0x47ffffff (0x4000000) MX[B](B)
	[2] -1	0	0x00001000 - 0x000010ff (0x100) IX[B](B)
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
	[4] -1	0	0x40200000 - 0x4020007f (0x80) MX[B]
	[5] -1	0	0x40100000 - 0x4010007f (0x80) MX[B]
	[6] -1	0	0x4c000000 - 0x4bffffff (0x0) MX[B]O
	[7] -1	0	0x48000000 - 0x49ffffff (0x2000000) MX[B](B)
	[8] -1	0	0x41000000 - 0x41ffffff (0x1000000) MX[B](B)
	[9] -1	0	0x40000000 - 0x40003fff (0x4000) MX[B](B)
	[10] -1	0	0x44000000 - 0x47ffffff (0x4000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x00001480 - 0x000014ff (0x80) IX[B]
	[14] -1	0	0x00001400 - 0x0000147f (0x80) IX[B]
	[15] -1	0	0x00002400 - 0x0000243f (0x40) IX[B]
	[16] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[17] -1	0	0x00002440 - 0x0000245f (0x20) IX[B]
	[18] -1	0	0x00002460 - 0x0000246f (0x10) IX[B]
	[19] -1	0	0x00001000 - 0x000010ff (0x100) IX[B](B)
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
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
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.7184
	Module class: XFree86 Server Extension
	ABI class: XFree86 Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.1
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.7184
	Module class: XFree86 Video Driver
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 6.6.3
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
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
(II) v4l driver for Video4Linux
(II) NVIDIA dlloader X Driver  1.0-7184  Tue Aug  1 18:40:06 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) ATI: ATI driver (version 6.6.3) for chipsets: ati, ativga
(II) R128: Driver for ATI Rage 128 chipsets:
	ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
	ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
	ATI Rage 128 Pro GL PA (AGP?), ATI Rage 128 Pro GL PB (AGP?),
	ATI Rage 128 Pro GL PC (AGP?), ATI Rage 128 Pro GL PD (PCI),
	ATI Rage 128 Pro GL PE (AGP?), ATI Rage 128 Pro GL PF (AGP),
	ATI Rage 128 Pro VR PG (AGP?), ATI Rage 128 Pro VR PH (AGP?),
	ATI Rage 128 Pro VR PI (AGP?), ATI Rage 128 Pro VR PJ (AGP?),
	ATI Rage 128 Pro VR PK (AGP?), ATI Rage 128 Pro VR PL (AGP?),
	ATI Rage 128 Pro VR PM (AGP?), ATI Rage 128 Pro VR PN (AGP?),
	ATI Rage 128 Pro VR PO (AGP?), ATI Rage 128 Pro VR PP (PCI),
	ATI Rage 128 Pro VR PQ (AGP?), ATI Rage 128 Pro VR PR (PCI),
	ATI Rage 128 Pro VR PS (AGP?), ATI Rage 128 Pro VR PT (AGP?),
	ATI Rage 128 Pro VR PU (AGP?), ATI Rage 128 Pro VR PV (AGP?),
	ATI Rage 128 Pro VR PW (AGP?), ATI Rage 128 Pro VR PX (AGP?),
	ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
	ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
	ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (AGP?),
	ATI Rage 128 4X SF (AGP?), ATI Rage 128 4X SG (AGP?),
	ATI Rage 128 4X SH (AGP?), ATI Rage 128 4X SK (AGP?),
	ATI Rage 128 4X SL (AGP?), ATI Rage 128 4X SM (AGP),
	ATI Rage 128 4X SN (AGP?), ATI Rage 128 Pro ULTRA TF (AGP),
	ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
	ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
	ATI Rage 128 Pro ULTRA TU (AGP?)
(II) RADEON: Driver for ATI Radeon chipsets: ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI Radeon VE/7000 QY (AGP/PCI), ATI Radeon VE/7000 QZ (AGP/PCI),
	ATI ES1000 515E (PCI), ATI ES1000 5969 (PCI),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI Radeon IGP320 (A3) 4136, ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330/340/350 (A4) 4137,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon 7000 IGP (A4+) 4237, ATI Radeon Mobility 7000 IGP 4437,
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 8500 AIW BB (AGP),
	ATI Radeon 8500 AIW BC (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP),
	ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835, ATI Radeon 9100 PRO IGP 7834,
	ATI Radeon Mobility 9200 IGP 7835, ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP), ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP),
	ATI FireGL RV360 AV (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon 9650,
	ATI Radeon 9800SE AH (AGP), ATI Radeon 9800 AI (AGP),
	ATI Radeon 9800 AJ (AGP), ATI FireGL X2 AK (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE),
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE),
	ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE), ATI FireGL V5000 (RV410) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 XT (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 SE (RV410) (PCIE),
	ATI Radeon X800 (R420) JH (AGP), ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800XT (R420) JP (AGP), ATI Radeon X800 SE (R420) (AGP),
	ATI Radeon AIW X800 VE (R420) JT (AGP),
	ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE), ATI FireGL V7100 (R423) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Radeon X800 (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 XTP (R430) (PCIE),
	ATI Radeon X850 5D4C (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP)
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x40200000 - 0x4020007f (0x80) MX[B]
	[5] -1	0	0x40100000 - 0x4010007f (0x80) MX[B]
	[6] -1	0	0x4c000000 - 0x4bffffff (0x0) MX[B]O
	[7] -1	0	0x48000000 - 0x49ffffff (0x2000000) MX[B](B)
	[8] -1	0	0x41000000 - 0x41ffffff (0x1000000) MX[B](B)
	[9] -1	0	0x40000000 - 0x40003fff (0x4000) MX[B](B)
	[10] -1	0	0x44000000 - 0x47ffffff (0x4000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x00001480 - 0x000014ff (0x80) IX[B]
	[14] -1	0	0x00001400 - 0x0000147f (0x80) IX[B]
	[15] -1	0	0x00002400 - 0x0000243f (0x40) IX[B]
	[16] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[17] -1	0	0x00002440 - 0x0000245f (0x20) IX[B]
	[18] -1	0	0x00002460 - 0x0000246f (0x10) IX[B]
	[19] -1	0	0x00001000 - 0x000010ff (0x100) IX[B](B)
(II) ATI:  Candidate "Device" section "VidCardATI".
(WW) R128: No matching Device section for instance (BusID PCI:2:8:0) found
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x40200000 - 0x4020007f (0x80) MX[B]
	[5] -1	0	0x40100000 - 0x4010007f (0x80) MX[B]
	[6] -1	0	0x4c000000 - 0x4bffffff (0x0) MX[B]O
	[7] -1	0	0x48000000 - 0x49ffffff (0x2000000) MX[B](B)
	[8] -1	0	0x41000000 - 0x41ffffff (0x1000000) MX[B](B)
	[9] -1	0	0x40000000 - 0x40003fff (0x4000) MX[B](B)
	[10] -1	0	0x44000000 - 0x47ffffff (0x4000000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x00001480 - 0x000014ff (0x80) IX[B]
	[17] -1	0	0x00001400 - 0x0000147f (0x80) IX[B]
	[18] -1	0	0x00002400 - 0x0000243f (0x40) IX[B]
	[19] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[20] -1	0	0x00002440 - 0x0000245f (0x20) IX[B]
	[21] -1	0	0x00002460 - 0x0000246f (0x10) IX[B]
	[22] -1	0	0x00001000 - 0x000010ff (0x100) IX[B](B)
	[23] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[24] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "False"
(**) NVIDIA(0): Option "AllowGLXWithComposite" "False"
(--) NVIDIA(0): Linear framebuffer at 0x48000000
(--) NVIDIA(0): MMIO registers at 0x41000000
(II) NVIDIA(0): NVIDIA GPU detected as: Vanta/Vanta LT
(--) NVIDIA(0): VideoBIOS: 03.07.01.00.00
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): VideoRAM: 16384 kBytes
(II) NVIDIA(0): Connected display device(s): CRT-0
(--) NVIDIA(0): Display device CRT-0: maximum pixel clock at  8 bpp: 250 MHz
(--) NVIDIA(0): Display device CRT-0: maximum pixel clock at 16 bpp: 250 MHz
(--) NVIDIA(0): Display device CRT-0: maximum pixel clock at 32 bpp: 215 MHz
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(WW) NVIDIA(0): Failure reading EDID parameters for display device CRT-0
(II) NVIDIA(0): Dell-P990: Using hsync range of 30.00-96.00 kHz
(II) NVIDIA(0): Dell-P990: Using vrefresh range of 48.00-120.00 Hz
(II) NVIDIA(0): Clock range:  12.00 to 215.00 MHz
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
(II) NVIDIA(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(**) NVIDIA(0): Validated modes for display device CRT-0:
(**) NVIDIA(0):      Default mode "1280x1024": 157.5 MHz, 91.1 kHz, 85.0 Hz
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(==) NVIDIA(0): DPI set to (75, 75)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(WW) NVIDIA(0): OpenGL is not fully supported in Xinerama
(II) UnloadModule: "ati"
(II) Unloading /usr/lib/xorg/modules/drivers//ati_drv.so
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0x48000000 - 0x49ffffff (0x2000000) MX[B]
	[1] 0	0	0x41000000 - 0x41ffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0x40200000 - 0x4020007f (0x80) MX[B]
	[7] -1	0	0x40100000 - 0x4010007f (0x80) MX[B]
	[8] -1	0	0x4c000000 - 0x4bffffff (0x0) MX[B]O
	[9] -1	0	0x48000000 - 0x49ffffff (0x2000000) MX[B](B)
	[10] -1	0	0x41000000 - 0x41ffffff (0x1000000) MX[B](B)
	[11] -1	0	0x40000000 - 0x40003fff (0x4000) MX[B](B)
	[12] -1	0	0x44000000 - 0x47ffffff (0x4000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00001480 - 0x000014ff (0x80) IX[B]
	[19] -1	0	0x00001400 - 0x0000147f (0x80) IX[B]
	[20] -1	0	0x00002400 - 0x0000243f (0x40) IX[B]
	[21] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[22] -1	0	0x00002440 - 0x0000245f (0x20) IX[B]
	[23] -1	0	0x00002460 - 0x0000246f (0x10) IX[B]
	[24] -1	0	0x00001000 - 0x000010ff (0x100) IX[B](B)
	[25] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[26] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1280x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
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
(EE) GLX is not supported with the Composite extension
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
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
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!

--------------------------------------------------------------


I woudl love some help!!!! Please!!!!  I am so lost!!!

Thanks much!
Myk

---

### Post by w4ett on 2007-07-26
looking at the output of

```
lspci
```

will give you the pci id of both cards.

---

### Post by myk.dinis on 2007-07-26
I believe I included the lspci output in my post...

What I have a problem with is why after correctly configuring everything it's still not working...when I boot back into windows, that works..windows still sees them and has a good time...

It's a no go with ubuntu...Kubuntu did it for me...but I kept getting xrandr errors and I didn't understand why so I reinstalled ubuntu instead...because I originally got no errors with ubuntu...

blah...

---

### Post by w4ett on 2007-07-26
Sorry, missed the lspci.. :(  .  I might be crazy or something, but the top quote is your existing xorg doesn't look quite right:


> ################################################## #######
########### Start ATI Section ###########################
################################################## #######
Section "Device"
Identifier "VidCardATI"
Boardname "ATI Rage 128"
Driver "ati"
#Screen 1
[COLOR="Magenta"]Busid "PCI:2a:0"[/COLOR]
VideoRam 16384
Vendorname "ATI"
#Option "MergedFB" "off"
EndSection

I modified the line with the Bus ID from your lspci

> 

################################################## #######
########### Start ATI Section ###########################
################################################## #######
Section "Device"
Identifier "VidCardATI"
Boardname "ATI Rage 128"
Driver "ati"
#Screen 1
[COLOR="Red"]Busid "PCI:02:08.0"[/COLOR]
VideoRam 16384
Vendorname "ATI"
#Option "MergedFB" "off"
EndSection


see if this will help.  I'm not a dual monitor kinda guy, but I see a wrong id in the original.

---

### Post by myk.dinis on 2007-07-27
It looked that way because I left these :) things on... and so colon zero looks like :0

But I figured it out...

For some reason gnome didn't want to give me the gui to setup up the dual head...so I wasn't starting x with -- -layout "default Layout' or something like that...I'm using twinview without the xinerama support right now...so it's not totally functional...but that's only becuase I wanted to see what it would do...

It's taken me since last friday to go from complete newbie to competently editing my xorg.conf...

So, I figure it's gonna take me forever to do anything more significant...ya know...

Cheers!!

the actual line is

startx -- -layout <what ever you called your layout in server layout identifier>

that will lt you start x with dual head goodness without worrying about a gui that may or may not know what you want...

it's funny but the documentation for linux is really good...but you have to EXPLICITLY know what you are looking for to find the help...and if you don't where to start how can you ask the right questions...

I had a friend who was a RedHat Developer....They shipped him here from London because he was that good...and even he couldn't give me the answer I was looking for...

startx -- -layout <blah>

so simple...yet so elusive...maybe this'll help someone else...

Now, How do I make x start that way everytime whithout having to quit x and restart it the right way?  ???  :)

TAGS --
dual head mutli head xorg xinerama dual card multi card dual-card dual-head multi-head

---

### Post by w4ett on 2007-07-27
I'm glad is sorted...and I can certainly appreciate the frustration levels rising (sort of like floodwater) .  Personnally I go nuts reading lines of logs, and prefer leaving it to someone else :)

Welcome to the community and Good Luck

---

