---
title: "SiliconMotion video driver - All attempts have failed - Walkabout XRT..."
date: 2013-03-18
forum: Hardware
---

### Post by 1branchonthevine on 2013-03-18
On older version of Ubuntu, 9.04 I think, the following instructions works like a charm:
[http://ubuntuforums.org/showthread.php?t=1162348](http://ubuntuforums.org/showthread.php?t=1162348)

After visiting numerous forums, I have determined no solutions seem to work.
Currently I think the problem resides in detecting the LCD panel, because most xorg.conf issues seem to around screen detection failure.

Any suggestions?

```
"$ X -configure
"no screens found"
```

Terminal commands that do nothing
--------------------------------

```
Tried:  sudo dpkg-reconfigure xserver-xorg 
Returned: nothing, returns to terminal
Tried: sudo ddcprobe | grep range
Returned:Nothing
Tried: jockey-text -l
Returned:nothing
```

Xorg.conf
---------------------------------
/usr/share/X11/xorg.conf.d/10-monitor.conf
```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen1"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection


Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection


Section "Module"
    Load  "glx"
EndSection


Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection


Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection


Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
    Horizsync    31.5-48.0
    Vertrefresh    56.0 - 65.0
#  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
#  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
#  modeline  "800x600"     38.25 800 832 912 1024 600 603 607 624 -hsync +vsync
  modeline  "800x600@60"  38.22  800 832 912 1024  600 601 604 622  -HSync +Vsync
#  modeline  "800x600@59.90"  38.09  800 832 912 1024  600 601 604 621  -HSync +Vsync
#  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
#    Gamma    1.0
EndSection


Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection


Section "Monitor"
    Identifier   "Monitor2"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection


Section "Device"
    Identifier    "Card0"
    Boardname    "Silicon Motion LynxEM+ (generic)"
    Busid        "PCI:2:5:0"
    Driver        "siliconmotion"
    Screen        0  "Screen0" 0 0
    Vendorname    "Silicon Motion"
    #Option "fifo_aggressive"
    #Option "fifo_moderate"
    #Option "fifo_conservative"
    #Option "pci_burst" "on"
    #Option "pci_retry" "on"
    Option "AccelMethod" "EXA"
        #Use the BIOS to set the modes. This is  used  for  custom  panel
        #timings.  Default: off for SM72x and SM5xx, otherwise on.
    #Option "UseBIOS" "boolean"
        #Enable dualhead mode.  Currently not all chips are supported and
        #hardware video overlay (XV) support may have  some  limitations.
        #Default: off.
    #Option "Dualhead" "on"
        #Override LCD panel dimension autodetection.
    #Option "PanelSize" "widthxheight"
        #Disable acceleration.  Very useful for determining if the driver
        #has  problems  with  drawing and acceleration routines.  This is
        #the first option to try if your server runs but you see  graphic
        #corruption on the screen.  Using it decreases performance, as it
        #uses software emulation for drawing operations the video  driver
        #can accelerate with hardware.  Default: acceleration is enabled.
    #Option "NoAccel"
EndSection


#Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "kmsdev"                 # <str>
        #Option     "ShadowFB"               # [<bool>]
    #Identifier  "Card0"
    #Driver      "modesetting"
    #BusID       "PCI:2:5:0"
#EndSection


Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "Rotate"                 # <str>
        #Option     "fbdev"                  # <str>
        #Option     "debug"                  # [<bool>]
    Identifier  "Card1"
    Driver      "fbdev"
    BusID       "PCI:2:5:0"
EndSection


Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "DefaultRefresh"         # [<bool>]
        #Option     "ModeSetClearScreen"     # [<bool>]
    Identifier  "Card2"
    Driver      "vesa"
    BusID       "PCI:2:5:0"
EndSection


Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    Defaultdepth    24
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth    24
        Virtual    800    600
        Modes    "800x600@60"
    EndSubSection
EndSection


Section "Screen"
    Identifier "Screen1"
    Device     "Card1"
    Monitor    "Monitor1"
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


Section "Screen"
    Identifier "Screen2"
    Device     "Card2"
    Monitor    "Monitor2"
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




Logs:
---------------------------------
no xorg.conf (deleted)
/var/log/Xorg.0.log
```
[    36.978] X.Org X Server 1.13.0
Release Date: 2012-09-05
[    36.978] X Protocol Version 11, Revision 0
[    36.978] Build Operating System: Linux 3.2.0-26-generic i686 Ubuntu
[    36.979] Current Operating System: Linux ychurch 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:32:08 UTC 2012 i686
[    36.979] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-17-generic root=UUID=a86efa56-6dea-4d00-9da0-8b0bc5b60ac8 ro quiet splash vt.handoff=7
[    36.979] Build Date: 27 November 2012  07:44:37AM
[    36.979] xorg-server 2:1.13.0-0ubuntu6.1 (For technical support please see http://www.ubuntu.com/support) 
[    36.979] Current version of pixman: 0.26.0
[    36.979]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    36.979] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    36.979] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Mar 18 13:11:56 2013
[    36.992] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    36.994] (==) No Layout section.  Using the first Screen section.
[    36.994] (==) No screen section available. Using defaults.
[    36.994] (**) |-->Screen "Default Screen Section" (0)
[    36.994] (**) |   |-->Monitor "<default monitor>"
[    36.994] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    36.995] (==) Automatically adding devices
[    36.995] (==) Automatically enabling devices
[    36.995] (==) Automatically adding GPU devices
[    36.995] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    36.995]     Entry deleted from font path.
[    36.995] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    36.995]     Entry deleted from font path.
[    36.995] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    36.995]     Entry deleted from font path.
[    36.995] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    36.995]     Entry deleted from font path.
[    36.995] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    36.995]     Entry deleted from font path.
[    36.995] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    36.995]     Entry deleted from font path.
[    36.995] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    36.995] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    36.995] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    36.995] (II) Loader magic: 0xb77e2640
[    36.995] (II) Module ABI versions:
[    36.995]     X.Org ANSI C Emulation: 0.4
[    36.995]     X.Org Video Driver: 13.0
[    36.996]     X.Org XInput driver : 18.0
[    36.997]     X.Org Server Extension : 7.0
[    37.004] (--) PCI:*(0:2:5:0) 126f:0712:126f:0712 rev 160, Mem @ 0xd1000000/16777216
[    37.005] (II) Open ACPI successful (/var/run/acpid.socket)
[    37.005] Initializing built-in extension Generic Event Extension
[    37.005] Initializing built-in extension SHAPE
[    37.005] Initializing built-in extension MIT-SHM
[    37.005] Initializing built-in extension XInputExtension
[    37.005] Initializing built-in extension XTEST
[    37.005] Initializing built-in extension BIG-REQUESTS
[    37.005] Initializing built-in extension SYNC
[    37.005] Initializing built-in extension XKEYBOARD
[    37.005] Initializing built-in extension XC-MISC
[    37.005] Initializing built-in extension SECURITY
[    37.005] Initializing built-in extension XINERAMA
[    37.005] Initializing built-in extension XFIXES
[    37.005] Initializing built-in extension RENDER
[    37.005] Initializing built-in extension RANDR
[    37.006] Initializing built-in extension COMPOSITE
[    37.006] Initializing built-in extension DAMAGE
[    37.006] Initializing built-in extension MIT-SCREEN-SAVER
[    37.006] Initializing built-in extension DOUBLE-BUFFER
[    37.006] Initializing built-in extension RECORD
[    37.006] Initializing built-in extension DPMS
[    37.006] Initializing built-in extension X-Resource
[    37.006] Initializing built-in extension XVideo
[    37.006] Initializing built-in extension XVideo-MotionCompensation
[    37.006] Initializing built-in extension XFree86-VidModeExtension
[    37.006] Initializing built-in extension XFree86-DGA
[    37.006] Initializing built-in extension XFree86-DRI
[    37.006] Initializing built-in extension DRI2
[    37.006] (II) LoadModule: "glx"
[    37.040] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    37.040] (II) Module glx: vendor="X.Org Foundation"
[    37.040]     compiled for 1.13.0, module version = 1.0.0
[    37.041]     ABI class: X.Org Server Extension, version 7.0
[    37.041] (==) AIGLX enabled
[    37.041] Loading extension GLX
[    37.041] (==) Matched siliconmotion as autoconfigured driver 0
[    37.041] (==) Matched vesa as autoconfigured driver 1
[    37.041] (==) Matched modesetting as autoconfigured driver 2
[    37.041] (==) Matched fbdev as autoconfigured driver 3
[    37.041] (==) Assigned the driver to the xf86ConfigLayout
[    37.041] (II) LoadModule: "siliconmotion"
[    37.042] (II) Loading /usr/lib/xorg/modules/drivers/siliconmotion_drv.so
[    37.042] (II) Module siliconmotion: vendor="X.Org Foundation"
[    37.042]     compiled for 1.12.99.902, module version = 1.7.7
[    37.042]     Module class: X.Org Video Driver
[    37.042]     ABI class: X.Org Video Driver, version 13.0
[    37.042] (II) LoadModule: "vesa"
[    37.043] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    37.043] (II) Module vesa: vendor="X.Org Foundation"
[    37.043]     compiled for 1.12.99.902, module version = 2.3.2
[    37.043]     Module class: X.Org Video Driver
[    37.043]     ABI class: X.Org Video Driver, version 13.0
[    37.043] (II) LoadModule: "modesetting"
[    37.048] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    37.048] (II) Module modesetting: vendor="X.Org Foundation"
[    37.048]     compiled for 1.13.0, module version = 0.5.0
[    37.049]     Module class: X.Org Video Driver
[    37.049]     ABI class: X.Org Video Driver, version 13.0
[    37.049] (II) LoadModule: "fbdev"
[    37.049] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    37.050] (II) Module fbdev: vendor="X.Org Foundation"
[    37.050]     compiled for 1.12.99.902, module version = 0.4.3
[    37.050]     Module class: X.Org Video Driver
[    37.050]     ABI class: X.Org Video Driver, version 13.0
[    37.050] (II) SMI: driver (version 1.7.7) for Silicon Motion Lynx chipsets: Lynx,
    LynxE, Lynx3D, LynxEM, LynxEM+, Lynx3DM, Cougar3DR, MSOC
[    37.050] (II) VESA: driver for VESA chipsets: vesa
[    37.050] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    37.050] (II) FBDEV: driver for framebuffer: fbdev
[    37.050] (++) using VT number 8


[    37.134] (WW) Falling back to old probe method for siliconmotion
[    37.134] (--) Assigning device section with no busID to primary device
[    37.135] (--) Chipset LynxEM+ found
[    37.135] (WW) Falling back to old probe method for vesa
[    37.135] (WW) Falling back to old probe method for modesetting
[    37.135] (EE) open /dev/dri/card0: No such file or directory
[    37.135] (WW) Falling back to old probe method for fbdev
[    37.135] (II) Loading sub module "fbdevhw"
[    37.135] (II) LoadModule: "fbdevhw"
[    37.136] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    37.136] (II) Module fbdevhw: vendor="X.Org Foundation"
[    37.136]     compiled for 1.13.0, module version = 0.0.2
[    37.136]     ABI class: X.Org Video Driver, version 13.0
[    37.137] (II) Loading sub module "vgahw"
[    37.137] (II) LoadModule: "vgahw"
[    37.137] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    37.138] (II) Module vgahw: vendor="X.Org Foundation"
[    37.138]     compiled for 1.13.0, module version = 0.1.0
[    37.138]     ABI class: X.Org Video Driver, version 13.0
[    37.138] (II) SMI(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    37.138] (==) SMI(0): Depth 24, (--) framebuffer bpp 32
[    37.138] (==) SMI(0): RGB weight 888
[    37.138] (==) SMI(0): Default visual is TrueColor
[    37.138] (==) SMI(0): PCI Burst enabled
[    37.138] (==) SMI(0): PCI Retry enabled
[    37.138] (==) SMI(0): Using Hardware Cursor
[    37.138] (II) Loading sub module "int10"
[    37.138] (II) LoadModule: "int10"
[    37.139] (II) Loading /usr/lib/xorg/modules/libint10.so
[    37.143] (II) Module int10: vendor="X.Org Foundation"
[    37.143]     compiled for 1.13.0, module version = 1.0.0
[    37.143]     ABI class: X.Org Video Driver, version 13.0
[    37.147] (II) SMI(0): Primary V_BIOS segment is: 0xc000
[    37.147] (II) Loading sub module "vbe"
[    37.147] (II) LoadModule: "vbe"
[    37.155] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    37.155] (II) Module vbe: vendor="X.Org Foundation"
[    37.155]     compiled for 1.13.0, module version = 1.1.0
[    37.155]     ABI class: X.Org Video Driver, version 13.0
[    38.178] (II) SMI(0): VESA BIOS not detected
[    38.178] (WW) SMI(0): VBE initialization failed: falling back to UseBIOS disabled.
[    38.178] (--) SMI(0): Chipset: "LynxEM+"
[    38.178] (==) SMI(0): Dual head disabled
[    38.178] (==) SMI(0): Using XAA acceleration architecture
[    38.179] (--) SMI(0): videoram: 4096kB
[    38.180] (II) SMI(0): Cursor Offset: 003FFC00
[    38.180] (II) SMI(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0
[    38.180] (II) SMI(0): Reserved: 003FF800
[    38.180] (II) SMI(0): TFT Panel Size = 800x600
[    38.180] (II) Loading sub module "i2c"
[    38.180] (II) LoadModule: "i2c"
[    38.181] (II) Module "i2c" already built-in
[    38.181] (II) SMI(0): I2C bus "I2C bus" initialized.
[    38.181] (II) Loading sub module "ddc"
[    38.181] (II) LoadModule: "ddc"
[    38.181] (II) Module "ddc" already built-in
[    38.181] (==) SMI(0): Using gamma correction (1.0, 1.0, 1.0)
[    38.181] (II) SMI(0): MCLK = 157.000
[    38.181] (II) SMI(0): Output LVDS has no monitor section
[    38.181] (II) SMI(0): Printing probed modes for output LVDS
[    38.181] (II) SMI(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    38.181] (II) SMI(0): Output LVDS connected
[    38.181] (II) SMI(0): Using exact sizes for initial modes
[    38.181] (II) SMI(0): Output LVDS using initial mode 800x600
[    38.181] (II) SMI(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    38.182] (==) SMI(0): DPI set to (96, 96)
[    38.182] (II) Loading sub module "fb"
[    38.182] (II) LoadModule: "fb"
[    38.183] (II) Loading /usr/lib/xorg/modules/libfb.so
[    38.183] (II) Module fb: vendor="X.Org Foundation"
[    38.183]     compiled for 1.13.0, module version = 1.0.0
[    38.183]     ABI class: X.Org ANSI C Emulation, version 0.4
[    38.183] (II) Loading sub module "xaa"
[    38.183] (II) LoadModule: "xaa"
[    38.185] (WW) Warning, couldn't open module xaa
[    38.185] (II) UnloadModule: "xaa"
[    38.185] (II) Unloading xaa
[    38.185] (EE) SMI: Failed to load module "xaa" (module does not exist, 0)
[    38.185] (WW) SMI(0): No acceleration
[    38.185] (II) Loading sub module "ramdac"
[    38.185] (II) LoadModule: "ramdac"
[    38.185] (II) Module "ramdac" already built-in
[    38.185] (II) UnloadModule: "vesa"
[    38.185] (II) Unloading vesa
[    38.186] (II) UnloadModule: "modesetting"
[    38.186] (II) Unloading modesetting
[    38.186] (II) UnloadModule: "fbdev"
[    38.186] (II) Unloading fbdev
[    38.186] (II) UnloadSubModule: "fbdevhw"
[    38.186] (II) Unloading fbdevhw
[    38.186] (--) Depth 24 pixmap format is 32 bpp
[    38.187] (II) SMI(0): Cursor Offset: 003FFC00
[    38.187] (II) SMI(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0
[    38.187] (II) SMI(0): Reserved: 003FF800
[    38.577] (II) SMI(0): FrameBuffer Box: 0,0 - 800,1310
[    38.611] (==) SMI(0): DPMS enabled
[    38.611] (II) SMI(0): I2C device "I2C bus:SAA 7111A" registered at address 0x48.
[    38.611] (II) SMI(0): I2C device "I2C bus:SAA 7111A" removed.
[    38.611] (II) SMI(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    38.612] (--) RandR disabled
[    38.646] (II) AIGLX: Screen 0 is not DRI2 capable
[    38.646] (II) AIGLX: Screen 0 is not DRI capable
[    38.712] (II) AIGLX: Loaded and initialized swrast
[    38.712] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    38.713] (II) SMI(0): Setting screen physical size to 211 x 158
[    38.851] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    38.863] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    38.863] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    38.863] (II) LoadModule: "evdev"
[    38.864] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    38.865] (II) Module evdev: vendor="X.Org Foundation"
[    38.865]     compiled for 1.13.0, module version = 2.7.3
[    38.865]     Module class: X.Org XInput Driver
[    38.865]     ABI class: X.Org XInput driver, version 18.0
[    38.865] (II) Using input driver 'evdev' for 'Power Button'
[    38.865] (**) Power Button: always reports core events
[    38.865] (**) evdev: Power Button: Device: "/dev/input/event0"
[    38.865] (--) evdev: Power Button: Vendor 0 Product 0x1
[    38.865] (--) evdev: Power Button: Found keys
[    38.866] (II) evdev: Power Button: Configuring as keyboard
[    38.866] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input0/event0"
[    38.866] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    38.866] (**) Option "xkb_rules" "evdev"
[    38.866] (**) Option "xkb_model" "pc105"
[    38.866] (**) Option "xkb_layout" "us"
[    38.868] (II) config/udev: Adding input device Multi-Input Device (/dev/input/event2)
[    38.868] (**) Multi-Input Device: Applying InputClass "evdev keyboard catchall"
[    38.868] (II) Using input driver 'evdev' for 'Multi-Input Device'
[    38.869] (**) Multi-Input Device: always reports core events
[    38.869] (**) evdev: Multi-Input Device: Device: "/dev/input/event2"
[    38.869] (--) evdev: Multi-Input Device: Vendor 0x518 Product 0x8
[    38.869] (--) evdev: Multi-Input Device: Found keys
[    38.869] (II) evdev: Multi-Input Device: Configuring as keyboard
[    38.869] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input2/event2"
[    38.869] (II) XINPUT: Adding extended input device "Multi-Input Device" (type: KEYBOARD, id 7)
[    38.869] (**) Option "xkb_rules" "evdev"
[    38.869] (**) Option "xkb_model" "pc105"
[    38.869] (**) Option "xkb_layout" "us"
[    38.871] (II) config/udev: Adding input device Multi-Input Device (/dev/input/event3)
[    38.871] (**) Multi-Input Device: Applying InputClass "evdev pointer catchall"
[    38.871] (**) Multi-Input Device: Applying InputClass "evdev keyboard catchall"
[    38.871] (II) Using input driver 'evdev' for 'Multi-Input Device'
[    38.872] (**) Multi-Input Device: always reports core events
[    38.872] (**) evdev: Multi-Input Device: Device: "/dev/input/event3"
[    38.872] (--) evdev: Multi-Input Device: Vendor 0x518 Product 0x8
[    38.872] (--) evdev: Multi-Input Device: Found 3 mouse buttons
[    38.872] (--) evdev: Multi-Input Device: Found scroll wheel(s)
[    38.872] (--) evdev: Multi-Input Device: Found relative axes
[    38.872] (--) evdev: Multi-Input Device: Found x and y relative axes
[    38.872] (--) evdev: Multi-Input Device: Found absolute axes
[    38.872] (II) evdev: Multi-Input Device: Forcing absolute x/y axes to exist.
[    38.872] (--) evdev: Multi-Input Device: Found keys
[    38.872] (II) evdev: Multi-Input Device: Configuring as mouse
[    38.872] (II) evdev: Multi-Input Device: Configuring as keyboard
[    38.872] (II) evdev: Multi-Input Device: Adding scrollwheel support
[    38.872] (**) evdev: Multi-Input Device: YAxisMapping: buttons 4 and 5
[    38.872] (**) evdev: Multi-Input Device: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    38.872] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.1/input/input3/event3"
[    38.872] (II) XINPUT: Adding extended input device "Multi-Input Device" (type: KEYBOARD, id 8)
[    38.873] (**) Option "xkb_rules" "evdev"
[    38.873] (**) Option "xkb_model" "pc105"
[    38.873] (**) Option "xkb_layout" "us"
[    38.874] (II) evdev: Multi-Input Device: initialized for relative axes.
[    38.874] (WW) evdev: Multi-Input Device: ignoring absolute axes.
[    38.874] (**) Multi-Input Device: (accel) keeping acceleration scheme 1
[    38.874] (**) Multi-Input Device: (accel) acceleration profile 0
[    38.874] (**) Multi-Input Device: (accel) acceleration factor: 2.000
[    38.874] (**) Multi-Input Device: (accel) acceleration threshold: 4
[    38.875] (II) config/udev: Adding input device Multi-Input Device (/dev/input/mouse0)
[    38.875] (II) No input driver specified, ignoring this device.
[    38.876] (II) This device may have been added with another device file.
[    38.877] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event1)
[    38.877] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    38.877] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    38.877] (**) AT Translated Set 2 keyboard: always reports core events
[    38.877] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event1"
[    38.877] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    38.877] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    38.877] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    38.877] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input1/event1"
[    38.877] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    38.877] (**) Option "xkb_rules" "evdev"
[    38.877] (**) Option "xkb_model" "pc105"
[    38.878] (**) Option "xkb_layout" "us"
[    38.885] (II) config/udev: Adding input device Serial Wacom Tablet (/dev/ttyS3)
[    38.885] (**) Serial Wacom Tablet: Applying InputClass "Wacom serial class"
[    38.885] (II) LoadModule: "wacom"
[    38.886] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    38.887] (II) Module wacom: vendor="X.Org Foundation"
[    38.887]     compiled for 1.13.0, module version = 0.17.0
[    38.887]     Module class: X.Org XInput Driver
[    38.887]     ABI class: X.Org XInput driver, version 18.0
[    38.887] (II) Using input driver 'wacom' for 'Serial Wacom Tablet'
[    38.887] (**) Serial Wacom Tablet: always reports core events
[    38.887] (**) Option "Device" "/dev/ttyS3"
[    38.888] (**) Option "StopBits" "1"
[    38.888] (**) Option "DataBits" "8"
[    38.888] (**) Option "Parity" "None"
[    38.888] (**) Option "Vmin" "1"
[    38.888] (**) Option "Vtime" "10"
[    38.888] (**) Option "FlowControl" "Xoff"
[    38.888] (II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
[    38.888] (II) Serial Wacom Tablet: other types will be automatically added.
[    39.153] (II) Serial Wacom Tablet stylus: serial tablet id 0x90.
[    39.153] (--) Serial Wacom Tablet stylus: using pressure threshold of 27 for button 1
[    39.153] (--) Serial Wacom Tablet stylus: Wacom General ISDV4 tablet maxX=21200 maxY=15900 maxZ=255 resX=100000 resY=100000  tilt=disabled
[    39.153] (II) Serial Wacom Tablet stylus: hotplugging dependent devices.
[    39.153] (EE) Serial Wacom Tablet stylus: Invalid type 'cursor' for this device.
[    39.153] (EE) Serial Wacom Tablet stylus: Invalid type 'touch' for this device.
[    39.153] (EE) Serial Wacom Tablet stylus: Invalid type 'pad' for this device.
[    39.153] (II) Serial Wacom Tablet stylus: hotplugging completed.
[    39.153] (**) Option "config_info" "udev:/sys/devices/pnp0/00:0a/tty/ttyS3"
[    39.153] (II) XINPUT: Adding extended input device "Serial Wacom Tablet stylus" (type: STYLUS, id 10)
[    39.155] (**) Serial Wacom Tablet stylus: (accel) keeping acceleration scheme 1
[    39.155] (**) Serial Wacom Tablet stylus: (accel) acceleration profile 0
[    39.155] (**) Serial Wacom Tablet stylus: (accel) acceleration factor: 2.000
[    39.155] (**) Serial Wacom Tablet stylus: (accel) acceleration threshold: 4
[    39.155] (**) Option "BaudRate" "19200"
[    39.171] (**) Serial Wacom Tablet eraser: Applying InputClass "Wacom serial class"
[    39.171] (II) Using input driver 'wacom' for 'Serial Wacom Tablet eraser'
[    39.171] (**) Serial Wacom Tablet eraser: always reports core events
[    39.171] (**) Option "Device" "/dev/ttyS3"
[    39.172] (**) Option "Type" "eraser"
[    39.172] (**) Option "BaudRate" "19200"
[    39.172] (**) Option "StopBits" "1"
[    39.172] (**) Option "DataBits" "8"
[    39.172] (**) Option "Parity" "None"
[    39.172] (**) Option "Vmin" "1"
[    39.172] (**) Option "Vtime" "10"
[    39.172] (**) Option "FlowControl" "Xoff"
[    39.173] (--) Serial Wacom Tablet eraser: Wacom General ISDV4 tablet maxX=21200 maxY=15900 maxZ=255 resX=100000 resY=100000  tilt=disabled
[    39.173] (**) Option "config_info" "udev:/sys/devices/pnp0/00:0a/tty/ttyS3"
[    39.173] (II) XINPUT: Adding extended input device "Serial Wacom Tablet eraser" (type: ERASER, id 11)
[    39.174] (**) Serial Wacom Tablet eraser: (accel) keeping acceleration scheme 1
[    39.175] (**) Serial Wacom Tablet eraser: (accel) acceleration profile 0
[    39.175] (**) Serial Wacom Tablet eraser: (accel) acceleration factor: 2.000
[    39.175] (**) Serial Wacom Tablet eraser: (accel) acceleration threshold: 4
[    43.199] (II) XKB: reuse xkmfile /var/lib/xkb/server-8AA988DD479FAABEC4FC3CCCF4CC29B4948840B4.xkm
```

Using failed X -configure xorg.conf
/var/log/Xorg.0.log.old

```
[   511.781] X.Org X Server 1.13.0
Release Date: 2012-09-05
[   511.839] X Protocol Version 11, Revision 0
[   511.858] Build Operating System: Linux 3.2.0-26-generic i686 Ubuntu
[   511.898] Current Operating System: Linux ychurch 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:32:08 UTC 2012 i686
[   512.465] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-17-generic root=UUID=a86efa56-6dea-4d00-9da0-8b0bc5b60ac8 ro screen=text quiet splash vt.handoff=7
[   512.535] Build Date: 27 November 2012  07:44:37AM
[   512.561] xorg-server 2:1.13.0-0ubuntu6.1 (For technical support please see http://www.ubuntu.com/support) 
[   512.588] Current version of pixman: 0.26.0
[   512.646]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   512.646] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   520.063] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Mar 18 12:48:00 2013
[   520.063] (II) Loader magic: 0xb7749640
[   520.063] (II) Module ABI versions:
[   520.063]     X.Org ANSI C Emulation: 0.4
[   520.063]     X.Org Video Driver: 13.0
[   520.063]     X.Org XInput driver : 18.0
[   520.064]     X.Org Server Extension : 7.0
[   520.067] (--) PCI:*(0:2:5:0) 126f:0712:126f:0712 rev 160, Mem @ 0xd1000000/16777216
[   520.103] List of video drivers:
[   520.137]     sis
[   520.171]     neomagic
[   520.205]     siliconmotion
[   522.111]     r128
[   522.145]     tdfx
[   522.179]     ati
[   522.213]     mach64
[   522.247]     savage
[   522.281]     openchrome
[   522.315]     intel
[   522.349]     s3
[   523.569]     modesetting
[   523.602]     vmware
[   523.633]     nouveau
[   523.663]     trident
[   523.692]     qxl
[   523.721]     radeon
[   523.749]     cirrus
[   523.776]     mga
[   523.804]     sisusb
[   523.831]     vboxvideo
[   523.857]     fbdev
[   523.881]     vesa
[   523.881] (II) LoadModule: "sis"
[   523.881] (II) Loading /usr/lib/xorg/modules/drivers/sis_drv.so
[   523.882] (II) Module sis: vendor="X.Org Foundation"
[   523.882]     compiled for 1.12.99.902, module version = 0.10.7
[   523.882]     Module class: X.Org Video Driver
[   523.882]     ABI class: X.Org Video Driver, version 13.0
[   523.882] (II) LoadModule: "neomagic"
[   523.883] (II) Loading /usr/lib/xorg/modules/drivers/neomagic_drv.so
[   523.883] (EE) Failed to load /usr/lib/xorg/modules/drivers/neomagic_drv.so: /usr/lib/xorg/modules/drivers/neomagic_drv.so: undefined symbol: NEO_Sync
[   523.883] (II) UnloadModule: "neomagic"
[   523.883] (II) Unloading neomagic
[   523.883] (EE) Failed to load module "neomagic" (loader failed, 7)
[   523.883] (II) LoadModule: "siliconmotion"
[   523.884] (II) Loading /usr/lib/xorg/modules/drivers/siliconmotion_drv.so
[   523.884] (II) Module siliconmotion: vendor="X.Org Foundation"
[   523.884]     compiled for 1.12.99.902, module version = 1.7.7
[   523.884]     Module class: X.Org Video Driver
[   523.884]     ABI class: X.Org Video Driver, version 13.0
[   523.884] (II) LoadModule: "r128"
[   523.885] (II) Loading /usr/lib/xorg/modules/drivers/r128_drv.so
[   523.885] (II) Module r128: vendor="X.Org Foundation"
[   523.885]     compiled for 1.13.0, module version = 6.9.1
[   523.885]     Module class: X.Org Video Driver
[   523.885]     ABI class: X.Org Video Driver, version 13.0
[   523.885] (II) LoadModule: "tdfx"
[   523.886] (II) Loading /usr/lib/xorg/modules/drivers/tdfx_drv.so
[   523.886] (II) Module tdfx: vendor="X.Org Foundation"
[   523.886]     compiled for 1.12.99.902, module version = 1.4.5
[   523.886]     Module class: X.Org Video Driver
[   523.886]     ABI class: X.Org Video Driver, version 13.0
[   523.886] (II) LoadModule: "ati"
[   523.887] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[   523.887] (II) Module ati: vendor="X.Org Foundation"
[   523.887]     compiled for 1.13.0, module version = 6.99.99
[   523.887]     Module class: X.Org Video Driver
[   523.887]     ABI class: X.Org Video Driver, version 13.0
[   523.887] (II) LoadModule: "mach64"
[   523.888] (II) Loading /usr/lib/xorg/modules/drivers/mach64_drv.so
[   523.888] (II) Module mach64: vendor="X.Org Foundation"
[   523.888]     compiled for 1.12.99.902, module version = 6.9.3
[   523.888]     Module class: X.Org Video Driver
[   523.888]     ABI class: X.Org Video Driver, version 13.0
[   523.888] (II) LoadModule: "savage"
[   523.889] (II) Loading /usr/lib/xorg/modules/drivers/savage_drv.so
[   523.889] (II) Module savage: vendor="X.Org Foundation"
[   523.889]     compiled for 1.12.99.902, module version = 2.3.6
[   523.889]     Module class: X.Org Video Driver
[   523.889]     ABI class: X.Org Video Driver, version 13.0
[   523.889] (II) LoadModule: "openchrome"
[   523.890] (II) Loading /usr/lib/xorg/modules/drivers/openchrome_drv.so
[   523.890] (II) Module openchrome: vendor="http://openchrome.org/"
[   523.890]     compiled for 1.12.99.905, module version = 0.3.1
[   523.890]     Module class: X.Org Video Driver
[   523.890]     ABI class: X.Org Video Driver, version 13.0
[   523.891] (II) LoadModule: "intel"
[   523.891] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   523.892] (II) Module intel: vendor="X.Org Foundation"
[   523.892]     compiled for 1.13.0, module version = 2.20.9
[   523.892]     Module class: X.Org Video Driver
[   523.892]     ABI class: X.Org Video Driver, version 13.0
[   523.892] (II) LoadModule: "s3"
[   523.893] (II) Loading /usr/lib/xorg/modules/drivers/s3_drv.so
[   523.893] (II) Module s3: vendor="X.Org Foundation"
[   523.893]     compiled for 1.12.99.902, module version = 0.6.5
[   523.893]     Module class: X.Org Video Driver
[   523.893]     ABI class: X.Org Video Driver, version 13.0
[   523.893] (II) LoadModule: "modesetting"
[   523.894] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   523.894] (II) Module modesetting: vendor="X.Org Foundation"
[   523.894]     compiled for 1.13.0, module version = 0.5.0
[   523.895]     Module class: X.Org Video Driver
[   523.895]     ABI class: X.Org Video Driver, version 13.0
[   523.895] (II) LoadModule: "vmware"
[   523.895] (II) Loading /usr/lib/xorg/modules/drivers/vmware_drv.so
[   523.935] (II) Module vmware: vendor="X.Org Foundation"
[   523.935]     compiled for 1.12.99.902, module version = 12.0.2
[   523.935]     Module class: X.Org Video Driver
[   523.935]     ABI class: X.Org Video Driver, version 13.0
[   523.935] (II) LoadModule: "nouveau"
[   523.935] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   523.936] (II) Module nouveau: vendor="X.Org Foundation"
[   523.936]     compiled for 1.13.0, module version = 1.0.2
[   523.936]     Module class: X.Org Video Driver
[   523.936]     ABI class: X.Org Video Driver, version 13.0
[   523.936] (II) LoadModule: "trident"
[   523.937] (II) Loading /usr/lib/xorg/modules/drivers/trident_drv.so
[   523.937] (II) Module trident: vendor="X.Org Foundation"
[   523.937]     compiled for 1.13.0, module version = 1.3.6
[   523.937]     Module class: X.Org Video Driver
[   523.937]     ABI class: X.Org Video Driver, version 13.0
[   523.937] (II) LoadModule: "qxl"
[   523.937] (II) Loading /usr/lib/xorg/modules/drivers/qxl_drv.so
[   523.938] (II) Module qxl: vendor="X.Org Foundation"
[   523.938]     compiled for 1.13.0, module version = 0.0.0
[   523.938]     Module class: X.Org Video Driver
[   523.938]     ABI class: X.Org Video Driver, version 13.0
[   523.938] (II) LoadModule: "radeon"
[   523.938] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[   523.939] (II) Module radeon: vendor="X.Org Foundation"
[   523.939]     compiled for 1.13.0, module version = 6.99.99
[   523.939]     Module class: X.Org Video Driver
[   523.939]     ABI class: X.Org Video Driver, version 13.0
[   523.939] (II) LoadModule: "cirrus"
[   523.939] (II) Loading /usr/lib/xorg/modules/drivers/cirrus_drv.so
[   523.940] (II) Module cirrus: vendor="X.Org Foundation"
[   523.940]     compiled for 1.12.99.904, module version = 1.5.1
[   523.940]     Module class: X.Org Video Driver
[   523.940]     ABI class: X.Org Video Driver, version 13.0
[   523.940] (II) LoadModule: "mga"
[   523.940] (II) Loading /usr/lib/xorg/modules/drivers/mga_drv.so
[   523.941] (II) Module mga: vendor="X.Org Foundation"
[   523.941]     compiled for 1.13.0, module version = 1.6.2
[   523.941]     Module class: X.Org Video Driver
[   523.941]     ABI class: X.Org Video Driver, version 13.0
[   523.941] (II) LoadModule: "sisusb"
[   523.941] (II) Loading /usr/lib/xorg/modules/drivers/sisusb_drv.so
[   523.941] (II) Module sisusb: vendor="X.Org Foundation"
[   523.942]     compiled for 1.12.99.902, module version = 0.9.6
[   523.942]     Module class: X.Org Video Driver
[   523.942]     ABI class: X.Org Video Driver, version 13.0
[   523.942] (II) LoadModule: "vboxvideo"
[   523.942] (II) Loading /usr/lib/xorg/modules/drivers/vboxvideo_drv.so
[   523.943] (II) Module vboxvideo: vendor="Oracle Corporation"
[   523.943]     compiled for 1.13.0, module version = 1.0.1
[   523.943]     Module class: X.Org Video Driver
[   523.943]     ABI class: X.Org Video Driver, version 13.0
[   523.943] (**) Load address of symbol "VBOXVIDEO" is 0xb501a280
[   523.943] (II) LoadModule: "fbdev"
[   523.943] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   523.943] (II) Module fbdev: vendor="X.Org Foundation"
[   523.943]     compiled for 1.12.99.902, module version = 0.4.3
[   523.943]     Module class: X.Org Video Driver
[   523.944]     ABI class: X.Org Video Driver, version 13.0
[   523.944] (II) LoadModule: "vesa"
[   523.944] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   523.944] (II) Module vesa: vendor="X.Org Foundation"
[   523.944]     compiled for 1.12.99.902, module version = 2.3.2
[   523.944]     Module class: X.Org Video Driver
[   523.944]     ABI class: X.Org Video Driver, version 13.0
[   523.944] (WW) Falling back to old probe method for sis
[   523.945] (WW) Falling back to old probe method for siliconmotion
[   523.945] (WW) Falling back to old probe method for s3
[   523.945] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   523.945] (WW) Falling back to old probe method for trident
[   523.945] (WW) Falling back to old probe method for cirrus
[   523.945] (II) Loading sub module "cirrus_laguna"
[   523.945] (II) LoadModule: "cirrus_laguna"
[   523.945] (II) Loading /usr/lib/xorg/modules/drivers/cirrus_laguna.so
[   523.946] (II) Module cirrus_laguna: vendor="X.Org Foundation"
[   523.946]     compiled for 1.12.99.904, module version = 1.0.0
[   523.946]     ABI class: X.Org Video Driver, version 13.0
[   523.946] (II) Loading sub module "cirrus_alpine"
[   523.946] (II) LoadModule: "cirrus_alpine"
[   523.946] (II) Loading /usr/lib/xorg/modules/drivers/cirrus_alpine.so
[   523.946] (II) Module cirrus_alpine: vendor="X.Org Foundation"
[   523.947]     compiled for 1.12.99.904, module version = 1.0.0
[   523.947]     ABI class: X.Org Video Driver, version 13.0
[   523.947] (WW) Falling back to old probe method for sisusb
[   523.947] (II) FBDEV: driver for framebuffer: fbdev
[   523.947] (II) VESA: driver for VESA chipsets: vesa
[   524.478] (++) Using config file: "/home/ychurch/xorg.conf.new"
[   524.502] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   524.505] (==) ServerLayout "X.org Configured"
[   524.505] (**) |-->Screen "Screen0" (0)
[   524.505] (**) |   |-->Monitor "Monitor0"
[   524.506] (**) |   |-->Device "Card0"
[   524.506] (**) |-->Screen "Screen1" (1)
[   524.506] (**) |   |-->Monitor "Monitor1"
[   524.507] (**) |   |-->Device "Card1"
[   524.507] (**) |-->Screen "Screen2" (2)
[   524.507] (**) |   |-->Monitor "Monitor2"
[   524.508] (**) |   |-->Device "Card2"
[   524.508] (**) |-->Input Device "Mouse0"
[   524.508] (**) |-->Input Device "Keyboard0"
[   524.508] (==) Automatically adding devices
[   524.508] (==) Automatically enabling devices
[   524.509] (==) Automatically adding GPU devices
[   524.509] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   524.509]     Entry deleted from font path.
[   524.509] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   524.509]     Entry deleted from font path.
[   524.509] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   524.509]     Entry deleted from font path.
[   524.509] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   524.509]     Entry deleted from font path.
[   524.509] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   524.509]     Entry deleted from font path.
[   524.509] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[   524.509]     Entry deleted from font path.
[   524.509] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   524.509]     Entry deleted from font path.
[   524.510] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   524.510]     Entry deleted from font path.
[   524.510] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   524.510]     Entry deleted from font path.
[   524.510] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   524.510]     Entry deleted from font path.
[   524.510] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   524.510]     Entry deleted from font path.
[   524.510] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[   524.510]     Entry deleted from font path.
[   524.510] (**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins,
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   524.510] (**) ModulePath set to "/usr/lib/xorg/modules"
[   524.510] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[   524.510] (WW) Disabling Mouse0
[   524.510] (WW) Disabling Keyboard0
[   524.511] (EE) open /dev/dri/card0: No such file or directory
[   524.511] (WW) Falling back to old probe method for modesetting
[   524.511] (EE) open /dev/dri/card0: No such file or directory
[   524.511] (II) Loading sub module "fbdevhw"
[   524.511] (II) LoadModule: "fbdevhw"
[   524.512] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   524.512] (II) Module fbdevhw: vendor="X.Org Foundation"
[   524.513]     compiled for 1.13.0, module version = 0.0.2
[   524.513]     ABI class: X.Org Video Driver, version 13.0
[   524.513] (**) FBDEV(1): claimed PCI slot 2@0:5:0
[   524.513] (II) FBDEV(1): using default device
[   524.513] (WW) Falling back to old probe method for vesa
[   524.559] Number of created screens does not match number of detected devices.
  Configuration failed.
```

Device Info:
---------------------------------
```
$lspci | grep VGA
02:05.0 VGA compatible controller: Silicon Motion, Inc. SM712 LynxEM+ (rev a0)
```

```
$lshw -c video
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: SM712 LynxEM+
       vendor: Silicon Motion, Inc.
       physical id: 5
       bus info: pci@0000:02:05.0
       version: a0
       width: 32 bits
       clock: 66MHz
       capabilities: vga_controller bus_master cap_list
       configuration: latency=64
       resources: memory:d1000000-d1ffffff
```

```
$find /dev -group video/dev/fb0
/dev/agpgart

```

```
$egrep -i " connected|card detect|primary dev" /var/log/Xorg.0.log
[    37.134] (--) Assigning device section with no busID to primary device
[    38.181] (II) SMI(0): Output LVDS connected

```

```
$grep LoadModule /var/log/Xorg.0.log
[    37.006] (II) LoadModule: "glx"
[    37.041] (II) LoadModule: "siliconmotion"
[    37.042] (II) LoadModule: "vesa"
[    37.043] (II) LoadModule: "modesetting"
[    37.049] (II) LoadModule: "fbdev"
[    37.135] (II) LoadModule: "fbdevhw"
[    37.137] (II) LoadModule: "vgahw"
[    37.138] (II) LoadModule: "int10"
[    37.147] (II) LoadModule: "vbe"
[    38.180] (II) LoadModule: "i2c"
[    38.181] (II) LoadModule: "ddc"
[    38.182] (II) LoadModule: "fb"
[    38.183] (II) LoadModule: "xaa"
[    38.185] (II) LoadModule: "ramdac"
[    38.863] (II) LoadModule: "evdev"
[    38.885] (II) LoadModule: "wacom"

```

```
$xdpyinfo
name of display:    :0.0
version number:    11.0
vendor string:    The X.Org Foundation
vendor release number:    11300000
X.Org version: 1.13.0
maximum request size:  16777212 bytes
motion buffer size:  256
bitmap unit, bit order, padding:    32, LSBFirst, 32
image byte order:    LSBFirst
number of supported pixmap formats:    7
supported pixmap formats:
    depth 1, bits_per_pixel 1, scanline_pad 32
    depth 4, bits_per_pixel 8, scanline_pad 32
    depth 8, bits_per_pixel 8, scanline_pad 32
    depth 15, bits_per_pixel 16, scanline_pad 32
    depth 16, bits_per_pixel 16, scanline_pad 32
    depth 24, bits_per_pixel 32, scanline_pad 32
    depth 32, bits_per_pixel 32, scanline_pad 32
keycode range:    minimum 8, maximum 255
focus:  window 0x3000005, revert to Parent
number of extensions:    27
    BIG-REQUESTS
    Composite
    DAMAGE
    DOUBLE-BUFFER
    DPMS
    DRI2
    GLX
    Generic Event Extension
    MIT-SCREEN-SAVER
    MIT-SHM
    RANDR
    RECORD
    RENDER
    SECURITY
    SGI-GLX
    SHAPE
    SYNC
    X-Resource
    XC-MISC
    XFIXES
    XFree86-DGA
    XFree86-VidModeExtension
    XINERAMA
    XInputExtension
    XKEYBOARD
    XTEST
    XVideo
default screen number:    0
number of screens:    1


screen #0:
  dimensions:    800x600 pixels (210x157 millimeters)
  resolution:    97x97 dots per inch
  depths (7):    24, 1, 4, 8, 15, 16, 32
  root window id:    0x171
  depth of root window:    24 planes
  number of colormaps:    minimum 1, maximum 1
  default colormap:    0x20
  default number of colormap cells:    256
  preallocated pixels:    black 0, white 16777215
  options:    backing-store NO, save-unders NO
  largest cursor:    32x32
  current input event mask:    0xfa800f
    KeyPressMask             KeyReleaseMask           ButtonPressMask          
    ButtonReleaseMask        ExposureMask             StructureNotifyMask      
    SubstructureNotifyMask   SubstructureRedirectMask FocusChangeMask          
    PropertyChangeMask       ColormapChangeMask       
  number of visuals:    120
  default visual id:  0x21
  visual:
    visual id:    0x21
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x22
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xfb
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xfc
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xfd
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xfe
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xff
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x100
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x101
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x102
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x103
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x104
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x105
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x106
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x107
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x108
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x109
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x10a
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x10b
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x10c
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x10d
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x10e
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x10f
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x110
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x111
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x112
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x113
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x114
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x115
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x116
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x117
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x118
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x119
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x11a
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x11b
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x11c
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x11d
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x11e
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x11f
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x120
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x121
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x122
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x123
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x124
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x125
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x126
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x127
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x128
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x129
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x12a
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x12b
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x12c
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x12d
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x12e
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x12f
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x130
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x131
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x132
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x133
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x134
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x135
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x136
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x137
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x138
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x139
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x13a
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x13b
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x13c
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x13d
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x13e
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x13f
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x140
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x141
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x142
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x143
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x144
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x145
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x146
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x147
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x148
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x149
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x14a
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x14b
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x14c
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x14d
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x14e
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x14f
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x150
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x151
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x152
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x153
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x154
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x155
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x156
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x157
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x158
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x159
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x15a
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x15b
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x15c
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x15d
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x15e
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x15f
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x160
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x161
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x162
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x163
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x164
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x165
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x166
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x167
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x168
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x169
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x16a
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x16b
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x16c
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x16d
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x16e
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x16f
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x46
    class:    TrueColor
    depth:    32 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits

```

```
$glxinfo | grep -i vendor
server glx vendor string: SGI
client glx vendor string: Mesa Project and SGI
OpenGL vendor string: VMware, Inc.

```

```
$sudo fbset -x
Mode "800x600"
    # D: 48.001 MHz, H: 46.876 kHz, V: 75.121 Hz
    DotClock 48.002
    HTimings 800 832 928 1024
    VTimings 600 604 608 624
    Flags    "-HSync" "-VSync"
EndMode

```

```
$xresprobe -nid: 
res: 
freq: 
disptype: lcd/lvds

```

```

$gtf 800 600 59.9
# 800x600 @ 59.90 Hz (GTF) hsync: 37.20 kHz; pclk: 38.09 MHz
Modeline "800x600_59.90"  38.09  800 832 912 1024  600 601 604 621  -HSync +Vsync


$gtf 800 600 60
# 800x600 @ 60.00 Hz (GTF) hsync: 37.32 kHz; pclk: 38.22 MHz
Modeline "800x600_60.00"  38.22  800 832 912 1024  600 601 604 622  -HSync +Vsync

```

```
$xvidtune -show"800x600"      38.25    800  832  912 1024    600  603  607  624 -hsync +vsync

```

```
$xrandr -q
Screen 0: minimum 128 x 128, current 800 x 600, maximum 800 x 800
LVDS connected 800x600+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   800x600        59.9* 

```

---

### Post by 1branchonthevine on 2013-03-25
Ok, apparently 1 of the 10 Walkabout tablets is using an intel video chipset, as opposed to SiliconMotion. With exception of the SiliconMotion systems, this one will not boot up without a black screen, and Xorg outputs the same error: "number of created screens does not match number of detected devices" Although with this intel chipset tablet, I was able to get a second monitor working on it (unlike the SiliconMotion chipset - even though it supports dual monitor). So now I'm certain it must be the tablet LCD settings not being detected properly! Or the new Xorg detection process has a bug.

Device data:
--------------------------

```
$ lspci
00:00.0 Host bridge: Intel Corporation 82830M/MG/MP Host Bridge (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82830M/MG Integrated Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation 82830M/MG Integrated Graphics Controller
00:1d.0 USB controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Wireless Network Adapter (rev 01)

```

```
$ sudo lshw -c video
  *-display:0             
       description: VGA compatible controller
       product: 82830M/MG Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:6 memory:d8000000-dfffffff memory:d0000000-d007ffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: 82830M/MG Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0 maxlatency=9
       resources: memory:20000000-27ffffff memory:30000000-3007ffff

```

```
$ find /dev -group video
/dev/fb0
/dev/dri/card0
/dev/dri/controlD64
/dev/agpgart

```

```
$ xdpyinfo
name of display:    :0.0
version number:    11.0
vendor string:    The X.Org Foundation
vendor release number:    11300000
X.Org version: 1.13.0
maximum request size:  16777212 bytes
motion buffer size:  256
bitmap unit, bit order, padding:    32, LSBFirst, 32
image byte order:    LSBFirst
number of supported pixmap formats:    7
supported pixmap formats:
    depth 1, bits_per_pixel 1, scanline_pad 32
    depth 4, bits_per_pixel 8, scanline_pad 32
    depth 8, bits_per_pixel 8, scanline_pad 32
    depth 15, bits_per_pixel 16, scanline_pad 32
    depth 16, bits_per_pixel 16, scanline_pad 32
    depth 24, bits_per_pixel 32, scanline_pad 32
    depth 32, bits_per_pixel 32, scanline_pad 32
keycode range:    minimum 8, maximum 255
focus:  window 0x3000005, revert to Parent
number of extensions:    27
    BIG-REQUESTS
    Composite
    DAMAGE
    DOUBLE-BUFFER
    DPMS
    DRI2
    GLX
    Generic Event Extension
    MIT-SCREEN-SAVER
    MIT-SHM
    RANDR
    RECORD
    RENDER
    SECURITY
    SGI-GLX
    SHAPE
    SYNC
    X-Resource
    XC-MISC
    XFIXES
    XFree86-DGA
    XFree86-VidModeExtension
    XINERAMA
    XInputExtension
    XKEYBOARD
    XTEST
    XVideo
default screen number:    0
number of screens:    1

screen #0:
  dimensions:    800x600 pixels (211x158 millimeters)
  resolution:    96x96 dots per inch
  depths (7):    24, 1, 4, 8, 15, 16, 32
  root window id:    0x9b
  depth of root window:    24 planes
  number of colormaps:    minimum 1, maximum 1
  default colormap:    0x20
  default number of colormap cells:    256
  preallocated pixels:    black 0, white 16777215
  options:    backing-store NO, save-unders NO
  largest cursor:    64x64
  current input event mask:    0xfa800f
    KeyPressMask             KeyReleaseMask           ButtonPressMask          
    ButtonReleaseMask        ExposureMask             StructureNotifyMask      
    SubstructureNotifyMask   SubstructureRedirectMask FocusChangeMask          
    PropertyChangeMask       ColormapChangeMask       
  number of visuals:    32
  default visual id:  0x21
  visual:
    visual id:    0x21
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x22
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x7d
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x7e
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x7f
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x80
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x81
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x82
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x83
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x84
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x85
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x86
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x87
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x88
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x89
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x8a
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x8b
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x8c
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x8d
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x8e
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x8f
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x90
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x91
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x92
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x93
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x94
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x95
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x96
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x97
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x98
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x99
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x4c
    class:    TrueColor
    depth:    32 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits

```

```
$ glxinfo | grep -i vendor
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  22
  Current serial number in output stream:  25

```


Logs:
---------------------------------
Tablet Display only (Without aux monitor)
/var/log/Xorg.0.log.old

```
[    47.176] 
X.Org X Server 1.13.0
Release Date: 2012-09-05
[    47.176] X Protocol Version 11, Revision 0
[    47.176] Build Operating System: Linux 3.2.0-26-generic i686 Ubuntu
[    47.176] Current Operating System: Linux ychurch 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:32:08 UTC 2012 i686
[    47.176] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-17-generic root=UUID=0bbcc6af-eb75-4483-bc0f-6881e364330f ro quiet vt.handoff=7
[    47.177] Build Date: 08 October 2012  03:34:08PM
[    47.177] xorg-server 2:1.13.0-0ubuntu6 (For technical support please see http://www.ubuntu.com/support) 
[    47.177] Current version of pixman: 0.26.0
[    47.177]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    47.177] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    47.177] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Mar 25 13:04:38 2013
[    47.178] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    47.179] (==) No Layout section.  Using the first Screen section.
[    47.179] (==) No screen section available. Using defaults.
[    47.179] (**) |-->Screen "Default Screen Section" (0)
[    47.179] (**) |   |-->Monitor "<default monitor>"
[    47.180] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    47.180] (==) Automatically adding devices
[    47.180] (==) Automatically enabling devices
[    47.180] (==) Automatically adding GPU devices
[    47.180] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    47.180]     Entry deleted from font path.
[    47.180] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    47.180]     Entry deleted from font path.
[    47.180] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    47.180]     Entry deleted from font path.
[    47.180] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    47.180]     Entry deleted from font path.
[    47.180] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    47.180]     Entry deleted from font path.
[    47.180] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    47.180]     Entry deleted from font path.
[    47.180] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    47.180] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    47.180] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    47.181] (II) Loader magic: 0xb77c2640
[    47.181] (II) Module ABI versions:
[    47.181]     X.Org ANSI C Emulation: 0.4
[    47.181]     X.Org Video Driver: 13.0
[    47.181]     X.Org XInput driver : 18.0
[    47.181]     X.Org Server Extension : 7.0
[    47.181] (II) config/udev: Adding drm device (/dev/dri/card0)
[    47.184] (--) PCI:*(0:0:2:0) 8086:3577:8086:1969 rev 4, Mem @ 0xd8000000/134217728, 0xd0000000/524288
[    47.184] (--) PCI: (0:0:2:1) 8086:3577:8086:1969 rev 0, Mem @ 0x20000000/134217728, 0x30000000/524288
[    47.185] (II) Open ACPI successful (/var/run/acpid.socket)
[    47.185] Initializing built-in extension Generic Event Extension
[    47.185] Initializing built-in extension SHAPE
[    47.185] Initializing built-in extension MIT-SHM
[    47.185] Initializing built-in extension XInputExtension
[    47.185] Initializing built-in extension XTEST
[    47.185] Initializing built-in extension BIG-REQUESTS
[    47.185] Initializing built-in extension SYNC
[    47.185] Initializing built-in extension XKEYBOARD
[    47.186] Initializing built-in extension XC-MISC
[    47.186] Initializing built-in extension SECURITY
[    47.186] Initializing built-in extension XINERAMA
[    47.186] Initializing built-in extension XFIXES
[    47.186] Initializing built-in extension RENDER
[    47.186] Initializing built-in extension RANDR
[    47.186] Initializing built-in extension COMPOSITE
[    47.186] Initializing built-in extension DAMAGE
[    47.186] Initializing built-in extension MIT-SCREEN-SAVER
[    47.186] Initializing built-in extension DOUBLE-BUFFER
[    47.186] Initializing built-in extension RECORD
[    47.186] Initializing built-in extension DPMS
[    47.186] Initializing built-in extension X-Resource
[    47.186] Initializing built-in extension XVideo
[    47.186] Initializing built-in extension XVideo-MotionCompensation
[    47.186] Initializing built-in extension XFree86-VidModeExtension
[    47.186] Initializing built-in extension XFree86-DGA
[    47.186] Initializing built-in extension XFree86-DRI
[    47.186] Initializing built-in extension DRI2
[    47.186] (II) LoadModule: "glx"
[    47.187] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    47.188] (II) Module glx: vendor="X.Org Foundation"
[    47.188]     compiled for 1.13.0, module version = 1.0.0
[    47.188]     ABI class: X.Org Server Extension, version 7.0
[    47.188] (==) AIGLX enabled
[    47.188] Loading extension GLX
[    47.188] (==) Matched intel as autoconfigured driver 0
[    47.188] (==) Matched intel as autoconfigured driver 1
[    47.188] (==) Matched vesa as autoconfigured driver 2
[    47.188] (==) Matched modesetting as autoconfigured driver 3
[    47.188] (==) Matched fbdev as autoconfigured driver 4
[    47.188] (==) Assigned the driver to the xf86ConfigLayout
[    47.188] (II) LoadModule: "intel"
[    47.189] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    47.190] (II) Module intel: vendor="X.Org Foundation"
[    47.190]     compiled for 1.13.0, module version = 2.20.9
[    47.190]     Module class: X.Org Video Driver
[    47.190]     ABI class: X.Org Video Driver, version 13.0
[    47.190] (II) LoadModule: "vesa"
[    47.191] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    47.191] (II) Module vesa: vendor="X.Org Foundation"
[    47.191]     compiled for 1.12.99.902, module version = 2.3.2
[    47.191]     Module class: X.Org Video Driver
[    47.191]     ABI class: X.Org Video Driver, version 13.0
[    47.191] (II) LoadModule: "modesetting"
[    47.192] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    47.192] (II) Module modesetting: vendor="X.Org Foundation"
[    47.192]     compiled for 1.13.0, module version = 0.5.0
[    47.192]     Module class: X.Org Video Driver
[    47.192]     ABI class: X.Org Video Driver, version 13.0
[    47.192] (II) LoadModule: "fbdev"
[    47.193] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    47.193] (II) Module fbdev: vendor="X.Org Foundation"
[    47.193]     compiled for 1.12.99.902, module version = 0.4.3
[    47.193]     Module class: X.Org Video Driver
[    47.193]     ABI class: X.Org Video Driver, version 13.0
[    47.193] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
    Ivybridge Server (GT2), Haswell Desktop (GT1), Haswell Desktop (GT2),
    Haswell Desktop (GT2+), Haswell Mobile (GT1), Haswell Mobile (GT2),
    Haswell Mobile (GT2+), Haswell Server (GT1), Haswell Server (GT2),
    Haswell Server (GT2+), Haswell SDV Desktop (GT1),
    Haswell SDV Desktop (GT2), Haswell SDV Desktop (GT2+),
    Haswell SDV Mobile (GT1), Haswell SDV Mobile (GT2),
    Haswell SDV Mobile (GT2+), Haswell SDV Server (GT1),
    Haswell SDV Server (GT2), Haswell SDV Server (GT2+),
    Haswell ULT Desktop (GT1), Haswell ULT Desktop (GT2),
    Haswell ULT Desktop (GT2+), Haswell ULT Mobile (GT1),
    Haswell ULT Mobile (GT2), Haswell ULT Mobile (GT2+),
    Haswell ULT Server (GT1), Haswell ULT Server (GT2),
    Haswell ULT Server (GT2+), Haswell CRW Desktop (GT1),
    Haswell CRW Desktop (GT2), Haswell CRW Desktop (GT2+),
    Haswell CRW Mobile (GT1), Haswell CRW Mobile (GT2),
    Haswell CRW Mobile (GT2+), Haswell CRW Server (GT1),
    Haswell CRW Server (GT2), Haswell CRW Server (GT2+),
    ValleyView PO board
[    47.197] (II) VESA: driver for VESA chipsets: vesa
[    47.197] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    47.197] (II) FBDEV: driver for framebuffer: fbdev
[    47.197] (++) using VT number 7

[    47.212] (II) intel(0): using device path '/dev/dri/card0'
[    47.212] (WW) Falling back to old probe method for vesa
[    47.212] (WW) Falling back to old probe method for modesetting
[    47.213] (WW) Falling back to old probe method for fbdev
[    47.213] (II) Loading sub module "fbdevhw"
[    47.213] (II) LoadModule: "fbdevhw"
[    47.213] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    47.213] (II) Module fbdevhw: vendor="X.Org Foundation"
[    47.213]     compiled for 1.13.0, module version = 0.0.2
[    47.213]     ABI class: X.Org Video Driver, version 13.0
[    47.214] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    47.214] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    47.214] (==) intel(0): RGB weight 888
[    47.214] (==) intel(0): Default visual is TrueColor
[    47.214] (--) intel(0): Integrated Graphics Chipset: Intel(R) i830M
[    47.214] (**) intel(0): Relaxed fencing disabled
[    47.215] (**) intel(0): Wait on SwapBuffers? enabled
[    47.215] (**) intel(0): Triple buffering? enabled
[    47.215] (**) intel(0): Framebuffer tiled
[    47.215] (**) intel(0): Pixmaps tiled
[    47.215] (**) intel(0): 3D buffers tiled
[    47.215] (**) intel(0): SwapBuffers wait enabled
[    47.215] (==) intel(0): video overlay key set to 0x101fe
[    47.393] (II) intel(0): Output VGA1 has no monitor section
[    47.561] (II) intel(0): EDID for output VGA1
[    47.561] (II) intel(0): Output VGA1 disconnected
[    47.561] (WW) intel(0): No outputs definitely connected, trying again...
[    47.561] (II) intel(0): Output VGA1 disconnected
[    47.561] (WW) intel(0): Unable to find connected outputs - setting 1024x768 initial framebuffer
[    47.561] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    47.561] (II) intel(0): Kernel page flipping support detected, enabling
[    47.561] (EE) intel(0): No modes.
[    47.561] (II) UnloadModule: "intel"
[    47.561] (EE) Screen(s) found, but none have a usable configuration.
[    47.561] 
Fatal server error:
[    47.561] no screens found
[    47.561] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    47.561] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    47.561] (EE) 
[    47.592] Server terminated with error (1). Closing log file.
```

Tablet Display with second aux working monitor.
/var/log/Xorg.0.log

```
[    38.663] 
X.Org X Server 1.13.0
Release Date: 2012-09-05
[    38.663] X Protocol Version 11, Revision 0
[    38.663] Build Operating System: Linux 3.2.0-26-generic i686 Ubuntu
[    38.663] Current Operating System: Linux ychurch 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:32:08 UTC 2012 i686
[    38.663] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-17-generic root=UUID=0bbcc6af-eb75-4483-bc0f-6881e364330f ro quiet vt.handoff=7
[    38.663] Build Date: 08 October 2012  03:34:08PM
[    38.663] xorg-server 2:1.13.0-0ubuntu6 (For technical support please see http://www.ubuntu.com/support) 
[    38.663] Current version of pixman: 0.26.0
[    38.668]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    38.668] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    38.669] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Mar 25 13:12:18 2013
[    39.366] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    39.368] (==) No Layout section.  Using the first Screen section.
[    39.368] (==) No screen section available. Using defaults.
[    39.368] (**) |-->Screen "Default Screen Section" (0)
[    39.368] (**) |   |-->Monitor "<default monitor>"
[    39.369] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    39.369] (==) Automatically adding devices
[    39.369] (==) Automatically enabling devices
[    39.369] (==) Automatically adding GPU devices
[    39.369] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    39.369]     Entry deleted from font path.
[    39.369] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    39.369]     Entry deleted from font path.
[    39.369] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    39.369]     Entry deleted from font path.
[    39.369] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    39.369]     Entry deleted from font path.
[    39.369] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    39.369]     Entry deleted from font path.
[    39.369] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    39.369]     Entry deleted from font path.
[    39.369] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    39.369] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    39.369] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    39.370] (II) Loader magic: 0xb771c640
[    39.370] (II) Module ABI versions:
[    39.370]     X.Org ANSI C Emulation: 0.4
[    39.370]     X.Org Video Driver: 13.0
[    39.370]     X.Org XInput driver : 18.0
[    39.370]     X.Org Server Extension : 7.0
[    39.371] (II) config/udev: Adding drm device (/dev/dri/card0)
[    39.373] (--) PCI:*(0:0:2:0) 8086:3577:8086:1969 rev 4, Mem @ 0xd8000000/134217728, 0xd0000000/524288
[    39.374] (--) PCI: (0:0:2:1) 8086:3577:8086:1969 rev 0, Mem @ 0x20000000/134217728, 0x30000000/524288
[    39.374] (II) Open ACPI successful (/var/run/acpid.socket)
[    39.375] Initializing built-in extension Generic Event Extension
[    39.375] Initializing built-in extension SHAPE
[    39.375] Initializing built-in extension MIT-SHM
[    39.375] Initializing built-in extension XInputExtension
[    39.375] Initializing built-in extension XTEST
[    39.375] Initializing built-in extension BIG-REQUESTS
[    39.375] Initializing built-in extension SYNC
[    39.375] Initializing built-in extension XKEYBOARD
[    39.375] Initializing built-in extension XC-MISC
[    39.375] Initializing built-in extension SECURITY
[    39.375] Initializing built-in extension XINERAMA
[    39.375] Initializing built-in extension XFIXES
[    39.375] Initializing built-in extension RENDER
[    39.375] Initializing built-in extension RANDR
[    39.375] Initializing built-in extension COMPOSITE
[    39.375] Initializing built-in extension DAMAGE
[    39.375] Initializing built-in extension MIT-SCREEN-SAVER
[    39.375] Initializing built-in extension DOUBLE-BUFFER
[    39.375] Initializing built-in extension RECORD
[    39.375] Initializing built-in extension DPMS
[    39.375] Initializing built-in extension X-Resource
[    39.375] Initializing built-in extension XVideo
[    39.375] Initializing built-in extension XVideo-MotionCompensation
[    39.376] Initializing built-in extension XFree86-VidModeExtension
[    39.376] Initializing built-in extension XFree86-DGA
[    39.376] Initializing built-in extension XFree86-DRI
[    39.376] Initializing built-in extension DRI2
[    39.376] (II) LoadModule: "glx"
[    39.748] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    39.749] (II) Module glx: vendor="X.Org Foundation"
[    39.749]     compiled for 1.13.0, module version = 1.0.0
[    39.749]     ABI class: X.Org Server Extension, version 7.0
[    39.749] (==) AIGLX enabled
[    39.749] Loading extension GLX
[    39.750] (==) Matched intel as autoconfigured driver 0
[    39.750] (==) Matched intel as autoconfigured driver 1
[    39.750] (==) Matched vesa as autoconfigured driver 2
[    39.750] (==) Matched modesetting as autoconfigured driver 3
[    39.750] (==) Matched fbdev as autoconfigured driver 4
[    39.750] (==) Assigned the driver to the xf86ConfigLayout
[    39.750] (II) LoadModule: "intel"
[    39.751] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    40.136] (II) Module intel: vendor="X.Org Foundation"
[    40.136]     compiled for 1.13.0, module version = 2.20.9
[    40.136]     Module class: X.Org Video Driver
[    40.136]     ABI class: X.Org Video Driver, version 13.0
[    40.136] (II) LoadModule: "vesa"
[    40.137] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    40.138] (II) Module vesa: vendor="X.Org Foundation"
[    40.138]     compiled for 1.12.99.902, module version = 2.3.2
[    40.138]     Module class: X.Org Video Driver
[    40.138]     ABI class: X.Org Video Driver, version 13.0
[    40.138] (II) LoadModule: "modesetting"
[    40.138] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    40.139] (II) Module modesetting: vendor="X.Org Foundation"
[    40.139]     compiled for 1.13.0, module version = 0.5.0
[    40.139]     Module class: X.Org Video Driver
[    40.139]     ABI class: X.Org Video Driver, version 13.0
[    40.139] (II) LoadModule: "fbdev"
[    40.139] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    40.142] (II) Module fbdev: vendor="X.Org Foundation"
[    40.142]     compiled for 1.12.99.902, module version = 0.4.3
[    40.142]     Module class: X.Org Video Driver
[    40.142]     ABI class: X.Org Video Driver, version 13.0
[    40.142] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
    Ivybridge Server (GT2), Haswell Desktop (GT1), Haswell Desktop (GT2),
    Haswell Desktop (GT2+), Haswell Mobile (GT1), Haswell Mobile (GT2),
    Haswell Mobile (GT2+), Haswell Server (GT1), Haswell Server (GT2),
    Haswell Server (GT2+), Haswell SDV Desktop (GT1),
    Haswell SDV Desktop (GT2), Haswell SDV Desktop (GT2+),
    Haswell SDV Mobile (GT1), Haswell SDV Mobile (GT2),
    Haswell SDV Mobile (GT2+), Haswell SDV Server (GT1),
    Haswell SDV Server (GT2), Haswell SDV Server (GT2+),
    Haswell ULT Desktop (GT1), Haswell ULT Desktop (GT2),
    Haswell ULT Desktop (GT2+), Haswell ULT Mobile (GT1),
    Haswell ULT Mobile (GT2), Haswell ULT Mobile (GT2+),
    Haswell ULT Server (GT1), Haswell ULT Server (GT2),
    Haswell ULT Server (GT2+), Haswell CRW Desktop (GT1),
    Haswell CRW Desktop (GT2), Haswell CRW Desktop (GT2+),
    Haswell CRW Mobile (GT1), Haswell CRW Mobile (GT2),
    Haswell CRW Mobile (GT2+), Haswell CRW Server (GT1),
    Haswell CRW Server (GT2), Haswell CRW Server (GT2+),
    ValleyView PO board
[    40.149] (II) VESA: driver for VESA chipsets: vesa
[    40.149] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    40.149] (II) FBDEV: driver for framebuffer: fbdev
[    40.149] (++) using VT number 8

[    40.165] (II) intel(0): using device path '/dev/dri/card0'
[    40.165] (WW) Falling back to old probe method for vesa
[    40.165] (WW) Falling back to old probe method for modesetting
[    40.165] (WW) Falling back to old probe method for fbdev
[    40.165] (II) Loading sub module "fbdevhw"
[    40.165] (II) LoadModule: "fbdevhw"
[    40.166] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    40.166] (II) Module fbdevhw: vendor="X.Org Foundation"
[    40.166]     compiled for 1.13.0, module version = 0.0.2
[    40.166]     ABI class: X.Org Video Driver, version 13.0
[    40.167] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    40.167] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    40.167] (==) intel(0): RGB weight 888
[    40.167] (==) intel(0): Default visual is TrueColor
[    40.167] (--) intel(0): Integrated Graphics Chipset: Intel(R) i830M
[    40.167] (**) intel(0): Relaxed fencing disabled
[    40.167] (**) intel(0): Wait on SwapBuffers? enabled
[    40.167] (**) intel(0): Triple buffering? enabled
[    40.167] (**) intel(0): Framebuffer tiled
[    40.167] (**) intel(0): Pixmaps tiled
[    40.167] (**) intel(0): 3D buffers tiled
[    40.169] (**) intel(0): SwapBuffers wait enabled
[    40.169] (==) intel(0): video overlay key set to 0x101fe
[    40.202] (II) intel(0): Output VGA1 has no monitor section
[    40.235] (II) intel(0): EDID for output VGA1
[    40.235] (II) intel(0): Printing probed modes for output VGA1
[    40.235] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    40.235] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    40.235] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    40.235] (II) intel(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz e)
[    40.235] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz e)
[    40.235] (II) intel(0): Output VGA1 connected
[    40.236] (II) intel(0): Using exact sizes for initial modes
[    40.236] (II) intel(0): Output VGA1 using initial mode 1024x768
[    40.236] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    40.236] (II) intel(0): Kernel page flipping support detected, enabling
[    40.236] (==) intel(0): DPI set to (96, 96)
[    40.236] (II) Loading sub module "fb"
[    40.236] (II) LoadModule: "fb"
[    40.314] (II) Loading /usr/lib/xorg/modules/libfb.so
[    40.354] (II) Module fb: vendor="X.Org Foundation"
[    40.354]     compiled for 1.13.0, module version = 1.0.0
[    40.354]     ABI class: X.Org ANSI C Emulation, version 0.4
[    40.354] (II) Loading sub module "dri2"
[    40.354] (II) LoadModule: "dri2"
[    40.354] (II) Module "dri2" already built-in
[    40.355] (II) UnloadModule: "vesa"
[    40.355] (II) Unloading vesa
[    40.355] (II) UnloadModule: "modesetting"
[    40.355] (II) Unloading modesetting
[    40.355] (II) UnloadModule: "fbdev"
[    40.355] (II) Unloading fbdev
[    40.355] (II) UnloadSubModule: "fbdevhw"
[    40.355] (II) Unloading fbdevhw
[    40.355] (==) Depth 24 pixmap format is 32 bpp
[    40.355] (II) intel(0): [DRI2] Setup complete
[    40.355] (II) intel(0): [DRI2]   DRI driver: i915
[    40.355] (II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled
[    40.356] (II) UXA(0): Driver registered support for the following operations:
[    40.356] (II)         solid
[    40.356] (II)         copy
[    40.356] (II)         composite (RENDER acceleration)
[    40.356] (II)         put_image
[    40.356] (II)         get_image
[    40.356] (==) intel(0): Backing store disabled
[    40.356] (==) intel(0): Silken mouse enabled
[    40.356] (II) intel(0): Initializing HW Cursor
[    40.356] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    40.357] (==) intel(0): DPMS enabled
[    40.357] (==) intel(0): Intel XvMC decoder disabled
[    40.357] (II) intel(0): Set up overlay video
[    40.357] (II) intel(0): direct rendering: DRI2 Enabled
[    40.357] (==) intel(0): hotplug detection: "enabled"
[    40.392] (--) RandR disabled
[    40.603] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    40.603] (II) AIGLX: enabled GLX_INTEL_swap_event
[    40.603] (II) AIGLX: enabled GLX_ARB_create_context
[    40.603] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    40.603] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    40.603] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    40.603] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    40.603] (II) AIGLX: Loaded and initialized i915
[    40.603] (II) GLX: Initialized DRI2 GL provider for screen 0
[    40.606] (II) intel(0): Setting screen physical size to 270 x 203
[    40.675] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    40.687] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    40.687] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    40.687] (II) LoadModule: "evdev"
[    40.688] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    40.689] (II) Module evdev: vendor="X.Org Foundation"
[    40.689]     compiled for 1.13.0, module version = 2.7.3
[    40.689]     Module class: X.Org XInput Driver
[    40.689]     ABI class: X.Org XInput driver, version 18.0
[    40.689] (II) Using input driver 'evdev' for 'Power Button'
[    40.689] (**) Power Button: always reports core events
[    40.689] (**) evdev: Power Button: Device: "/dev/input/event0"
[    40.690] (--) evdev: Power Button: Vendor 0 Product 0x1
[    40.690] (--) evdev: Power Button: Found keys
[    40.690] (II) evdev: Power Button: Configuring as keyboard
[    40.690] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input0/event0"
[    40.690] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    40.690] (**) Option "xkb_rules" "evdev"
[    40.690] (**) Option "xkb_model" "pc105"
[    40.690] (**) Option "xkb_layout" "us"
[    40.692] (II) config/udev: Adding drm device (/dev/dri/card0)
[    40.693] (II) config/udev: Adding input device Multi-Input Device (/dev/input/event2)
[    40.693] (**) Multi-Input Device: Applying InputClass "evdev keyboard catchall"
[    40.693] (II) Using input driver 'evdev' for 'Multi-Input Device'
[    40.693] (**) Multi-Input Device: always reports core events
[    40.693] (**) evdev: Multi-Input Device: Device: "/dev/input/event2"
[    40.694] (--) evdev: Multi-Input Device: Vendor 0x518 Product 0x8
[    40.694] (--) evdev: Multi-Input Device: Found keys
[    40.694] (II) evdev: Multi-Input Device: Configuring as keyboard
[    40.694] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb2/2-2/2-2:1.0/input/input2/event2"
[    40.694] (II) XINPUT: Adding extended input device "Multi-Input Device" (type: KEYBOARD, id 7)
[    40.694] (**) Option "xkb_rules" "evdev"
[    40.694] (**) Option "xkb_model" "pc105"
[    40.694] (**) Option "xkb_layout" "us"
[    40.696] (II) config/udev: Adding input device Multi-Input Device (/dev/input/event3)
[    40.696] (**) Multi-Input Device: Applying InputClass "evdev pointer catchall"
[    40.696] (**) Multi-Input Device: Applying InputClass "evdev keyboard catchall"
[    40.697] (II) Using input driver 'evdev' for 'Multi-Input Device'
[    40.697] (**) Multi-Input Device: always reports core events
[    40.697] (**) evdev: Multi-Input Device: Device: "/dev/input/event3"
[    40.697] (--) evdev: Multi-Input Device: Vendor 0x518 Product 0x8
[    40.697] (--) evdev: Multi-Input Device: Found 3 mouse buttons
[    40.697] (--) evdev: Multi-Input Device: Found scroll wheel(s)
[    40.697] (--) evdev: Multi-Input Device: Found relative axes
[    40.697] (--) evdev: Multi-Input Device: Found x and y relative axes
[    40.697] (--) evdev: Multi-Input Device: Found absolute axes
[    40.697] (II) evdev: Multi-Input Device: Forcing absolute x/y axes to exist.
[    40.697] (--) evdev: Multi-Input Device: Found keys
[    40.697] (II) evdev: Multi-Input Device: Configuring as mouse
[    40.697] (II) evdev: Multi-Input Device: Configuring as keyboard
[    40.697] (II) evdev: Multi-Input Device: Adding scrollwheel support
[    40.697] (**) evdev: Multi-Input Device: YAxisMapping: buttons 4 and 5
[    40.697] (**) evdev: Multi-Input Device: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    40.697] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb2/2-2/2-2:1.1/input/input3/event3"
[    40.697] (II) XINPUT: Adding extended input device "Multi-Input Device" (type: KEYBOARD, id 8)
[    40.698] (**) Option "xkb_rules" "evdev"
[    40.698] (**) Option "xkb_model" "pc105"
[    40.698] (**) Option "xkb_layout" "us"
[    40.699] (II) evdev: Multi-Input Device: initialized for relative axes.
[    40.699] (WW) evdev: Multi-Input Device: ignoring absolute axes.
[    40.699] (**) Multi-Input Device: (accel) keeping acceleration scheme 1
[    40.699] (**) Multi-Input Device: (accel) acceleration profile 0
[    40.699] (**) Multi-Input Device: (accel) acceleration factor: 2.000
[    40.699] (**) Multi-Input Device: (accel) acceleration threshold: 4
[    40.711] (II) config/udev: Adding input device Multi-Input Device (/dev/input/mouse0)
[    40.711] (II) No input driver specified, ignoring this device.
[    40.711] (II) This device may have been added with another device file.
[    40.717] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event1)
[    40.717] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    40.717] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    40.717] (**) AT Translated Set 2 keyboard: always reports core events
[    40.717] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event1"
[    40.718] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    40.718] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    40.724] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    40.724] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input1/event1"
[    40.724] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    40.725] (**) Option "xkb_rules" "evdev"
[    40.725] (**) Option "xkb_model" "pc105"
[    40.725] (**) Option "xkb_layout" "us"
[    40.744] (II) config/udev: Adding input device Serial Wacom Tablet (/dev/ttyS3)
[    40.745] (**) Serial Wacom Tablet: Applying InputClass "Wacom serial class"
[    40.751] (II) LoadModule: "wacom"
[    40.752] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    40.753] (II) Module wacom: vendor="X.Org Foundation"
[    40.753]     compiled for 1.13.0, module version = 0.17.0
[    40.753]     Module class: X.Org XInput Driver
[    40.753]     ABI class: X.Org XInput driver, version 18.0
[    40.753] (II) Using input driver 'wacom' for 'Serial Wacom Tablet'
[    40.753] (**) Serial Wacom Tablet: always reports core events
[    40.753] (**) Option "Device" "/dev/ttyS3"
[    40.756] (**) Option "StopBits" "1"
[    40.756] (**) Option "DataBits" "8"
[    40.756] (**) Option "Parity" "None"
[    40.756] (**) Option "Vmin" "1"
[    40.757] (**) Option "Vtime" "10"
[    40.757] (**) Option "FlowControl" "Xoff"
[    40.757] (II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
[    40.757] (II) Serial Wacom Tablet: other types will be automatically added.
[    41.038] (II) Serial Wacom Tablet stylus: serial tablet id 0x90.
[    41.038] (--) Serial Wacom Tablet stylus: using pressure threshold of 27 for button 1
[    41.038] (--) Serial Wacom Tablet stylus: Wacom General ISDV4 tablet maxX=21200 maxY=15900 maxZ=255 resX=100000 resY=100000  tilt=disabled
[    41.038] (II) Serial Wacom Tablet stylus: hotplugging dependent devices.
[    41.038] (EE) Serial Wacom Tablet stylus: Invalid type 'cursor' for this device.
[    41.038] (EE) Serial Wacom Tablet stylus: Invalid type 'touch' for this device.
[    41.038] (EE) Serial Wacom Tablet stylus: Invalid type 'pad' for this device.
[    41.038] (II) Serial Wacom Tablet stylus: hotplugging completed.
[    41.038] (**) Option "config_info" "udev:/sys/devices/pnp0/00:09/tty/ttyS3"
[    41.038] (II) XINPUT: Adding extended input device "Serial Wacom Tablet stylus" (type: STYLUS, id 10)
[    41.040] (**) Serial Wacom Tablet stylus: (accel) keeping acceleration scheme 1
[    41.040] (**) Serial Wacom Tablet stylus: (accel) acceleration profile 0
[    41.040] (**) Serial Wacom Tablet stylus: (accel) acceleration factor: 2.000
[    41.040] (**) Serial Wacom Tablet stylus: (accel) acceleration threshold: 4
[    41.040] (**) Option "BaudRate" "19200"
[    41.057] (**) Serial Wacom Tablet eraser: Applying InputClass "Wacom serial class"
[    41.057] (II) Using input driver 'wacom' for 'Serial Wacom Tablet eraser'
[    41.057] (**) Serial Wacom Tablet eraser: always reports core events
[    41.057] (**) Option "Device" "/dev/ttyS3"
[    41.057] (**) Option "Type" "eraser"
[    41.057] (**) Option "BaudRate" "19200"
[    41.057] (**) Option "StopBits" "1"
[    41.058] (**) Option "DataBits" "8"
[    41.058] (**) Option "Parity" "None"
[    41.058] (**) Option "Vmin" "1"
[    41.058] (**) Option "Vtime" "10"
[    41.058] (**) Option "FlowControl" "Xoff"
[    41.058] (--) Serial Wacom Tablet eraser: Wacom General ISDV4 tablet maxX=21200 maxY=15900 maxZ=255 resX=100000 resY=100000  tilt=disabled
[    41.058] (**) Option "config_info" "udev:/sys/devices/pnp0/00:09/tty/ttyS3"
[    41.058] (II) XINPUT: Adding extended input device "Serial Wacom Tablet eraser" (type: ERASER, id 11)
[    41.060] (**) Serial Wacom Tablet eraser: (accel) keeping acceleration scheme 1
[    41.060] (**) Serial Wacom Tablet eraser: (accel) acceleration profile 0
[    41.060] (**) Serial Wacom Tablet eraser: (accel) acceleration factor: 2.000
[    41.060] (**) Serial Wacom Tablet eraser: (accel) acceleration threshold: 4
[    43.054] (II) XKB: reuse xkmfile /var/lib/xkb/server-8AA988DD479FAABEC4FC3CCCF4CC29B4948840B4.xkm
[    43.880] (II) intel(0): Allocated new frame buffer 832x600 stride 4096, tiled
```

---

### Post by Yellow Pasque on 2013-03-25
So what happens on the siliconmotion system when you try to use the vesa driver with a simple xorg.conf?

```
Section "Device"
        Identifier      "Configured Video Device"
	Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

---

### Post by 1branchonthevine on 2013-03-25
Thanks for the reply, but I think it is already  falling back to the vesa driver (on the siliconmotion tablets) because I do eventually get past the black screen on boot, and then it loads xfce just fine, but framebuffer is really jerkey when scrolling when not using Siliconmotion driver, which is why I hope to get it working. It just seems to fail at loading the siliconmotion driver or detecting the screens on this driver.

When I create the basic simple xorg.conf like you show, now I stay stuck at the black screen on boot, no xfce. Can't even ctrl-alt-F3. So now the siliconmotion tablt stays black like the Intel tablet. Also still no second LCD display screen past Grub boot screen.

The xorg.log now says it is failing at: screens found, but none have a usable configuration. Fatal server error, no screens found.

---

### Post by 1branchonthevine on 2013-03-25
Sorry, I want to clarify what happens with my current configuration (Dual monitor setup with original Walkabout tablet LCD, and Dell LCD on aux VGA port)...

Original fresh install on siliconmotion video chipset walkabout tablet: both screens see bios and grub, then both go black until xfce loads. Once xfce loads, tablet has display running xfce, but aux LCD is black.

Original fresh install on Intel video chipset walkabout tablet: both screens see bios and grub, then both stay black until xfce loads. Once xfce loads, tablet display stays black, and aux LCD displays xfce.

Siliconmotion system seems to fall back to vesa and basic frame buffer driver, since scrolling is very jerky.  System will not tolerate xorg.conf changes. Otherwise faults at screen detection.

Intel system seems to hold Intel driver, but fails to detect tablet screen. Sees Dell screen though.

Like I said earlier, the latest version of ubuntu (since 9.04), no longer seems to be able to detect screens/displays properly. And for some reason, the siliconmotion driver gets dumped for vesa as if the driver is bad (it does fail at loading some default driver setting). But since both chipsets seem to have issues detecting screens, I'm thinking this is a bug with the latest version of ubuntu.

---

### Post by Yellow Pasque on 2013-03-25
> Siliconmotion system seems to fall back to vesa and basic frame buffer driver, since scrolling is very jerky.
It's not falling back to VESA per se. The siliconmotion/SMI driver is still being used, but it's not giving you any benefit over VESA driver, since the Xorg log indicates that 2D accel is disabled. Even though you explicitly specified the newer EXA 2D acceleration, it's still trying to use the old XAA 2D acceleration, which was stripped out of Xserver 1.13 (Ubuntu 12.10 uses X 1.13): [http://www.phoronix.com/scan.php?page=news_item&px=MTA0NDg](http://www.phoronix.com/scan.php?page=news_item&px=MTA0NDg)

It wouldn't surprise me if EXA was broken for the SMI driver.

---

### Post by 1branchonthevine on 2013-03-25
Great read BTW! 

> [COLOR=#000000]Even though you explicitly specified the newer EXA 2D acceleration, it's still trying to use the old XAA 2D acceleration[/COLOR]

When I specify EXA in the xorg.conf file, I don't see in the log where it is instead loading XAA mode? Actually I don't even see it loading EXA at all... maybe I should run the custom xorg.conf again and see if I printed the wrong log. But yes, I do know that when I am not using a custom xorg.conf, the system does attempt to load XAA, and then fails. What would be calling it to load XAA anyhow? I know this was the default mode, but shouldn't the latest siliconmotion.so be compiled with EXA as default now? I think I even checked the SMI changelog from [http://cgit.freedesktop.org/xorg/driver/xf86-video-siliconmotion/](http://cgit.freedesktop.org/xorg/driver/xf86-video-siliconmotion/) to see if XAA was not set as default anymore, but maybe I assumed "[smi: fix build against XAA-less server]("http://cgit.freedesktop.org/xorg/driver/xf86-video-siliconmotion/commit/?id=891ea02395079b1480faf701156185ad01405e6d") and [Make failure to XAA non-fatal]("http://cgit.freedesktop.org/xorg/driver/xf86-video-siliconmotion/commit/?id=208a703776d6dfbd01babbe2f220a7198dea4f5c") was a patch to force EXA... Guessing not. 

So, with that said, where should I start? Should I see if it is possible to recompile the driver without any XAA, or set EXA as default? Or should I keep playing with my xorg.conf file? Or, something else?

Lastly, assuming I can get acceleration working, this works great for fixing 9 of the tablets using the SMI chipset, but this doesn't resolve the issue with failing to detect the aux monitor. Nor does this answer why the Intel chipset tablet also has monitor detection issues too. What is the system checking for and hoping to find when it fails to find usable screens? I know they work, I can even xrandr them, but something is not getting through.

My biggest concern is getting all the tablet LCD screens loading and accelerated, I can do without dual monitor.

Thanks a bunch!

---

### Post by Yellow Pasque on 2013-03-29
Sorry for delayed response (been busy).
> When I specify EXA in the xorg.conf file, I don't see in the log where it is instead loading XAA mode?
I was a bit confused and was looking at the "no xorg.conf" log.

> Or should I keep playing with my xorg.conf file?
I would do that. Start with a simple skeleton:
```
Section "Device"
        Identifier      "Configured Video Device"
	Driver          "siliconmotion"
        Option         "AccelMethod" "EXA"
#      Option         "DualHead" "true"
#      Option         "PanelSize" "800x600"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```
After trying that, look in at the Xorg log and see if it enables EXA (post/paste it here it if you want). As for the auxiliary screen detection, you might want to play with the two options that are commented out in the above example.

---

### Post by 1branchonthevine on 2013-04-02
It took a while to get back to these, but it looks like tinkering with the xorg.conf file helped. I must have posted the wrong log, because I was able to eventually force EXA acceleration, but unfortunately the SMI driver acceleration had random artifacts distorting the screen from time to time. Acceleration was much better, but artifacts are unacceptable, just have to deal with out acceleration.

Here is a working SMI xorg.conf file. I was able to get the LCD to be detected by adding xrandr modlines, although this did not work for the Intel machine. I was unable to get dualhead working, I think it is becuase I read somewhere that their is a 16bit color depth limit, and my monitor section was defaulting to 24, so this wasn't worth it to me to have dualhead. The file could definitely be cleaned up a bit, but this seemed to work:

```
Section "ServerLayout"	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
	Screen      2  "Screen2" RightOf "Screen1"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection


Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
#	FontPath     "/usr/share/fonts/X11/misc"
#	FontPath     "/usr/share/fonts/X11/cyrillic"
#	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
#	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
#	FontPath     "/usr/share/fonts/X11/Type1"
#	FontPath     "/usr/share/fonts/X11/100dpi"
#	FontPath     "/usr/share/fonts/X11/75dpi"
#	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
#	FontPath     "built-ins"
EndSection


#Section "Module"
#	Load  "glx"
#EndSection


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
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
	 #800x600 @ 60.30 Hz (GTF) hsync: 37.51 kHz; pclk: 38.41 MHz
	Modeline "800x600_60.30"  38.41  800 832 912 1024  600 601 604 622  -HSync +Vsync
	 #800x600 60.25 Hz (CVT) hsync: 37.60 kHz; pclk: 38.50 MHz
	Modeline "800x600_60.30"   38.50  800 832 912 1024  600 603 607 624 -hsync +vsync
	 #800x600 @ 59.90 Hz (GTF) hsync: 37.20 kHz; pclk: 38.09 MHz
	Modeline "800x600_59.90"  38.09  800 832 912 1024  600 601 604 621  -HSync +Vsync
	 #800x600 59.47 Hz (CVT) hsync: 37.11 kHz; pclk: 38.00 MHz
	Modeline "800x600_59.90"   38.00  800 832 912 1024  600 603 607 624 -hsync +vsync
	 #800x600 59.86 Hz (CVT 0.48M3) hsync: 37.35 kHz; pclk: 38.25 MHz
	Modeline "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync
	 #800x600 @ 60.00 Hz (GTF) hsync: 37.32 kHz; pclk: 38.22 MHz
	Modeline "800x600_60.00"  38.22  800 832 912 1024  600 601 604 622  -HSync +Vsync
	 #From Website:http://ubuntuforums.org/showthread.php?t=1162348
	modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
	Gamma	1.0
#	Option "DPMS" "true"
	Option "DPMS" "false"
EndSection


Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection


Section "Monitor"
	Identifier   "Monitor2"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection


Section "Device"
	Identifier	"Card0"
	Boardname	"Silicon Motion LynxEM+ (generic)"
	Busid		"PCI:2:5:0"
	Driver		"siliconmotion"
#	Screen		"Screen0"
	Vendorname	"Silicon Motion"


#	Option "VideoKey" "integer"
#Set the video color key.  Default: a little off full blue.


#	Option "ByteSwap" "boolean"
#Turn on byte swapping for capturing using SMI demo board.  Default: off.


#	Option "Interlaced" "boolean"
#Turn on interlaced video capturing.  Default: off.


#	Option "UseBIOS" "on"
#Use the BIOS to set the modes. This is  used  for  custom  panel
#timings. Default: off for SM72x and SM5xx, otherwise on.


#	Option "Dualhead" "on"
#Enable dualhead mode.  Currently not all chips are supported and
#hardware video overlay (XV) support may have  some  limitations.
#Default: off.


#	Option "PanelSize" "800x600"
#Override LCD panel dimension autodetection.


#	Option "UseFBDev" "boolean"
#Don't actually program the hardware mode registers, but leave it as set by
#the operating system. Only available on MSOC chips. Default: off.


#	Option "CSCVideo" "boolean"
#CSC video uses color space  conversion  to  render  video  directly  to  the
#framebuffer,  without  using  an  overlay.   Only  available  on MSOC chips.
#Default: on.


#	Option "mclk" "integer"
#Sets the memory clock. You must specify the units.  For example 50Mhz is the
#same as 50000Khz or 50000000Hz.  On MSOC chips this is the main clock source
#for all functional blocks, such as the 2D engine, GPIO,  Video  Engine,  and
#DMA  Engine.  This option is only used for debugging purposes on MSOC chips.
#Default: probe the memory clock value, and use it at server start.


#	Option "mxclk" "integer"
#Sets the memory clock. You must specify the units.  For example 50Mhz is the
#same   as  50000Khz  or  50000000Hz.   Clock  source  for  the  local  SDRAM
#controller. This option is only available on MSOC chips and  used  only  for
#debugging  purposes.   Default:  probe the memory clock value, and use it at
#server start.
	 
#	Option "NoAccel"
#Disable acceleration.  Very useful for determining if the driver
#has  problems  with  drawing and acceleration routines.  This is
#the first option to try if your server runs but you see  graphic
#corruption on the screen.  Using it decreases performance, as it
#uses software emulation for drawing operations the video  driver
#can accelerate with hardware.  Default: acceleration is enabled.


	Option "AccelMethod" "EXA"
#Chooses between available acceleration architectures. Valid options are 
#XAA and EXA. XAA is the traditional acceleration architecture and support
#for it is very stable. EXA is a newer acceleration architecture with 
#better performance for the Render and Composite extensions, but the 
#rendering code for it is newer and possibly unstable. The default is XAA.


	Option "PciBurst" "on"
#will  enable  PCI  burst  mode. This should work on all but a few broken PCI
#chipsets, and will increase performance.  Default: on.


	Option "PciRetry" "on"
#will allow the driver to  rely  on  PCI  Retry  to  program  the  registers.
#PciBurst  must be enabled for this to work.  This will increase performance,
#especially for small fills/blits, because the driver does not have  to  poll
#the card before sending it commands to make sure it is ready. It should work
#on most recent PCI chipsets.  Default: value of PciBurst option.


EndSection


#Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"           	# [<bool>]
        #Option     "kmsdev"             	# <str>
        #Option     "ShadowFB"           	# [<bool>]
	#Identifier  "Card0"
	#Driver      "modesetting"
	#BusID       "PCI:2:5:0"
#EndSection


#Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "Rotate"             	# <str>
        #Option     "fbdev"              	# <str>
        #Option     "debug"              	# [<bool>]
	#Identifier  "Card1"
	#Driver      "fbdev"
	#BusID       "PCI:2:5:0"
#EndSection


#Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "DefaultRefresh"     	# [<bool>]
        #Option     "ModeSetClearScreen" 	# [<bool>]
	#Identifier  "Card2"
	#Driver      "vesa"
	#BusID       "PCI:2:5:0"
#EndSection


Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	Defaultdepth	24
	SubSection "Display"
		Viewport   0 0
		Depth	24
		Virtual	800	600
		Modes	"800x600@60"
		Modes	"800x600@60.30"
		Modes   "800x600@59.90"
	EndSubSection
EndSection


Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
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


Section "Screen"
	Identifier "Screen2"
	Device     "Card2"
	Monitor    "Monitor2"
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


I think this is the correct xorg log:

```
[    39.985] X.Org X Server 1.13.0
Release Date: 2012-09-05
[    39.985] X Protocol Version 11, Revision 0
[    39.985] Build Operating System: Linux 3.2.0-26-generic i686 Ubuntu
[    39.986] Current Operating System: Linux ychurch9 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:32:08 UTC 2012 i686
[    39.986] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-17-generic root=UUID=0bbcc6af-eb75-4483-bc0f-6881e364330f ro quiet vt.handoff=7
[    39.986] Build Date: 08 October 2012  03:34:08PM
[    39.986] xorg-server 2:1.13.0-0ubuntu6 (For technical support please see http://www.ubuntu.com/support) 
[    39.986] Current version of pixman: 0.26.0
[    39.986] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    39.986] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    39.987] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Mar 27 13:44:54 2013
[    39.987] (==) Using config file: "/etc/X11/xorg.conf"
[    39.987] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    40.030] (==) ServerLayout "X.org Configured"
[    40.030] (**) |-->Screen "Screen0" (0)
[    40.030] (**) |   |-->Monitor "Monitor0"
[    40.031] (**) |   |-->Device "Card0"
[    40.031] (**) |-->Screen "Screen1" (1)
[    40.031] (**) |   |-->Monitor "Monitor1"
[    40.032] (==) No device specified for screen "Screen1".
	Using the first device section listed.
[    40.032] (**) |   |-->Device "Card0"
[    40.032] (**) |-->Screen "Screen2" (2)
[    40.032] (**) |   |-->Monitor "Monitor2"
[    40.033] (==) No device specified for screen "Screen2".
	Using the first device section listed.
[    40.033] (**) |   |-->Device "Card0"
[    40.033] (**) |-->Input Device "Mouse0"
[    40.033] (**) |-->Input Device "Keyboard0"
[    40.033] (==) Automatically adding devices
[    40.033] (==) Automatically enabling devices
[    40.033] (==) Automatically adding GPU devices
[    40.033] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    40.033] 	Entry deleted from font path.
[    40.033] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    40.033] 	Entry deleted from font path.
[    40.033] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    40.033] 	Entry deleted from font path.
[    40.033] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    40.034] 	Entry deleted from font path.
[    40.034] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    40.034] 	Entry deleted from font path.
[    40.034] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    40.034] 	Entry deleted from font path.
[    40.034] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    40.034] 	Entry deleted from font path.
[    40.034] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    40.034] 	Entry deleted from font path.
[    40.034] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    40.034] 	Entry deleted from font path.
[    40.034] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    40.034] 	Entry deleted from font path.
[    40.034] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    40.034] 	Entry deleted from font path.
[    40.034] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    40.034] 	Entry deleted from font path.
[    40.034] (**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    40.034] (**) ModulePath set to "/usr/lib/xorg/modules"
[    40.034] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    40.034] (WW) Disabling Mouse0
[    40.034] (WW) Disabling Keyboard0
[    40.034] (II) Loader magic: 0xb7742640
[    40.034] (II) Module ABI versions:
[    40.034] 	X.Org ANSI C Emulation: 0.4
[    40.034] 	X.Org Video Driver: 13.0
[    40.035] 	X.Org XInput driver : 18.0
[    40.035] 	X.Org Server Extension : 7.0
[    40.047] (--) PCI:*(0:2:5:0) 126f:0712:126f:0712 rev 160, Mem @ 0xd1000000/16777216
[    40.047] (II) Open ACPI successful (/var/run/acpid.socket)
[    40.047] Initializing built-in extension Generic Event Extension
[    40.047] Initializing built-in extension SHAPE
[    40.047] Initializing built-in extension MIT-SHM
[    40.047] Initializing built-in extension XInputExtension
[    40.047] Initializing built-in extension XTEST
[    40.047] Initializing built-in extension BIG-REQUESTS
[    40.048] Initializing built-in extension SYNC
[    40.048] Initializing built-in extension XKEYBOARD
[    40.048] Initializing built-in extension XC-MISC
[    40.048] Initializing built-in extension SECURITY
[    40.048] Initializing built-in extension XINERAMA
[    40.048] Initializing built-in extension XFIXES
[    40.048] Initializing built-in extension RENDER
[    40.048] Initializing built-in extension RANDR
[    40.048] Initializing built-in extension COMPOSITE
[    40.048] Initializing built-in extension DAMAGE
[    40.048] Initializing built-in extension MIT-SCREEN-SAVER
[    40.048] Initializing built-in extension DOUBLE-BUFFER
[    40.048] Initializing built-in extension RECORD
[    40.048] Initializing built-in extension DPMS
[    40.048] Initializing built-in extension X-Resource
[    40.048] Initializing built-in extension XVideo
[    40.048] Initializing built-in extension XVideo-MotionCompensation
[    40.048] Initializing built-in extension XFree86-VidModeExtension
[    40.048] Initializing built-in extension XFree86-DGA
[    40.048] Initializing built-in extension XFree86-DRI
[    40.049] Initializing built-in extension DRI2
[    40.049] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    40.049] (II) LoadModule: "glx"
[    40.049] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    40.050] (II) Module glx: vendor="X.Org Foundation"
[    40.050] 	compiled for 1.13.0, module version = 1.0.0
[    40.050] 	ABI class: X.Org Server Extension, version 7.0
[    40.050] (==) AIGLX enabled
[    40.050] Loading extension GLX
[    40.050] (II) LoadModule: "siliconmotion"
[    40.051] (II) Loading /usr/lib/xorg/modules/drivers/siliconmotion_drv.so
[    40.051] (II) Module siliconmotion: vendor="X.Org Foundation"
[    40.051] 	compiled for 1.12.99.902, module version = 1.7.7
[    40.051] 	Module class: X.Org Video Driver
[    40.051] 	ABI class: X.Org Video Driver, version 13.0
[    40.051] (II) SMI: driver (version 1.7.7) for Silicon Motion Lynx chipsets: Lynx,
	LynxE, Lynx3D, LynxEM, LynxEM+, Lynx3DM, Cougar3DR, MSOC
[    40.051] (++) using VT number 8


[    40.133] (WW) Falling back to old probe method for siliconmotion
[    40.133] (WW) SMI: More than one matching Device section for instances
	(BusID: PCI:2:5:0) found: Card0
[    40.133] (WW) SMI: More than one matching Device section for instances
	(BusID: PCI:2:5:0) found: Card0
[    40.133] (--) Chipset LynxEM+ found
[    40.134] (II) Loading sub module "vgahw"
[    40.134] (II) LoadModule: "vgahw"
[    40.166] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    40.166] (II) Module vgahw: vendor="X.Org Foundation"
[    40.166] 	compiled for 1.13.0, module version = 0.1.0
[    40.166] 	ABI class: X.Org Video Driver, version 13.0
[    40.166] (**) SMI(0): Depth 24, (--) framebuffer bpp 32
[    40.167] (==) SMI(0): RGB weight 888
[    40.167] (==) SMI(0): Default visual is TrueColor
[    40.167] (**) SMI(0): Option "pci_burst" "on"
[    40.167] (**) SMI(0): Option "pci_retry" "on"
[    40.167] (**) SMI(0): Option "UseBIOS" "on"
[    40.167] (**) SMI(0): Option "AccelMethod" "EXA"
[    40.167] (**) SMI(0): Option "PanelSize" "800x600"
[    40.167] (**) SMI(0): PCI Burst enabled
[    40.167] (**) SMI(0): PCI Retry enabled
[    40.167] (==) SMI(0): Using Hardware Cursor
[    40.167] (**) SMI(0): Option: UseBIOS enabled.
[    40.167] (II) Loading sub module "int10"
[    40.167] (II) LoadModule: "int10"
[    40.167] (II) Loading /usr/lib/xorg/modules/libint10.so
[    40.168] (II) Module int10: vendor="X.Org Foundation"
[    40.168] 	compiled for 1.13.0, module version = 1.0.0
[    40.168] 	ABI class: X.Org Video Driver, version 13.0
[    40.171] (II) SMI(0): Primary V_BIOS segment is: 0xc000
[    40.171] (II) Loading sub module "vbe"
[    40.171] (II) LoadModule: "vbe"
[    40.176] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    40.177] (II) Module vbe: vendor="X.Org Foundation"
[    40.177] 	compiled for 1.13.0, module version = 1.1.0
[    40.177] 	ABI class: X.Org Video Driver, version 13.0
[    41.222] (II) SMI(0): VESA BIOS not detected
[    41.222] (WW) SMI(0): VBE initialization failed: falling back to UseBIOS disabled.
[    41.222] (--) SMI(0): Chipset: "LynxEM+"
[    41.222] (==) SMI(0): Dual head disabled
[    41.222] (**) SMI(0): Using EXA acceleration architecture
[    41.223] (--) SMI(0): videoram: 4096kB
[    41.224] (II) SMI(0): Cursor Offset: 003FFC00
[    41.224] (II) SMI(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0
[    41.224] (II) SMI(0): Reserved: 003FF800
[    41.224] (II) SMI(0): OFF Panel Size = 800x600
[    41.224] (II) Loading sub module "i2c"
[    41.224] (II) LoadModule: "i2c"
[    41.224] (II) Module "i2c" already built-in
[    41.224] (II) SMI(0): I2C bus "I2C bus" initialized.
[    41.225] (II) Loading sub module "ddc"
[    41.225] (II) LoadModule: "ddc"
[    41.225] (II) Module "ddc" already built-in
[    41.225] (**) SMI(0): Using gamma correction (1.0, 1.0, 1.0)
[    41.225] (II) SMI(0): MCLK = 157.000
[    41.225] (II) SMI(0): Output LVDS using monitor section Monitor0
[    41.225] (II) SMI(0): Printing probed modes for output LVDS
[    41.225] (II) SMI(0): Modeline "800x600@60"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz UP)
[    41.225] (II) SMI(0): Modeline "800x600_60.30"x60.3   38.50  800 832 912 1024  600 603 607 624 -hsync +vsync (37.6 kHz)
[    41.225] (II) SMI(0): Modeline "800x600_60.30"x60.3   38.41  800 832 912 1024  600 601 604 622 -hsync +vsync (37.5 kHz)
[    41.225] (II) SMI(0): Modeline "800x600_60.00"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    41.225] (II) SMI(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    41.225] (II) SMI(0): Modeline "800x600_60.00"x60.0   38.22  800 832 912 1024  600 601 604 622 -hsync +vsync (37.3 kHz)
[    41.225] (II) SMI(0): Modeline "800x600_59.90"x59.9   38.09  800 832 912 1024  600 601 604 621 -hsync +vsync (37.2 kHz)
[    41.225] (II) SMI(0): Modeline "800x600_59.90"x59.5   38.00  800 832 912 1024  600 603 607 624 -hsync +vsync (37.1 kHz)
[    41.225] (II) SMI(0): Output LVDS connected
[    41.225] (II) SMI(0): Using user preference for initial modes
[    41.225] (II) SMI(0): Output LVDS using initial mode 800x600@60
[    41.226] (II) SMI(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    41.226] (==) SMI(0): DPI set to (96, 96)
[    41.226] (II) Loading sub module "fb"
[    41.226] (II) LoadModule: "fb"
[    41.227] (II) Loading /usr/lib/xorg/modules/libfb.so
[    41.227] (II) Module fb: vendor="X.Org Foundation"
[    41.227] 	compiled for 1.13.0, module version = 1.0.0
[    41.227] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    41.227] (II) Loading sub module "exa"
[    41.227] (II) LoadModule: "exa"
[    41.228] (II) Loading /usr/lib/xorg/modules/libexa.so
[    41.253] (II) Module exa: vendor="X.Org Foundation"
[    41.253] 	compiled for 1.13.0, module version = 2.6.0
[    41.253] 	ABI class: X.Org Video Driver, version 13.0
[    41.253] (II) Loading sub module "ramdac"
[    41.253] (II) LoadModule: "ramdac"
[    41.253] (II) Module "ramdac" already built-in
[    41.253] (--) Depth 24 pixmap format is 32 bpp
[    41.254] (II) SMI(0): Cursor Offset: 003FFC00
[    41.254] (II) SMI(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0
[    41.254] (II) SMI(0): Reserved: 003FF800
[    41.639] (II) SMI(0): EXA offscreen memory manager enabled.
[    41.639] (II) EXA(0): Offscreen pixmap area of 4192256 bytes
[    41.639] (II) EXA(0): Driver registered support for the following operations:
[    41.639] (II)         Solid
[    41.639] (II)         Copy
[    41.639] (II)         Composite (RENDER acceleration)
[    41.639] (II) SMI(0): EXA Acceleration enabled.
[    41.672] (II) SMI(0): I2C device "I2C bus:SAA 7111A" registered at address 0x48.
[    41.672] (II) SMI(0): I2C device "I2C bus:SAA 7111A" removed.
[    41.672] (II) SMI(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    41.672] (WW) SMI(0): Option "fifo_aggressive" is not used
[    41.673] (--) RandR disabled
[    41.707] (II) AIGLX: Screen 0 is not DRI2 capable
[    41.707] (II) AIGLX: Screen 0 is not DRI capable
[    41.743] (II) AIGLX: Loaded and initialized swrast
[    41.743] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    41.745] (II) SMI(0): Setting screen physical size to 211 x 158
[    41.833] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    41.844] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    41.845] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    41.845] (II) LoadModule: "evdev"
[    41.846] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    41.846] (II) Module evdev: vendor="X.Org Foundation"
[    41.846] 	compiled for 1.13.0, module version = 2.7.3
[    41.846] 	Module class: X.Org XInput Driver
[    41.846] 	ABI class: X.Org XInput driver, version 18.0
[    41.846] (II) Using input driver 'evdev' for 'Power Button'
[    41.846] (**) Power Button: always reports core events
[    41.846] (**) evdev: Power Button: Device: "/dev/input/event0"
[    41.847] (--) evdev: Power Button: Vendor 0 Product 0x1
[    41.847] (--) evdev: Power Button: Found keys
[    41.847] (II) evdev: Power Button: Configuring as keyboard
[    41.847] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input0/event0"
[    41.847] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    41.847] (**) Option "xkb_rules" "evdev"
[    41.847] (**) Option "xkb_model" "pc105"
[    41.847] (**) Option "xkb_layout" "us"
[    41.851] (II) config/udev: Adding input device Multi-Input Device (/dev/input/event2)
[    41.851] (**) Multi-Input Device: Applying InputClass "evdev keyboard catchall"
[    41.851] (II) Using input driver 'evdev' for 'Multi-Input Device'
[    41.851] (**) Multi-Input Device: always reports core events
[    41.852] (**) evdev: Multi-Input Device: Device: "/dev/input/event2"
[    41.852] (--) evdev: Multi-Input Device: Vendor 0x518 Product 0x8
[    41.852] (--) evdev: Multi-Input Device: Found keys
[    41.852] (II) evdev: Multi-Input Device: Configuring as keyboard
[    41.852] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input2/event2"
[    41.852] (II) XINPUT: Adding extended input device "Multi-Input Device" (type: KEYBOARD, id 7)
[    41.852] (**) Option "xkb_rules" "evdev"
[    41.852] (**) Option "xkb_model" "pc105"
[    41.852] (**) Option "xkb_layout" "us"
[    41.855] (II) config/udev: Adding input device Multi-Input Device (/dev/input/event3)
[    41.855] (**) Multi-Input Device: Applying InputClass "evdev pointer catchall"
[    41.855] (**) Multi-Input Device: Applying InputClass "evdev keyboard catchall"
[    41.855] (II) Using input driver 'evdev' for 'Multi-Input Device'
[    41.855] (**) Multi-Input Device: always reports core events
[    41.855] (**) evdev: Multi-Input Device: Device: "/dev/input/event3"
[    41.855] (--) evdev: Multi-Input Device: Vendor 0x518 Product 0x8
[    41.855] (--) evdev: Multi-Input Device: Found 3 mouse buttons
[    41.855] (--) evdev: Multi-Input Device: Found scroll wheel(s)
[    41.855] (--) evdev: Multi-Input Device: Found relative axes
[    41.855] (--) evdev: Multi-Input Device: Found x and y relative axes
[    41.855] (--) evdev: Multi-Input Device: Found absolute axes
[    41.855] (II) evdev: Multi-Input Device: Forcing absolute x/y axes to exist.
[    41.855] (--) evdev: Multi-Input Device: Found keys
[    41.855] (II) evdev: Multi-Input Device: Configuring as mouse
[    41.856] (II) evdev: Multi-Input Device: Configuring as keyboard
[    41.856] (II) evdev: Multi-Input Device: Adding scrollwheel support
[    41.856] (**) evdev: Multi-Input Device: YAxisMapping: buttons 4 and 5
[    41.856] (**) evdev: Multi-Input Device: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    41.856] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.1/input/input3/event3"
[    41.856] (II) XINPUT: Adding extended input device "Multi-Input Device" (type: KEYBOARD, id 8)
[    41.856] (**) Option "xkb_rules" "evdev"
[    41.856] (**) Option "xkb_model" "pc105"
[    41.856] (**) Option "xkb_layout" "us"
[    41.857] (II) evdev: Multi-Input Device: initialized for relative axes.
[    41.857] (WW) evdev: Multi-Input Device: ignoring absolute axes.
[    41.857] (**) Multi-Input Device: (accel) keeping acceleration scheme 1
[    41.858] (**) Multi-Input Device: (accel) acceleration profile 0
[    41.858] (**) Multi-Input Device: (accel) acceleration factor: 2.000
[    41.858] (**) Multi-Input Device: (accel) acceleration threshold: 4
[    41.859] (II) config/udev: Adding input device Multi-Input Device (/dev/input/mouse0)
[    41.859] (II) No input driver specified, ignoring this device.
[    41.859] (II) This device may have been added with another device file.
[    41.860] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event1)
[    41.860] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    41.860] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    41.860] (**) AT Translated Set 2 keyboard: always reports core events
[    41.860] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event1"
[    41.860] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    41.860] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    41.860] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    41.860] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input1/event1"
[    41.860] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    41.860] (**) Option "xkb_rules" "evdev"
[    41.860] (**) Option "xkb_model" "pc105"
[    41.861] (**) Option "xkb_layout" "us"
[    41.868] (II) config/udev: Adding input device Serial Wacom Tablet (/dev/ttyS3)
[    41.868] (**) Serial Wacom Tablet: Applying InputClass "Wacom serial class"
[    41.868] (II) LoadModule: "wacom"
[    41.869] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    41.870] (II) Module wacom: vendor="X.Org Foundation"
[    41.870] 	compiled for 1.13.0, module version = 0.17.0
[    41.870] 	Module class: X.Org XInput Driver
[    41.870] 	ABI class: X.Org XInput driver, version 18.0
[    41.870] (II) Using input driver 'wacom' for 'Serial Wacom Tablet'
[    41.870] (**) Serial Wacom Tablet: always reports core events
[    41.870] (**) Option "Device" "/dev/ttyS3"
[    41.870] (**) Option "StopBits" "1"
[    41.870] (**) Option "DataBits" "8"
[    41.870] (**) Option "Parity" "None"
[    41.871] (**) Option "Vmin" "1"
[    41.871] (**) Option "Vtime" "10"
[    41.871] (**) Option "FlowControl" "Xoff"
[    41.871] (II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
[    41.871] (II) Serial Wacom Tablet: other types will be automatically added.
[    42.150] (II) Serial Wacom Tablet stylus: serial tablet id 0x90.
[    42.150] (--) Serial Wacom Tablet stylus: using pressure threshold of 27 for button 1
[    42.150] (--) Serial Wacom Tablet stylus: Wacom General ISDV4 tablet maxX=21200 maxY=15900 maxZ=255 resX=100000 resY=100000  tilt=disabled
[    42.150] (II) Serial Wacom Tablet stylus: hotplugging dependent devices.
[    42.150] (EE) Serial Wacom Tablet stylus: Invalid type 'cursor' for this device.
[    42.150] (EE) Serial Wacom Tablet stylus: Invalid type 'touch' for this device.
[    42.150] (EE) Serial Wacom Tablet stylus: Invalid type 'pad' for this device.
[    42.151] (II) Serial Wacom Tablet stylus: hotplugging completed.
[    42.151] (**) Option "config_info" "udev:/sys/devices/pnp0/00:0a/tty/ttyS3"
[    42.151] (II) XINPUT: Adding extended input device "Serial Wacom Tablet stylus" (type: STYLUS, id 10)
[    42.152] (**) Serial Wacom Tablet stylus: (accel) keeping acceleration scheme 1
[    42.152] (**) Serial Wacom Tablet stylus: (accel) acceleration profile 0
[    42.153] (**) Serial Wacom Tablet stylus: (accel) acceleration factor: 2.000
[    42.153] (**) Serial Wacom Tablet stylus: (accel) acceleration threshold: 4
[    42.153] (**) Option "BaudRate" "19200"
[    42.169] (**) Serial Wacom Tablet eraser: Applying InputClass "Wacom serial class"
[    42.169] (II) Using input driver 'wacom' for 'Serial Wacom Tablet eraser'
[    42.169] (**) Serial Wacom Tablet eraser: always reports core events
[    42.169] (**) Option "Device" "/dev/ttyS3"
[    42.169] (**) Option "Type" "eraser"
[    42.169] (**) Option "BaudRate" "19200"
[    42.169] (**) Option "StopBits" "1"
[    42.170] (**) Option "DataBits" "8"
[    42.170] (**) Option "Parity" "None"
[    42.170] (**) Option "Vmin" "1"
[    42.170] (**) Option "Vtime" "10"
[    42.170] (**) Option "FlowControl" "Xoff"
[    42.170] (--) Serial Wacom Tablet eraser: Wacom General ISDV4 tablet maxX=21200 maxY=15900 maxZ=255 resX=100000 resY=100000  tilt=disabled
[    42.170] (**) Option "config_info" "udev:/sys/devices/pnp0/00:0a/tty/ttyS3"
[    42.170] (II) XINPUT: Adding extended input device "Serial Wacom Tablet eraser" (type: ERASER, id 11)
[    42.172] (**) Serial Wacom Tablet eraser: (accel) keeping acceleration scheme 1
[    42.172] (**) Serial Wacom Tablet eraser: (accel) acceleration profile 0
[    42.172] (**) Serial Wacom Tablet eraser: (accel) acceleration factor: 2.000
[    42.172] (**) Serial Wacom Tablet eraser: (accel) acceleration threshold: 4
[    43.988] (II) XKB: reuse xkmfile /var/lib/xkb/server-8AA988DD479FAABEC4FC3CCCF4CC29B4948840B4.xkm
```


Like I said earlier, I was unable to get the Intel chipset to detect the screens even when I defined xrandr modlines, so something is all wacked out there... Oh, and apparently card1 is the connection for the LVDS LCD, and card0 is the VGA aux for this system.

Intel xorg.conf

```
Section "ServerLayout"	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
	Screen      2  "Screen2" RightOf "Screen1"
	Screen      3  "Screen3" RightOf "Screen2"
	Screen      4  "Screen4" RightOf "Screen3"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection


Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection


Section "Module"
	Load  "glx"
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
	Horizsync    31.5-48.0
	Vertrefresh  56.0 - 65.0
	Modeline "800x600_60.00"  38.22  800 832 912 1024  600 601 604 622  -HSync +Vsync
	Modeline "800x600_60.00"  38.25  800 832 912 1024  600 603 607 624  -hsync +vsync
	Modeline "800x600_59.90"  38.09  800 832 912 1024  600 601 604 621  -HSync +Vsync
	Modeline "800x600_59.90"  38.00  800 832 912 1024  600 603 607 624  -hsync +vsync
	Modeline "800x600_60.30"  38.41  800 832 912 1024  600 601 604 622  -HSync +Vsync
	Modeline "800x600_60.30"  38.50  800 832 912 1024  600 603 607 624  -hsync +vsync
	Gamma	1.0
	Option "DPMS" "false"
EndSection


Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
	Horizsync    31.5-48.0
	Vertrefresh  56.0 - 65.0
	Modeline "800x600_60.00"  38.22  800 832 912 1024  600 601 604 622  -HSync +Vsync
	Modeline "800x600_60.00"  38.25  800 832 912 1024  600 603 607 624  -hsync +vsync
	Modeline "800x600_59.90"  38.09  800 832 912 1024  600 601 604 621  -HSync +Vsync
	Modeline "800x600_59.90"  38.00  800 832 912 1024  600 603 607 624  -hsync +vsync
	Modeline "800x600_60.30"  38.41  800 832 912 1024  600 601 604 622  -HSync +Vsync
	Modeline "800x600_60.30"  38.50  800 832 912 1024  600 603 607 624  -hsync +vsync
	Gamma	1.0
	Option "DPMS" "false"
EndSection


#Section "Monitor"
#	Identifier   "Monitor2"
#	VendorName   "Monitor Vendor"
#	ModelName    "Monitor Model"
#	Horizsync    31.5-48.0
#	Vertrefresh  56.0 - 65.0
#	Modeline "800x600_60.00"  38.22  800 832 912 1024  600 601 604 622  -HSync +Vsync
#	Modeline "800x600_60.00"  38.25  800 832 912 1024  600 603 607 624  -hsync +vsync
#	Modeline "800x600_59.90"  38.09  800 832 912 1024  600 601 604 621  -HSync +Vsync
#	Modeline "800x600_59.90"  38.00  800 832 912 1024  600 603 607 624  -hsync +vsync
#	Modeline "800x600_60.30"  38.41  800 832 912 1024  600 601 604 622  -HSync +Vsync
#	Modeline "800x600_60.30"  38.50  800 832 912 1024  600 603 607 624  -hsync +vsync
#	Gamma	1.0
#	Option "DPMS" "false"
#EndSection


#Section "Monitor"
#	Identifier   "Monitor3"
#	VendorName   "Monitor Vendor"
#	ModelName    "Monitor Model"
#	Horizsync    31.5-48.0
#	Vertrefresh  56.0 - 65.0
#	Modeline "800x600_60.00"  38.22  800 832 912 1024  600 601 604 622  -HSync +Vsync
#	Modeline "800x600_60.00"  38.25  800 832 912 1024  600 603 607 624  -hsync +vsync
#	Modeline "800x600_59.90"  38.09  800 832 912 1024  600 601 604 621  -HSync +Vsync
#	Modeline "800x600_59.90"  38.00  800 832 912 1024  600 603 607 624  -hsync +vsync
#	Modeline "800x600_60.30"  38.41  800 832 912 1024  600 601 604 622  -HSync +Vsync
#	Modeline "800x600_60.30"  38.50  800 832 912 1024  600 603 607 624  -hsync +vsync
#	Gamma	1.0
#	Option "DPMS" "false"
#EndSection


#Section "Monitor"
#	Identifier   "Monitor4"
#	VendorName   "Monitor Vendor"
#	ModelName    "Monitor Model"
#	Horizsync    31.5-48.0
#	Vertrefresh  56.0 - 65.0
#	Modeline "800x600_60.00"  38.22  800 832 912 1024  600 601 604 622  -HSync +Vsync
#	Modeline "800x600_60.00"  38.25  800 832 912 1024  600 603 607 624  -hsync +vsync
#	Modeline "800x600_59.90"  38.09  800 832 912 1024  600 601 604 621  -HSync +Vsync
#	Modeline "800x600_59.90"  38.00  800 832 912 1024  600 603 607 624  -hsync +vsync
#	Modeline "800x600_60.30"  38.41  800 832 912 1024  600 601 604 622  -HSync +Vsync
#	Modeline "800x600_60.30"  38.50  800 832 912 1024  600 603 607 624  -hsync +vsync
#	Gamma	1.0
#	Option "DPMS" "false"
#EndSection


Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "AccelMethod"        	# <str>
        #Option     "Backlight"          	# <str>
        #Option     "DRI"                	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "VideoKey"           	# <i>
        #Option     "Tiling"             	# [<bool>]
        #Option     "LinearFramebuffer"  	# [<bool>]
        #Option     "SwapbuffersWait"    	# [<bool>]
        #Option     "XvPreferOverlay"    	# [<bool>]
        #Option     "HotPlug"            	# [<bool>]
        #Option     "RelaxedFencing"     	# [<bool>]
        #Option     "XvMC"               	# [<bool>]
        #Option     "Throttle"           	# [<bool>]
        #Option     "ZaphodHeads"        	# <str>
        #Option     "DelayedFlush"       	# [<bool>]
        #Option     "TearFree"           	# [<bool>]
        #Option     "PerCrtcPixmaps"     	# [<bool>]
        #Option     "FallbackDebug"      	# [<bool>]
        #Option     "DebugFlushBatches"  	# [<bool>]
        #Option     "DebugFlushCaches"   	# [<bool>]
        #Option     "DebugWait"          	# [<bool>]
        #Option     "BufferCache"        	# [<bool>]
        #Option     "TripleBuffer"       	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	BusID       "PCI:0:2:0"
EndSection


Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "AccelMethod"        	# <str>
        #Option     "Backlight"          	# <str>
        #Option     "DRI"                	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "VideoKey"           	# <i>
        #Option     "Tiling"             	# [<bool>]
        #Option     "LinearFramebuffer"  	# [<bool>]
        #Option     "SwapbuffersWait"    	# [<bool>]
        #Option     "XvPreferOverlay"    	# [<bool>]
        #Option     "HotPlug"            	# [<bool>]
        #Option     "RelaxedFencing"     	# [<bool>]
        #Option     "XvMC"               	# [<bool>]
        #Option     "Throttle"           	# [<bool>]
        #Option     "ZaphodHeads"        	# <str>
        #Option     "DelayedFlush"       	# [<bool>]
        #Option     "TearFree"           	# [<bool>]
        #Option     "PerCrtcPixmaps"     	# [<bool>]
        #Option     "FallbackDebug"      	# [<bool>]
        #Option     "DebugFlushBatches"  	# [<bool>]
        #Option     "DebugFlushCaches"   	# [<bool>]
        #Option     "DebugWait"          	# [<bool>]
        #Option     "BufferCache"        	# [<bool>]
        #Option     "TripleBuffer"       	# [<bool>]
	Identifier  "Card1"
	Driver      "intel"
	BusID       "PCI:0:2:1"
EndSection


Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"           	# [<bool>]
        #Option     "kmsdev"             	# <str>
        #Option     "ShadowFB"           	# [<bool>]
	Identifier  "Card2"
	Driver      "modesetting"
	BusID       "PCI:0:2:0"
EndSection


Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "Rotate"             	# <str>
        #Option     "fbdev"              	# <str>
        #Option     "debug"              	# [<bool>]
	Identifier  "Card3"
	Driver      "fbdev"
	BusID       "PCI:0:2:0"
EndSection


Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "DefaultRefresh"     	# [<bool>]
        #Option     "ModeSetClearScreen" 	# [<bool>]
	Identifier  "Card4"
	Driver      "vesa"
	BusID       "PCI:0:2:0"
EndSection


Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	Defaultdepth	24
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
		Virtual 800 600
		Modes "800x600@60"
		Modes "800x600@60.30"
		Modes "800x600@59.90"
	EndSubSection
EndSection


Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
	Defaultdepth	24
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
		Virtual 800 600
		Modes "800x600@60"
		Modes "800x600@60.30"
		Modes "800x600@59.90"
	EndSubSection
EndSection


Section "Screen"
	Identifier "Screen2"
	Device     "Card2"
	Monitor    "Monitor2"
	Defaultdepth	24
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
		Virtual 800 600
		Modes "800x600@60"
		Modes "800x600@60.30"
		Modes "800x600@59.90"
	EndSubSection
EndSection


Section "Screen"
	Identifier "Screen3"
	Device     "Card3"
	Monitor    "Monitor3"
	Defaultdepth	24
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
		Virtual 800 600
		Modes "800x600@60"
		Modes "800x600@60.30"
		Modes "800x600@59.90"
	EndSubSection
EndSection


Section "Screen"
	Identifier "Screen4"
	Device     "Card4"
	Monitor    "Monitor4"
	Defaultdepth	24
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
		Virtual 800 600
		Modes "800x600@60"
		Modes "800x600@60.30"
		Modes "800x600@59.90"
	EndSubSection
EndSection

```

intel xorg log:

```
[    38.615] 
X.Org X Server 1.13.0
Release Date: 2012-09-05
[    38.615] X Protocol Version 11, Revision 0
[    38.615] Build Operating System: Linux 3.2.0-26-generic i686 Ubuntu
[    38.615] Current Operating System: Linux ychurch 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:32:08 UTC 2012 i686
[    38.615] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-17-generic root=UUID=0bbcc6af-eb75-4483-bc0f-6881e364330f ro quiet vt.handoff=7
[    38.615] Build Date: 08 October 2012  03:34:08PM
[    38.615] xorg-server 2:1.13.0-0ubuntu6 (For technical support please see http://www.ubuntu.com/support) 
[    38.616] Current version of pixman: 0.26.0
[    38.616] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    38.616] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    38.616] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Mar 28 18:10:47 2013
[    38.617] (==) Using config file: "/etc/X11/xorg.conf"
[    38.620] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    38.640] (==) ServerLayout "X.org Configured"
[    38.640] (**) |-->Screen "Screen0" (0)
[    38.640] (**) |   |-->Monitor "Monitor0"
[    38.641] (**) |   |-->Device "Card0"
[    38.641] (**) |-->Screen "Screen1" (1)
[    38.641] (**) |   |-->Monitor "Monitor1"
[    38.642] (**) |   |-->Device "Card1"
[    38.642] (**) |-->Screen "Screen2" (2)
[    38.642] (**) |   |-->Monitor "Monitor2"
[    38.643] (**) |   |-->Device "Card2"
[    38.643] (**) |-->Screen "Screen3" (3)
[    38.643] (**) |   |-->Monitor "Monitor3"
[    38.644] (**) |   |-->Device "Card3"
[    38.644] (**) |-->Screen "Screen4" (4)
[    38.644] (**) |   |-->Monitor "Monitor4"
[    38.645] (**) |   |-->Device "Card4"
[    38.645] (**) |-->Input Device "Mouse0"
[    38.645] (**) |-->Input Device "Keyboard0"
[    38.645] (==) Automatically adding devices
[    38.645] (==) Automatically enabling devices
[    38.645] (==) Automatically adding GPU devices
[    38.645] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    38.645] 	Entry deleted from font path.
[    38.645] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    38.645] 	Entry deleted from font path.
[    38.646] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    38.646] 	Entry deleted from font path.
[    38.646] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    38.646] 	Entry deleted from font path.
[    38.646] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    38.646] 	Entry deleted from font path.
[    38.646] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    38.646] 	Entry deleted from font path.
[    38.646] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    38.646] 	Entry deleted from font path.
[    38.646] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    38.646] 	Entry deleted from font path.
[    38.646] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    38.646] 	Entry deleted from font path.
[    38.646] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    38.646] 	Entry deleted from font path.
[    38.646] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    38.646] 	Entry deleted from font path.
[    38.646] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    38.646] 	Entry deleted from font path.
[    38.646] (**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    38.646] (**) ModulePath set to "/usr/lib/xorg/modules"
[    38.646] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    38.646] (WW) Disabling Mouse0
[    38.646] (WW) Disabling Keyboard0
[    38.647] (II) Loader magic: 0xb771d640
[    38.647] (II) Module ABI versions:
[    38.647] 	X.Org ANSI C Emulation: 0.4
[    38.647] 	X.Org Video Driver: 13.0
[    38.647] 	X.Org XInput driver : 18.0
[    38.647] 	X.Org Server Extension : 7.0
[    38.664] (II) config/udev: Adding drm device (/dev/dri/card0)
[    38.667] (--) PCI:*(0:0:2:0) 8086:3577:8086:1969 rev 4, Mem @ 0xd8000000/134217728, 0xd0000000/524288
[    38.667] (--) PCI: (0:0:2:1) 8086:3577:8086:1969 rev 0, Mem @ 0x20000000/134217728, 0x30000000/524288
[    38.672] (II) Open ACPI successful (/var/run/acpid.socket)
[    38.672] Initializing built-in extension Generic Event Extension
[    38.672] Initializing built-in extension SHAPE
[    38.672] Initializing built-in extension MIT-SHM
[    38.672] Initializing built-in extension XInputExtension
[    38.672] Initializing built-in extension XTEST
[    38.672] Initializing built-in extension BIG-REQUESTS
[    38.673] Initializing built-in extension SYNC
[    38.673] Initializing built-in extension XKEYBOARD
[    38.673] Initializing built-in extension XC-MISC
[    38.673] Initializing built-in extension SECURITY
[    38.673] Initializing built-in extension XINERAMA
[    38.673] Initializing built-in extension XFIXES
[    38.673] Initializing built-in extension RENDER
[    38.673] Initializing built-in extension RANDR
[    38.673] Initializing built-in extension COMPOSITE
[    38.673] Initializing built-in extension DAMAGE
[    38.673] Initializing built-in extension MIT-SCREEN-SAVER
[    38.673] Initializing built-in extension DOUBLE-BUFFER
[    38.673] Initializing built-in extension RECORD
[    38.673] Initializing built-in extension DPMS
[    38.673] Initializing built-in extension X-Resource
[    38.673] Initializing built-in extension XVideo
[    38.673] Initializing built-in extension XVideo-MotionCompensation
[    38.673] Initializing built-in extension XFree86-VidModeExtension
[    38.673] Initializing built-in extension XFree86-DGA
[    38.674] Initializing built-in extension XFree86-DRI
[    38.674] Initializing built-in extension DRI2
[    38.674] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    38.674] (II) LoadModule: "glx"
[    38.674] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    38.675] (II) Module glx: vendor="X.Org Foundation"
[    38.675] 	compiled for 1.13.0, module version = 1.0.0
[    38.675] 	ABI class: X.Org Server Extension, version 7.0
[    38.675] (==) AIGLX enabled
[    38.675] Loading extension GLX
[    38.675] (II) LoadModule: "modesetting"
[    38.676] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    38.676] (II) Module modesetting: vendor="X.Org Foundation"
[    38.676] 	compiled for 1.13.0, module version = 0.5.0
[    38.676] 	Module class: X.Org Video Driver
[    38.676] 	ABI class: X.Org Video Driver, version 13.0
[    38.676] (II) LoadModule: "intel"
[    38.677] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    38.746] (II) Module intel: vendor="X.Org Foundation"
[    38.746] 	compiled for 1.13.0, module version = 2.20.9
[    38.746] 	Module class: X.Org Video Driver
[    38.746] 	ABI class: X.Org Video Driver, version 13.0
[    38.747] (II) LoadModule: "fbdev"
[    38.747] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    38.748] (II) Module fbdev: vendor="X.Org Foundation"
[    38.748] 	compiled for 1.12.99.902, module version = 0.4.3
[    38.748] 	Module class: X.Org Video Driver
[    38.748] 	ABI class: X.Org Video Driver, version 13.0
[    38.748] (II) LoadModule: "vesa"
[    38.748] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    38.749] (II) Module vesa: vendor="X.Org Foundation"
[    38.749] 	compiled for 1.12.99.902, module version = 2.3.2
[    38.749] 	Module class: X.Org Video Driver
[    38.749] 	ABI class: X.Org Video Driver, version 13.0
[    38.749] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    38.749] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
	Ivybridge Server (GT2), Haswell Desktop (GT1), Haswell Desktop (GT2),
	Haswell Desktop (GT2+), Haswell Mobile (GT1), Haswell Mobile (GT2),
	Haswell Mobile (GT2+), Haswell Server (GT1), Haswell Server (GT2),
	Haswell Server (GT2+), Haswell SDV Desktop (GT1),
	Haswell SDV Desktop (GT2), Haswell SDV Desktop (GT2+),
	Haswell SDV Mobile (GT1), Haswell SDV Mobile (GT2),
	Haswell SDV Mobile (GT2+), Haswell SDV Server (GT1),
	Haswell SDV Server (GT2), Haswell SDV Server (GT2+),
	Haswell ULT Desktop (GT1), Haswell ULT Desktop (GT2),
	Haswell ULT Desktop (GT2+), Haswell ULT Mobile (GT1),
	Haswell ULT Mobile (GT2), Haswell ULT Mobile (GT2+),
	Haswell ULT Server (GT1), Haswell ULT Server (GT2),
	Haswell ULT Server (GT2+), Haswell CRW Desktop (GT1),
	Haswell CRW Desktop (GT2), Haswell CRW Desktop (GT2+),
	Haswell CRW Mobile (GT1), Haswell CRW Mobile (GT2),
	Haswell CRW Mobile (GT2+), Haswell CRW Server (GT1),
	Haswell CRW Server (GT2), Haswell CRW Server (GT2+),
	ValleyView PO board
[    38.758] (II) FBDEV: driver for framebuffer: fbdev
[    38.758] (II) VESA: driver for VESA chipsets: vesa
[    38.758] (++) using VT number 8


[    38.777] (II) modesetting(0): using drv /dev/dri/card0
[    38.787] (WW) Falling back to old probe method for fbdev
[    38.787] (II) Loading sub module "fbdevhw"
[    38.787] (II) LoadModule: "fbdevhw"
[    38.787] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    38.787] (II) Module fbdevhw: vendor="X.Org Foundation"
[    38.787] 	compiled for 1.13.0, module version = 0.0.2
[    38.787] 	ABI class: X.Org Video Driver, version 13.0
[    38.787] (WW) Falling back to old probe method for vesa
[    38.792] (**) modesetting(0): Depth 24, (--) framebuffer bpp 32
[    38.792] (==) modesetting(0): RGB weight 888
[    38.792] (==) modesetting(0): Default visual is TrueColor
[    38.792] (II) modesetting(0): ShadowFB: preferred YES, enabled YES
[    38.820] (II) modesetting(0): Output VGA-0 using monitor section Monitor0
[    38.822] (II) modesetting(0): EDID for output VGA-0
[    38.822] (II) modesetting(0): Not using mode "1024x768" (height too large for virtual size)
[    38.822] (II) modesetting(0): Not using mode "848x480" (height too large for virtual size)
[    38.822] (II) modesetting(0): Printing probed modes for output VGA-0
[    38.822] (II) modesetting(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    38.822] (II) modesetting(0): Modeline "800x600_60.30"x60.3   38.50  800 832 912 1024  600 603 607 624 -hsync +vsync (37.6 kHz)
[    38.822] (II) modesetting(0): Modeline "800x600_60.30"x60.3   38.41  800 832 912 1024  600 601 604 622 -hsync +vsync (37.5 kHz)
[    38.822] (II) modesetting(0): Modeline "800x600_60.00"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    38.823] (II) modesetting(0): Modeline "800x600_60.00"x60.0   38.22  800 832 912 1024  600 601 604 622 -hsync +vsync (37.3 kHz)
[    38.823] (II) modesetting(0): Modeline "800x600_59.90"x59.9   38.09  800 832 912 1024  600 601 604 621 -hsync +vsync (37.2 kHz)
[    38.823] (II) modesetting(0): Modeline "800x600_59.90"x59.5   38.00  800 832 912 1024  600 603 607 624 -hsync +vsync (37.1 kHz)
[    38.823] (II) modesetting(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    38.823] (II) modesetting(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz e)
[    38.823] (II) modesetting(0): Output VGA-0 connected
[    38.823] (II) modesetting(0): Using exact sizes for initial modes
[    38.823] (II) modesetting(0): Output VGA-0 using initial mode 800x600
[    38.823] (II) modesetting(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    38.823] (==) modesetting(0): DPI set to (96, 96)
[    38.823] (II) Loading sub module "fb"
[    38.823] (II) LoadModule: "fb"
[    39.224] (II) Loading /usr/lib/xorg/modules/libfb.so
[    39.224] (II) Module fb: vendor="X.Org Foundation"
[    39.224] 	compiled for 1.13.0, module version = 1.0.0
[    39.224] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    39.224] (II) Loading sub module "shadow"
[    39.224] (II) LoadModule: "shadow"
[    39.225] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    39.273] (II) Module shadow: vendor="X.Org Foundation"
[    39.273] 	compiled for 1.13.0, module version = 1.1.0
[    39.273] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    39.273] (II) UnloadModule: "fbdev"
[    39.274] (II) Unloading fbdev
[    39.274] (II) UnloadSubModule: "fbdevhw"
[    39.274] (II) Unloading fbdevhw
[    39.274] (II) UnloadModule: "vesa"
[    39.274] (II) Unloading vesa
[    39.274] (==) Depth 24 pixmap format is 32 bpp
[    39.275] (==) modesetting(0): Backing store disabled
[    39.275] (==) modesetting(0): Silken mouse enabled
[    39.275] (II) modesetting(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    39.456] (--) RandR disabled
[    39.998] (II) AIGLX: Screen 0 is not DRI2 capable
[    39.998] (II) AIGLX: Screen 0 is not DRI capable
[    40.069] (II) AIGLX: Loaded and initialized swrast
[    40.069] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    40.071] (II) modesetting(0): Damage tracking initialized
[    40.079] (II) modesetting(0): Setting screen physical size to 211 x 158
[    40.159] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    40.171] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    40.171] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    40.171] (II) LoadModule: "evdev"
[    40.172] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    40.173] (II) Module evdev: vendor="X.Org Foundation"
[    40.173] 	compiled for 1.13.0, module version = 2.7.3
[    40.173] 	Module class: X.Org XInput Driver
[    40.173] 	ABI class: X.Org XInput driver, version 18.0
[    40.173] (II) Using input driver 'evdev' for 'Power Button'
[    40.173] (**) Power Button: always reports core events
[    40.173] (**) evdev: Power Button: Device: "/dev/input/event0"
[    40.173] (--) evdev: Power Button: Vendor 0 Product 0x1
[    40.173] (--) evdev: Power Button: Found keys
[    40.173] (II) evdev: Power Button: Configuring as keyboard
[    40.173] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input0/event0"
[    40.174] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    40.174] (**) Option "xkb_rules" "evdev"
[    40.174] (**) Option "xkb_model" "pc105"
[    40.174] (**) Option "xkb_layout" "us"
[    40.175] (II) config/udev: Adding drm device (/dev/dri/card0)
[    40.177] (II) config/udev: Adding input device Multi-Input Device (/dev/input/event2)
[    40.177] (**) Multi-Input Device: Applying InputClass "evdev keyboard catchall"
[    40.177] (II) Using input driver 'evdev' for 'Multi-Input Device'
[    40.177] (**) Multi-Input Device: always reports core events
[    40.177] (**) evdev: Multi-Input Device: Device: "/dev/input/event2"
[    40.177] (--) evdev: Multi-Input Device: Vendor 0x518 Product 0x8
[    40.177] (--) evdev: Multi-Input Device: Found keys
[    40.177] (II) evdev: Multi-Input Device: Configuring as keyboard
[    40.177] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb2/2-2/2-2:1.0/input/input2/event2"
[    40.177] (II) XINPUT: Adding extended input device "Multi-Input Device" (type: KEYBOARD, id 7)
[    40.177] (**) Option "xkb_rules" "evdev"
[    40.178] (**) Option "xkb_model" "pc105"
[    40.178] (**) Option "xkb_layout" "us"
[    40.180] (II) config/udev: Adding input device Multi-Input Device (/dev/input/event3)
[    40.180] (**) Multi-Input Device: Applying InputClass "evdev pointer catchall"
[    40.180] (**) Multi-Input Device: Applying InputClass "evdev keyboard catchall"
[    40.180] (II) Using input driver 'evdev' for 'Multi-Input Device'
[    40.180] (**) Multi-Input Device: always reports core events
[    40.180] (**) evdev: Multi-Input Device: Device: "/dev/input/event3"
[    40.180] (--) evdev: Multi-Input Device: Vendor 0x518 Product 0x8
[    40.180] (--) evdev: Multi-Input Device: Found 3 mouse buttons
[    40.181] (--) evdev: Multi-Input Device: Found scroll wheel(s)
[    40.181] (--) evdev: Multi-Input Device: Found relative axes
[    40.181] (--) evdev: Multi-Input Device: Found x and y relative axes
[    40.181] (--) evdev: Multi-Input Device: Found absolute axes
[    40.181] (II) evdev: Multi-Input Device: Forcing absolute x/y axes to exist.
[    40.181] (--) evdev: Multi-Input Device: Found keys
[    40.181] (II) evdev: Multi-Input Device: Configuring as mouse
[    40.181] (II) evdev: Multi-Input Device: Configuring as keyboard
[    40.181] (II) evdev: Multi-Input Device: Adding scrollwheel support
[    40.181] (**) evdev: Multi-Input Device: YAxisMapping: buttons 4 and 5
[    40.181] (**) evdev: Multi-Input Device: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    40.181] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb2/2-2/2-2:1.1/input/input3/event3"
[    40.181] (II) XINPUT: Adding extended input device "Multi-Input Device" (type: KEYBOARD, id 8)
[    40.181] (**) Option "xkb_rules" "evdev"
[    40.181] (**) Option "xkb_model" "pc105"
[    40.181] (**) Option "xkb_layout" "us"
[    40.182] (II) evdev: Multi-Input Device: initialized for relative axes.
[    40.182] (WW) evdev: Multi-Input Device: ignoring absolute axes.
[    40.183] (**) Multi-Input Device: (accel) keeping acceleration scheme 1
[    40.183] (**) Multi-Input Device: (accel) acceleration profile 0
[    40.183] (**) Multi-Input Device: (accel) acceleration factor: 2.000
[    40.183] (**) Multi-Input Device: (accel) acceleration threshold: 4
[    40.184] (II) config/udev: Adding input device Multi-Input Device (/dev/input/mouse0)
[    40.184] (II) No input driver specified, ignoring this device.
[    40.184] (II) This device may have been added with another device file.
[    40.185] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event1)
[    40.185] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    40.185] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    40.185] (**) AT Translated Set 2 keyboard: always reports core events
[    40.185] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event1"
[    40.185] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    40.185] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    40.185] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    40.185] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input1/event1"
[    40.186] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    40.186] (**) Option "xkb_rules" "evdev"
[    40.186] (**) Option "xkb_model" "pc105"
[    40.186] (**) Option "xkb_layout" "us"
[    40.194] (II) config/udev: Adding input device Serial Wacom Tablet (/dev/ttyS3)
[    40.194] (**) Serial Wacom Tablet: Applying InputClass "Wacom serial class"
[    40.194] (II) LoadModule: "wacom"
[    40.195] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    40.195] (II) Module wacom: vendor="X.Org Foundation"
[    40.195] 	compiled for 1.13.0, module version = 0.17.0
[    40.195] 	Module class: X.Org XInput Driver
[    40.195] 	ABI class: X.Org XInput driver, version 18.0
[    40.195] (II) Using input driver 'wacom' for 'Serial Wacom Tablet'
[    40.195] (**) Serial Wacom Tablet: always reports core events
[    40.195] (**) Option "Device" "/dev/ttyS3"
[    40.196] (**) Option "StopBits" "1"
[    40.196] (**) Option "DataBits" "8"
[    40.196] (**) Option "Parity" "None"
[    40.196] (**) Option "Vmin" "1"
[    40.196] (**) Option "Vtime" "10"
[    40.196] (**) Option "FlowControl" "Xoff"
[    40.197] (II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
[    40.197] (II) Serial Wacom Tablet: other types will be automatically added.
[    40.465] (II) Serial Wacom Tablet stylus: serial tablet id 0x90.
[    40.465] (--) Serial Wacom Tablet stylus: using pressure threshold of 27 for button 1
[    40.465] (--) Serial Wacom Tablet stylus: Wacom General ISDV4 tablet maxX=21200 maxY=15900 maxZ=255 resX=100000 resY=100000  tilt=disabled
[    40.465] (II) Serial Wacom Tablet stylus: hotplugging dependent devices.
[    40.465] (EE) Serial Wacom Tablet stylus: Invalid type 'cursor' for this device.
[    40.465] (EE) Serial Wacom Tablet stylus: Invalid type 'touch' for this device.
[    40.465] (EE) Serial Wacom Tablet stylus: Invalid type 'pad' for this device.
[    40.465] (II) Serial Wacom Tablet stylus: hotplugging completed.
[    40.465] (**) Option "config_info" "udev:/sys/devices/pnp0/00:09/tty/ttyS3"
[    40.465] (II) XINPUT: Adding extended input device "Serial Wacom Tablet stylus" (type: STYLUS, id 10)
[    40.467] (**) Serial Wacom Tablet stylus: (accel) keeping acceleration scheme 1
[    40.467] (**) Serial Wacom Tablet stylus: (accel) acceleration profile 0
[    40.467] (**) Serial Wacom Tablet stylus: (accel) acceleration factor: 2.000
[    40.467] (**) Serial Wacom Tablet stylus: (accel) acceleration threshold: 4
[    40.467] (**) Option "BaudRate" "19200"
[    40.483] (**) Serial Wacom Tablet eraser: Applying InputClass "Wacom serial class"
[    40.484] (II) Using input driver 'wacom' for 'Serial Wacom Tablet eraser'
[    40.484] (**) Serial Wacom Tablet eraser: always reports core events
[    40.484] (**) Option "Device" "/dev/ttyS3"
[    40.484] (**) Option "Type" "eraser"
[    40.484] (**) Option "BaudRate" "19200"
[    40.484] (**) Option "StopBits" "1"
[    40.484] (**) Option "DataBits" "8"
[    40.484] (**) Option "Parity" "None"
[    40.484] (**) Option "Vmin" "1"
[    40.485] (**) Option "Vtime" "10"
[    40.485] (**) Option "FlowControl" "Xoff"
[    40.485] (--) Serial Wacom Tablet eraser: Wacom General ISDV4 tablet maxX=21200 maxY=15900 maxZ=255 resX=100000 resY=100000  tilt=disabled
[    40.485] (**) Option "config_info" "udev:/sys/devices/pnp0/00:09/tty/ttyS3"
[    40.485] (II) XINPUT: Adding extended input device "Serial Wacom Tablet eraser" (type: ERASER, id 11)
[    40.487] (**) Serial Wacom Tablet eraser: (accel) keeping acceleration scheme 1
[    40.487] (**) Serial Wacom Tablet eraser: (accel) acceleration profile 0
[    40.487] (**) Serial Wacom Tablet eraser: (accel) acceleration factor: 2.000
[    40.487] (**) Serial Wacom Tablet eraser: (accel) acceleration threshold: 4
[    41.996] (II) XKB: reuse xkmfile /var/lib/xkb/server-8AA988DD479FAABEC4FC3CCCF4CC29B4948840B4.xkm
[    42.518] (II) modesetting(0): Allocate new frame buffer 1024x768 stride
```

---

