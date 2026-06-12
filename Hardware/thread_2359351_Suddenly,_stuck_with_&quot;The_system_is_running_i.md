---
title: "Suddenly, stuck with &quot;The system is running in low-graphics mode&quot;"
date: 2017-04-23
forum: Hardware
---

### Post by balleyne on 2017-04-23
I have a computer that's always on in my living room, hooked up to the TV screen. I had to swap out the hardware recently, maybe November or so, but it's been running fine on new hardware since then. Somewhere between Sunday night and Wednesday night, the display server crashed. I went to use it Wednesday night, and there was small text on the screen, looked like possibly a kernel panic from a distance, but I couldn't tell from the couch, so I just rebooted the machine. Since then, I've been getting this warning, no working graphics (only console and SSH access), and I don't know how to fix it.

> **The system is running in low-graphics mode**
"Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself."

I think I've found the kernel error in /var/log/syslog.3.gz:
[https://paste.ubuntu.com/24438639/](https://paste.ubuntu.com/24438639/)

Honestly, I have no idea what would have changed. I'v etried booting into multiple kernels.

It looks like I ran some updates on Apr 17:
[https://paste.ubuntu.com/24438646/](https://paste.ubuntu.com/24438646/)

Most of my Xorg.*.log files are ancient:
```
balleyne@terry:/var/log$ ls -lht Xorg.*
-rw-r--r-- 1 root root 36K Apr 23 00:30 Xorg.failsafe.log
-rw-r--r-- 1 root root 37K Apr 23 00:20 Xorg.failsafe.log.old
-rw-r--r-- 1 root root 32K Aug 21  2016 Xorg.0.log
-rw-r--r-- 1 root root 22K Aug 21  2016 Xorg.2.log
-rw-r--r-- 1 root root 31K Aug 20  2016 Xorg.0.log.old
-rw-r--r-- 1 root root 33K Aug 17  2016 Xorg.1.log
-rw-r--r-- 1 root root 44K Aug 11  2016 Xorg.1.log.old
-rw-r--r-- 1 root root 33K Jul 26  2016 Xorg.3.log
-rw-r--r-- 1 root root 26K Jul 23  2016 Xorg.2.log.old
-rw-r--r-- 1 root root 34K Jan 26  2016 Xorg.3.log.old
-rw-r--r-- 1 root root 33K Oct  6  2015 Xorg.4.log
-rw-r--r-- 1 root root 26K Apr  6  2014 Xorg.5.log
-rw-r--r-- 1 root root 26K Apr  6  2014 Xorg.6.log
-rw-r--r-- 1 root root 31K Apr  5  2014 Xorg.4.log.old
-rw-r--r-- 1 root root 30K Mar 26  2014 Xorg.6.log.old
-rw-r--r-- 1 root root 30K Mar 26  2014 Xorg.5.log.old
-rw-r--r-- 1 root root 25K Jul 21  2013 Xorg.8.log
-rw-r--r-- 1 root root 25K Jul 21  2013 Xorg.7.log
-rw-r--r-- 1 root root 25K Jun 29  2013 Xorg.7.log.old
-rw-r--r-- 1 root root 26K Aug 20  2012 Xorg.10.log
-rw-r--r-- 1 root root 29K Aug 20  2012 Xorg.9.log
-rw-r--r-- 1 root root 29K Aug 20  2012 Xorg.8.log.old
```

The only recent one:
```
balleyne@terry:/var/log$ cat Xorg.failsafe.log
[    64.606] 
X.Org X Server 1.18.4
Release Date: 2016-07-19
[    64.606] X Protocol Version 11, Revision 0
[    64.606] Build Operating System: Linux 4.4.0-45-generic i686 Ubuntu
[    64.606] Current Operating System: Linux terry.haise.ca 4.4.0-72-generic #93-Ubuntu SMP Fri Mar 31 14:07:23 UTC 2017 i686
[    64.606] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-72-generic root=UUID=504e3d4e-11d3-48c8-8467-436941ade75a ro quiet splash vt.handoff=7
[    64.606] Build Date: 02 November 2016  10:05:16PM
[    64.606] xorg-server 2:1.18.4-0ubuntu0.2 (For technical support please see http://www.ubuntu.com/support) 
[    64.606] Current version of pixman: 0.33.6
[    64.606] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    64.606] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    64.606] (++) Log file: "/var/log/Xorg.failsafe.log", Time: Sun Apr 23 00:30:50 2017
[    64.606] (++) Using config file: "/etc/X11/xorg.conf.failsafe"
[    64.606] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    64.606] (==) No Layout section.  Using the first Screen section.
[    64.606] (**) |-->Screen "Default Screen" (0)
[    64.606] (**) |   |-->Monitor "Configured Monitor"
[    64.640] (**) |   |-->Device "Configured Video Device"
[    64.640] (==) Automatically adding devices
[    64.640] (==) Automatically enabling devices
[    64.640] (==) Automatically adding GPU devices
[    64.640] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    64.640] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    64.640] 	Entry deleted from font path.
[    64.640] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	built-ins
[    64.640] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    64.640] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    64.677] (II) Loader magic: 0x802eb700
[    64.677] (II) Module ABI versions:
[    64.677] 	X.Org ANSI C Emulation: 0.4
[    64.677] 	X.Org Video Driver: 20.0
[    64.677] 	X.Org XInput driver : 22.1
[    64.677] 	X.Org Server Extension : 9.0
[    64.678] (--) using VT number 2

[    64.678] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[    64.678] (II) xfree86: Adding drm device (/dev/dri/card0)
[    64.680] (--) PCI:*(0:0:2:0) 8086:1616:19da:b246 rev 9, Mem @ 0xf6000000/16777216, 0xe0000000/268435456, I/O @ 0x0000f000/64
[    64.709] (II) LoadModule: "glx"
[    64.779] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    65.571] (II) Module glx: vendor="X.Org Foundation"
[    65.571] 	compiled for 1.18.4, module version = 1.0.0
[    65.571] 	ABI class: X.Org Server Extension, version 9.0
[    65.571] (==) AIGLX enabled
[    65.571] (II) LoadModule: "fbdev"
[    65.571] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    65.572] (II) Module fbdev: vendor="X.Org Foundation"
[    65.572] 	compiled for 1.18.1, module version = 0.4.4
[    65.572] 	Module class: X.Org Video Driver
[    65.572] 	ABI class: X.Org Video Driver, version 20.0
[    65.572] (II) FBDEV: driver for framebuffer: fbdev
[    65.579] (II) Loading sub module "fbdevhw"
[    65.579] (II) LoadModule: "fbdevhw"
[    65.579] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    65.579] (II) Module fbdevhw: vendor="X.Org Foundation"
[    65.579] 	compiled for 1.18.4, module version = 0.0.2
[    65.579] 	ABI class: X.Org Video Driver, version 20.0
[    65.579] (**) FBDEV(0): claimed PCI slot 0@0:2:0
[    65.579] (II) FBDEV(0): using default device
[    65.579] (II) FBDEV(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
[    65.579] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    65.579] (==) FBDEV(0): RGB weight 888
[    65.579] (==) FBDEV(0): Default visual is TrueColor
[    65.579] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    65.579] (II) FBDEV(0): hardware: inteldrmfb (video memory: 8100kB)
[    65.579] (II) FBDEV(0): checking modes against framebuffer device...
[    65.579] (II) FBDEV(0): checking modes against monitor...
[    65.579] (--) FBDEV(0): Virtual size is 1920x1080 (pitch 1920)
[    65.579] (**) FBDEV(0):  Built-in mode "current"
[    65.579] (==) FBDEV(0): DPI set to (96, 96)
[    65.579] (II) Loading sub module "fb"
[    65.579] (II) LoadModule: "fb"
[    65.580] (II) Loading /usr/lib/xorg/modules/libfb.so
[    65.631] (II) Module fb: vendor="X.Org Foundation"
[    65.631] 	compiled for 1.18.4, module version = 1.0.0
[    65.631] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    65.631] (**) FBDEV(0): using shadow framebuffer
[    65.631] (II) Loading sub module "shadow"
[    65.631] (II) LoadModule: "shadow"
[    65.631] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    65.631] (II) Module shadow: vendor="X.Org Foundation"
[    65.631] 	compiled for 1.18.4, module version = 1.1.0
[    65.631] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    65.631] (==) Depth 24 pixmap format is 32 bpp
[    66.942] (==) FBDEV(0): Backing store enabled
[    66.989] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.989] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.989] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.989] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.989] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.989] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.990] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    66.991] (==) FBDEV(0): DPMS enabled
[    67.053] (==) RandR enabled
[    67.079] (II) SELinux: Disabled on system
[    67.133] (II) AIGLX: Screen 0 is not DRI2 capable
[    67.133] (EE) AIGLX: reverting to software rendering
[    72.131] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    72.131] (II) AIGLX: Loaded and initialized swrast
[    72.249] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    72.781] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    72.781] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    72.782] (II) LoadModule: "evdev"
[    72.782] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    73.071] (II) Module evdev: vendor="X.Org Foundation"
[    73.102] 	compiled for 1.18.1, module version = 2.10.1
[    73.102] 	Module class: X.Org XInput Driver
[    73.102] 	ABI class: X.Org XInput driver, version 22.1
[    73.102] (II) Using input driver 'evdev' for 'Power Button'
[    73.102] (**) Power Button: always reports core events
[    73.102] (**) evdev: Power Button: Device: "/dev/input/event2"
[    73.102] (--) evdev: Power Button: Vendor 0 Product 0x1
[    73.102] (--) evdev: Power Button: Found keys
[    73.102] (II) evdev: Power Button: Configuring as keyboard
[    73.102] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    73.102] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    73.102] (**) Option "xkb_rules" "evdev"
[    73.102] (**) Option "xkb_model" "pc105"
[    73.102] (**) Option "xkb_layout" "us"
[    73.103] (II) config/udev: Adding input device Video Bus (/dev/input/event3)
[    73.103] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    73.103] (II) Using input driver 'evdev' for 'Video Bus'
[    73.103] (**) Video Bus: always reports core events
[    73.103] (**) evdev: Video Bus: Device: "/dev/input/event3"
[    73.103] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    73.103] (--) evdev: Video Bus: Found keys
[    73.103] (II) evdev: Video Bus: Configuring as keyboard
[    73.103] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input3/event3"
[    73.103] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    73.103] (**) Option "xkb_rules" "evdev"
[    73.103] (**) Option "xkb_model" "pc105"
[    73.103] (**) Option "xkb_layout" "us"
[    73.104] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    73.104] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    73.104] (II) Using input driver 'evdev' for 'Power Button'
[    73.104] (**) Power Button: always reports core events
[    73.104] (**) evdev: Power Button: Device: "/dev/input/event1"
[    73.104] (--) evdev: Power Button: Vendor 0 Product 0x1
[    73.104] (--) evdev: Power Button: Found keys
[    73.104] (II) evdev: Power Button: Configuring as keyboard
[    73.104] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[    73.104] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    73.104] (**) Option "xkb_rules" "evdev"
[    73.104] (**) Option "xkb_model" "pc105"
[    73.104] (**) Option "xkb_layout" "us"
[    73.105] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[    73.105] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    73.105] (II) Using input driver 'evdev' for 'Sleep Button'
[    73.105] (**) Sleep Button: always reports core events
[    73.105] (**) evdev: Sleep Button: Device: "/dev/input/event0"
[    73.105] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    73.105] (--) evdev: Sleep Button: Found keys
[    73.105] (II) evdev: Sleep Button: Configuring as keyboard
[    73.105] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0/event0"
[    73.105] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    73.105] (**) Option "xkb_rules" "evdev"
[    73.105] (**) Option "xkb_model" "pc105"
[    73.105] (**) Option "xkb_layout" "us"
[    73.105] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=3 (/dev/input/event12)
[    73.106] (II) No input driver specified, ignoring this device.
[    73.106] (II) This device may have been added with another device file.
[    73.106] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=7 (/dev/input/event13)
[    73.106] (II) No input driver specified, ignoring this device.
[    73.106] (II) This device may have been added with another device file.
[    73.106] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=8 (/dev/input/event14)
[    73.106] (II) No input driver specified, ignoring this device.
[    73.106] (II) This device may have been added with another device file.
[    73.107] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event4)
[    73.107] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    73.107] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    73.107] (**) Logitech USB Receiver: always reports core events
[    73.107] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event4"
[    73.160] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc526
[    73.160] (--) evdev: Logitech USB Receiver: Found 20 mouse buttons
[    73.160] (--) evdev: Logitech USB Receiver: Found scroll wheel(s)
[    73.160] (--) evdev: Logitech USB Receiver: Found relative axes
[    73.160] (--) evdev: Logitech USB Receiver: Found x and y relative axes
[    73.160] (II) evdev: Logitech USB Receiver: Configuring as mouse
[    73.160] (II) evdev: Logitech USB Receiver: Adding scrollwheel support
[    73.160] (**) evdev: Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    73.160] (**) evdev: Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    73.160] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb2/2-2/2-2:1.0/0003:046D:C526.0001/input/input4/event4"
[    73.160] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE, id 10)
[    73.160] (II) evdev: Logitech USB Receiver: initialized for relative axes.
[    73.160] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    73.160] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    73.160] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    73.160] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    73.161] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    73.161] (II) No input driver specified, ignoring this device.
[    73.161] (II) This device may have been added with another device file.
[    73.161] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event5)
[    73.161] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    73.161] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    73.161] (**) Logitech USB Receiver: always reports core events
[    73.161] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event5"
[    73.161] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc526
[    73.161] (--) evdev: Logitech USB Receiver: Found 1 mouse buttons
[    73.161] (--) evdev: Logitech USB Receiver: Found scroll wheel(s)
[    73.161] (--) evdev: Logitech USB Receiver: Found relative axes
[    73.161] (II) evdev: Logitech USB Receiver: Forcing relative x/y axes to exist.
[    73.161] (--) evdev: Logitech USB Receiver: Found absolute axes
[    73.161] (II) evdev: Logitech USB Receiver: Forcing absolute x/y axes to exist.
[    73.161] (--) evdev: Logitech USB Receiver: Found keys
[    73.161] (II) evdev: Logitech USB Receiver: Configuring as mouse
[    73.161] (II) evdev: Logitech USB Receiver: Configuring as keyboard
[    73.161] (II) evdev: Logitech USB Receiver: Adding scrollwheel support
[    73.161] (**) evdev: Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    73.161] (**) evdev: Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    73.161] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb2/2-2/2-2:1.1/0003:046D:C526.0002/input/input5/event5"
[    73.161] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD, id 11)
[    73.161] (**) Option "xkb_rules" "evdev"
[    73.161] (**) Option "xkb_model" "pc105"
[    73.161] (**) Option "xkb_layout" "us"
[    73.162] (II) evdev: Logitech USB Receiver: initialized for relative axes.
[    73.162] (WW) evdev: Logitech USB Receiver: ignoring absolute axes.
[    73.162] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    73.162] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    73.162] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    73.162] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    73.162] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event6)
[    73.162] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    73.162] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    73.162] (**) Logitech USB Receiver: always reports core events
[    73.162] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event6"
[    73.163] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc517
[    73.163] (--) evdev: Logitech USB Receiver: Found keys
[    73.163] (II) evdev: Logitech USB Receiver: Configuring as keyboard
[    73.163] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb2/2-7/2-7:1.0/0003:046D:C517.0003/input/input6/event6"
[    73.163] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD, id 12)
[    73.163] (**) Option "xkb_rules" "evdev"
[    73.163] (**) Option "xkb_model" "pc105"
[    73.163] (**) Option "xkb_layout" "us"
[    73.163] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event7)
[    73.163] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    73.163] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    73.163] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    73.164] (**) Logitech USB Receiver: always reports core events
[    73.164] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event7"
[    73.164] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc517
[    73.164] (--) evdev: Logitech USB Receiver: Found 12 mouse buttons
[    73.164] (--) evdev: Logitech USB Receiver: Found scroll wheel(s)
[    73.164] (--) evdev: Logitech USB Receiver: Found relative axes
[    73.164] (--) evdev: Logitech USB Receiver: Found x and y relative axes
[    73.164] (--) evdev: Logitech USB Receiver: Found absolute axes
[    73.164] (II) evdev: Logitech USB Receiver: Forcing absolute x/y axes to exist.
[    73.164] (--) evdev: Logitech USB Receiver: Found keys
[    73.164] (II) evdev: Logitech USB Receiver: Configuring as mouse
[    73.164] (II) evdev: Logitech USB Receiver: Configuring as keyboard
[    73.164] (II) evdev: Logitech USB Receiver: Adding scrollwheel support
[    73.164] (**) evdev: Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    73.164] (**) evdev: Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    73.164] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb2/2-7/2-7:1.1/0003:046D:C517.0004/input/input7/event7"
[    73.164] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD, id 13)
[    73.164] (**) Option "xkb_rules" "evdev"
[    73.164] (**) Option "xkb_model" "pc105"
[    73.164] (**) Option "xkb_layout" "us"
[    73.164] (II) evdev: Logitech USB Receiver: initialized for relative axes.
[    73.164] (WW) evdev: Logitech USB Receiver: ignoring absolute axes.
[    73.164] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    73.164] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    73.164] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    73.164] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    73.165] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
[    73.165] (II) No input driver specified, ignoring this device.
[    73.165] (II) This device may have been added with another device file.
[    73.165] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event10)
[    73.165] (II) No input driver specified, ignoring this device.
[    73.165] (II) This device may have been added with another device file.
[    73.165] (II) config/udev: Adding input device HDA Intel PCH Line Out (/dev/input/event11)
[    73.165] (II) No input driver specified, ignoring this device.
[    73.165] (II) This device may have been added with another device file.
[    73.167] (II) config/udev: Adding input device Nuvoton w836x7hg Infrared Remote Transceiver (/dev/input/event8)
[    73.167] (**) Nuvoton w836x7hg Infrared Remote Transceiver: Applying InputClass "evdev keyboard catchall"
[    73.167] (II) Using input driver 'evdev' for 'Nuvoton w836x7hg Infrared Remote Transceiver'
[    73.167] (**) Nuvoton w836x7hg Infrared Remote Transceiver: always reports core events
[    73.167] (**) evdev: Nuvoton w836x7hg Infrared Remote Transceiver: Device: "/dev/input/event8"
[    73.167] (--) evdev: Nuvoton w836x7hg Infrared Remote Transceiver: Vendor 0x1050 Product 0xc5
[    73.167] (--) evdev: Nuvoton w836x7hg Infrared Remote Transceiver: Found keys
[    73.167] (II) evdev: Nuvoton w836x7hg Infrared Remote Transceiver: Configuring as keyboard
[    73.167] (**) Option "config_info" "udev:/sys/devices/pnp0/00:02/rc/rc0/input8/event8"
[    73.167] (II) XINPUT: Adding extended input device "Nuvoton w836x7hg Infrared Remote Transceiver" (type: KEYBOARD, id 14)
[    73.167] (**) Option "xkb_rules" "evdev"
[    73.167] (**) Option "xkb_model" "pc105"
[    73.167] (**) Option "xkb_layout" "us"
[    73.168] (II) config/udev: Adding input device MCE IR Keyboard/Mouse (nuvoton-cir) (/dev/input/event9)
[    73.168] (**) MCE IR Keyboard/Mouse (nuvoton-cir): Applying InputClass "evdev pointer catchall"
[    73.168] (**) MCE IR Keyboard/Mouse (nuvoton-cir): Applying InputClass "evdev keyboard catchall"
[    73.168] (II) Using input driver 'evdev' for 'MCE IR Keyboard/Mouse (nuvoton-cir)'
[    73.168] (**) MCE IR Keyboard/Mouse (nuvoton-cir): always reports core events
[    73.168] (**) evdev: MCE IR Keyboard/Mouse (nuvoton-cir): Device: "/dev/input/event9"
[    73.168] (--) evdev: MCE IR Keyboard/Mouse (nuvoton-cir): Vendor 0 Product 0
[    73.168] (--) evdev: MCE IR Keyboard/Mouse (nuvoton-cir): Found 3 mouse buttons
[    73.168] (--) evdev: MCE IR Keyboard/Mouse (nuvoton-cir): Found relative axes
[    73.168] (--) evdev: MCE IR Keyboard/Mouse (nuvoton-cir): Found x and y relative axes
[    73.168] (--) evdev: MCE IR Keyboard/Mouse (nuvoton-cir): Found keys
[    73.168] (II) evdev: MCE IR Keyboard/Mouse (nuvoton-cir): Configuring as mouse
[    73.168] (II) evdev: MCE IR Keyboard/Mouse (nuvoton-cir): Configuring as keyboard
[    73.168] (**) evdev: MCE IR Keyboard/Mouse (nuvoton-cir): YAxisMapping: buttons 4 and 5
[    73.168] (**) evdev: MCE IR Keyboard/Mouse (nuvoton-cir): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    73.168] (**) Option "config_info" "udev:/sys/devices/virtual/input/input9/event9"
[    73.168] (II) XINPUT: Adding extended input device "MCE IR Keyboard/Mouse (nuvoton-cir)" (type: KEYBOARD, id 15)
[    73.168] (**) Option "xkb_rules" "evdev"
[    73.168] (**) Option "xkb_model" "pc105"
[    73.168] (**) Option "xkb_layout" "us"
[    73.168] (II) evdev: MCE IR Keyboard/Mouse (nuvoton-cir): initialized for relative axes.
[    73.168] (**) MCE IR Keyboard/Mouse (nuvoton-cir): (accel) keeping acceleration scheme 1
[    73.168] (**) MCE IR Keyboard/Mouse (nuvoton-cir): (accel) acceleration profile 0
[    73.168] (**) MCE IR Keyboard/Mouse (nuvoton-cir): (accel) acceleration factor: 2.000
[    73.168] (**) MCE IR Keyboard/Mouse (nuvoton-cir): (accel) acceleration threshold: 4
[    73.169] (II) config/udev: Adding input device MCE IR Keyboard/Mouse (nuvoton-cir) (/dev/input/mouse2)
[    73.169] (II) No input driver specified, ignoring this device.
[    73.169] (II) This device may have been added with another device file.
```

I've had no luck searching for that error.

When I try to sudo service gdm restart or sudo service lightdm restart, I get something like the following 
```
balleyne@terry:/var/log$ sudo service gdm restart
Job for gdm.service failed because the control process exited with error code. See "systemctl status gdm.service" and "journalctl -xe" for details.
```

Then, from journalctl -xe:
[https://paste.ubuntu.com/24438651/](https://paste.ubuntu.com/24438651/)

I don't have an active xorg.conf file.

Help?

---

### Post by TheFu on 2017-04-23
If the TV still works, then I'd check the cables.
If the GPU isn't working, I'd try a different GPU.

Is the card recognized still?  **sudo lshw -C video** will tell us much. Please use 'code tags' so things line up.

---

### Post by RobGoss on 2017-04-23
Hello and welcome to the forum, I think in most cases low graphic mode is do to **driver issues**, have you made any changes lately to your current drivers?

This post may be of help to you please see here: [https://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error](https://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error)

---

### Post by balleyne on 2017-04-24
> **TheFu said:**
> If the TV still works, then I'd check the cables.

TV still works. I can see the HDMI input from this computer, console and the safemode troubleshooting window, and other inputs (antennae, RCA, VGA) still work.

I tried swapping the HDMI cables, using a different cable and going into a different HDMI input on the screen, and rebooting. No difference.

> **TheFu said:**
> If the GPU isn't working, I'd try a different GPU.

I'm not sure how to test if the GPU is working, or how to try a different GPU?

> **TheFu said:**
> Is the card recognized still?  **sudo lshw -C video** will tell us much. Please use 'code tags' so things line up.

```
balleyne@terry:~$ sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: Broadwell-U Integrated Graphics
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:46 memory:f6000000-f6ffffff memory:e0000000-efffffff ioport:f000(size=64)
```

Thank you!

---

### Post by balleyne on 2017-04-24
> **RobGoss said:**
> I think in most cases low graphic mode is do to **driver issues**, have you made any changes lately to your current drivers?

Definitely not intentionally. The problem started days in between anyone using it graphically. The only thing I can imagine is the apt-get upgrade I ran via SSH somewhere during that time period, if something broke during an otherwise routine upgrade. But that didn't even line up with the date/time of the kernal panic stuff I found in the logs.

> **RobGoss said:**
> This post may be of help to you please see here: [https://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error](https://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error)

Thanks. I've tried those steps, and for Intel, installing the PPA, apt-get update && apt-get upgrade, reboot, and the problem persists. No luck. =\

---

### Post by TheFu on 2017-04-24
Ok, you are using the on-board video - iGPU.  I have that same video chip, it seems - from my chromebook:
```
$ sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: Broadwell-U Integrated Graphics
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:43 memory:e0000000-e0ffffff memory:d0000000-dfffffff ioport:1800(size=64)
```

On a desktop, you can go into the bios and disabled that on-board GPU AFTER adding another GPU. Which you should get depends on your system bus.  PCIe and $20-$40 is more than sufficient for a GPU if you are using the onboard one. Stick with AMD or nVidia cards for the best help.

On my chromebook, if the iGPU is fried, I'd sell it for parts and buy a new netbook. It isn't possible to swap out the GPU on 99.999% of laptops. There are USB-to-VGA options, but support under Linux is poor to zero (I've heard).

If you are seeing **any** video output on the screen, then the GPU isn't fried.  Most integrated GPUs take RAM from the main system RAM.  I've never seen a RAM stick fail, but maybe that could be it?  Or a failing power supply?

---

### Post by balleyne on 2017-04-24
Hey, thanks for all the help.

I don't think the GPU is fried.  I can see everything on the screen, it just loads into failsafe mode. So, I can see the BIOS screen, the grub screen, the splash screen loading, but then instead of taking me to the login screen, I see that "The system is running in low-graphics mode" window (and can interact with it with the mouse). I can also CTRL+ALT+F1 and get to a console and see all of that through the screen. Everything else about the system seems to be working fine... e.g. OpenSSH, Apache, MySQL, NextCloud are all working as before. It's just the display manager / xserver that's loading into failsafe mode now.

Also, it isn't possible to switch out the GPU on this machine. It's a little Zotac ZBOX mini PC thing, everything is integrated. I just bought it in November, so I guess hardware failure is possible, but it seems unlikely given that it's relatively new and I can still see everything else through the screen. I've also tried another cable, and hooking up another HDMI device to the same port on the TV screen, and it doesn't seem to be the cable or the screen that's the problem.

Failing power supply doesn't make sense because the thing is still on and working. Failing RAM... maybe I'll run a memtest? It seems weird that failing RAM would consistently affect only the xserver and everything else would work normally though.

Any advice on how to confirm what's going on with the software drivers?

---

### Post by TheFu on 2017-04-24
Different parts of a system are more picky about good power.  External GPUs would be more likely to have a power issue. I have seen that a few times.  But ... since this is on the CPU AND it is Intel, I think you are right.  It is not likely to be the iGPU.

The RAM taken for the video will come from the same area, ever boot.

You could reinstall the drivers. On my box, the package name is i915. If the storage isn't showing any issues, I doubt the driver is an issue.
I take it that xrandr and/or lxrandr don't show the mode you want?

---

