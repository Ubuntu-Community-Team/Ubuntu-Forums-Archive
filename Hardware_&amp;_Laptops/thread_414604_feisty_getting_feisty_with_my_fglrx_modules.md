---
title: "feisty getting feisty with my fglrx modules"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by inspiteofmyself on 2007-04-20
i did the fresh install of the newly released ubuntu...figured i wouldnt have many problems since i pretty much breezed through edgy and the ati drivers with very few issues...the usual things like lockups when logging out of gnome, etc...but i had full 3d and 2d acceleration, the choice of beryl or compiz, and a solidly working wine install.

well, first i tried that new "restricted drivers manager" in system administration...no 3d acceleration for my card. i used it again to remove those fglrx drivers...and went on my quest to install build tools, download the ati drivers (most recent 8.36.5 amd64) and compile and install them. no problems doing any of that.

for a short time i was having errors from xorg that were saying that it was loading an 8.35 driver, im not even sure where it would get that. i issued another depmod -ae, made sure it was in the restricted and blacklisted modules configurations and rebooted the laptop.

i dont see that error anymore, but i do see something new. first i see ati-agp loading and that seems to be successful...then a few lines later, i get an error about GART not being initialized...

here is where i stand now:

```

fluid@fluid-laptop:~$ cat /var/log/Xorg.0.log | grep fglrx
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
(II) fglrx(0): pEnt->device->identifier=0x7c4850
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) fglrx(0): PCI bus 1 card 5 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DPMS"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "ATI Radeon Xpress Series" (Chipset = 0x5955)
(--) fglrx(0): (PciSubVendor = 0x103c, PciSubDevice = 0x3085)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
(--) fglrx(0): MMIO registers at 0xb0100000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 262144 kB
(II) fglrx(0): VESA VBE OEM: ATI MOBILITY RADEON Xpress 200G Series
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: MS48
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[drm] failed to load kernel module "fglrx"
(WW) fglrx(0): Failed to open DRM connection
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) fglrx(0): Connected Display1: LCD on internal LVDS [lvds]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: LPL  Model: 0  Serial#: 0
(II) fglrx(0): Year: 2005  Week: 0
(II) fglrx(0): EDID Version: 1.2
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 33  vert.: 21
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): No DPMS capabilities specified; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.590 redY: 0.344   greenX: 0.323 greenY: 0.534
(II) fglrx(0): blueX: 0.156 blueY: 0.138   whiteX: 0.312 whiteY: 0.328
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 71.2 MHz   Image Size:  289 x 21 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) fglrx(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(II) fglrx(0):  LGPhilipsLCD
(II) fglrx(0):  LP154W01-TLA2
(II) fglrx(0): EDID (in hex):
(II) fglrx(0):  00ffffffffffff00320c000000000000
(II) fglrx(0):  000f0102802115780a0f109758528828
(II) fglrx(0):  23505400000001010101010101010101
(II) fglrx(0):  010101010101d51b00a0502017303020
(II) fglrx(0):  26002115100000190000000000000000
(II) fglrx(0):  00000000000000000000000000fe004c
(II) fglrx(0):  475068696c6970734c43440a000000fe
(II) fglrx(0):  004c503135345730312d544c41320008
(II) fglrx(0): End of Display1 EDID data --------------------
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000008
(II) fglrx(0): POWERplay version 3.  1 power state available:
(II) fglrx(0):   1. 301/250MHz @ 60Hz [enable load balancing]
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 13 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x800 (pitch 0)
(**) fglrx(0): *Mode "1280x800": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"   71.25  1280 1328 1360 1440  800 802 808 823
(**) fglrx(0):  Default mode "1024x768": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   71.25  1024 1200 1232 1440  768 786 792 823
(**) fglrx(0):  Default mode "848x480": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   71.25  848 1112 1144 1440  480 642 648 823
(**) fglrx(0):  Default mode "800x600": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   71.25  800 1088 1120 1440  600 702 708 823
(**) fglrx(0):  Default mode "720x576": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   71.25  720 1048 1080 1440  576 690 696 823
(**) fglrx(0):  Default mode "720x480": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   71.25  720 1048 1080 1440  480 642 648 823
(**) fglrx(0):  Default mode "640x480": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   71.25  640 1008 1040 1440  480 642 648 823
(**) fglrx(0):  Default mode "640x400": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   71.25  640 1008 1040 1440  400 602 608 823
(**) fglrx(0):  Default mode "640x350": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x350"   71.25  640 1008 1040 1440  350 577 583 823
(**) fglrx(0):  Default mode "512x384": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   71.25  512 944 976 1440  384 594 600 823
(**) fglrx(0):  Default mode "400x300": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   71.25  400 888 920 1440  300 702 708 823 doublescan
(**) fglrx(0):  Default mode "320x240": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   71.25  320 848 880 1440  240 642 648 823 doublescan
(**) fglrx(0):  Default mode "320x200": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   71.25  320 848 880 1440  200 602 608 823 doublescan
(--) fglrx(0): Display dimensions: (330, 210) mm
(--) fglrx(0): DPI set to (98, 96)
(--) fglrx(0): Virtual size is 1280x800 (pitch 1280)
(**) fglrx(0): *Mode "1280x800": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"   71.25  1280 1328 1360 1440  800 802 808 823
(**) fglrx(0):  Default mode "1024x768": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   71.25  1024 1200 1232 1440  768 786 792 823
(**) fglrx(0):  Default mode "848x480": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   71.25  848 1112 1144 1440  480 642 648 823
(**) fglrx(0):  Default mode "800x600": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   71.25  800 1088 1120 1440  600 702 708 823
(**) fglrx(0):  Default mode "720x576": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   71.25  720 1048 1080 1440  576 690 696 823
(**) fglrx(0):  Default mode "720x480": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   71.25  720 1048 1080 1440  480 642 648 823
(**) fglrx(0):  Default mode "640x480": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   71.25  640 1008 1040 1440  480 642 648 823
(**) fglrx(0):  Default mode "640x400": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   71.25  640 1008 1040 1440  400 602 608 823
(**) fglrx(0):  Default mode "640x350": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x350"   71.25  640 1008 1040 1440  350 577 583 823
(**) fglrx(0):  Default mode "512x384": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   71.25  512 944 976 1440  384 594 600 823
(**) fglrx(0):  Default mode "400x300": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   71.25  400 888 920 1440  300 702 708 823 doublescan
(**) fglrx(0):  Default mode "320x240": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   71.25  320 848 880 1440  240 642 648 823 doublescan
(**) fglrx(0):  Default mode "320x200": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   71.25  320 848 880 1440  200 602 608 823 doublescan
(==) fglrx(0): NoAccel = NO
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000000b
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 128 MB
(WW) fglrx(0): No DRM connection for driver fglrx.
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(EE) fglrx(0): GART is not initialized, disabling DRI
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0x48000000 FBMappedSize: 0x08000000
(==) fglrx(0): Write-combining range (0xc0000000,0x8000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,800) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 7391
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(**) fglrx(0): DPMS enabled
(**) fglrx(0): Video overlay enabled on CRTC1
(II) fglrx(0): GLESX enableFlags = 0
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
(II) fglrx(0): Acceleration enabled
(WW) fglrx(0): Option "UseFBDev" is not used
(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Using hardware cursor

```

of course, screensavers are doggish. both gear demos start out ok and then go chunky in a matter of seconds. 

fglrxinfo returns the following:

```

fluid@fluid-laptop:~$ fglrxinfo 
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

```

like i said, i had absolutely no problems getting all of this working on edgy, but feisty is being mean to me.

anyone got any clues or suggestions on what i should try next?

---

### Post by inspiteofmyself on 2007-04-20
UPDATE: 
```

fluid@fluid-laptop:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6458 (8.36.5)

```

now hopefully my Xgl session will work...lol. last time i tried it it looked pretty squirrely

---

### Post by hashstat on 2007-04-20
So what was the solution?  I'm seeing the same problem with my Radeon Mobility X600.

---

### Post by speakman on 2007-04-20
Same here with 9800XT.

---

### Post by sowelie on 2007-04-20
Thanks for telling us you fixed a problem we're having and not showing the solution!

---

### Post by ShinjiLeery on 2007-04-22
yeah... how do you solve the problem?
I have the same issue with mobility X600

---

### Post by nhimf on 2007-04-22
Hi I got the same problem and when i looked to which modules were loaded, I missed fglrx. You can see which modules are loaded with the command lsmod.

For some reason the module doesn't get loaded.

To "fix" this, add fglrx to /etc/modules

> 
sudo su -
echo fglrx >> /etc/modules


You can reboot or do "modprobe fglrx" and reset the X server (ctrl-alt-backspace)

---

### Post by 2DC on 2007-04-23
> **nhimf said:**
> Hi I got the same problem and when i looked to which modules were loaded, I missed fglrx. You can see which modules are loaded with the command lsmod.

For some reason the module doesn't get loaded.

To "fix" this, add fglrx to /etc/modules



You can reboot or do "modprobe fglrx" and reset the X server (ctrl-alt-backspace)

:guitar: Thanks!! this is definetly one of the missing piece...finally enabled direct_rendering.. now I can move on with Xgl and compiz/beryl...

Just a little problem though.. I still get screen flickering every second or so...do you have a fix for this???

---

### Post by P4VV37 on 2007-04-29
I've got the same problem.
I had no problems with instalation of the fglrx in my Ubuntu 7.04 and it was working. Everything was O.K. but wanted to try AIGLX. I've turned off fglrx in "restricted drivers manager" and "install" AIGLX. It's working, but it's very slow. Now I'm going to install fglrx again.
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide")
but it,s not working. 
```
# /etc/modules: kernel modules to load at boot time. 
 # 
 # This file contains the names of kernel modules that should be loaded 
 # at boot time, one per line. Lines beginning with "#" are ignored. 
 
 lp 
 fuse 
 fglrx
```
I don't know what can I do :( 
I've got Radeon 9550
p.s. sorry for my english :)

---

### Post by waxblood on 2007-05-02
I have xubuntu with xorg restricted ati drivers in Feisty for a radeon 9500Pro, but 3d doesn't work anymore. With Edgy I didn't have this problem. I've tried to put fglrx in /etc/modules, but the problem persists. I've also tried open source and proprietary drivers. These are my xorg.0.log strange lines: 

```
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
..... same for card1->14
(WW) fglrx(0): Failed to open DRM connection
etc......
(WW) fglrx(0): No DRM connection for driver fglrx.
etc.......
(==) AIGLX enabled
(II) Loading extension GLX
(EE) fglrx(0): GART is not initialized, disabling DRI
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

(EE) AIGLX: Screen 0 is not DRI capable
```


In fact I don't know very well what is AIGLX and how it relates to Ubuntu, but for sure it is used for 3d desktops, which I don't need. I saw these lines, so I was thinking if AIGLX is related to my problem, and if yes, how could I disable it.

 (==) AIGLX enabled
(II) Loading extension GLX
(EE) fglrx(0): GART is not initialized, disabling DRI



this is all the xorg log
```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux claxtron 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed May  2 11:47:31 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "L568"
(**) |   |-->Device "ATI Technologies, Inc. Radeon R300 NE [Radeon 9500 Pro]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/X11/fonts/misc,
	/usr/share/X11/fonts/100dpi/:unscaled,
	/usr/share/X11/fonts/75dpi/:unscaled,
	/usr/share/X11/fonts/Type1,
	/usr/share/X11/fonts/100dpi,
	/usr/share/X11/fonts/75dpi,
	/usr/share/fonts/X11/misc,
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
(**) Extension "Composite" is disabled
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
(II) PCI: 00:00:0: chip 1106,3189 card 1043,807f rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b168 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 14e4,4401 card 1043,80a8 rev 01 class 02,00,00 hdr 00
(II) PCI: 00:0e:0: chip 109e,0350 card 0000,0000 rev 12 class 04,00,00 hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1043,808c rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1043,808c rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1043,808c rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3104 card 1043,808c rev 82 class 0c,03,20 hdr 00
(II) PCI: 00:11:0: chip 1106,3177 card 1043,808c rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:1: chip 1106,0571 card 1043,808c rev 06 class 01,01,8a hdr 00
(II) PCI: 00:11:5: chip 1106,3059 card 1043,8095 rev 50 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 1002,4e45 card 1002,0002 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,4e65 card 1002,0003 rev 00 class 03,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xf7ffffff (0x18000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI: (0:14:0) Brooktree Corporation Bt848 Video Capture rev 18, Mem @ 0xdf000000/12
(--) PCI:*(1:0:0) ATI Technologies Inc Radeon R300 NE [Radeon 9500 Pro] rev 0, Mem @ 0xf0000000/27, 0xde800000/16, I/O @ 0xd800/8, BIOS @ 0xeffe0000/17
(--) PCI: (1:0:1) ATI Technologies Inc Radeon R300 [Radeon 9500 Pro] (Secondary) rev 0, Mem @ 0xe0000000/27, 0xde000000/16
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
(II) PCI Memory resource overlap reduced 0xf8000000 from 0xfbffffff to 0xf7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xdd000000 - 0xdd0000ff (0x100) MX[B]
	[1] -1	0	0xdd800000 - 0xdd801fff (0x2000) MX[B]
	[2] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[3] -1	0	0xde000000 - 0xde00ffff (0x10000) MX[B](B)
	[4] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[5] -1	0	0xeffe0000 - 0xefffffff (0x20000) MX[B](B)
	[6] -1	0	0xde800000 - 0xde80ffff (0x10000) MX[B](B)
	[7] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0xdf000000 - 0xdf000fff (0x1000) MX[B](B)
	[9] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[10] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[11] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[12] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[13] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[14] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdd000000 - 0xdd0000ff (0x100) MX[B]
	[1] -1	0	0xdd800000 - 0xdd801fff (0x2000) MX[B]
	[2] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[3] -1	0	0xde000000 - 0xde00ffff (0x10000) MX[B](B)
	[4] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[5] -1	0	0xeffe0000 - 0xefffffff (0x20000) MX[B](B)
	[6] -1	0	0xde800000 - 0xde80ffff (0x10000) MX[B](B)
	[7] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0xdf000000 - 0xdf000fff (0x1000) MX[B](B)
	[9] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[10] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[11] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[12] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[13] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[14] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
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
	[4] -1	0	0xdd000000 - 0xdd0000ff (0x100) MX[B]
	[5] -1	0	0xdd800000 - 0xdd801fff (0x2000) MX[B]
	[6] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[7] -1	0	0xde000000 - 0xde00ffff (0x10000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xeffe0000 - 0xefffffff (0x20000) MX[B](B)
	[10] -1	0	0xde800000 - 0xde80ffff (0x10000) MX[B](B)
	[11] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xdf000000 - 0xdf000fff (0x1000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[16] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[17] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[18] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[19] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[20] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
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
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
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
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules//fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.34.8
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
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
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.34.8
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.34g1                           
(II) ATI Proprietary Linux Driver Build Date: Feb 20 2007 11:49:19
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.34.1.1.2.3-driver-lnx-x86-x86_64-327152
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset Supported AMD Graphics Processor (0x4E45) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdd000000 - 0xdd0000ff (0x100) MX[B]
	[5] -1	0	0xdd800000 - 0xdd801fff (0x2000) MX[B]
	[6] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[7] -1	0	0xde000000 - 0xde00ffff (0x10000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xeffe0000 - 0xefffffff (0x20000) MX[B](B)
	[10] -1	0	0xde800000 - 0xde80ffff (0x10000) MX[B](B)
	[11] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xdf000000 - 0xdf000fff (0x1000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[16] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[17] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[18] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[19] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[20] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x81e68e8
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdd000000 - 0xdd0000ff (0x100) MX[B]
	[5] -1	0	0xdd800000 - 0xdd801fff (0x2000) MX[B]
	[6] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[7] -1	0	0xde000000 - 0xde00ffff (0x10000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xeffe0000 - 0xefffffff (0x20000) MX[B](B)
	[10] -1	0	0xde800000 - 0xde80ffff (0x10000) MX[B](B)
	[11] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xdf000000 - 0xdf000fff (0x1000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[19] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[20] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[21] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[22] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[23] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[24] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[25] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DPMS"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) Loading sub module "vm86"
(II) LoadModule: "vm86"
(II) Loading /usr/lib/xorg/modules//libvm86.so
(II) Module vm86: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "RADEON 9500 PRO / 9700" (Chipset = 0x4e45)
(--) fglrx(0): (PciSubVendor = 0x1002, PciSubDevice = 0x0002)
(--) fglrx(0): board vendor info: original ATI graphics adapter
(--) fglrx(0): Linear framebuffer (phys) at 0xf0000000
(--) fglrx(0): MMIO registers at 0xde800000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 131072 kB
(II) fglrx(0): VESA VBE OEM: ATI R300
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: R300
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
(WW) fglrx(0): Failed to open DRM connection
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(II) fglrx(0): board/chipset is supported by this driver (original ATI board)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) fglrx(0): Connected Display1: DFP on internal TMDS [tmds1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: ENC  Model: 1733  Serial#: 16843009
(II) fglrx(0): Year: 2004  Week: 46
(II) fglrx(0): EDID Version: 1.2
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) fglrx(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) fglrx(0): Serial No: 53614114
(II) fglrx(0): Ranges: V min: 59  V max: 61 Hz, H min: 31  H max: 64 kHz, PixClock max 110 MHz
(II) fglrx(0): Monitor name: L568
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff0015c3331701010101
(II) fglrx(0): 	2e0e010280221b78eaee95a3544c9926
(II) fglrx(0): 	0f5054a1080081800101010101010101
(II) fglrx(0): 	010101010101302a009851002a403070
(II) fglrx(0): 	1300520e1100001e000000ff00353336
(II) fglrx(0): 	31343131340a20202020000000fd003b
(II) fglrx(0): 	3d1f400b000a202020202020000000fc
(II) fglrx(0): 	004c3536380a202020202020202000e3
(II) fglrx(0): End of Display1 EDID data --------------------
(II) fglrx(0): Primary Controller - DFP on internal TMDS
(II) fglrx(0): Internal Desktop Setting: 0x00000008
(II) fglrx(0): POWERplay not supported on this hardware
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 15 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x1024 (pitch 0)
(**) fglrx(0): *Mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0): *Mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   74.48  1280 1336 1472 1664  720 721 724 746 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0):  Default mode "1024x480": 38.2 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x480"   38.16  1024 1048 1152 1280  480 481 484 497 +hsync
(**) fglrx(0):  Default mode "848x480": 31.5 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   31.48  848 864 952 1056  480 481 484 497 +hsync
(**) fglrx(0):  Default mode "720x576": 32.7 MHz (scaled from 0.0 MHz), 35.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   32.66  720 744 816 912  576 577 580 597 +hsync
(**) fglrx(0):  Default mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(--) fglrx(0): Display dimensions: (340, 270) mm
(--) fglrx(0): DPI set to (95, 96)
(--) fglrx(0): Virtual size is 1280x1024 (pitch 1280)
(**) fglrx(0): *Mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0): *Mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   74.48  1280 1336 1472 1664  720 721 724 746 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0):  Default mode "1024x480": 38.2 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x480"   38.16  1024 1048 1152 1280  480 481 484 497 +hsync
(**) fglrx(0):  Default mode "848x480": 31.5 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   31.48  848 864 952 1056  480 481 484 497 +hsync
(**) fglrx(0):  Default mode "720x576": 32.7 MHz (scaled from 0.0 MHz), 35.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   32.66  720 744 816 912  576 577 580 597 +hsync
(**) fglrx(0):  Default mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
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
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.34.8
	ABI class: X.Org Server Extension, version 0.3
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000000f
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(WW) fglrx(0): No DRM connection for driver fglrx.
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xde800000 - 0xde80ffff (0x10000) MX[B]
	[1] 0	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xdd000000 - 0xdd0000ff (0x100) MX[B]
	[7] -1	0	0xdd800000 - 0xdd801fff (0x2000) MX[B]
	[8] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[9] -1	0	0xde000000 - 0xde00ffff (0x10000) MX[B](B)
	[10] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[11] -1	0	0xeffe0000 - 0xefffffff (0x20000) MX[B](B)
	[12] -1	0	0xde800000 - 0xde80ffff (0x10000) MX[B](B)
	[13] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0xdf000000 - 0xdf000fff (0x1000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[18] 0	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[22] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[23] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[24] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[25] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[26] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[27] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[28] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(II) Loading sub module "glx"
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(EE) fglrx(0): GART is not initialized, disabling DRI
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xf0000000 FBMappedSize: 0x08000000
(==) fglrx(0): Write-combining range (0xf0000000,0x8000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 7167
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Using hardware cursor
fbarea0->box.x1 0x00000000, fbarea0->box.y1 0x00000404
fbarea0->box.x2 0x00000500, fbarea0->box.y2 0x00000406
icon[0].start=0x505000
fbarea1->box.x1 0x00000000, fbarea1->box.y1 0x00000406
fbarea1->box.x2 0x00000500, fbarea1->box.y2 0x00000408
icon[1].start=0x508000
(**) fglrx(0): Video overlay enabled on CRTC1
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
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "it"
(**) Generic Keyboard: XkbLayout: "it"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
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
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
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
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!

```


Ciao,
David

---

### Post by jespdj on 2007-05-02
AIGLX does not work with the ATI fglrx driver according to [this page from the Compiz documentation](http://compiz.org/ATI):
> Fglrx is the official ATI's driver. Latest version works only for Radeon 9200 and newer versions. Older versions of fglrx (up to 8.28) work with older cards too. It is recommended, if you have any card up to 9200, to use the free drivers, otherwise use fglrx. **Fglrx doesn't support AIGLX. That means you must use XGL with it.** AIGLX support is expected to be added in next few versions (few months).
So you can stop trying to get AIGLX to work with the fglrx driver. You must use XGL instead of AIGLX if you want to have something like Compiz or Beryl working on your ATI card.

Look at [these instructions](https://help.ubuntu.com/community/CompositeManager/Xgl) to get XGL working. I followed this and I have Compiz working on my ATI X1600 card. I have now two displays, 0 and 1 running (NOT two monitors, just one monitor). On display 1, Xgl is running, as the instructions said.
```

$ fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 2.0.6334 (8.34.8)

$ fglrxinfo -display :1
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 1.2 (2.0.6334 (8.34.8))
```
The "DRI" is something that the ATI driver does not support.

I hope this info is useful. Getting this stuff running, especially with an ATI card, is a pain...

---

