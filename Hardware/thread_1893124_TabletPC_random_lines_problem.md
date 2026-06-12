---
title: "TabletPC random lines problem"
date: 2011-12-09
forum: Hardware
---

### Post by grunzasr on 2011-12-09
I have an Acer C100 TravelMate. It's a convertible TabletPC meaning that it can be used as a regular laptop or the screen can be rotated 180 degrees and closed to turn it into a slate (which is real similar to a tablet). The only time I use the slate mode is when I am using Xournal to either handwrite notes or to mark-up PDF documents (saving trees and all that). It used to work great. Now I'm getting random lines while drawing. Using the xinput --test command shows some odd behaviour. As best as I can tell the information coming from the tablet digitizer is sometimes not including the X-axis information.
 
I'm starting to dig into the various X11 specs and so on but if someone that knows this stuff could provide some help I would appreciate it.
 
The problem is most likely not in Xournal since some of the times the Panel would get grabbed and moved; as if I had moved the stylus to the edge of the screen and selected the panel, then dragged it to where I was drawing.
 
My suspicion is that either the tablet hardware or the wacom driver is not reporting the X-axis co-ordinate if it hasn't changed but that some driver is getting confused by this.
 
This problem has rendered my TabletPC useless as a Tablet. When drawing a simple op-amp design I spent more time clicking on undo and trying to redraw the affected portions of the design that it would have been quicker to use a pen and paper, walk down the hall, scan the paper, then import the drawing. I'm trying to push for Tablet technology and non-Windows solutions but this problem is a show stopper.
 
This C100 ran WindowsXP without any problems like these random lines; it was just so slow with SP3 and anti-virus that it was unusable (10+ minutes to boot, etc).

---

### Post by Favux on 2011-12-09
Hi grunzasr,

Welcome to Ubuntu forums!

We need to know the Ubuntu release you are using, e.g. Lucid (10.04) or whatever so we know what kernel, X server, and xf86-input-wacom you are using.  That's a Wacom digitizer correct?  Usb or serial?
```
xinput list
```

---

### Post by grunzasr on 2011-12-09
My bad :(
 
The following information was cut-n-paste or copied by Flash drive.  My TabletPC is currently without network access.
 
 
 
**cat /etc/lsb-release shows:**
   DISTRIB_ID=Ubuntu
   DISTRIB_RELEASE=11.10
   DISTRIB_CODENAME=oneiric
 
 
**xinput --list shows:  (the funky characters look better on Xubuntu...)**
 
âŽ¡ Virtual core pointer id=2 [master pointer (3)]
âŽœ â†³ Virtual core XTEST pointer id=4 [slave pointer (2)]
âŽœ â†³ SynPS/2 Synaptics TouchPad id=10 [slave pointer (2)]
âŽœ â†³ [COLOR=red]Serial Wacom Tablet stylus id=11 [slave pointer (2)][/COLOR]
âŽœ â†³ Serial Wacom Tablet eraser id=12 [slave pointer (2)]
âŽ£ Virtual core keyboard id=3 [master keyboard (2)]
â†³ Virtual core XTEST keyboard id=5 [slave keyboard (3)]
â†³ Power Button id=6 [slave keyboard (3)]
â†³ Video Bus id=7 [slave keyboard (3)]
â†³ Sleep Button id=8 [slave keyboard (3)]
â†³ AT Translated Set 2 keyboard id=9 [slave keyboard (3)]
 
 
**uname -a shows:**
  
Linux tabby 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:25:36 UTC 2011 i686 i686 i386 GNU/Linux
 
 
**xinput --test [COLOR=red]11[/COLOR] shows:**
[snip]
motion a[0]=16195 a[1]=8139 a[2]=0 a[3]=0 a[4]=0 a[5]=-900 
motion a[0]=16196 a[1]=8156 a[2]=0 a[3]=0 a[4]=0 a[5]=-900 
motion a[0]=16198 a[1]=8170 a[2]=0 a[3]=0 a[4]=0 a[5]=-900 
motion a[0]=16200 a[1]=8185 a[2]=0 a[3]=0 a[4]=0 a[5]=-900 
motion a[0]=16201 a[1]=8198 a[2]=0 a[3]=0 a[4]=0 a[5]=-900 
motion a[0]=16203 a[1]=8210 a[2]=0 a[3]=0 a[4]=0 a[5]=-900 
motion a[1]=8222 a[2]=0 a[3]=0 a[4]=0 a[5]=-900 
motion a[0]=16204 a[1]=8233 a[2]=0 a[3]=0 a[4]=0 a[5]=-900 
motion a[0]=16203 a[1]=8245 a[2]=0 a[3]=0 a[4]=0 a[5]=-900 
motion a[0]=16202 a[1]=8256 a[2]=0 a[3]=0 a[4]=0 a[5]=-900 
motion a[0]=16201 a[1]=8267 a[2]=0 a[3]=0 a[4]=0 a[5]=-900 
motion a[0]=16199 a[1]=8279 a[2]=0 a[3]=0 a[4]=0 a[5]=-900 
motion a[0]=16197 a[1]=8289 a[2]=0 a[3]=0 a[4]=0 a[5]=-900 
motion a[0]=16195 a[1]=8300 a[2]=0 a[3]=0 a[4]=0 a[5]=-900 
motion a[0]=16194 a[1]=8305 a[2]=0 a[3]=0 a[4]=0 a[5]=-900 
motion a[0]=16192 a[1]=8316 a[2]=0 a[3]=0 a[4]=0 a[5]=-900 
motion a[1]=8323 a[2]=0 a[3]=0 a[4]=0 a[5]=-900 
motion a[0]=16191 a[1]=8330 a[2]=0 a[3]=0 a[4]=0 a[5]=-900 
motion a[0]=16190 a[1]=8343 a[2]=0 a[3]=0 a[4]=0 a[5]=-900 
motion a[1]=8350 a[2]=0 a[3]=0 a[4]=0 a[5]=-900 
motion a[1]=8356 a[2]=0 a[3]=0 a[4]=0 a[5]=-900 
motion a[1]=8363 a[2]=0 a[3]=0 a[4]=0 a[5]=-900 
motion a[0]=16184 a[1]=8361 a[2]=0 a[3]=0 a[4]=0 a[5]=-900 
[snip]
 
**cat /var/log/Xorg.0.log shows:**
X.Org X Server 1.10.4
Release Date: 2011-08-19
[ 36.196] X Protocol Version 11, Revision 0
[ 36.196] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[ 36.196] Current Operating System: Linux tabby 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:25:36 UTC 2011 i686
[ 36.196] Kernel command line: BOOT_IMAGE=/vmlinuz-3.0.0-13-generic root=UUID=ab657527-36e4-40cf-b5f1-23b56d9a07b1 ro quiet splash vt.handoff=7
[ 36.196] Build Date: 19 October 2011 05:09:41AM
[ 36.196] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[ 36.196] Current version of pixman: 0.22.2
[ 36.196] Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
to make sure that you have the latest version.
[ 36.196] Markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[ 36.197] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Dec 9 14:33:01 2011
[ 36.274] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[ 36.604] (==) No Layout section. Using the first Screen section.
[ 36.604] (==) No screen section available. Using defaults.
[ 36.604] (**) |-->Screen "Default Screen Section" (0)
[ 36.604] (**) | |-->Monitor "<default monitor>"
[ 36.605] (==) No monitor specified for screen "Default Screen Section".
Using a default monitor configuration.
[ 36.605] (==) Automatically adding devices
[ 36.605] (==) Automatically enabling devices
[ 36.605] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[ 36.605] Entry deleted from font path.
[ 36.605] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[ 36.606] Entry deleted from font path.
[ 36.606] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[ 36.606] Entry deleted from font path.
[ 36.606] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[ 36.606] Entry deleted from font path.
[ 36.606] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[ 36.606] Entry deleted from font path.
[ 36.606] (==) FontPath set to:
/usr/share/fonts/X11/misc,
/usr/share/fonts/X11/Type1,
/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
built-ins
[ 36.606] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[ 36.606] (II) The server relies on udev to provide the list of input devices.
If no devices become available, reconfigure udev or disable AutoAddDevices.
[ 36.606] (II) Loader magic: 0x823ada0
[ 36.606] (II) Module ABI versions:
[ 36.606] X.Org ANSI C Emulation: 0.4
[ 36.606] X.Org Video Driver: 10.0
[ 36.606] X.Org XInput driver : 12.3
[ 36.606] X.Org Server Extension : 5.0
[ 36.607] (--) PCI:*(0:0:2:0) 126f:0720:1025:101b rev 193, Mem @ 0x14000000/67108864
[ 36.609] (II) Open ACPI successful (/var/run/acpid.socket)
[ 36.610] (II) LoadModule: "extmod"
[ 36.646] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[ 36.674] (II) Module extmod: vendor="X.Org Foundation"
[ 36.674] compiled for 1.10.4, module version = 1.0.0
[ 36.674] Module class: X.Org Server Extension
[ 36.674] ABI class: X.Org Server Extension, version 5.0
[ 36.674] (II) Loading extension MIT-SCREEN-SAVER
[ 36.674] (II) Loading extension XFree86-VidModeExtension
[ 36.674] (II) Loading extension XFree86-DGA
[ 36.674] (II) Loading extension DPMS
[ 36.674] (II) Loading extension XVideo
[ 36.674] (II) Loading extension XVideo-MotionCompensation
[ 36.674] (II) Loading extension X-Resource
[ 36.674] (II) LoadModule: "dbe"
[ 36.675] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[ 36.717] (II) Module dbe: vendor="X.Org Foundation"
[ 36.717] compiled for 1.10.4, module version = 1.0.0
[ 36.717] Module class: X.Org Server Extension
[ 36.717] ABI class: X.Org Server Extension, version 5.0
[ 36.717] (II) Loading extension DOUBLE-BUFFER
[ 36.717] (II) LoadModule: "glx"
[ 36.718] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[ 36.817] (II) Module glx: vendor="X.Org Foundation"
[ 36.817] compiled for 1.10.4, module version = 1.0.0
[ 36.817] ABI class: X.Org Server Extension, version 5.0
[ 36.817] (==) AIGLX enabled
[ 36.817] (II) Loading extension GLX
[ 36.817] (II) LoadModule: "record"
[ 36.818] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[ 36.860] (II) Module record: vendor="X.Org Foundation"
[ 36.860] compiled for 1.10.4, module version = 1.13.0
[ 36.860] Module class: X.Org Server Extension
[ 36.860] ABI class: X.Org Server Extension, version 5.0
[ 36.861] (II) Loading extension RECORD
[ 36.861] (II) LoadModule: "dri"
[ 36.861] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[ 36.867] (II) Module dri: vendor="X.Org Foundation"
[ 36.867] compiled for 1.10.4, module version = 1.0.0
[ 36.867] ABI class: X.Org Server Extension, version 5.0
[ 36.867] (II) Loading extension XFree86-DRI
[ 36.867] (II) LoadModule: "dri2"
[ 36.868] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[ 36.909] (II) Module dri2: vendor="X.Org Foundation"
[ 36.909] compiled for 1.10.4, module version = 1.2.0
[ 36.909] ABI class: X.Org Server Extension, version 5.0
[ 36.909] (II) Loading extension DRI2
[ 36.909] (==) Matched siliconmotion as autoconfigured driver 0
[ 36.909] (==) Matched vesa as autoconfigured driver 1
[ 36.910] (==) Matched fbdev as autoconfigured driver 2
[ 36.910] (==) Assigned the driver to the xf86ConfigLayout
[ 36.910] (II) LoadModule: "siliconmotion"
[ 36.930] (II) Loading /usr/lib/xorg/modules/drivers/siliconmotion_drv.so
[ 36.957] (II) Module siliconmotion: vendor="X.Org Foundation"
[ 36.957] compiled for 1.10.2.902, module version = 1.7.5
[ 36.957] Module class: X.Org Video Driver
[ 36.957] ABI class: X.Org Video Driver, version 10.0
[ 36.957] (II) LoadModule: "vesa"
[ 36.958] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[ 36.966] (II) Module vesa: vendor="X.Org Foundation"
[ 36.966] compiled for 1.10.2, module version = 2.3.0
[ 36.967] Module class: X.Org Video Driver
[ 36.967] ABI class: X.Org Video Driver, version 10.0
[ 36.967] (II) LoadModule: "fbdev"
[ 36.968] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[ 36.986] (II) Module fbdev: vendor="X.Org Foundation"
[ 36.987] compiled for 1.10.0, module version = 0.4.2
[ 36.987] ABI class: X.Org Video Driver, version 10.0
[ 36.987] (II) SMI: driver (version 1.7.5) for Silicon Motion Lynx chipsets: Lynx,
LynxE, Lynx3D, LynxEM, LynxEM+, Lynx3DM, Cougar3DR, MSOC
[ 36.987] (II) VESA: driver for VESA chipsets: vesa
[ 36.987] (II) FBDEV: driver for framebuffer: fbdev
[ 36.987] (++) using VT number 7
[ 36.987] (WW) Falling back to old probe method for siliconmotion
[ 36.987] (--) Assigning device section with no busID to primary device
[ 36.987] (--) Chipset Lynx3DM found
[ 36.988] (II) Loading /usr/lib/xorg/modules/drivers/siliconmotion_drv.so
[ 36.988] (WW) Falling back to old probe method for vesa
[ 36.988] (WW) Falling back to old probe method for fbdev
[ 36.988] (II) Loading sub module "fbdevhw"
[ 36.988] (II) LoadModule: "fbdevhw"
[ 36.988] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[ 37.020] (II) Module fbdevhw: vendor="X.Org Foundation"
[ 37.020] compiled for 1.10.4, module version = 0.0.2
[ 37.020] ABI class: X.Org Video Driver, version 10.0
[ 37.020] (II) Loading sub module "vgahw"
[ 37.020] (II) LoadModule: "vgahw"
[ 37.021] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[ 37.026] (II) Module vgahw: vendor="X.Org Foundation"
[ 37.026] compiled for 1.10.4, module version = 0.1.0
[ 37.026] ABI class: X.Org Video Driver, version 10.0
[ 37.026] (II) SMI(0): Creating default Display subsection in Screen section
"Default Screen Section" for depth/fbbpp 24/32
[ 37.026] (==) SMI(0): Depth 24, (--) framebuffer bpp 32
[ 37.026] (==) SMI(0): RGB weight 888
[ 37.026] (==) SMI(0): Default visual is TrueColor
[ 37.026] (==) SMI(0): PCI Burst enabled
[ 37.026] (==) SMI(0): PCI Retry enabled
[ 37.026] (==) SMI(0): Using Hardware Cursor
[ 37.026] (--) SMI(0): Chipset: "Lynx3DM"
[ 37.026] (==) SMI(0): Dual head disabled
[ 37.026] (==) SMI(0): Using XAA acceleration architecture
[ 37.027] (--) SMI(0): videoram: 8192kB
[ 37.030] (II) SMI(0): Cursor Offset: 007FFC00
[ 37.030] (II) SMI(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[ 37.030] (II) SMI(0): Reserved: 007FF800
[ 37.030] (II) SMI(0): TFT Panel Size = 1024x768
[ 37.030] (II) Loading sub module "i2c"
[ 37.030] (II) LoadModule: "i2c"
[ 37.030] (II) Module "i2c" already built-in
[ 37.030] (II) SMI(0): I2C bus "I2C bus" initialized.
[ 37.030] (II) Loading sub module "ddc"
[ 37.030] (II) LoadModule: "ddc"
[ 37.030] (II) Module "ddc" already built-in
[ 37.030] (==) SMI(0): Using gamma correction (1.0, 1.0, 1.0)
[ 37.030] (II) SMI(0): MCLK = 100.227
[ 37.030] (II) SMI(0): Output LVDS has no monitor section
[ 37.031] (II) SMI(0): Printing probed modes for output LVDS
[ 37.031] (II) SMI(0): Modeline "1024x768"x59.9 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync (47.8 kHz)
[ 37.031] (II) SMI(0): Output LVDS connected
[ 37.031] (II) SMI(0): Using fuzzy aspect match for initial modes
[ 37.031] (II) SMI(0): Output LVDS using initial mode 1024x768
[ 37.031] (II) SMI(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[ 37.034] (==) SMI(0): DPI set to (96, 96)
[ 37.034] (II) Loading sub module "fb"
[ 37.034] (II) LoadModule: "fb"
[ 37.035] (II) Loading /usr/lib/xorg/modules/libfb.so
[ 37.073] (II) Module fb: vendor="X.Org Foundation"
[ 37.074] compiled for 1.10.4, module version = 1.0.0
[ 37.074] ABI class: X.Org ANSI C Emulation, version 0.4
[ 37.074] (II) Loading sub module "xaa"
[ 37.074] (II) LoadModule: "xaa"
[ 37.075] (II) Loading /usr/lib/xorg/modules/libxaa.so
[ 37.146] (II) Module xaa: vendor="X.Org Foundation"
[ 37.147] compiled for 1.10.4, module version = 1.2.1
[ 37.147] ABI class: X.Org Video Driver, version 10.0
[ 37.147] (II) Loading sub module "ramdac"
[ 37.147] (II) LoadModule: "ramdac"
[ 37.147] (II) Module "ramdac" already built-in
[ 37.147] (II) UnloadModule: "vesa"
[ 37.147] (II) Unloading vesa
[ 37.147] (II) UnloadModule: "fbdev"
[ 37.147] (II) Unloading fbdev
[ 37.147] (II) UnloadModule: "fbdevhw"
[ 37.147] (II) Unloading fbdevhw
[ 37.147] (--) Depth 24 pixmap format is 32 bpp
[ 37.150] (II) SMI(0): Cursor Offset: 007FFC00
[ 37.150] (II) SMI(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[ 37.150] (II) SMI(0): Reserved: 007FF800
[ 37.821] (II) SMI(0): FrameBuffer Box: 0,0 - 1024,2047
[ 37.822] (II) SMI(0): Using XFree86 Acceleration Architecture (XAA)
[ 37.822] Screen to screen bit blits
[ 37.822] Solid filled rectangles
[ 37.822] 8x8 mono pattern filled rectangles
[ 37.822] 8x8 color pattern filled rectangles
[ 37.822] CPU to Screen color expansion
[ 37.822] Solid Horizontal and Vertical Lines
[ 37.822] Setting up tile and stipple cache:
[ 37.822] 28 128x128 slots
[ 37.822] 7 256x256 slots
[ 37.822] 32 8x8 color pattern slots
[ 37.846] (==) SMI(0): DPMS enabled
[ 37.846] (II) SMI(0): I2C device "I2C bus:SAA 7111A" registered at address 0x48.
[ 37.846] (II) SMI(0): I2C device "I2C bus:SAA 7111A" removed.
[ 37.847] (II) SMI(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[ 37.847] (--) RandR disabled
[ 37.847] (II) Initializing built-in extension Generic Event Extension
[ 37.847] (II) Initializing built-in extension SHAPE
[ 37.847] (II) Initializing built-in extension MIT-SHM
[ 37.847] (II) Initializing built-in extension XInputExtension
[ 37.847] (II) Initializing built-in extension XTEST
[ 37.847] (II) Initializing built-in extension BIG-REQUESTS
[ 37.847] (II) Initializing built-in extension SYNC
[ 37.847] (II) Initializing built-in extension XKEYBOARD
[ 37.847] (II) Initializing built-in extension XC-MISC
[ 37.847] (II) Initializing built-in extension SECURITY
[ 37.847] (II) Initializing built-in extension XINERAMA
[ 37.847] (II) Initializing built-in extension XFIXES
[ 37.847] (II) Initializing built-in extension RENDER
[ 37.847] (II) Initializing built-in extension RANDR
[ 37.847] (II) Initializing built-in extension COMPOSITE
[ 37.847] (II) Initializing built-in extension DAMAGE
[ 37.847] (II) Initializing built-in extension GESTURE
[ 37.879] (II) AIGLX: Screen 0 is not DRI2 capable
[ 37.879] (II) AIGLX: Screen 0 is not DRI capable
[ 37.879] (II) AIGLX: Trying DRI driver /usr/lib/i386-linux-gnu/dri/swrast_dri.so
[ 37.958] (II) AIGLX: Loaded and initialized swrast
[ 37.958] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[ 37.960] (II) SMI(0): Setting screen physical size to 270 x 203
[ 38.326] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[ 38.426] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[ 38.426] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[ 38.426] (II) LoadModule: "evdev"
[ 38.427] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 38.515] (II) Module evdev: vendor="X.Org Foundation"
[ 38.515] compiled for 1.10.2, module version = 2.6.0
[ 38.515] Module class: X.Org XInput Driver
[ 38.515] ABI class: X.Org XInput driver, version 12.3
[ 38.515] (II) Using input driver 'evdev' for 'Power Button'
[ 38.515] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 38.515] (**) Power Button: always reports core events
[ 38.515] (**) Power Button: Device: "/dev/input/event2"
[ 38.516] (--) Power Button: Found keys
[ 38.516] (II) Power Button: Configuring as keyboard
[ 38.516] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[ 38.516] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[ 38.516] (**) Option "xkb_rules" "evdev"
[ 38.516] (**) Option "xkb_model" "pc105"
[ 38.516] (**) Option "xkb_layout" "us"
[ 38.524] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[ 38.524] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[ 38.524] (II) Using input driver 'evdev' for 'Video Bus'
[ 38.524] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 38.524] (**) Video Bus: always reports core events
[ 38.524] (**) Video Bus: Device: "/dev/input/event5"
[ 38.524] (--) Video Bus: Found keys
[ 38.524] (II) Video Bus: Configuring as keyboard
[ 38.524] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input5/event5"
[ 38.524] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[ 38.524] (**) Option "xkb_rules" "evdev"
[ 38.524] (**) Option "xkb_model" "pc105"
[ 38.525] (**) Option "xkb_layout" "us"
[ 38.564] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[ 38.565] (II) No input driver/identifier specified (ignoring)
[ 38.566] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[ 38.566] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[ 38.566] (II) Using input driver 'evdev' for 'Sleep Button'
[ 38.566] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 38.566] (**) Sleep Button: always reports core events
[ 38.566] (**) Sleep Button: Device: "/dev/input/event0"
[ 38.566] (--) Sleep Button: Found keys
[ 38.566] (II) Sleep Button: Configuring as keyboard
[ 38.567] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0/event0"
[ 38.567] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[ 38.567] (**) Option "xkb_rules" "evdev"
[ 38.567] (**) Option "xkb_model" "pc105"
[ 38.567] (**) Option "xkb_layout" "us"
[ 38.598] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[ 38.598] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[ 38.598] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[ 38.598] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 38.598] (**) AT Translated Set 2 keyboard: always reports core events
[ 38.598] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[ 38.599] (--) AT Translated Set 2 keyboard: Found keys
[ 38.599] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[ 38.599] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[ 38.599] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[ 38.599] (**) Option "xkb_rules" "evdev"
[ 38.599] (**) Option "xkb_model" "pc105"
[ 38.599] (**) Option "xkb_layout" "us"
[ 38.611] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event4)
[ 38.611] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[ 38.611] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[ 38.611] (II) LoadModule: "synaptics"
[ 38.619] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[ 38.620] (II) Module synaptics: vendor="X.Org Foundation"
[ 38.620] compiled for 1.10.4, module version = 1.4.1
[ 38.620] Module class: X.Org XInput Driver
[ 38.620] ABI class: X.Org XInput driver, version 12.3
[ 38.620] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[ 38.620] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[ 38.620] (**) SynPS/2 Synaptics TouchPad: always reports core events
[ 38.620] (**) Option "Device" "/dev/input/event4"
[ 38.621] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[ 38.621] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[ 38.621] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[ 38.621] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[ 38.621] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple scroll-buttons
[ 38.621] (--) SynPS/2 Synaptics TouchPad: touchpad found
[ 38.621] (**) SynPS/2 Synaptics TouchPad: always reports core events
[ 38.621] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input4/event4"
[ 38.621] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[ 38.621] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[ 38.621] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[ 38.621] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[ 38.622] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[ 38.622] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[ 38.622] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[ 38.622] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[ 38.622] (II) SynPS/2 Synaptics TouchPad: failed to open grail, no gesture support
[ 38.622] (--) SynPS/2 Synaptics TouchPad: touchpad found
[ 38.623] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[ 38.623] (II) No input driver/identifier specified (ignoring)
[ 38.635] (II) config/udev: Adding input device Serial Wacom Tablet (/dev/ttyS4)
[ 38.636] (**) Serial Wacom Tablet: Applying InputClass "Wacom serial class"
[ 38.636] (II) LoadModule: "wacom"
[ 38.638] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[ 38.692] (II) Module wacom: vendor="X.Org Foundation"
[ 38.692] compiled for 1.10.4, module version = 0.11.0
[ 38.692] Module class: X.Org XInput Driver
[ 38.692] ABI class: X.Org XInput driver, version 12.3
[ 38.692] (II) Using input driver 'wacom' for 'Serial Wacom Tablet'
[ 38.692] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[ 38.692] (**) Serial Wacom Tablet: always reports core events
[ 38.692] (**) Option "Device" "/dev/ttyS4"
[ 38.693] (**) Option "StopBits" "1"
[ 38.693] (**) Option "DataBits" "8"
[ 38.693] (**) Option "Parity" "None"
[ 38.693] (**) Option "Vmin" "1"
[ 38.693] (**) Option "Vtime" "10"
[ 38.693] (**) Option "FlowControl" "Xoff"
[ 38.694] (II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
[ 38.694] (II) Serial Wacom Tablet: other types will be automatically added.
[ 38.967] (II) Serial Wacom Tablet stylus: serial tablet id 0x90.
[ 38.967] (--) Serial Wacom Tablet stylus: using pressure threshold of 27 for button 1
[ 38.967] (--) Serial Wacom Tablet stylus: Wacom General ISDV4 tablet maxX=21240 maxY=15980 maxZ=127 resX=100000 resY=100000 tilt=disabled
[ 38.967] (II) Serial Wacom Tablet stylus: hotplugging dependent devices.
[ 38.967] (II) Serial Wacom Tablet stylus: hotplugging completed.
[ 38.967] (**) Option "config_info" "udev:/sys/devices/pnp0/00:08/tty/ttyS4"
[ 38.967] (II) XINPUT: Adding extended input device "Serial Wacom Tablet stylus" (type: STYLUS)
[ 38.969] (**) Serial Wacom Tablet stylus: (accel) keeping acceleration scheme 1
[ 38.969] (**) Serial Wacom Tablet stylus: (accel) acceleration profile 0
[ 38.969] (**) Serial Wacom Tablet stylus: (accel) acceleration factor: 2.000
[ 38.969] (**) Serial Wacom Tablet stylus: (accel) acceleration threshold: 4
[ 38.969] (**) Option "BaudRate" "19200"
[ 39.020] (**) Serial Wacom Tablet eraser: Applying InputClass "Wacom serial class"
[ 39.020] (II) Using input driver 'wacom' for 'Serial Wacom Tablet eraser'
[ 39.020] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[ 39.020] (**) Serial Wacom Tablet eraser: always reports core events
[ 39.020] (**) Option "Device" "/dev/ttyS4"
[ 39.020] (**) Option "BaudRate" "19200"
[ 39.021] (**) Option "StopBits" "1"
[ 39.021] (**) Option "DataBits" "8"
[ 39.021] (**) Option "Parity" "None"
[ 39.021] (**) Option "Vmin" "1"
[ 39.021] (**) Option "Vtime" "10"
[ 39.021] (**) Option "FlowControl" "Xoff"
[ 39.021] (--) Serial Wacom Tablet eraser: Wacom General ISDV4 tablet maxX=21240 maxY=15980 maxZ=127 resX=100000 resY=100000 tilt=disabled
[ 39.021] (**) Option "config_info" "udev:/sys/devices/pnp0/00:08/tty/ttyS4"
[ 39.021] (II) XINPUT: Adding extended input device "Serial Wacom Tablet eraser" (type: ERASER)
[ 39.022] (**) Serial Wacom Tablet eraser: (accel) keeping acceleration scheme 1
[ 39.022] (**) Serial Wacom Tablet eraser: (accel) acceleration profile 0
[ 39.022] (**) Serial Wacom Tablet eraser: (accel) acceleration factor: 2.000
[ 39.022] (**) Serial Wacom Tablet eraser: (accel) acceleration threshold: 4

---

### Post by Favux on 2011-12-09
Well the Xorg.0.log seems to indicate your serial Wacom digitizer is initializing correctly.  Some serial tablets with touch had this problem with Xournal so we just came up with a touch toggle script to turn touch off and fixed the problem.  Not your case since no touch.

The problem is likely with Oneiric's (and probably Natty's) X stack.  Some folks have reported problems in other app.s like Xournal but it is mainly Gimp where the problem is seen because of Gimp's history buffer.  And the bug(s) are presumably due to Ubuntu's custom multi-touch additions.

Are you seeing horizontal lines going to the left?  *xinput -test* seems to show the x coordinate disappearing periodically.  I think it would be useful if you posted the test result on this Launchpad bug report:  [https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154)

You could see if there is something new on the Xorg edgers PPA.  The link I provide to the Qt bug in Krita etc. links to it and there was an attempt to fix the valuator problem.  But most likely you would have to use either Maverick or Lucid.  Possibly Natty might be OK.  Some people found going to 2D and/or removing desktop effects fixed it.  Maverick's my current favorite release but only has 5 months of life left.  Or another distro like Fedora since this is a Ubuntu specific problem.  16 just came out.

FYI Peter Hutterer has spent the last month or two working on multi-touch for the X server.  Since he is also the lead developer on xf86-input-wacom hopefully it won't have the Ubuntu bugs.  Don't know if that means it will be available in time for Precise or whether Ubuntu will drop their custom stuff and go back to the community version.  One can hope.

---

### Post by grunzasr on 2011-12-09
The problem is also in Natty.  This random line problem was the reason I upgraded to Oneiric (hoping it was fixed and not wanting to file problem reports on out of date code).  I'll look into the link you sent.  I would prefer to not leave (X)ubuntu since I was looking for a Linux distro that would work with older, less capable machines.  My experience with CentOS has been that older distro's don't have the necessary libraries, headers, etc to do development work so I'm reluctant to move back to pre-Natty.
 
As I said I haven't looked at the link you sent but are there any work arounds?

---

### Post by Favux on 2011-12-09
For Gimp deactivating the history buffer.  That was supplied by a Gimp developer Alexia.

Otherwise it would be to try an updated X server that hopefully has a fix.  There was some hope there was an update in the wings and that's why Ubuntu labeled priority low.  That's why I was thinking of Xorg edgers PPA and the Qt "fix".  Although that one was for Natty there may be something for Oneiric by now.

---

### Post by grunzasr on 2011-12-28
I tried the Xorg edgers PPA but I still get random lines.  It looks like Xubuntu is unusable on TabletPC for now (at least for slate-mode).  I'll give Fedora a try and see if it's any better.

---

### Post by Favux on 2011-12-28
Hi grunzasr,

Well for Gimp Aapo Rantalainen's PPA works fine.  It is the Oneiric Gimp with Alexia's history buffer patch applied and is working fine for me and others:  [https://launchpad.net/~aapo-rantalainen/+archive/gimp26-noghostline](https://launchpad.net/~aapo-rantalainen/+archive/gimp26-noghostline)  Haven't seen anything for Xournal though.  Apparently not many reporting a problem with it?

---

