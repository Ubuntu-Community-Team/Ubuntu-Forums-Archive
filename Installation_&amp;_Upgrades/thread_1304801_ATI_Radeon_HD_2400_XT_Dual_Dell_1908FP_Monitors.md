---
title: "ATI Radeon HD 2400 XT Dual Dell 1908FP Monitors"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by charleshbaker on 2009-10-29
Display applet only "sees" one monitor. I've got desktopbackground on both. Gnome toolbar at top of both. Toolbar at bottom only on left monitor. Can't drag apps between monitors. Help! This worked in 9.04

Using:
cbaker@rain:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2400 XT
OpenGL version string: 2.1.9016



display: :0.0  screen: 1
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2400 XT
OpenGL version string: 2.1.9016

cbaker@rain:~$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: RV610 [Radeon HD 2400 XT]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:28 memory:d0000000-dfffffff(prefetchable) memory:fe9f0000-fe9fffff ioport:dc00(size=256) memory:fea00000-fea1ffff(prefetchable)

cbaker@rain:~$ cat /etc/X11/xorg.conf | grep -v '^#'


Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "Default Screen" 0 0
	Screen         "aticonfig-Screen[0]-1" LeftOf "Default Screen"
	Option "RenderAccel" true
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	Option	    "OverlayOnCRTC2" "1"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-1"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
	SubSection "Display"
		Virtual   2560 1024
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-1"
	Device     "aticonfig-Device[0]-1"
	Monitor    "aticonfig-Monitor[0]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

---

### Post by charleshbaker on 2009-10-29
Well, I returned to the open driver instead of the proprietary one and now desktop effects don't work, but dual monitors work as expected. In addition I have a black box around Cairo Dock which is why I tried the proprietary driver to begin with.

So, how can I have dual monitors work and desktop effects?

Current set up:

cbaker@rain:~$ fglrxinfo
The program 'fglrxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install xorg-driver-fglrx
fglrxinfo: command not found
cbaker@rain:~$ sudo lshw -C display
[sudo] password for cbaker: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: RV610 [Radeon HD 2400 XT]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: latency=0
       resources: memory:d0000000-dfffffff(prefetchable) memory:fe9f0000-fe9fffff ioport:dc00(size=256) memory:fea00000-fea1ffff(prefetchable)
cbaker@rain:~$ cat /etc/X11/xorg.conf | grep -v '^#'

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2560 1024
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

cbaker@rain:~$

---

