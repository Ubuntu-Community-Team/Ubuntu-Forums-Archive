---
title: "cant enable simple desktop effects openchrome"
date: 2012-02-15
forum: Hardware
---

### Post by maestrobwh1 on 2012-02-15
Anyone have desktop effects with Openchrome Driver with Lucid?

I am trying to get basic 3D in Ubuntu Lucid using openchrome.  It fails to start in the appearance settings after it tries to load drivers.  I thought it possible to run simple effects with this driver so I am not sure why it is searching.  

here is some info

ubuntu@ubuntu-oqo:~$ glxinfo | grep -i direct
direct rendering: Yes
ubuntu@ubuntu-oqo:~$ cat /var/log/Xorg.0.log | grep -i accel
(**) CHROME(0): Option "AccelMethod" "EXA"
(==) CHROME(0): Hardware acceleration is enabled.
(**) CHROME(0): Using EXA acceleration architecture.
(==) CHROME(0): EXA composite acceleration enabled.
(==) CHROME(0): AGP DMA will be used for 2D acceleration.
(II)         Composite (RENDER acceleration)
(II) CHROME(0): [EXA] Trying to enable EXA acceleration.
(II) CHROME(0): [EXA] Enabled EXA acceleration.
ubuntu@ubuntu-oqo:~$ cat /var/log/Xorg.0.log | grep "dri"
	X.Org XInput driver : 7.0
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri2" will be loaded by default.
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
(II) Loading /usr/lib/xorg/modules/drivers/openchrome_drv.so
(!!) VIA Technologies does not support this driver in any way.
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
(II) [drm] loaded kernel module for "via" driver.
(II) CHROME(0): [dri] visual configs initialized.
(II) CHROME(0): [dri] mmio mapped.
(II) CHROME(0): [dri] Using PCI.
(II) CHROME(0): [dri] Frame buffer initialized.
(II) CHROME(0): [dri] Kernel data initialized.
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
(II) AIGLX: Loaded and initialized /usr/lib/dri/unichrome_dri.so
	ABI class: X.Org XInput driver, version 7.0
(II) No input driver/identifier specified (ignoring)
(II) No input driver/identifier specified (ignoring)
(II) No input driver/identifier specified (ignoring)
(II) No input driver/identifier specified (ignoring)
(II) No input driver/identifier specified (ignoring)
ubuntu@ubuntu-oqo:~$ 

Here is my xorg:

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "openchrome"
	Option 		"VBEModes" "true"
   	Option 		"EnableAGPDMA" "true"
	Option          "AccelMethod" "EXA"
	Option 		"MigrationHeuristic" "greedy"
	Option 		"SWCursor"
#	Option 		"PanelSize" "800x480"
#	Option 		"ActiveDevice" "LCD"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"800x480" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 		"Default Screen"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

