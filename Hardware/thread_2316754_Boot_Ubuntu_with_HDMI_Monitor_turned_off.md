---
title: "Boot Ubuntu with HDMI Monitor turned off"
date: 2016-03-10
forum: Hardware
---

### Post by b-barry-z on 2016-03-10
I am using Ubuntu 14.04 to drive a digital display in a public place.   The display shows upcoming events, weather so on.   Every so often a "good deed doer" turns off the TV that is connected to PC via HDMI at night.  If the machine for some reason boots up in this scenario the GUI will not load.  I then have to turn on the monitor ssh in and force reboot.   Is there anyway to force the GUI to load even though monitor is off?  


monitor@monitor-OptiPlex-790:/var/log$ cat Xorg.0.log
[    14.487]
X.Org X Server 1.17.1
Release Date: 2015-02-10
[    14.487] X Protocol Version 11, Revision 0
[    14.487] Build Operating System: Linux 3.19.0-28-generic x86_64 Ubuntu
[    14.487] Current Operating System: Linux monitor-OptiPlex-790 3.19.0-51-generic #58~14.04.1-Ubuntu SMP Fri Feb 26 22:02:58 UTC 2016 x86_64
[    14.487] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-51-generic root=UUID=e4cd72ac-3197-452d-b225-ddec6ac5b640 ro quiet splash
[    14.487] Build Date: 11 September 2015  10:33:14AM
[    14.487] xorg-server 2:1.17.1-0ubuntu3.1~trusty1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support))
[    14.487] Current version of pixman: 0.30.2
[    14.487]    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
[    14.487] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.487] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Mar 10 14:20:46 2016
[    14.487] (==) Using config file: "/etc/X11/xorg.conf"
[    14.487] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    14.488] (==) ServerLayout "Layout0"
[    14.488] (**) |-->Screen "Screen0" (0)
[    14.488] (**) |   |-->Monitor "Monitor0"
[    14.488] (**) |   |-->Device "Device0"
[    14.488] (**) |-->Input Device "Keyboard0"
[    14.488] (**) |-->Input Device "Mouse0"
[    14.488] (==) Automatically adding devices
[    14.488] (==) Automatically enabling devices
[    14.488] (==) Automatically adding GPU devices
[    14.488] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.488]    Entry deleted from font path.
[    14.488] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    14.488]    Entry deleted from font path.
[    14.488] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    14.488]    Entry deleted from font path.
[    14.488] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    14.488]    Entry deleted from font path.
[    14.488] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    14.488]    Entry deleted from font path.
[    14.488] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        built-ins
[    14.488] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    14.488] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    14.488] (WW) Disabling Keyboard0
[    14.488] (WW) Disabling Mouse0
[    14.488] (II) Loader magic: 0x55caceb2bc60
[    14.488] (II) Module ABI versions:
[    14.488]    X.Org ANSI C Emulation: 0.4
[    14.488]    X.Org Video Driver: 19.0
[    14.488]    X.Org XInput driver : 21.0
[    14.488]    X.Org Server Extension : 9.0
[    14.488] (II) xfree86: Adding drm device (/dev/dri/card0)
[    14.489] (--) PCI:*(0:3:0:0) 10de:0a65:1458:3525 rev 162, Mem @ 0xe3000000/16777216, 0xd0000000/268435456, 0xe0000000/33554432, I/O @ 0x00002000/128, BIOS @ 0x????????/524288
[    14.489] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    14.489] (II) "glx" will be loaded by default.
[    14.489] (II) LoadModule: "glx"
[    14.489] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    14.494] (II) Module glx: vendor="NVIDIA Corporation"
[    14.494]    compiled for 4.0.2, module version = 1.0.0
[    14.494]    Module class: X.Org Server Extension
[    14.494] (II) NVIDIA GLX Module  304.131  Sun Nov  8 22:03:20 PST 2015
[    14.494] (II) LoadModule: "nvidia"
[    14.494] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    14.494] (II) Module nvidia: vendor="NVIDIA Corporation"
[    14.494]    compiled for 4.0.2, module version = 1.0.0
[    14.494]    Module class: X.Org Video Driver
[    14.494] (II) NVIDIA dlloader X Driver  304.131  Sun Nov  8 21:45:02 PST 2015
[    14.494] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    14.494] (++) using VT number 7

[    14.498] (II) Loading sub module "fb"
[    14.498] (II) LoadModule: "fb"
[    14.498] (II) Loading /usr/lib/xorg/modules/libfb.so
[    14.498] (II) Module fb: vendor="X.Org Foundation"
[    14.498]    compiled for 1.17.1, module version = 1.0.0
[    14.498]    ABI class: X.Org ANSI C Emulation, version 0.4
[    14.498] (II) Loading sub module "wfb"
[    14.498] (II) LoadModule: "wfb"
[    14.498] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    14.498] (II) Module wfb: vendor="X.Org Foundation"
[    14.498]    compiled for 1.17.1, module version = 1.0.0
[    14.498]    ABI class: X.Org ANSI C Emulation, version 0.4
[    14.498] (II) Loading sub module "ramdac"
[    14.498] (II) LoadModule: "ramdac"
[    14.498] (II) Module "ramdac" already built-in
[    14.498] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    14.498] (==) NVIDIA(0): RGB weight 888
[    14.498] (==) NVIDIA(0): Default visual is TrueColor
[    14.498] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    14.498] (**) NVIDIA(0): Enabling 2D acceleration
[    14.806] (II) NVIDIA(0): NVIDIA GPU GeForce 210 (GT218) at PCI:3:0:0 (GPU-0)
[    14.806] (--) NVIDIA(0): Memory: 1048576 kBytes
[    14.806] (--) NVIDIA(0): VideoBIOS: 70.18.70.00.06
[    14.806] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    14.806] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    14.808] (--) NVIDIA(0): Valid display device(s) on GeForce 210 at PCI:3:0:0
[    14.808] (--) NVIDIA(0):     CRT-0
[    14.808] (--) NVIDIA(0):     CRT-1
[    14.808] (--) NVIDIA(0):     DFP-0
[    14.808] (--) NVIDIA(0):     DFP-1
[    14.808] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[    14.808] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[    14.808] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[    14.808] (--) NVIDIA(0): DFP-0: Internal Single Link TMDS
[    14.808] (--) NVIDIA(0): DFP-1: 165.0 MHz maximum pixel clock
[    14.808] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[    14.808] (EE) NVIDIA(0): Failed to assign any connected display devices to X screen 0
[    14.835] (EE) NVIDIA(0): Failing initialization of X screen 0
[    15.131] (II) UnloadModule: "nvidia"
[    15.131] (II) UnloadSubModule: "wfb"
[    15.131] (II) UnloadSubModule: "fb"
[    15.131] (EE) Screen(s) found, but none have a usable configuration.
[    15.132] (EE)
Fatal server error:
[    15.132] (EE) no screens found(EE)
[    15.132] (EE)
Please consult the The X.Org Foundation support
         at [http://wiki.x.org](http://wiki.x.org)
 for help.
[    15.132] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    15.132] (EE)
[    15.132] (EE) Server terminated with error (1). Closing log file.

---

### Post by papibe on 2016-03-10
Hi b-barry-z. Welcome to the forum ):P

Do you have an Xorg config file? (it is located at '/etc/X11/xorg.conf')

If so, delete it because it may be serving another monitor. This way you are forcing both Xorg, and the Nvidia driver to do more probing before setting up the monitor:
```
sudo mv -vi /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
(renaming it works too)

Alternatively, try to create a personalized xorg.conf for the TV: Turn the monitor on, and boot normally. Once you get to the desktop and anything looks OK, open a terminal, and run this:
```
sudo nvidia-xconfig
```
That would create a custom /etc/X11/xorg.conf file with the TV's information.

After that, try testing if the computer boots ok with the TV off.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by b-barry-z on 2016-03-14
Thank you so much Papibe.  I really do appreacte your feedback.  Sadly I have the same results.  


monitor@monitor-OptiPlex-790:~$ cat /etc/X11/xorg.conf
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 304.131  (buildmeister@swio-display-x64-rhel04-16)  Sun Nov  8 22:48:17 PST 2015

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

monitor@monitor-OptiPlex-790:~$




The Log file

monitor@monitor-OptiPlex-790:~$ cat /var/log/Xorg.0.log
[    21.168]
X.Org X Server 1.17.1
Release Date: 2015-02-10
[    21.168] X Protocol Version 11, Revision 0
[    21.168] Build Operating System: Linux 3.19.0-28-generic x86_64 Ubuntu
[    21.168] Current Operating System: Linux monitor-OptiPlex-790 3.19.0-51-gene                                                                                                                     ric #58~14.04.1-Ubuntu SMP Fri Feb 26 22:02:58 UTC 2016 x86_64
[    21.168] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-51-generic roo                                                                                                                     t=UUID=e4cd72ac-3197-452d-b225-ddec6ac5b640 ro quiet splash
[    21.168] Build Date: 11 September 2015  10:33:14AM
[    21.168] xorg-server 2:1.17.1-0ubuntu3.1~trusty1 (For technical support plea                                                                                                                     se see [http://www.ubuntu.com/support](http://www.ubuntu.com/support))
[    21.168] Current version of pixman: 0.30.2
[    21.168]    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
[    21.168] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    21.168] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Mar 14 07:00:49 201                                                                                                                     6
[    21.168] (==) Using config file: "/etc/X11/xorg.conf"
[    21.168] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    21.168] (==) ServerLayout "Layout0"
[    21.168] (**) |-->Screen "Screen0" (0)
[    21.168] (**) |   |-->Monitor "Monitor0"
[    21.169] (**) |   |-->Device "Device0"
[    21.169] (**) |-->Input Device "Keyboard0"
[    21.169] (**) |-->Input Device "Mouse0"
[    21.169] (==) Automatically adding devices
[    21.169] (==) Automatically enabling devices
[    21.169] (==) Automatically adding GPU devices
[    21.169] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    21.169]    Entry deleted from font path.
[    21.169] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    21.169]    Entry deleted from font path.
[    21.169] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    21.169]    Entry deleted from font path.
[    21.169] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    21.169]    Entry deleted from font path.
[    21.169] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    21.169]    Entry deleted from font path.
[    21.169] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        built-ins
[    21.169] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-module                                                                                                                     s,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    21.169] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vm                                                                                                                     mouse' will be disabled.
[    21.169] (WW) Disabling Keyboard0
[    21.169] (WW) Disabling Mouse0
[    21.169] (II) Loader magic: 0x560a369b9c60
[    21.169] (II) Module ABI versions:
[    21.169]    X.Org ANSI C Emulation: 0.4
[    21.169]    X.Org Video Driver: 19.0
[    21.169]    X.Org XInput driver : 21.0
[    21.169]    X.Org Server Extension : 9.0
[    21.169] (II) xfree86: Adding drm device (/dev/dri/card0)
[    21.170] (--) PCI:*(0:3:0:0) 10de:0a65:1458:3525 rev 162, Mem @ 0xe3000000/1                                                                                                                     6777216, 0xd0000000/268435456, 0xe0000000/33554432, I/O @ 0x00002000/128, BIOS @                                                                                                                      0x????????/524288
[    21.170] (WW) "glamoregl" will not be loaded unless you've specified it to b                                                                                                                     e loaded elsewhere.
[    21.170] (II) "glx" will be loaded by default.
[    21.170] (II) LoadModule: "glx"
[    21.170] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    21.175] (II) Module glx: vendor="NVIDIA Corporation"
[    21.175]    compiled for 4.0.2, module version = 1.0.0
[    21.175]    Module class: X.Org Server Extension
[    21.175] (II) NVIDIA GLX Module  304.131  Sun Nov  8 22:03:20 PST 2015
[    21.175] (II) LoadModule: "nvidia"
[    21.175] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_dr                                                                                                                     v.so
[    21.175] (II) Module nvidia: vendor="NVIDIA Corporation"
[    21.175]    compiled for 4.0.2, module version = 1.0.0
[    21.175]    Module class: X.Org Video Driver
[    21.175] (II) NVIDIA dlloader X Driver  304.131  Sun Nov  8 21:45:02 PST 201                                                                                                                     5
[    21.175] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    21.175] (++) using VT number 7

[    21.178] (II) Loading sub module "fb"
[    21.178] (II) LoadModule: "fb"
[    21.179] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.179] (II) Module fb: vendor="X.Org Foundation"
[    21.179]    compiled for 1.17.1, module version = 1.0.0
[    21.179]    ABI class: X.Org ANSI C Emulation, version 0.4
[    21.179] (II) Loading sub module "wfb"
[    21.179] (II) LoadModule: "wfb"
[    21.179] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    21.179] (II) Module wfb: vendor="X.Org Foundation"
[    21.179]    compiled for 1.17.1, module version = 1.0.0
[    21.179]    ABI class: X.Org ANSI C Emulation, version 0.4
[    21.179] (II) Loading sub module "ramdac"
[    21.179] (II) LoadModule: "ramdac"
[    21.179] (II) Module "ramdac" already built-in
[    21.179] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    21.179] (==) NVIDIA(0): RGB weight 888
[    21.179] (==) NVIDIA(0): Default visual is TrueColor
[    21.179] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    21.179] (**) NVIDIA(0): Enabling 2D acceleration
[    21.488] (II) NVIDIA(0): NVIDIA GPU GeForce 210 (GT218) at PCI:3:0:0 (GPU-0)
[    21.488] (--) NVIDIA(0): Memory: 1048576 kBytes
[    21.488] (--) NVIDIA(0): VideoBIOS: 70.18.70.00.06
[    21.488] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    21.488] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    21.490] (--) NVIDIA(0): Valid display device(s) on GeForce 210 at PCI:3:0:0
[    21.490] (--) NVIDIA(0):     CRT-0
[    21.490] (--) NVIDIA(0):     CRT-1
[    21.490] (--) NVIDIA(0):     DFP-0
[    21.490] (--) NVIDIA(0):     DFP-1
[    21.490] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[    21.490] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[    21.490] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[    21.490] (--) NVIDIA(0): DFP-0: Internal Single Link TMDS
[    21.490] (--) NVIDIA(0): DFP-1: 165.0 MHz maximum pixel clock
[    21.490] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[    21.490] (EE) NVIDIA(0): Failed to assign any connected display devices to X                                                                                                                      screen 0
[    21.525] (EE) NVIDIA(0): Failing initialization of X screen 0
[    21.821] (II) UnloadModule: "nvidia"
[    21.821] (II) UnloadSubModule: "wfb"
[    21.821] (II) UnloadSubModule: "fb"
[    21.821] (EE) Screen(s) found, but none have a usable configuration.
[    21.821] (EE)
Fatal server error:
[    21.821] (EE) no screens found(EE)
[    21.821] (EE)
Please consult the The X.Org Foundation support
         at [http://wiki.x.org](http://wiki.x.org)
 for help.
[    21.821] (EE) Please also check the log file at "/var/log/Xorg.0.log" for ad                                                                                                                     ditional information.
[    21.821] (EE)
[    21.822] (EE) Server terminated with error (1). Closing log file.
monitor@monitor-OptiPlex-790:~$

---

### Post by papibe on 2016-03-14
There's another possible solution: hardcode the EDID information into the xorg.conf

First we need to get the data. Boot normally so get to the desktop. Then either:
[LIST]
[*]Open 'Nvidia X Server Settings' and go the the GPU->DFP, or GPU-> HDMI on the right list, and 'Acquire EDID' save the file on your directory. Or
[*]Install read-edit, and the command line to get the file:
```
sudo apt-get install read-edid

sudo get-edid > edid_data.bin
```
[/LIST]
Once we have that I'll give you directions on how to link that file on the xorg.conf

Let us know how it goes.
Regards/

---

### Post by b-barry-z on 2016-03-15
I have attached the file.  I hope it is readable.  Your assistance is much appreciated. 

[ATTACH]267822[/ATTACH]

---

### Post by papibe on 2016-03-15
Great! This is the information that I get when I run:
```
$ parse-edid < ./edid_data.bin 
Checksum Correct

Section "Monitor"
	Identifier "EW39T6MZ"
	ModelName "EW39T6MZ"
	VendorName "WDT"
	# Monitor Manufactured week 28 of 2012
	# EDID version 1.3
	# Digital Display
	DisplaySize 430 250
	Gamma 2.20
	Option "DPMS" "false"
	Horizsync 15-68
	VertRefresh 59-61
	# Maximum pixel clock is 150MHz
	#Not giving standard mode: 1440x900, 60Hz
	#Not giving standard mode: 1024x768, 60Hz
	#Not giving standard mode: 1680x1050, 60Hz

	#Extension block found. Parsing...
	Modeline 	"Mode 17" 148.50 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync 
	Modeline 	"Mode 0" 148.50 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync 
	Modeline 	"Mode 1" 148.500 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
	Modeline 	"Mode 2" 74.250 1920 2008 2052 2200 1080 1082 1087 1125 +hsync +vsync interlace
	Modeline 	"Mode 3" 74.250 1280 1390 1420 1650 720 725 730 750 +hsync +vsync
	Modeline 	"Mode 4" 27.027 720 736 798 858 480 489 495 525 -hsync -vsync
	Modeline 	"Mode 5" 27.027 720 736 798 858 480 489 495 525 -hsync -vsync
	Modeline 	"Mode 6" 27.027 1440 1478 1602 1716 480 484 487 525 -hsync -vsync interlace
	Modeline 	"Mode 7" 27.027 1440 1478 1602 1716 480 484 487 525 -hsync -vsync interlace
	Modeline 	"Mode 8" 27.000 720 732 796 864 576 581 586 625 -hsync -vsync
	Modeline 	"Mode 9" 27.000 720 732 796 864 576 581 586 625 -hsync -vsync
	Modeline 	"Mode 10" 74.250 1280 1720 1760 1980 720 725 730 750 +hsync +vsync
	Modeline 	"Mode 11" 74.250 1920 2448 2492 2640 1080 1082 1089 1125 +hsync +vsync interlace
	Modeline 	"Mode 12" 27.000 1440 1464 1590 1728 576 578 581 625 -hsync -vsync interlace
	Modeline 	"Mode 13" 27.000 1440 1464 1590 1728 576 578 581 625 -hsync -vsync interlace
	Modeline 	"Mode 14" 148.500 1920 2448 2492 2640 1080 1084 1089 1125 +hsync +vsync
	Modeline 	"Mode 15" 25.200 640 656 752 800 480 490 492 525 -hsync -vsync
	Modeline 	"Mode 16" 74.250 1920 2558 2602 2750 1080 1084 1089 1125 +hsync +vsync
	Modeline 	"Mode 18" 74.25 1920 2008 2052 2200 540 542 547 562 +hsync +vsync interlace
	Modeline 	"Mode 19" 27.00 720 736 798 858 480 489 495 525 -hsync -vsync 
	Modeline 	"Mode 20" 27.00 720 736 798 858 480 489 495 525 -hsync -vsync 
	Option "PreferredMode" "Mode 17"
EndSection

```
Now, these would be the steps to point to the file:

First we need to know how the Nvidia driver is naming the TV. To do that open the Xorg log file after a successful boot:
```
gedit /var/log/Xorg.0.log
```
You are looking for things like DFP-0, HDMI-1, etc. For example, I can identify my 2 monitors in these lines (in red):
```
[    13.542] (II) NVIDIA(0): Display (Seiko/Epson (**[COLOR="#FF0000"]DFP-0[/COLOR]**)) does not support NVIDIA 3D
[    13.543] (II) NVIDIA(0):     Vision stereo.                                 
[    13.558] (II) NVIDIA(0): Display (DELL 1907FP ([COLOR="#FF0000"]**DFP-1**[/COLOR])) does not support NVIDIA 3D
[    13.558] (II) NVIDIA(0):     Vision stereo.        
``` 
Let's say you get DFP-0. Keep it in mind.

Copy the file on the X11 directory:
```
sudo cp edid_data.bin /etc/X11
```
Then edit your Xorg config file:
```
sudo nano /etc/X11/xorg.conf
```
(change nano with vi if you fill more comfortable with it)

Go to the "Screen" section, and insert a line like this:
```

Section "Screen"
    ...
    Option      "CustomEDID"  "DFP-0:/etc/X11/edid_data.bin"
    ....
EndSection

```
That would be it. I'd try to boot with the monitor on first, and then see what happens when off.

Let us know how that goes.
Regards.

---

### Post by b-barry-z on 2016-03-17
Sadly this did not work.  It boots normally if the HDMI connected monitor (TV) is connected but if the monitor is off X fails to load.  I wonder if I should just abandon the HDMI and try and use a VGA cable.  Given that is not digital might that work better?


```
[    14.864]
X.Org X Server 1.17.1
Release Date: 2015-02-10
[    14.864] X Protocol Version 11, Revision 0
[    14.864] Build Operating System: Linux 3.19.0-28-generic x86_64 Ubuntu
[    14.864] Current Operating System: Linux monitor-OptiPlex-790 3.19.0-51-generic #58~14.04.1-Ubuntu SMP Fri Feb 26 22:02:58 UTC 2016 x86_64
[    14.864] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-51-generic root=UUID=e4cd72ac-3197-452d-b225-ddec6ac5b640 ro quiet splash
[    14.864] Build Date: 11 September 2015  10:33:14AM
[    14.864] xorg-server 2:1.17.1-0ubuntu3.1~trusty1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support))
[    14.864] Current version of pixman: 0.30.2
[    14.864]    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
[    14.864] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.864] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Mar 16 21:15:35 2016
[    14.864] (==) Using config file: "/etc/X11/xorg.conf"
[    14.864] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    14.864] (==) ServerLayout "Layout0"
[    14.864] (**) |-->Screen "Screen0" (0)
[    14.864] (**) |   |-->Monitor "Monitor0"
[    14.865] (**) |   |-->Device "Device0"
[    14.865] (**) |-->Input Device "Keyboard0"
[    14.865] (**) |-->Input Device "Mouse0"
[    14.865] (==) Automatically adding devices
[    14.865] (==) Automatically enabling devices
[    14.865] (==) Automatically adding GPU devices
[    14.865] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.865]    Entry deleted from font path.
[    14.865] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    14.865]    Entry deleted from font path.
[    14.865] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    14.865]    Entry deleted from font path.
[    14.865] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    14.865]    Entry deleted from font path.
[    14.865] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    14.865]    Entry deleted from font path.
[    14.865] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        built-ins
[    14.865] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    14.865] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    14.865] (WW) Disabling Keyboard0
[    14.865] (WW) Disabling Mouse0
[    14.865] (II) Loader magic: 0x55b4fab55c60
[    14.865] (II) Module ABI versions:
[    14.865]    X.Org ANSI C Emulation: 0.4
[    14.865]    X.Org Video Driver: 19.0
[    14.865]    X.Org XInput driver : 21.0
[    14.865]    X.Org Server Extension : 9.0
[    14.865] (II) xfree86: Adding drm device (/dev/dri/card0)
[    14.866] (--) PCI:*(0:3:0:0) 10de:0a65:1458:3525 rev 162, Mem @ 0xe3000000/16777216, 0xd0000000/268435456, 0xe0000000/33554432, I/O @ 0x00002000/128, BIOS @ 0x????????/524288
[    14.866] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    14.866] (II) "glx" will be loaded by default.
[    14.866] (II) LoadModule: "glx"
[    14.866] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    14.871] (II) Module glx: vendor="NVIDIA Corporation"
[    14.871]    compiled for 4.0.2, module version = 1.0.0
[    14.871]    Module class: X.Org Server Extension
[    14.871] (II) NVIDIA GLX Module  304.131  Sun Nov  8 22:03:20 PST 2015
[    14.871] (II) LoadModule: "nvidia"
[    14.871] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    14.871] (II) Module nvidia: vendor="NVIDIA Corporation"
[    14.871]    compiled for 4.0.2, module version = 1.0.0
[    14.871]    Module class: X.Org Video Driver
[    14.871] (II) NVIDIA dlloader X Driver  304.131  Sun Nov  8 21:45:02 PST 2015
[    14.871] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    14.871] (++) using VT number 7

[    14.874] (II) Loading sub module "fb"
[    14.874] (II) LoadModule: "fb"
[    14.874] (II) Loading /usr/lib/xorg/modules/libfb.so
[    14.875] (II) Module fb: vendor="X.Org Foundation"
[    14.875]    compiled for 1.17.1, module version = 1.0.0
[    14.875]    ABI class: X.Org ANSI C Emulation, version 0.4
[    14.875] (II) Loading sub module "wfb"
[    14.875] (II) LoadModule: "wfb"
[    14.875] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    14.875] (II) Module wfb: vendor="X.Org Foundation"
[    14.875]    compiled for 1.17.1, module version = 1.0.0
[    14.875]    ABI class: X.Org ANSI C Emulation, version 0.4
[    14.875] (II) Loading sub module "ramdac"
[    14.875] (II) LoadModule: "ramdac"
[    14.875] (II) Module "ramdac" already built-in
[    14.875] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    14.875] (==) NVIDIA(0): RGB weight 888
[    14.875] (==) NVIDIA(0): Default visual is TrueColor
[    14.875] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    14.875] (**) NVIDIA(0): Option "CustomEDID" "DFP-1:/etc/X11/edid_data.bin"
[    14.875] (**) NVIDIA(0): Enabling 2D acceleration
[    15.183] (II) NVIDIA(0): NVIDIA GPU GeForce 210 (GT218) at PCI:3:0:0 (GPU-0)
[    15.183] (--) NVIDIA(0): Memory: 1048576 kBytes
[    15.183] (--) NVIDIA(0): VideoBIOS: 70.18.70.00.06
[    15.183] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    15.183] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    15.185] (--) NVIDIA(0): Valid display device(s) on GeForce 210 at PCI:3:0:0
[    15.185] (--) NVIDIA(0):     CRT-0
[    15.185] (--) NVIDIA(0):     CRT-1
[    15.185] (--) NVIDIA(0):     DFP-0
[    15.185] (--) NVIDIA(0):     DFP-1
[    15.185] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[    15.185] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[    15.185] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[    15.185] (--) NVIDIA(0): DFP-0: Internal Single Link TMDS
[    15.185] (--) NVIDIA(0): DFP-1: 165.0 MHz maximum pixel clock
[    15.185] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[    15.185] (EE) NVIDIA(0): Failed to assign any connected display devices to X screen 0
[    15.219] (EE) NVIDIA(0): Failing initialization of X screen 0
[    15.515] (II) UnloadModule: "nvidia"
[    15.515] (II) UnloadSubModule: "wfb"
[    15.515] (II) UnloadSubModule: "fb"
[    15.515] (EE) Screen(s) found, but none have a usable configuration.
[    15.515] (EE)
Fatal server error:
[    15.515] (EE) no screens found(EE)
[    15.515] (EE)
Please consult the The X.Org Foundation support
         at [http://wiki.x.org](http://wiki.x.org)
 for help.
[    15.515] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    15.515] (EE)
[    15.516] (EE) Server terminated with error (1). Closing log file.
```

---

### Post by Bucky Ball on 2016-03-17
PLEASE use code tags! See the link in my signature at the bottom of this post for how. Thanks.

---

### Post by papibe on 2016-03-17
> **b-barry-z said:**
> Sadly this did not work.
:(
> **b-barry-z said:**
> I wonder if I should just abandon the HDMI and try and use a VGA cable.  Given that is not digital might that work better?
At this point, it wouldn't hurt to try. My experience is the other way around, as more and more VGA monitors don't even give proper EDID info.

Save your config, boot without a config file and see how it goes:
```
sudo mv -iv /etc/X11/xorg.conf /etc/X11/xorg.conf.HDMI_with_EDID
```
BTW, it looks like there are other monitors connected? At least being recognized:
```
[    15.185] (--) NVIDIA(0):     CRT-0
[    15.185] (--) NVIDIA(0):     CRT-1
[    15.185] (--) NVIDIA(0):     DFP-0
[    15.185] (--) NVIDIA(0):     DFP-1
[    15.185] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[    15.185] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[    15.185] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[    15.185] (--) NVIDIA(0): DFP-0: Internal Single Link TMDS
[    15.185] (--) NVIDIA(0): DFP-1: 165.0 MHz maximum pixel clock
[    15.185] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
```
Another idea: most HDTV have several HDMI inputs, have you try other inputs?
Regards

---

### Post by b-barry-z on 2016-03-17
This is the only monitor.  It is just a desktop hidden in a closet that drives a TV serving as a digital dislplay on the other side of the wall.    If I could ensure people did not turn the TV off, or the computer never rebooted all would be fine but that is not the case.  

Now that you mention it I am not sure the TV is giving the right EDID info.  If  you look at the bottom of the log for when the TV is on during boot there are lots of errors about conflicting info.    I will give the VGA a try.  First I will try a cold boot of the TV, it could be in a weird state.

```

[    12.797]
X.Org X Server 1.17.1
Release Date: 2015-02-10
[    12.797] X Protocol Version 11, Revision 0
[    12.797] Build Operating System: Linux 3.19.0-28-generic x86_64 Ubuntu
[    12.797] Current Operating System: Linux monitor-OptiPlex-790 3.19.0-51-generic #58~14.04.1-Ubuntu SMP Fri Feb 26 22:02:58 UTC 2016 x86_64
[    12.797] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-51-generic root=UUID=e4cd72ac-3197-452d-b225-ddec6ac5b640 ro quiet splash
[    12.797] Build Date: 11 September 2015  10:33:14AM
[    12.797] xorg-server 2:1.17.1-0ubuntu3.1~trusty1 (For technical support please see http://www.ubuntu.com/support)
[    12.797] Current version of pixman: 0.30.2
[    12.797]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[    12.797] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    12.797] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Mar 17 13:59:20 2016
[    12.828] (==) Using config file: "/etc/X11/xorg.conf"
[    12.828] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    12.868] (==) ServerLayout "Layout0"
[    12.868] (**) |-->Screen "Screen0" (0)
[    12.868] (**) |   |-->Monitor "Monitor0"
[    12.868] (**) |   |-->Device "Device0"
[    12.868] (**) |-->Input Device "Keyboard0"
[    12.868] (**) |-->Input Device "Mouse0"
[    12.868] (==) Automatically adding devices
[    12.868] (==) Automatically enabling devices
[    12.868] (==) Automatically adding GPU devices
[    12.905] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    12.905]    Entry deleted from font path.
[    12.905] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    12.905]    Entry deleted from font path.
[    12.905] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    12.905]    Entry deleted from font path.
[    12.905] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    12.905]    Entry deleted from font path.
[    12.905] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    12.905]    Entry deleted from font path.
[    12.905] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        built-ins
[    12.905] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    12.905] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    12.905] (WW) Disabling Keyboard0
[    12.905] (WW) Disabling Mouse0
[    12.905] (II) Loader magic: 0x55e3d7cd4c60
[    12.905] (II) Module ABI versions:
[    12.905]    X.Org ANSI C Emulation: 0.4
[    12.905]    X.Org Video Driver: 19.0
[    12.905]    X.Org XInput driver : 21.0
[    12.905]    X.Org Server Extension : 9.0
[    12.905] (II) xfree86: Adding drm device (/dev/dri/card0)
[    12.906] (--) PCI:*(0:3:0:0) 10de:0a65:1458:3525 rev 162, Mem @ 0xe3000000/16777216, 0xd0000000/268435456, 0xe0000000/33554432, I/O @ 0x00002000/128, BIOS @ 0x????????/524288
[    12.906] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    12.906] (II) "glx" will be loaded by default.
[    12.906] (II) LoadModule: "glx"
[    12.906] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    13.235] (II) Module glx: vendor="NVIDIA Corporation"
[    13.235]    compiled for 4.0.2, module version = 1.0.0
[    13.235]    Module class: X.Org Server Extension
[    13.235] (II) NVIDIA GLX Module  304.131  Sun Nov  8 22:03:20 PST 2015
[    13.235] (II) LoadModule: "nvidia"
[    13.235] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    13.236] (II) Module nvidia: vendor="NVIDIA Corporation"
[    13.236]    compiled for 4.0.2, module version = 1.0.0
[    13.236]    Module class: X.Org Video Driver
[    13.236] (II) NVIDIA dlloader X Driver  304.131  Sun Nov  8 21:45:02 PST 2015
[    13.236] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    13.236] (++) using VT number 7

[    13.237] (II) Loading sub module "fb"
[    13.237] (II) LoadModule: "fb"
[    13.238] (II) Loading /usr/lib/xorg/modules/libfb.so
[    13.238] (II) Module fb: vendor="X.Org Foundation"
[    13.238]    compiled for 1.17.1, module version = 1.0.0
[    13.238]    ABI class: X.Org ANSI C Emulation, version 0.4
[    13.238] (II) Loading sub module "wfb"
[    13.238] (II) LoadModule: "wfb"
[    13.258] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    13.258] (II) Module wfb: vendor="X.Org Foundation"
[    13.258]    compiled for 1.17.1, module version = 1.0.0
[    13.258]    ABI class: X.Org ANSI C Emulation, version 0.4
[    13.258] (II) Loading sub module "ramdac"
[    13.258] (II) LoadModule: "ramdac"
[    13.258] (II) Module "ramdac" already built-in
[    13.258] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    13.258] (==) NVIDIA(0): RGB weight 888
[    13.258] (==) NVIDIA(0): Default visual is TrueColor
[    13.258] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    13.259] (**) NVIDIA(0): Option "CustomEDID" "DFP-1:/etc/X11/edid_data.bin"
[    13.259] (**) NVIDIA(0): Enabling 2D acceleration
[    14.243] (II) NVIDIA(GPU-0): Display (WDT EW39T6MZ (DFP-1)) does not support NVIDIA 3D
[    14.243] (II) NVIDIA(GPU-0):     Vision stereo.
[    14.246] (II) NVIDIA(0): NVIDIA GPU GeForce 210 (GT218) at PCI:3:0:0 (GPU-0)
[    14.246] (--) NVIDIA(0): Memory: 1048576 kBytes
[    14.246] (--) NVIDIA(0): VideoBIOS: 70.18.70.00.06
[    14.246] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    14.246] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    14.248] (--) NVIDIA(0): Valid display device(s) on GeForce 210 at PCI:3:0:0
[    14.248] (--) NVIDIA(0):     CRT-0
[    14.248] (--) NVIDIA(0):     CRT-1
[    14.248] (--) NVIDIA(0):     DFP-0
[    14.248] (--) NVIDIA(0):     WDT EW39T6MZ (DFP-1) (connected)
[    14.248] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[    14.248] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[    14.248] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[    14.248] (--) NVIDIA(0): DFP-0: Internal Single Link TMDS
[    14.248] (--) NVIDIA(0): WDT EW39T6MZ (DFP-1): 165.0 MHz maximum pixel clock
[    14.248] (--) NVIDIA(0): WDT EW39T6MZ (DFP-1): Internal Single Link TMDS
[    14.248] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    14.248] (**) NVIDIA(0):     device WDT EW39T6MZ (DFP-1) (Using EDID frequencies has
[    14.248] (**) NVIDIA(0):     been enabled on all display devices.)
[    14.251] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    14.251] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    14.251] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    14.251] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    14.251] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    14.252] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    14.252] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    14.252] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    14.252] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    14.252] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    14.252] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    14.252] (WW) NVIDIA(GPU-0):     "1280x720" is specified in the EDID; however, the EDID's
[    14.252] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    14.252] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    14.252] (WW) NVIDIA(GPU-0):     check for mode "1280x720".
[    14.252] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    14.252] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    14.252] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    14.252] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    14.252] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".
[    14.253] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    14.253] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    14.253] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    14.253] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    14.253] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    14.253] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    14.253] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    14.253] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    14.253] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    14.253] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    14.253] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    14.253] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    14.253] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    14.253] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    14.253] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".
[    14.254] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    14.254] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    14.254] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    14.254] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (24.0 Hz); ignoring VertRefresh
[    14.254] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".
[    14.256] (==) NVIDIA(0):
[    14.256] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    14.256] (==) NVIDIA(0):     will be used as the requested mode.
[    14.256] (==) NVIDIA(0):
[    14.256] (II) NVIDIA(0): Validated MetaModes:
[    14.256] (II) NVIDIA(0):     "DFP-1:nvidia-auto-select"
[    14.256] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    14.317] (--) NVIDIA(0): DPI set to (113, 109); computed from "UseEdidDpi" X config
[    14.317] (--) NVIDIA(0):     option
[    14.317] (--) Depth 24 pixmap format is 32 bpp
[    14.317] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    14.323] (II) NVIDIA(0): Setting mode "DFP-1:nvidia-auto-select"
[    14.805] (==) NVIDIA(0): Disabling shared memory pixmaps
[    14.805] (==) NVIDIA(0): Backing store enabled
[    14.805] (==) NVIDIA(0): Silken mouse enabled
[    14.839] (**) NVIDIA(0): DPMS enabled
[    14.840] (II) Loading sub module "dri2"
[    14.840] (II) LoadModule: "dri2"
[    14.840] (II) Module "dri2" already built-in
[    14.840] (II) NVIDIA(0): [DRI2] Setup complete
[    14.840] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    14.840] (--) RandR disabled
[    14.844] (II) Initializing extension GLX
[    14.844] (II) Indirect GLX disabled.(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    15.111] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    15.111] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    15.111] (II) LoadModule: "evdev"
[    15.131] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.159] (II) Module evdev: vendor="X.Org Foundation"
[    15.159]    compiled for 1.17.1, module version = 2.9.0
[    15.159]    Module class: X.Org XInput Driver
[    15.159]    ABI class: X.Org XInput driver, version 21.0
[    15.159] (II) Using input driver 'evdev' for 'Power Button'
[    15.159] (**) Power Button: always reports core events
[    15.159] (**) evdev: Power Button: Device: "/dev/input/event1"
[    15.159] (--) evdev: Power Button: Vendor 0 Product 0x1
[    15.159] (--) evdev: Power Button: Found keys
[    15.159] (II) evdev: Power Button: Configuring as keyboard
[    15.159] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    15.159] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    15.159] (**) Option "xkb_rules" "evdev"
[    15.159] (**) Option "xkb_model" "pc105"
[    15.160] (**) Option "xkb_layout" "us"
[    15.160] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    15.160] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    15.160] (II) Using input driver 'evdev' for 'Power Button'
[    15.160] (**) Power Button: always reports core events
[    15.160] (**) evdev: Power Button: Device: "/dev/input/event0"
[    15.160] (--) evdev: Power Button: Vendor 0 Product 0x1
[    15.160] (--) evdev: Power Button: Found keys
[    15.160] (II) evdev: Power Button: Configuring as keyboard
[    15.160] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    15.160] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    15.160] (**) Option "xkb_rules" "evdev"
[    15.160] (**) Option "xkb_model" "pc105"
[    15.160] (**) Option "xkb_layout" "us"
[    15.160] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event7)
[    15.160] (II) No input driver specified, ignoring this device.
[    15.160] (II) This device may have been added with another device file.
[    15.160] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event4)
[    15.160] (II) No input driver specified, ignoring this device.
[    15.160] (II) This device may have been added with another device file.
[    15.160] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event5)
[    15.160] (II) No input driver specified, ignoring this device.
[    15.161] (II) This device may have been added with another device file.
[    15.161] (II) config/udev: Adding input device HDA Intel PCH Line Out (/dev/input/event6)
[    15.161] (II) No input driver specified, ignoring this device.
[    15.161] (II) This device may have been added with another device file.
[    15.161] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event8)
[    15.161] (II) No input driver specified, ignoring this device.
[    15.161] (II) This device may have been added with another device file.
[    15.161] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event9)
[    15.161] (II) No input driver specified, ignoring this device.
[    15.161] (II) This device may have been added with another device file.
[    15.161] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event10)
[    15.161] (II) No input driver specified, ignoring this device.
[    15.161] (II) This device may have been added with another device file.
[    15.161] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event11)
[    15.161] (II) No input driver specified, ignoring this device.
[    15.161] (II) This device may have been added with another device file.
[    15.161] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event2)
[    15.161] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    15.161] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    15.161] (**) Logitech USB Receiver: always reports core events
[    15.161] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event2"
[    15.161] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc52e
[    15.161] (--) evdev: Logitech USB Receiver: Found keys
[    15.161] (II) evdev: Logitech USB Receiver: Configuring as keyboard
[    15.161] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/0003:046D:C52E.0001/input/input5/event2"
[    15.161] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD, id 8)
[    15.161] (**) Option "xkb_rules" "evdev"
[    15.161] (**) Option "xkb_model" "pc105"
[    15.161] (**) Option "xkb_layout" "us"
[    15.162] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[    15.162] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    15.162] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    15.162] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    15.162] (**) Logitech USB Receiver: always reports core events
[    15.162] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event3"
[    15.162] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc52e
[    15.162] (--) evdev: Logitech USB Receiver: Found 20 mouse buttons
[    15.162] (--) evdev: Logitech USB Receiver: Found scroll wheel(s)
[    15.162] (--) evdev: Logitech USB Receiver: Found relative axes
[    15.162] (--) evdev: Logitech USB Receiver: Found x and y relative axes
[    15.162] (--) evdev: Logitech USB Receiver: Found absolute axes
[    15.162] (II) evdev: Logitech USB Receiver: Forcing absolute x/y axes to exist.
[    15.162] (--) evdev: Logitech USB Receiver: Found keys
[    15.162] (II) evdev: Logitech USB Receiver: Configuring as mouse
[    15.162] (II) evdev: Logitech USB Receiver: Configuring as keyboard
[    15.162] (II) evdev: Logitech USB Receiver: Adding scrollwheel support
[    15.162] (**) evdev: Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    15.162] (**) evdev: Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    15.162] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/0003:046D:C52E.0002/input/input6/event3"
[    15.162] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD, id 9)
[    15.162] (**) Option "xkb_rules" "evdev"
[    15.162] (**) Option "xkb_model" "pc105"
[    15.162] (**) Option "xkb_layout" "us"
[    15.162] (II) evdev: Logitech USB Receiver: initialized for relative axes.
[    15.162] (WW) evdev: Logitech USB Receiver: ignoring absolute axes.
[    15.162] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    15.162] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    15.162] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    15.162] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    15.162] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    15.162] (II) No input driver specified, ignoring this device.
[    15.162] (II) This device may have been added with another device file.
[    21.779] (II) NVIDIA(GPU-0): Display (WDT EW39T6MZ (DFP-1)) does not support NVIDIA 3D
[    21.779] (II) NVIDIA(GPU-0):     Vision stereo.
[    21.779] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    21.779] (**) NVIDIA(0):     device WDT EW39T6MZ (DFP-1) (Using EDID frequencies has
[    21.779] (**) NVIDIA(0):     been enabled on all display devices.)
[    21.782] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    21.782] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    21.783] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    21.783] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    21.783] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    21.783] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    21.783] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    21.783] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    21.783] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    21.783] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    21.783] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    21.783] (WW) NVIDIA(GPU-0):     "1280x720" is specified in the EDID; however, the EDID's
[    21.783] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    21.783] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    21.783] (WW) NVIDIA(GPU-0):     check for mode "1280x720".
[    21.783] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    21.783] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    21.783] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    21.783] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    21.783] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".
[    21.784] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    21.784] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    21.784] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    21.784] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    21.784] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    21.784] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    21.784] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    21.784] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    21.784] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    21.784] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    21.784] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    21.784] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    21.784] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    21.784] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    21.784] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".
[    21.785] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    21.785] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    21.785] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    21.785] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (24.0 Hz); ignoring VertRefresh
[    21.785] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".
[    26.771] (II) NVIDIA(GPU-0): Display (WDT EW39T6MZ (DFP-1)) does not support NVIDIA 3D
[    26.771] (II) NVIDIA(GPU-0):     Vision stereo.
[    26.771] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    26.771] (**) NVIDIA(0):     device WDT EW39T6MZ (DFP-1) (Using EDID frequencies has
[    26.771] (**) NVIDIA(0):     been enabled on all display devices.)
[    26.774] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    26.774] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    26.774] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    26.774] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    26.774] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    26.775] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    26.775] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    26.775] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    26.775] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    26.775] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    26.775] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    26.775] (WW) NVIDIA(GPU-0):     "1280x720" is specified in the EDID; however, the EDID's
[    26.775] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    26.775] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    26.775] (WW) NVIDIA(GPU-0):     check for mode "1280x720".
[    26.775] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    26.775] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    26.775] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    26.775] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    26.775] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".
[    26.775] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    26.775] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    26.775] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    26.775] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    26.775] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    26.776] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    26.776] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    26.776] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    26.776] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    26.776] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    26.776] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    26.776] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    26.776] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    26.776] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    26.776] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".
[    26.777] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    26.777] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    26.777] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    26.777] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (24.0 Hz); ignoring VertRefresh
[    26.777] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".
[    29.413] (II) NVIDIA(GPU-0): Display (WDT EW39T6MZ (DFP-1)) does not support NVIDIA 3D
[    29.413] (II) NVIDIA(GPU-0):     Vision stereo.
[    29.413] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    29.413] (**) NVIDIA(0):     device WDT EW39T6MZ (DFP-1) (Using EDID frequencies has
[    29.413] (**) NVIDIA(0):     been enabled on all display devices.)
[    29.416] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    29.416] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    29.416] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    29.416] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    29.416] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    29.417] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    29.417] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    29.417] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    29.417] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    29.417] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    29.417] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    29.417] (WW) NVIDIA(GPU-0):     "1280x720" is specified in the EDID; however, the EDID's
[    29.417] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    29.417] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    29.417] (WW) NVIDIA(GPU-0):     check for mode "1280x720".
[    29.417] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    29.417] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    29.417] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    29.417] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    29.417] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".
[    29.418] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    29.418] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    29.418] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    29.418] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    29.418] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    29.418] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    29.418] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    29.418] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    29.418] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    29.418] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    29.418] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    29.418] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    29.418] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    29.418] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    29.418] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".
[    29.419] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    29.419] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    29.419] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    29.419] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (24.0 Hz); ignoring VertRefresh
[    29.419] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".
[    30.011] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    30.021] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    31.174] (II) NVIDIA(GPU-0): Display (WDT EW39T6MZ (DFP-1)) does not support NVIDIA 3D
[    31.174] (II) NVIDIA(GPU-0):     Vision stereo.
[    31.174] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    31.174] (**) NVIDIA(0):     device WDT EW39T6MZ (DFP-1) (Using EDID frequencies has
[    31.174] (**) NVIDIA(0):     been enabled on all display devices.)
[    31.177] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    31.177] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    31.177] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    31.177] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    31.177] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    31.177] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    31.177] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    31.177] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    31.177] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    31.177] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    31.177] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    31.177] (WW) NVIDIA(GPU-0):     "1280x720" is specified in the EDID; however, the EDID's
[    31.177] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    31.177] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    31.177] (WW) NVIDIA(GPU-0):     check for mode "1280x720".
[    31.178] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    31.178] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    31.178] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    31.178] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    31.178] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".
[    31.178] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    31.178] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    31.178] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    31.178] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    31.178] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    31.178] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    31.178] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    31.178] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    31.178] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    31.178] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    31.179] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    31.179] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    31.179] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    31.179] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    31.179] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".
[    31.179] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    31.179] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    31.179] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    31.179] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (24.0 Hz); ignoring VertRefresh
[    31.179] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".
[    38.174] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[    49.912] (II) NVIDIA(GPU-0): Display (WDT EW39T6MZ (DFP-1)) does not support NVIDIA 3D
[    49.912] (II) NVIDIA(GPU-0):     Vision stereo.
[    49.913] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    49.913] (**) NVIDIA(0):     device WDT EW39T6MZ (DFP-1) (Using EDID frequencies has
[    49.913] (**) NVIDIA(0):     been enabled on all display devices.)
[    49.916] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    49.916] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    49.916] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    49.916] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    49.916] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    49.916] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    49.916] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    49.916] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    49.916] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    49.916] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    49.916] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    49.916] (WW) NVIDIA(GPU-0):     "1280x720" is specified in the EDID; however, the EDID's
[    49.916] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    49.916] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    49.916] (WW) NVIDIA(GPU-0):     check for mode "1280x720".
[    49.917] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    49.917] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    49.917] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    49.917] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    49.917] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".
[    49.917] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    49.917] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    49.917] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    49.917] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    49.917] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    49.917] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    49.917] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    49.917] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    49.917] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    49.917] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    49.918] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    49.918] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    49.918] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    49.918] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    49.918] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".
[    49.918] (WW) NVIDIA(GPU-0): The EDID for WDT EW39T6MZ (DFP-1) contradicts itself: mode
[    49.918] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    49.918] (WW) NVIDIA(GPU-0):     valid VertRefresh range (59.000-61.000 Hz) would exclude
[    49.918] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (24.0 Hz); ignoring VertRefresh
[    49.918] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".


```

---

