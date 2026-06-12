---
title: "Resolution Does Not Go Beyond 800x600"
date: 2010-12-23
forum: Hardware
---

### Post by jmate on 2010-12-23
Summarizing from:
[http://ubuntuforums.org/showthread.php?t=1621991](http://ubuntuforums.org/showthread.php?t=1621991)

I have tested the monitor on windows, and it works for resolutions up to 1280x720. It is a monitor/tv from fortec.

I have tried using xrandr to manually set add a 1024x768 resolution; however, it rejected the resolution.
```

[FONT=Courier New]$ xrandr --addmode default 1024x768_60.00[/FONT]
[FONT=Courier New]$ xrandr --output  default --mode 1024x768_60.00[/FONT]
[FONT=Courier New]xrandr: screen cannot be larger than 800x600 (desired size 1024x76[/FONT]8

```

I have tried creating an xorg.conf file, but that just results in a blank screen.

I have tried upgrading to ubuntu 10.10. When I boot 10.10, the screen is just black. As a result, I am back on 10.04.

lshw gives:
```

  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Rage 128 Pro Ultra TR
       vendor: ATI Technologies Inc
       physical id: 4
       bus info: pci@0000:05:04.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=66 mingnt=8
       resources: memory:f8000000-fbffffff(prefetchable) ioport:1000(size=256) memory:fc400000-fc403fff memory:fc000000-fc01ffff(prefetchable)

```Any ideas on why I cannot get a higher resolution than 800x600?

---

### Post by akand074 on 2010-12-23
Do you have your proprietary drivers installed? (System > Administration > Hardware Drivers (Additional Drivers in 10.10) )

---

### Post by jmate on 2010-12-23
System -> Administration -> Hardware Drivers does not list any proprietary drivers for use.

I have "Proprietary drivers for devices (restricted)" checked in Software Sources -> Ubuntu Software.

---

### Post by akand074 on 2010-12-24
> **jmate said:**
> System -> Administration -> Hardware Drivers does not list any proprietary drivers for use.

I have "Proprietary drivers for devices (restricted)" checked in Software Sources -> Ubuntu Software.

I just looked up your graphics card at the AMD support website. It doesn't have Linux support. Matter of fact it doesn't have Windows support past Windows XP. It must be super old. You should be able to get resolutions higher than that using the open source drivers.. you just wouldn't get 3D acceleration, but judging with the extremely low clock speed and width that wouldn't have been possible anyways. Though unfortunately I don't know how to help troubleshoot from here. Perhaps someone else might have more experience.

---

### Post by jmate on 2010-12-24
Thanks for you help [akand074]("http://ubuntuforums.org/member.php?u=840786").

I don't care about 3d acceleration. I am using this machine for web development and school work. I'm a bit happy that it's not possible to have 3d acceleration because I won't be distracted by video games while studying! :D

---

### Post by jmate on 2010-12-24
I used the Knoppix live CD and the xorg.conf it create work. As a result I copied it and tried to use it with ubuntu. However, when I tried testing the script I got a blank screen:

Here is the contents of the xorg.conf that I tried to get working:
```

# /etc/X11/xorg.conf
# Created by KNOPPIX # Delete this line if you don't want KNOPPIX to overwrite your /etc/X11/xorg.conf

Section "ServerLayout"
    Identifier     "XFree86 Configured"
    Screen      0  "Screen0" 0 0
    
    # Since evdev, manual keyboard/mice entries are mostly ignored:
    # Keyboard auto-probed
    
    # Touchpad auto-probed
    # USB mouse auto-probed
    # Serial Mouse auto-probed
### AIGLX for compiz 3D-Support with DRI & Composite
### This option doesn't hurt even if it's not supported by the individual card
        Option         "AIGLX"     "true"
    
EndSection

Section "ServerFlags"
    Option "AllowMouseOpenFail"  "true"
    Option    "DPMS"    "true"
    
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi:unscaled"
    FontPath     "/usr/share/fonts/X11/100dpi:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/Speedo"
    FontPath     "/usr/share/fonts/X11/PEX"
# Additional fonts: Locale, Gimp, TTF...
    FontPath     "/usr/share/fonts/X11/cyrillic"
#    FontPath     "/usr/share/fonts/X11/latin2/75dpi"
#    FontPath     "/usr/share/fonts/X11/latin2/100dpi"
# True type and type1 fonts are also handled via xftlib, see /etc/X11/XftConfig!
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "/usr/share/fonts/truetype"
    FontPath     "/usr/share/fonts/latex-ttf-fonts"
EndSection

Section "Module"
# Comments: see http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=346408
    Load  "dbe" # Double Buffering Extension, very important.
    Load  "dri" # This shouldn't be available choice if user has selected driver vga, vesa or nv.
    Load  "glx" # GLX Extension.
    Load  "freetype" # Freetype fonts.
    Load  "type1"  # Type 1 fonts
    Load  "record" # Developer extension, usually not needed
    Load  "extmod" # This is okay, but if you look into "man xorg.conf" you'll find option NOT to include DGA extension with extmod, and for a good reason.. DGA causes instability as it accesses videoram without consulting X about it.
    SubSection      "extmod"
        Option          "omit xfree86-dga"
    EndSubSection
#    Load  "speedo" # Speedo fonts, this module doesn't exist in Xorg 7.0.17
# The following are deprecated/unstable/unneeded in Xorg 7.0
#       Load  "ddc"  # ddc probing of monitor, this should be never present, as it gets automatically loaded.
#    Load  "GLcore" # This should be never present, as it gets automatically loaded.
#       Load  "bitmap" # Should be never present, as it gets automatically loaded. This is a font module, and loading it in xorg.conf makes X try to load it twice.
EndSection

Section "Extensions"
    # compiz needs Composite, but it can cause bad (end even softreset-resistant)
    # effects in some graphics cards, especially nv.
    Option "Composite" "Enable"
EndSection




# Monitor section auto-generated by KNOPPIX mkxorgconfig

Section "Monitor"
    Identifier   "Monitor0"
    ModelName    "Generic Monitor"
#    HorizSync    28.0 - 78.0 # Warning: This may fry very old Monitors
#    HorizSync    28.0 - 96.0 # Warning: This may fry old Monitors
#    VertRefresh  50.0 - 76.0 # Very conservative. May flicker.
#    VertRefresh  50.0 - 60.0 # Extreme conservative. Will flicker. TFT default.
        
    
    Option "MonitorLayout" "LVDS,AUTO"

EndSection


Section "Device"
    ### Available Driver options are:-
# sw_cursor is needed for some ati and radeon cards
        #Option     "sw_cursor"
        #Option     "hw_cursor"
        #Option     "NoAccel"
        #Option     "ShowCache"
        #Option     "ShadowFB"
        #Option     "UseFBDev"
        #Option     "Rotate"
    Identifier  "Card0"
    # Driver (chipset) autodetect
    VendorName  "All"
    BoardName   "All"
#    BusID       "PCI:1:0:0"

# compiz, beryl 3D-Support with DRI & Composite
    Option "XAANoOffscreenPixmaps"
    Option "AllowGLXWithComposite" "true"
    Option "EnablePageFlip" "true"
    Option "TripleBuffer" "true"

# Tweaks for the xorg 7.4 (otherwise broken) "intel" driver
    Option "Tiling" "no"
    Option "Legacy3D" "false"

# These two lines are (presumably) needed to prevent fonts from being scrambled
        Option  "XaaNoScanlineImageWriteRect" "true"
        Option  "XaaNoScanlineCPUToScreenColorExpandFill" "true"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    
    Option "AddARGBGLXVisuals" "true"
    Option "DisableGLXRootClipping" "true"
    SubSection "Display"
        Depth     1
        
    EndSubSection
    SubSection "Display"
        Depth     4
        
    EndSubSection
    SubSection "Display"
        Depth     8
        
    EndSubSection
    SubSection "Display"
        Depth     15
        
    EndSubSection
    SubSection "Display"
        Depth     16
        
    EndSubSection
    SubSection "Display"
        Depth     24
        
    EndSubSection
    SubSection "Display"
        Depth     32
        
    EndSubSection
EndSection

Section "DRI"
    Mode 0666
EndSection

```Here is the log file from testing that xorg.conf:

```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
Current Operating System: Linux jmate-desktop 2.6.32-26-generic #48-Ubuntu SMP Wed Nov 24 09:00:03 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-26-generic root=UUID=4da2b71e-7715-41b3-bba8-30eac1c12eb3 ro single vga=758
Build Date: 10 November 2010  11:25:26AM
xorg-server 2:1.7.6-2ubuntu7.4 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Dec 24 12:23:43 2010
(++) Using config file: "/home/jmate/xorg.test.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "XFree86 Configured"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Card0"
(**) Option "AllowMouseOpenFail" "true"
(**) Option "AIGLX" "true"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/Speedo" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/PEX" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/usr/share/fonts/truetype".
    Entry deleted from font path.
    (Run 'mkfontdir' on "/usr/share/fonts/truetype").
(WW) The directory "/usr/share/fonts/latex-ttf-fonts" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(**) FontPath set to:
    /usr/share/fonts/X11/misc:unscaled,
    /usr/share/fonts/X11/75dpi:unscaled,
    /usr/share/fonts/X11/100dpi:unscaled,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(**) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f1b20
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(--) using VT number 2

(--) PCI:*(0:5:4:0) 1002:5452:1002:0009 ATI Technologies Inc Rage 128 Pro Ultra TR rev 0, Mem @ 0xf8000000/67108864, 0xfc400000/16384, I/O @ 0x00001000/256, BIOS @ 0x????????/131072
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri2" will be loaded by default.
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
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(**) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
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
(II) LoadModule: "extmod"
(II) Reloading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched ati as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 6.13.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "r128"
(II) Loading /usr/lib/xorg/modules/drivers/r128_drv.so
(II) Module r128: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 6.8.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.4.1
    ABI class: X.Org Video Driver, version 6.0
(II) R128: Driver for ATI Rage 128 chipsets:
    ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
    ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
    ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
    ATI Rage 128 Pro GL PC (PCI/AGP), ATI Rage 128 Pro GL PD (PCI),
    ATI Rage 128 Pro GL PE (PCI/AGP), ATI Rage 128 Pro GL PF (AGP),
    ATI Rage 128 Pro VR PG (PCI/AGP), ATI Rage 128 Pro VR PH (PCI/AGP),
    ATI Rage 128 Pro VR PI (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
    ATI Rage 128 Pro VR PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
    ATI Rage 128 Pro VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
    ATI Rage 128 Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
    ATI Rage 128 Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
    ATI Rage 128 Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
    ATI Rage 128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
    ATI Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
    ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
    ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
    ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (PCI/AGP),
    ATI Rage 128 4X SF (PCI/AGP), ATI Rage 128 4X SG (PCI/AGP),
    ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128 4X SK (PCI/AGP),
    ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM (AGP),
    ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
    ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
    ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
    ATI Rage 128 Pro ULTRA TU (AGP?)
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 05@00:04:0
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.0.2
    ABI class: X.Org Video Driver, version 6.0
(II) R128(0): PCI bus 5 card 4 func 0
(==) R128(0): Depth 24, (--) framebuffer bpp 32
(II) R128(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) R128(0): Default visual is TrueColor
(**) R128(0): Option "EnablePageFlip" "true"
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.1.0
    ABI class: X.Org Video Driver, version 6.0
(II) R128(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) R128(0): RGB weight 888
(II) R128(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Video Driver, version 6.0
(II) R128(0): initializing int10
(II) R128(0): Primary V_BIOS segment is: 0xc000
(--) R128(0): Chipset: "ATI Rage 128 Pro ULTRA TR (AGP)" (ChipID = 0x5452)
(--) R128(0): Linear framebuffer at 0xf8000000
(--) R128(0): MMIO registers at 0xfc400000
(--) R128(0): VideoRAM: 16384 kByte (128-bit SDR SGRAM 1:1)
(**) R128(0): Using external CRT for display
(II) R128(0): Primary Display == Type 3
(WW) R128(0): Can't determine panel dimensions, and none specified.
    Disabling programming of FP registers.
(II) R128(0): PLL parameters: rf=2950 rd=65 min=12500 max=35000; xclk=13000
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Video Driver, version 6.0
(II) R128(0): VESA BIOS detected
(II) R128(0): VESA VBE Version 2.0
(II) R128(0): VESA VBE Total Mem: 16384 kB
(II) R128(0): VESA VBE OEM: ATI RAGE128
(II) R128(0): VESA VBE OEM Software Rev: 1.0
(II) R128(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) R128(0): VESA VBE OEM Product: R128
(II) R128(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) R128(0): VESA VBE DDC supported
(II) R128(0): VESA VBE DDC Level none
(II) R128(0): VESA VBE DDC transfer in appr. 2 sec.
(II) R128(0): VESA VBE DDC read failed
(==) R128(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) R128(0): I2C bus "DDC" initialized.
(II) R128(0): I2C device "DDC:ddc2" registered at address 0xA0.
(EE) R128(0): No DFP detected
(II) R128(0): Monitor0: Using default hsync range of 31.50-37.90 kHz
(II) R128(0): Monitor0: Using default vrefresh range of 50.00-70.00 Hz
(WW) R128(0): Unable to estimate virtual size
(II) R128(0): Clock range:  12.50 to 350.00 MHz
(II) R128(0): Not using default mode "640x350" (vrefresh out of range)
(II) R128(0): Not using default mode "320x175" (vrefresh out of range)
(II) R128(0): Not using default mode "640x400" (vrefresh out of range)
(II) R128(0): Not using default mode "320x200" (vrefresh out of range)
(II) R128(0): Not using default mode "720x400" (vrefresh out of range)
(II) R128(0): Not using default mode "360x200" (vrefresh out of range)
(II) R128(0): Not using default mode "640x480" (vrefresh out of range)
(II) R128(0): Not using default mode "320x240" (vrefresh out of range)
(II) R128(0): Not using default mode "640x480" (vrefresh out of range)
(II) R128(0): Not using default mode "320x240" (vrefresh out of range)
(II) R128(0): Not using default mode "640x480" (hsync out of range)
(II) R128(0): Not using default mode "320x240" (hsync out of range)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "400x300" (hsync out of range)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "400x300" (hsync out of range)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "400x300" (hsync out of range)
(II) R128(0): Not using default mode "1024x768" (vrefresh out of range)
(II) R128(0): Not using default mode "512x384" (vrefresh out of range)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "512x384" (hsync out of range)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "512x384" (hsync out of range)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "512x384" (hsync out of range)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "512x384" (hsync out of range)
(II) R128(0): Not using default mode "1152x864" (hsync out of range)
(II) R128(0): Not using default mode "576x432" (hsync out of range)
(II) R128(0): Not using default mode "1280x960" (hsync out of range)
(II) R128(0): Not using default mode "640x480" (hsync out of range)
(II) R128(0): Not using default mode "1280x960" (hsync out of range)
(II) R128(0): Not using default mode "640x480" (hsync out of range)
(II) R128(0): Not using default mode "1280x1024" (hsync out of range)
(II) R128(0): Not using default mode "640x512" (hsync out of range)
(II) R128(0): Not using default mode "1280x1024" (hsync out of range)
(II) R128(0): Not using default mode "640x512" (hsync out of range)
(II) R128(0): Not using default mode "1280x1024" (hsync out of range)
(II) R128(0): Not using default mode "640x512" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (hsync out of range)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (hsync out of range)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (hsync out of range)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (hsync out of range)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (hsync out of range)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1792x1344" (hsync out of range)
(II) R128(0): Not using default mode "896x672" (hsync out of range)
(II) R128(0): Not using default mode "1792x1344" (hsync out of range)
(II) R128(0): Not using default mode "896x672" (hsync out of range)
(II) R128(0): Not using default mode "1856x1392" (hsync out of range)
(II) R128(0): Not using default mode "928x696" (hsync out of range)
(II) R128(0): Not using default mode "1856x1392" (hsync out of range)
(II) R128(0): Not using default mode "928x696" (hsync out of range)
(II) R128(0): Not using default mode "1920x1440" (hsync out of range)
(II) R128(0): Not using default mode "960x720" (hsync out of range)
(II) R128(0): Not using default mode "1920x1440" (hsync out of range)
(II) R128(0): Not using default mode "960x720" (hsync out of range)
(II) R128(0): Not using default mode "832x624" (hsync out of range)
(II) R128(0): Not using default mode "416x312" (hsync out of range)
(II) R128(0): Not using default mode "1152x864" (hsync out of range)
(II) R128(0): Not using default mode "576x432" (hsync out of range)
(II) R128(0): Not using default mode "1152x864" (hsync out of range)
(II) R128(0): Not using default mode "576x432" (hsync out of range)
(II) R128(0): Not using default mode "1152x864" (hsync out of range)
(II) R128(0): Not using default mode "576x432" (hsync out of range)
(II) R128(0): Not using default mode "1152x864" (hsync out of range)
(II) R128(0): Not using default mode "576x432" (hsync out of range)
(II) R128(0): Not using default mode "1152x864" (hsync out of range)
(II) R128(0): Not using default mode "576x432" (hsync out of range)
(II) R128(0): Not using default mode "1152x864" (hsync out of range)
(II) R128(0): Not using default mode "576x432" (hsync out of range)
(II) R128(0): Not using default mode "1360x768" (hsync out of range)
(II) R128(0): Not using default mode "680x384" (hsync out of range)
(II) R128(0): Not using default mode "1360x768" (hsync out of range)
(II) R128(0): Not using default mode "680x384" (hsync out of range)
(II) R128(0): Not using default mode "1400x1050" (hsync out of range)
(II) R128(0): Not using default mode "700x525" (hsync out of range)
(II) R128(0): Not using default mode "1400x1050" (hsync out of range)
(II) R128(0): Not using default mode "700x525" (hsync out of range)
(II) R128(0): Not using default mode "1400x1050" (hsync out of range)
(II) R128(0): Not using default mode "700x525" (hsync out of range)
(II) R128(0): Not using default mode "1400x1050" (hsync out of range)
(II) R128(0): Not using default mode "700x525" (hsync out of range)
(II) R128(0): Not using default mode "1440x900" (hsync out of range)
(II) R128(0): Not using default mode "720x450" (hsync out of range)
(II) R128(0): Not using default mode "1600x1024" (hsync out of range)
(II) R128(0): Not using default mode "800x512" (hsync out of range)
(II) R128(0): Not using default mode "1680x1050" (hsync out of range)
(II) R128(0): Not using default mode "840x525" (hsync out of range)
(II) R128(0): Not using default mode "1680x1050" (hsync out of range)
(II) R128(0): Not using default mode "840x525" (hsync out of range)
(II) R128(0): Not using default mode "1680x1050" (hsync out of range)
(II) R128(0): Not using default mode "840x525" (hsync out of range)
(II) R128(0): Not using default mode "1680x1050" (hsync out of range)
(II) R128(0): Not using default mode "840x525" (hsync out of range)
(II) R128(0): Not using default mode "1680x1050" (hsync out of range)
(II) R128(0): Not using default mode "840x525" (hsync out of range)
(II) R128(0): Not using default mode "1920x1080" (hsync out of range)
(II) R128(0): Not using default mode "960x540" (hsync out of range)
(II) R128(0): Not using default mode "1920x1200" (hsync out of range)
(II) R128(0): Not using default mode "960x600" (hsync out of range)
(II) R128(0): Not using default mode "1920x1440" (hsync out of range)
(II) R128(0): Not using default mode "960x720" (hsync out of range)
(II) R128(0): Not using default mode "2048x1536" (hsync out of range)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "2048x1536" (hsync out of range)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(--) R128(0): Virtual size is 800x600 (pitch 800)
(**) R128(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) R128(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) R128(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) R128(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) R128(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) R128(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) R128(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) R128(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) R128(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) R128(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
(**) R128(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) R128(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(==) R128(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.2.1
    ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "shadowfb"
(II) LoadModule: "shadowfb"
(II) Loading /usr/lib/xorg/modules/libshadowfb.so
(II) Module shadowfb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) R128(0): Page flipping enabled
(!!) R128(0): For information on using the multimedia capabilities
    of this adapter, please see http://gatos.sf.net.
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(--) Depth 24 pixmap format is 32 bpp
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: Searching for BusID pci:0000:05:04.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 13, (OK)
drmOpenByBusid: drmOpenMinor returns 13
drmOpenByBusid: drmGetBusid reports pci:0000:05:04.0
(II) [drm] loaded kernel module for "r128" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) R128(0): [drm] Using the DRM lock SAREA also for drawables.
(II) R128(0): [drm] framebuffer handle = 0xf8000000
(II) R128(0): [drm] added 1 reserved context for kernel
(II) R128(0): X context handle = 0x1
(II) R128(0): [drm] installed DRM signal handler
(WW) R128(0): [agp] AGP not available
(WW) R128(0): [agp] AGP failed to initialize -- falling back to PCI mode.
(WW) R128(0): [agp] Make sure you have the agpgart kernel module loaded.
(II) R128(0): [pci] 8192 kB allocated with handle 0xf84c2000
(II) R128(0): [pci] ring handle = 0xf84c2000
(II) R128(0): [pci] Ring mapped at 0xb75fe000
(II) R128(0): [pci] Ring contents 0x00000000
(II) R128(0): [pci] ring read ptr handle = 0xf85c3000
(II) R128(0): [pci] Ring read ptr mapped at 0xb75fd000
(II) R128(0): [pci] Ring read ptr contents 0x00000000
(II) R128(0): [pci] vertex/indirect buffers handle = 0xf85c4000
(II) R128(0): [pci] Vertex/indirect buffers mapped at 0xb63b4000
(II) R128(0): [pci] Vertex/indirect buffers contents 0x00000000
(II) R128(0): [drm] register handle = 0xfc400000
(II) R128(0): [dri] Visual configs initialized
(II) R128(0): CCE in BM mode
(II) R128(0): Using 8 MB AGP aperture
(II) R128(0): Using 1 MB for the ring buffer
(II) R128(0): Using 2 MB for vertex/indirect buffers
(II) R128(0): Using 5 MB for AGP textures
(II) R128(0): Memory manager initialized to (0,0) (800,2457)
(II) R128(0): Reserved area from (0,600) to (800,602)
(II) R128(0): Largest offscreen area available: 800 x 1855
(II) R128(0): Reserved back buffer from (0,602) to (800,1202)
(II) R128(0): Reserved depth buffer from (0,1202) to (800,1803)
(II) R128(0): Reserved depth span from (0,1802) offset 0x57fd00
(II) R128(0): Reserved 8704 kb for textures at offset 0x77f880
(**) R128(0): Option "XaaNoScanlineCPUToScreenColorExpandFill" "true"
(**) R128(0): Option "XaaNoScanlineImageWriteRect" "true"
(**) R128(0): Option "XaaNoOffscreenPixmaps"
(II) R128(0): Using XFree86 Acceleration Architecture (XAA)
    Screen to screen bit blits
    Solid filled rectangles
    8x8 mono pattern filled rectangles
    Solid Lines
    Dashed Lines
    Setting up tile and stipple cache:
        30 128x128 slots
(II) R128(0): Acceleration enabled
(==) R128(0): Backing store disabled
(==) R128(0): Silken mouse enabled
(II) R128(0): Using hardware cursor (scanline 7212)
(II) R128(0): Largest offscreen area available: 800 x 651
(==) R128(0): DPMS enabled
(WW) R128(0): Option "AllowGLXWithComposite" is not used
(WW) R128(0): Option "TripleBuffer" is not used
(WW) R128(0): Option "Tiling" is not used
(WW) R128(0): Option "Legacy3D" is not used
(WW) R128(0): Option "MonitorLayout" is not used
(WW) R128(0): Option "AddARGBGLXVisuals" is not used
(WW) R128(0): Option "DisableGLXRootClipping" is not used
(II) R128(0): [DRI] installation complete
(II) R128(0): [drm] Added 128 16384 byte vertex/indirect buffers
(II) R128(0): [drm] Mapped 128 vertex/indirect buffers
(II) R128(0): [drm] dma control initialized, using IRQ 16
(II) R128(0): Direct rendering enabled
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 14, (OK)
drmOpenByBusid: Searching for BusID pci:0000:05:04.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 14, (OK)
drmOpenByBusid: drmOpenMinor returns 14
drmOpenByBusid: drmGetBusid reports pci:0000:05:04.0
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: Loaded and initialized /usr/lib/dri/r128_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) (/dev/input/event4)
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Applying InputClass "evdev pointer catchall"
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): always reports core events
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Device: "/dev/input/event4"
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found 3 mouse buttons
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found scroll wheel(s)
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found relative axes
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found x and y relative axes
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Configuring as mouse
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): YAxisMapping: buttons 4 and 5
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)" (type: MOUSE)
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): initialized for relative axes.
(II) config/udev: Adding input device Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)

```

---

### Post by akand074 on 2010-12-24
Take a look at [this]("https://wiki.ubuntu.com/X/Config/Resolution") site. It might help. Though it seems to mostly be dealing with xrandr which you have been working with. But still it might have more information.

---

### Post by jmate on 2010-12-24
I finally created an xorg.conf that works. However it refused to accept the 1024x786 resolution.

How do I force a different default hsync range and vrefresh range
```


This is what I got from Xorg.0.log
(II) R128(0): External VGA: Using default hsync range of 31.50-37.90 kHz
(II) R128(0): External VGA: Using default vrefresh range of 50.00-70.00 Hz

This is my modeline from the xorg.conf failing:
(II) R128(0): Not using mode "1024x786_60.00" (hsync out of range)

This is what the modeline looks like in my xorg.conf:
Modeline        "1024x786_60.00"   65.75  1024 1080 1184 1344  786 789 799 816 -hsync +vsync

```
?

Cheers

xorg.conf:
```

Section "Monitor"
    Identifier      "External VGA"
    Modeline        "1024x786_60.00"   65.75  1024 1080 1184 1344  786 789 799 816 -hsync +vsync
    Option          "PreferredMode" "1024x786_60.00"
EndSection

Section "Device"
    Identifier      "Rage 128 Pro Ultra TR"
    Driver          "ati"
    Option          "Monitor-VGA-0" "External VGA"
EndSection

Section "Screen"
    Identifier      "Primary Screen"
    Monitor         "External VGA"
    Device          "Rage 128 Pro Ultra TR"
    DefaultDepth    24
    SubSection "Display"
        Depth           24
        Modes   "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier      "Default Layout"
    Screen          "Primary Screen"
EndSection

```

/var/logXorg.0.log
```


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
Current Operating System: Linux jmate-desktop 2.6.32-26-generic #48-Ubuntu SMP Wed Nov 24 09:00:03 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-26-generic root=UUID=4da2b71e-7715-41b3-bba8-30eac1c12eb3 ro vga=758 quiet splash
Build Date: 10 November 2010  11:25:26AM
xorg-server 2:1.7.6-2ubuntu7.4 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Dec 24 14:34:04 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Primary Screen" (0)
(**) |   |-->Monitor "External VGA"
(**) |   |-->Device "Rage 128 Pro Ultra TR"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f1b20
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:5:4:0) 1002:5452:1002:0009 ATI Technologies Inc Rage 128 Pro Ultra TR rev 0, Mem @ 0xf8000000/67108864, 0xfc400000/16384, I/O @ 0x00001000/256, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 6.13.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "r128"
(II) Loading /usr/lib/xorg/modules/drivers/r128_drv.so
(II) Module r128: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 6.8.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) R128: Driver for ATI Rage 128 chipsets:
    ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
    ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
    ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
    ATI Rage 128 Pro GL PC (PCI/AGP), ATI Rage 128 Pro GL PD (PCI),
    ATI Rage 128 Pro GL PE (PCI/AGP), ATI Rage 128 Pro GL PF (AGP),
    ATI Rage 128 Pro VR PG (PCI/AGP), ATI Rage 128 Pro VR PH (PCI/AGP),
    ATI Rage 128 Pro VR PI (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
    ATI Rage 128 Pro VR PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
    ATI Rage 128 Pro VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
    ATI Rage 128 Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
    ATI Rage 128 Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
    ATI Rage 128 Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
    ATI Rage 128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
    ATI Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
    ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
    ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
    ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (PCI/AGP),
    ATI Rage 128 4X SF (PCI/AGP), ATI Rage 128 4X SG (PCI/AGP),
    ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128 4X SK (PCI/AGP),
    ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM (AGP),
    ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
    ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
    ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
    ATI Rage 128 Pro ULTRA TU (AGP?)
(II) Primary Device is: PCI 05@00:04:0
(II) R128(0): PCI bus 5 card 4 func 0
(**) R128(0): Depth 24, (--) framebuffer bpp 32
(II) R128(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) R128(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.1.0
    ABI class: X.Org Video Driver, version 6.0
(II) R128(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) R128(0): RGB weight 888
(II) R128(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Video Driver, version 6.0
(II) R128(0): initializing int10
(II) R128(0): Primary V_BIOS segment is: 0xc000
(--) R128(0): Chipset: "ATI Rage 128 Pro ULTRA TR (AGP)" (ChipID = 0x5452)
(--) R128(0): Linear framebuffer at 0xf8000000
(--) R128(0): MMIO registers at 0xfc400000
(--) R128(0): VideoRAM: 16384 kByte (128-bit SDR SGRAM 1:1)
(**) R128(0): Using external CRT for display
(II) R128(0): Primary Display == Type 3
(WW) R128(0): Can't determine panel dimensions, and none specified.
    Disabling programming of FP registers.
(II) R128(0): PLL parameters: rf=2950 rd=65 min=12500 max=35000; xclk=13000
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Video Driver, version 6.0
(II) R128(0): VESA BIOS detected
(II) R128(0): VESA VBE Version 2.0
(II) R128(0): VESA VBE Total Mem: 16384 kB
(II) R128(0): VESA VBE OEM: ATI RAGE128
(II) R128(0): VESA VBE OEM Software Rev: 1.0
(II) R128(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) R128(0): VESA VBE OEM Product: R128
(II) R128(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) R128(0): VESA VBE DDC supported
(II) R128(0): VESA VBE DDC Level none
(II) R128(0): VESA VBE DDC transfer in appr. 2 sec.
(II) R128(0): VESA VBE DDC read failed
(==) R128(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) R128(0): I2C bus "DDC" initialized.
(II) R128(0): I2C device "DDC:ddc2" registered at address 0xA0.
(EE) R128(0): No DFP detected
(II) R128(0): External VGA: Using default hsync range of 31.50-37.90 kHz
(II) R128(0): External VGA: Using default vrefresh range of 50.00-70.00 Hz
(II) R128(0): Clock range:  12.50 to 350.00 MHz
(II) R128(0): Not using mode "1024x786_60.00" (hsync out of range)
(II) R128(0): Not using default mode "640x350" (vrefresh out of range)
(II) R128(0): Not using default mode "320x175" (vrefresh out of range)
(II) R128(0): Not using default mode "640x400" (vrefresh out of range)
(II) R128(0): Not using default mode "320x200" (vrefresh out of range)
(II) R128(0): Not using default mode "720x400" (vrefresh out of range)
(II) R128(0): Not using default mode "360x200" (vrefresh out of range)
(II) R128(0): Not using default mode "640x480" (vrefresh out of range)
(II) R128(0): Not using default mode "320x240" (vrefresh out of range)
(II) R128(0): Not using default mode "640x480" (vrefresh out of range)
(II) R128(0): Not using default mode "320x240" (vrefresh out of range)
(II) R128(0): Not using default mode "640x480" (hsync out of range)
(II) R128(0): Not using default mode "320x240" (hsync out of range)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "400x300" (hsync out of range)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "400x300" (hsync out of range)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "400x300" (hsync out of range)
(II) R128(0): Not using default mode "1024x768" (vrefresh out of range)
(II) R128(0): Not using default mode "512x384" (vrefresh out of range)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "512x384" (hsync out of range)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "512x384" (hsync out of range)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "512x384" (hsync out of range)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "512x384" (hsync out of range)
(II) R128(0): Not using default mode "1152x864" (hsync out of range)
(II) R128(0): Not using default mode "576x432" (hsync out of range)
(II) R128(0): Not using default mode "1280x960" (hsync out of range)
(II) R128(0): Not using default mode "640x480" (hsync out of range)
(II) R128(0): Not using default mode "1280x960" (hsync out of range)
(II) R128(0): Not using default mode "640x480" (hsync out of range)
(II) R128(0): Not using default mode "1280x1024" (hsync out of range)
(II) R128(0): Not using default mode "640x512" (hsync out of range)
(II) R128(0): Not using default mode "1280x1024" (hsync out of range)
(II) R128(0): Not using default mode "640x512" (hsync out of range)
(II) R128(0): Not using default mode "1280x1024" (hsync out of range)
(II) R128(0): Not using default mode "640x512" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (hsync out of range)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (hsync out of range)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (hsync out of range)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (hsync out of range)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (hsync out of range)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1792x1344" (hsync out of range)
(II) R128(0): Not using default mode "896x672" (hsync out of range)
(II) R128(0): Not using default mode "1792x1344" (hsync out of range)
(II) R128(0): Not using default mode "896x672" (hsync out of range)
(II) R128(0): Not using default mode "1856x1392" (hsync out of range)
(II) R128(0): Not using default mode "928x696" (hsync out of range)
(II) R128(0): Not using default mode "1856x1392" (hsync out of range)
(II) R128(0): Not using default mode "928x696" (hsync out of range)
(II) R128(0): Not using default mode "1920x1440" (hsync out of range)
(II) R128(0): Not using default mode "960x720" (hsync out of range)
(II) R128(0): Not using default mode "1920x1440" (hsync out of range)
(II) R128(0): Not using default mode "960x720" (hsync out of range)
(II) R128(0): Not using default mode "832x624" (hsync out of range)
(II) R128(0): Not using default mode "416x312" (hsync out of range)
(II) R128(0): Not using default mode "1152x864" (hsync out of range)
(II) R128(0): Not using default mode "576x432" (hsync out of range)
(II) R128(0): Not using default mode "1152x864" (hsync out of range)
(II) R128(0): Not using default mode "576x432" (hsync out of range)
(II) R128(0): Not using default mode "1152x864" (hsync out of range)
(II) R128(0): Not using default mode "576x432" (hsync out of range)
(II) R128(0): Not using default mode "1152x864" (hsync out of range)
(II) R128(0): Not using default mode "576x432" (hsync out of range)
(II) R128(0): Not using default mode "1152x864" (hsync out of range)
(II) R128(0): Not using default mode "576x432" (hsync out of range)
(II) R128(0): Not using default mode "1152x864" (hsync out of range)
(II) R128(0): Not using default mode "576x432" (hsync out of range)
(II) R128(0): Not using default mode "1360x768" (hsync out of range)
(II) R128(0): Not using default mode "680x384" (hsync out of range)
(II) R128(0): Not using default mode "1360x768" (hsync out of range)
(II) R128(0): Not using default mode "680x384" (hsync out of range)
(II) R128(0): Not using default mode "1400x1050" (hsync out of range)
(II) R128(0): Not using default mode "700x525" (hsync out of range)
(II) R128(0): Not using default mode "1400x1050" (hsync out of range)
(II) R128(0): Not using default mode "700x525" (hsync out of range)
(II) R128(0): Not using default mode "1400x1050" (hsync out of range)
(II) R128(0): Not using default mode "700x525" (hsync out of range)
(II) R128(0): Not using default mode "1400x1050" (hsync out of range)
(II) R128(0): Not using default mode "700x525" (hsync out of range)
(II) R128(0): Not using default mode "1440x900" (hsync out of range)
(II) R128(0): Not using default mode "720x450" (hsync out of range)
(II) R128(0): Not using default mode "1600x1024" (hsync out of range)
(II) R128(0): Not using default mode "800x512" (hsync out of range)
(II) R128(0): Not using default mode "1680x1050" (hsync out of range)
(II) R128(0): Not using default mode "840x525" (hsync out of range)
(II) R128(0): Not using default mode "1680x1050" (hsync out of range)
(II) R128(0): Not using default mode "840x525" (hsync out of range)
(II) R128(0): Not using default mode "1680x1050" (hsync out of range)
(II) R128(0): Not using default mode "840x525" (hsync out of range)
(II) R128(0): Not using default mode "1680x1050" (hsync out of range)
(II) R128(0): Not using default mode "840x525" (hsync out of range)
(II) R128(0): Not using default mode "1680x1050" (hsync out of range)
(II) R128(0): Not using default mode "840x525" (hsync out of range)
(II) R128(0): Not using default mode "1920x1080" (hsync out of range)
(II) R128(0): Not using default mode "960x540" (hsync out of range)
(II) R128(0): Not using default mode "1920x1200" (hsync out of range)
(II) R128(0): Not using default mode "960x600" (hsync out of range)
(II) R128(0): Not using default mode "1920x1440" (hsync out of range)
(II) R128(0): Not using default mode "960x720" (hsync out of range)
(II) R128(0): Not using default mode "2048x1536" (hsync out of range)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "2048x1536" (hsync out of range)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using mode "1024x768" (no mode of this name)
(--) R128(0): Virtual size is 800x600 (pitch 800)
(**) R128(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) R128(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) R128(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) R128(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) R128(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) R128(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) R128(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) R128(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) R128(0):  Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) R128(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
(**) R128(0):  Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) R128(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(==) R128(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.2.1
    ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "shadowfb"
(II) LoadModule: "shadowfb"
(II) Loading /usr/lib/xorg/modules/libshadowfb.so
(II) Module shadowfb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) R128(0): Page flipping disabled
(!!) R128(0): For information on using the multimedia capabilities
    of this adapter, please see http://gatos.sf.net.
(--) Depth 24 pixmap format is 32 bpp
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: Searching for BusID pci:0000:05:04.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:05:04.0
(II) [drm] loaded kernel module for "r128" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) R128(0): [drm] Using the DRM lock SAREA also for drawables.
(II) R128(0): [drm] framebuffer handle = 0xf8000000
(II) R128(0): [drm] added 1 reserved context for kernel
(II) R128(0): X context handle = 0x1
(II) R128(0): [drm] installed DRM signal handler
(WW) R128(0): [agp] AGP not available
(WW) R128(0): [agp] AGP failed to initialize -- falling back to PCI mode.
(WW) R128(0): [agp] Make sure you have the agpgart kernel module loaded.
(II) R128(0): [pci] 8192 kB allocated with handle 0xf84a0000
(II) R128(0): [pci] ring handle = 0xf84a0000
(II) R128(0): [pci] Ring mapped at 0xb76ab000
(II) R128(0): [pci] Ring contents 0x00000000
(II) R128(0): [pci] ring read ptr handle = 0xf85a1000
(II) R128(0): [pci] Ring read ptr mapped at 0xb77ca000
(II) R128(0): [pci] Ring read ptr contents 0x00000000
(II) R128(0): [pci] vertex/indirect buffers handle = 0xf85a2000
(II) R128(0): [pci] Vertex/indirect buffers mapped at 0xb646b000
(II) R128(0): [pci] Vertex/indirect buffers contents 0x00000000
(II) R128(0): [drm] register handle = 0xfc400000
(II) R128(0): [dri] Visual configs initialized
(II) R128(0): CCE in BM mode
(II) R128(0): Using 8 MB AGP aperture
(II) R128(0): Using 1 MB for the ring buffer
(II) R128(0): Using 2 MB for vertex/indirect buffers
(II) R128(0): Using 5 MB for AGP textures
(II) R128(0): Memory manager initialized to (0,0) (800,2457)
(II) R128(0): Reserved area from (0,600) to (800,602)
(II) R128(0): Largest offscreen area available: 800 x 1855
(II) R128(0): Reserved back buffer from (0,602) to (800,1202)
(II) R128(0): Reserved depth buffer from (0,1202) to (800,1803)
(II) R128(0): Reserved depth span from (0,1802) offset 0x57fd00
(II) R128(0): Reserved 8704 kb for textures at offset 0x77f880
(II) R128(0): Using XFree86 Acceleration Architecture (XAA)
    Screen to screen bit blits
    Solid filled rectangles
    8x8 mono pattern filled rectangles
    Indirect CPU to Screen color expansion
    Solid Lines
    Dashed Lines
    Setting up tile and stipple cache:
        30 128x128 slots
(II) R128(0): Acceleration enabled
(==) R128(0): Backing store disabled
(==) R128(0): Silken mouse enabled
(II) R128(0): Using hardware cursor (scanline 7212)
(II) R128(0): Largest offscreen area available: 800 x 651
(==) R128(0): DPMS enabled
(WW) R128(0): Option "Monitor-VGA-0" is not used
(WW) R128(0): Option "PreferredMode" is not used
(II) R128(0): [DRI] installation complete
(II) R128(0): [drm] Added 128 16384 byte vertex/indirect buffers
(II) R128(0): [drm] Mapped 128 vertex/indirect buffers
(II) R128(0): [drm] dma control initialized, using IRQ 16
(II) R128(0): Direct rendering enabled
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: Searching for BusID pci:0000:05:04.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: drmOpenMinor returns 12
drmOpenByBusid: drmGetBusid reports pci:0000:05:04.0
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: Loaded and initialized /usr/lib/dri/r128_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) (/dev/input/event4)
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Applying InputClass "evdev pointer catchall"
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): always reports core events
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Device: "/dev/input/event4"
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found 3 mouse buttons
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found scroll wheel(s)
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found relative axes
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found x and y relative axes
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Configuring as mouse
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): YAxisMapping: buttons 4 and 5
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)" (type: MOUSE)
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): initialized for relative axes.
(II) config/udev: Adding input device Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)

```

---

### Post by jmate on 2010-12-24
It's fixed! YES!

The root cause was that ubuntu had no idea what monitor I was using. You can't find it online. It's a FORTEC star monitor. As a result, it gave it a default hsync and vrefresh range. These ranges did not allow anything above 800x600 to work. It was just a matter of creating my own xorg.conf with my own hsync and vrefresh ranges.

I hope this information will be valuable to someone.

Cheers

```

Section "Monitor"
    VendorName      "FORTEC"
    Identifier      "External VGA"
    HorizSync       30 - 50
    VertRefresh     50 - 70
    #Modeline        "1024x786_60.00"   65.75  1024 1080 1184 1344  786 789 799 816 -hsync +vsync
    Option          "PreferredMode" "800x600"
    #Option          "PreferredMode" "1024x786_60.00"
EndSection

Section "Device"
    Identifier      "Rage 128 Pro Ultra TR"
    Driver          "ati"
    Option          "Monitor-VGA-0" "External VGA"
EndSection

Section "Screen"
    Identifier      "Primary Screen"
    Monitor         "External VGA"
    Device          "Rage 128 Pro Ultra TR"
    DefaultDepth    24
    SubSection "Display"
        Depth           24
        Modes   "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier      "Default Layout"
    Screen          "Primary Screen"
EndSection

```

---

### Post by akand074 on 2010-12-24
Congratulations on fixing the problem! Mark this thread as "Solved" from the thread tools at the top to make it easier for people to find this thread to help solve issues.

---

