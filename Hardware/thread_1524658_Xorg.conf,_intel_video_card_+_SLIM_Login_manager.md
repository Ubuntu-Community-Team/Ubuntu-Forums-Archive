---
title: "Xorg.conf, intel video card + SLIM Login manager"
date: 2010-07-05
forum: Hardware
---

### Post by PaLoBo on 2010-07-05
Hey all.

I'm trying to setup a lightweight system. I've installed Openbox and all works great if I use GDM/KDM/XDM, however if I try and use SLiM, it just hangs on startup.

Opening a console, I can see that slim fails with the following error:

```
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux LT-PLOBO 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.32-23-generic root=UUID=9a29530c-6f3c-4268-8983-244244be0c29 ro quiet splash
Build Date: 16 June 2010  09:31:32AM
xorg-server 2:1.7.6-2ubuntu7.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jul  5 20:23:30 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(EE) Failed to load module "kms" (module does not exist, 0)
(EE) intel(0): [drm] failed to set drm interface version.
(EE) intel(0): Failed to become DRM master.
DRM_IOCTL_I915_GEM_APERTURE failed: Bad file descriptor
Assuming 131072kB available aperture size.
May lead to reduced performance or incorrect rendering.
get chip id failed: -1 [9]
param: 4, val: 0
get fences failed: -1 [9]
param: 6, val: 0
(EE) intel(0): failed to get resources: Bad file descriptor
(EE) intel(0): Kernel modesetting setup failed
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
```

If I start GDM then all goes well once again.

My current xorg.conf:
```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load "drm"
EndSection

Section "Monitor"
    Identifier   "LVDS1"
    Option       "PreferredMode" "1280x800"
    Option       "NoDDC"
EndSection

Section "Monitor"
    Identifier   "VGA1"
    Option       "PreferredMode" "1280x1024"
    Option       "RightOf"  "LVDS"
    Option       "Position"      "1280 0"
    Option       "Enable"   "true"
    Option       "NoDDC"
EndSection

Section "Device"
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
    Option      "monitor-LVDS"  "LVDS1"
    Option      "monitor-VGA"   "VGA1"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "LVDS1"
	SubSection "Display"
		Viewport   0 0
		Depth     24
                Virtual  2560 1024           
	EndSubSection
EndSection
```

Any ideas or help will be greatly appreciated.

Cheers,
PL

---

