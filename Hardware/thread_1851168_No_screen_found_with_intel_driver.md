---
title: "No screen found with intel driver"
date: 2011-09-27
forum: Hardware
---

### Post by pgcudahy on 2011-09-27
Hello, I've been slowly trying to set up my old m1400 tablet pc with ubuntu and have hit a snag. Earlier I was able to get the digitizer pen input working with this xorg.conf
```
Section "InputDevice"
  Driver "wacom"
  Identifier "stylus"
  Option "Device" "/dev/ttyS4"
  Option "Type" "stylus"
  Option "Button2" "3"
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "eraser"
  Option "Device" "/dev/ttyS4"
  Option "Type" "eraser"
EndSection

Section "ServerLayout"
  Identifier "X.org Configured"
  InputDevice "stylus"
  InputDevice "eraser"
EndSection
```

That Favux was nice enough to hook me up with. Works perfectly

My next step was trying to speed up the graphics enough to run xbmc. According to lspci I have an "Intel Corporation 82852/855GM Integrated Graphics Device" and by searching the googles it looks like 11.04 installs a frame buffer driver by default which doesn't have 3d acceleration.  I then found [https://launchpad.net/~glasen/+archive/intel-driver](https://launchpad.net/~glasen/+archive/intel-driver) which will install the intel driver with 3d acceleration! Now I'm trying to modify my xorg.conf to use this intel driver but running into issues. 

Most guides recommend this in xorg.conf
```
Section "Device"
    Identifier "Configured Video Device"
    Driver "intel"
EndSection

Section "Monitor"
    Identifier "Configured Monitor"
EndSection

Section "Screen"
    Identifier "Default Screen"
    Monitor "Configured Monitor"
    Device "Configured Video Device"
EndSection
```

How can I merge these two snippets to get a working xorg? When I past them together I get an error that no screens are found. I tried adding Screen "Default Screen" to the ServerLayout section but get the same error. 

Here's my current xorg.conf
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "stylus"
  Option "Device" "/dev/ttyS4"
  Option "Type" "stylus"
  Option "Button2" "3"
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "eraser"
  Option "Device" "/dev/ttyS4"
  Option "Type" "eraser"
EndSection

Section "ServerLayout"
  Identifier "X.org Configured"
  Screen  "Default Screen"
  InputDevice "stylus"
  InputDevice "eraser"
EndSection
```

And my xorg.0.log
```
[   719.157] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[   719.157] X Protocol Version 11, Revision 0
[   719.157] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[   719.158] Current Operating System: Linux DisplayBox 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:18:14 UTC 2011 i686
[   719.158] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-11-generic root=UUID=893089d1-36c8-42dd-b377-bdfdcd17b061 ro splash acpi=off i915.modeset=1 vt.handoff=7
[   719.158] Build Date: 11 August 2011  03:47:56PM
[   719.158] xorg-server 2:1.10.1-1ubuntu1.2 (For technical support please see http://www.ubuntu.com/support) 
[   719.158] Current version of pixman: 0.20.2
[   719.158] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   719.158] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   719.159] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Sep 27 15:34:51 2011
[   719.159] (==) Using config file: "/etc/X11/xorg.conf"
[   719.159] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   719.161] (==) ServerLayout "X.org Configured"
[   719.161] (**) |-->Screen "Default Screen" (0)
[   719.161] (**) |   |-->Monitor "Configured Monitor"
[   719.162] (**) |   |-->Device "Configured Video Device"
[   719.162] (**) |-->Input Device "stylus"
[   719.162] (**) |-->Input Device "eraser"
[   719.162] (==) Automatically adding devices
[   719.162] (==) Automatically enabling devices
[   719.163] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   719.163] 	Entry deleted from font path.
[   719.163] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   719.163] 	Entry deleted from font path.
[   719.163] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   719.163] 	Entry deleted from font path.
[   719.163] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   719.163] 	Entry deleted from font path.
[   719.163] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   719.163] 	Entry deleted from font path.
[   719.163] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[   719.164] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   719.164] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[   719.164] (II) Loader magic: 0x81ffde0
[   719.164] (II) Module ABI versions:
[   719.164] 	X.Org ANSI C Emulation: 0.4
[   719.164] 	X.Org Video Driver: 10.0
[   719.164] 	X.Org XInput driver : 12.3
[   719.164] 	X.Org Server Extension : 5.0
[   719.167] (--) PCI:*(0:0:2:0) 8086:3582:14c0:0012 rev 2, Mem @ 0xe8000000/134217728, 0xe0000000/524288, I/O @ 0x00001800/8
[   719.168] (--) PCI: (0:0:2:1) 8086:3582:14c0:0012 rev 2, Mem @ 0xf0000000/134217728, 0xe0080000/524288
[   719.169] (II) Open ACPI successful (/var/run/acpid.socket)
[   719.169] (II) LoadModule: "extmod"
[   719.172] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   719.172] (II) Module extmod: vendor="X.Org Foundation"
[   719.172] 	compiled for 1.10.1, module version = 1.0.0
[   719.173] 	Module class: X.Org Server Extension
[   719.173] 	ABI class: X.Org Server Extension, version 5.0
[   719.173] (II) Loading extension MIT-SCREEN-SAVER
[   719.173] (II) Loading extension XFree86-VidModeExtension
[   719.173] (II) Loading extension XFree86-DGA
[   719.173] (II) Loading extension DPMS
[   719.173] (II) Loading extension XVideo
[   719.173] (II) Loading extension XVideo-MotionCompensation
[   719.173] (II) Loading extension X-Resource
[   719.173] (II) LoadModule: "dbe"
[   719.175] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   719.175] (II) Module dbe: vendor="X.Org Foundation"
[   719.175] 	compiled for 1.10.1, module version = 1.0.0
[   719.176] 	Module class: X.Org Server Extension
[   719.176] 	ABI class: X.Org Server Extension, version 5.0
[   719.176] (II) Loading extension DOUBLE-BUFFER
[   719.176] (II) LoadModule: "glx"
[   719.178] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   719.178] (II) Module glx: vendor="X.Org Foundation"
[   719.178] 	compiled for 1.10.1, module version = 1.0.0
[   719.178] 	ABI class: X.Org Server Extension, version 5.0
[   719.178] (==) AIGLX enabled
[   719.179] (II) Loading extension GLX
[   719.179] (II) LoadModule: "record"
[   719.181] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   719.181] (II) Module record: vendor="X.Org Foundation"
[   719.181] 	compiled for 1.10.1, module version = 1.13.0
[   719.181] 	Module class: X.Org Server Extension
[   719.181] 	ABI class: X.Org Server Extension, version 5.0
[   719.181] (II) Loading extension RECORD
[   719.181] (II) LoadModule: "dri"
[   719.183] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   719.184] (II) Module dri: vendor="X.Org Foundation"
[   719.184] 	compiled for 1.10.1, module version = 1.0.0
[   719.184] 	ABI class: X.Org Server Extension, version 5.0
[   719.184] (II) Loading extension XFree86-DRI
[   719.184] (II) LoadModule: "dri2"
[   719.186] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   719.187] (II) Module dri2: vendor="X.Org Foundation"
[   719.187] 	compiled for 1.10.1, module version = 1.2.0
[   719.187] 	ABI class: X.Org Server Extension, version 5.0
[   719.187] (II) Loading extension DRI2
[   719.187] (II) LoadModule: "intel"
[   719.188] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   719.229] (II) Module intel: vendor="X.Org Foundation"
[   719.229] 	compiled for 1.10.1, module version = 2.15.0
[   719.229] 	Module class: X.Org Video Driver
[   719.229] 	ABI class: X.Org Video Driver, version 10.0
[   719.230] (II) LoadModule: "wacom"
[   719.231] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[   719.232] (II) Module wacom: vendor="X.Org Foundation"
[   719.232] 	compiled for 1.10.0, module version = 0.10.11
[   719.232] 	Module class: X.Org XInput Driver
[   719.232] 	ABI class: X.Org XInput driver, version 12.3
[   719.232] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[   719.236] (--) using VT number 8

[   719.386] (EE) No devices detected.
[   719.386] 
Fatal server error:
[   719.386] no screens found
[   719.386] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[   719.386] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   719.386] 
```

Any help would be much appreciated

---

### Post by Superwayne on 2011-12-06
I encounted the same problem with the same xorg.conf file and the packages from Glasen Hardt under Ubuntu Oneiric. Under Debian Lenny everything worked fine but from Squeeze (6.0)/Lucid (10.04) on I've always got "no screen found". No matter if I tried the stock packages or the ones from Glasen. :(

---

