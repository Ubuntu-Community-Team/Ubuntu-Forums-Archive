---
title: "No screens found, no GUI after upgrade to 9.10"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by SillyKirby on 2009-11-12
I choose the auto upgrade to 9.10 when i was updating packages, and when finished got no GUI, came up with console. i tried startkde, no luck, said no Xserver. I then tried startx, no luck said No Screens Found. I looked on the forums and tried a bunch of stuff, like installing xinit, like reconfiguring xorg, and some other stuff. Still get the same error when i try to startx. looks like kdm is running, but an Xserver is not. But then i am an idiot, and barely understand what is going on. any help? Obviously i can't go forward without some help. sorry, but thanks if you have any ideas? Silly

---

### Post by earthpigg on 2009-11-12
hi,

still get an internet connection?

```
ping -c 3 google.com
```

if so, try uninstalling and reinstalling X.

```
sudo apt-get remove --purge xorg
```

if it tries to remove gnome and a zillion other things like gdm and/or gnome, etc (it may, i don't remember and haven't tried it in a while) you may need to read through the man page to find out the additional argument you need to add. or, if 'man apt-get' is to much for ya... post back here and we can read through it and tell you the exact command.

once X is gone, reinstall it.

```
sudo apt-get install xorg
```

---

### Post by SillyKirby on 2009-11-12
Tanks Earth PIGG, i do have an internet connection. i tried your advice and removed xorg, got a simple removal with no confusions, then tried to restart it, and ended up with the same problem:
startx results in a no screens found. hmm, still totally stuck???
but thanks for trying. any other ideas?

---

### Post by determined on 2009-11-13
I have the same problem.  Tried the remove-install of xorg with no change in "no screens found message".  Here is the full message from startx until I terminate it with ctrl+c:

> X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server x86_64 Ubuntu
Current Operating System: Linux waddle 2.6.31-14-server #48-Ubuntu SMP Fri Oct 16 15:07:34 UTC 2009 x86_64
Kernel command line: root=/dev/mapper/waddle-root ro quiet splash
Build Date: 26 October 2009  05:19:56PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@)
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Nov 13 13:09:08 2009
(==) Using config file: "/etc/X11/xorg.conf"
(EE) Unable to initialize PCS database
(EE)   Missing PCS defaults file /etc/ati/amdpcsdb.default
(EE) No devices detected.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support
         at [http://wiki.x.org](http://wiki.x.org)
 for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
giving up.^M
xinit:  No such file or directory (errno 2):  unable to connect to X server^M
xinit:  No such process (errno 3):  unexpected signal 2.

This is the file /var/log/Xorg.0.log,

> 

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server x86_64 Ubuntu
Current Operating System: Linux waddle 2.6.31-14-server #48-Ubuntu SMP Fri Oct 16 15:07:34 UTC 2009 x86_64
Kernel command line: root=/dev/mapper/waddle-root ro quiet splash 
Build Date: 26 October 2009  05:19:56PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Nov 13 13:44:05 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "amdcccle Layout"
(**) |-->Screen "amdcccle-Screen[1]-0" (0)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "amdcccle-Device[1]-0"
(==) No monitor specified for screen "amdcccle-Screen[1]-0".
	Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0xb40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0:1:0:0) 1002:94c1:1028:0d02 ATI Technologies Inc RV610 [Radeon HD 2400 XT] rev 0, Mem @ 0xd0000000/268435456, 0xfddf0000/65536, I/O @ 0x0000ce00/256, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.4.0, module version = 1.0.0
(II) Loading extension GLX
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.4.0, module version = 1.0.0
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.4.99.906, module version = 8.66.10
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.4.99.906, module version = 8.66.10
	Module class: X.Org Video Driver
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for fglrx
(II) ATI Proprietary Linux Driver Version Identifier:8.66.10
(II) ATI Proprietary Linux Driver Release Identifier: 8.66.1                               
(II) ATI Proprietary Linux Driver Build Date: Sep  3 2009 21:35:39
(EE) Unable to initialize PCS database
(EE)   Missing PCS defaults file /etc/ati/amdpcsdb.default
(EE) No devices detected.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
 

Here's (part of) the output from lspci:

> 
...
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV610 [Radeon HD 2400 XT]

I sincerely appreciate any advice and help anybody more familiar with this stuff might be able to offer.

---

### Post by determined on 2009-11-17
bump?

---

### Post by Mark Phelps on 2009-11-18
From your thread, it appears you have an ATI 2400XT.  IF this is an HD2400, then it should be supported in the latest ATI drivers.  That being the case, you should go to the AMD site and download Catalyst 9.11 and install the drivers, or you could also try using EnvyNG to install the drivers.

Barring that, you could also simply remove the ATI drivers for now using the link below:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

Following these instructions will install the open source drivers -- which aren't great -- but at least you'll get working video back.

---

