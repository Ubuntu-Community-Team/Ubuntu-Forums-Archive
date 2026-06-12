---
title: "XOrg problems"
date: 2012-07-20
forum: Hardware
---

### Post by hunter.allen on 2012-07-20
Hello all, 

Issues with xorg in ubuntu 10.04... Don't know what I did wrong. Here my xorg file: 


```
allenh1@roboard:~$ cat /var/log/Xorg.0.log

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
Current Operating System: Linux roboard 2.6.34.10-vortex86-sg #3 Tue Jul 12 02:05:36 CST 2011 i586
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.34.10-vortex86-sg root=UUID=f9e0c253-c285-46fa-82e2-365e4a970fba ro quiet splash text
Build Date: 25 February 2012  06:59:39AM
xorg-server 2:1.7.6-2ubuntu7.11 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jul 20 10:49:20 2012
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "X.org Configured"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "XGIGraphic"
(**) |-->Input Device "Mouse0"
(**) |-->Input Device "Keyboard0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	catalogue:/etc/X11/fontpath.d,
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
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(--) using VT number 7

(--) PCI:*(0:0:3:0) 18ca:0020:18ca:0020 XGI Technology Inc. (eXtreme Graphics Innovation) Volari Z7/Z9/Z9s series VGA rev 0, Mem @ 0xf8000000/67108864, 0xfefc0000/262144, I/O @ 0x0000df80/128, BIOS @ 0x????????/32768
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "vnc"
(WW) Warning, couldn't open module vnc
(II) UnloadModule: "vnc"
(EE) Failed to load module "vnc" (module does not exist, 0)
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "xgiz"
(II) Loading /usr/lib/xorg/modules/drivers/xgiz_drv.so
(II) Module xgiz: vendor="X.Org Foundation"
	compiled for 1.7.1, module version = 2.81.8
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) XGIZ: driver for XGI chipsets: Volari Z7_Z9_Z9s, Volari Z9_Z9s,
	Volari Z11
(II) Primary Device is: PCI 00@00:03:0
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.1.0
	ABI class: X.Org Video Driver, version 6.0
(II) XGIZ(0): XGI driver (2010/08/13-1)
(II) XGIZ(0): Copyright (C) 2001-2004 Thomas Winischhofer <thomas@winischhofer.net> and others
(II) XGIZ(0): Compiled for XFree86 1.7.1.0

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x3b) [0x80e954b]
1: /usr/bin/X (0x8048000+0x61e2d) [0x80a9e2d]
2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb773f410]
3: /usr/bin/X (InitOutput+0x5c8) [0x80b9e28]
4: /usr/bin/X (0x8048000+0x1ebbb) [0x8066bbb]
5: /lib/libc.so.6 (__libc_start_main+0xe6) [0xb7485bc6]
6: /usr/bin/X (0x8048000+0x1e961) [0x8066961]
Illegal instruction at address 0xb72fee43

Caught signal 4 (Illegal instruction). Server aborting

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
```


This is my configuration file: 


```
allenh1@roboard:~$ cat /etc/X11/xorg.conf
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "catalogue:/etc/X11/fontpath.d"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "glx"
	Load  "vnc"
	Load  "dbe"
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
EndSection


Section "Device"
    Identifier  "XGIGraphic"
    BoardName   "XGI Volari Z7_Z9_Z9s_Z9M"
    VendorName  "XGI Technology Inc."
    Driver      "xgiz"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "XGIGraphic"
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

Any ideas as to why I can't get my desktop going? 

thanks, 
-Hunter A.

---

### Post by TheFu on 2012-07-20
No ideas and I didn't look closely.
Did you try moving the xorg.conf file to a different name "xorg.conf-save" and letting the X defaults work? Around 10.04, the defaults became pretty good for most needs. I don't even have a file one on my current desktop.

---

### Post by hunter.allen on 2012-07-20
How do I use the defaults?

---

### Post by hunter.allen on 2012-07-20
So I ran these commands: 

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-save

sudo rm -rf /etc/X11/xorg.conf
```

When I did "startx" it failed in a worse manner than previously. No screens found...

---

### Post by TheFu on 2012-07-22
.

---

### Post by TheFu on 2012-07-22
So that means to me that the defaults won't work on your system. This means you will need to learn more than anyone wants to know about the xorg.conf file. Sorry.

I'd start that learning here: 
* [https://wiki.ubuntu.com/X/Config/](https://wiki.ubuntu.com/X/Config/)
* 'man xorg.conf'

You'll probably need to know your graphics card(s) and monitor(s) intimately to make this work. At the end of the X start output there is a log file mentioned.  Reviewing that log file should help determine what the actual error is.  A likely place for the most recent log file is: /var/log/Xorg.0.log

---

### Post by hunter.allen on 2012-07-24
after fussing with it, I think I have a fix for this. I updated my nvidia driver from their [website]("http://www.nvidia.com/object/unix.html") (I was just as scared as you are). The driver was not so easily installed... 

First, remove all the nvidia stuff you have on your system. After you got them all, you can install it. Press crtl+alt+F1. Close X11:

```
sudo service lightdm stop
```

Log in, then change to root user: 

```
sudo -i
```

Now, use the .run file. Should install. After that, just reboot.

---

