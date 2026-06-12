---
title: "Running into trouble, monitor won't retun DCC probe info"
date: 2013-08-30
forum: Hardware
---

### Post by Jerry_Biehler on 2013-08-30
I am installing the LinuxCNC package which runs on 10.04. This is an industrial system with a PIII SBC with the Rage Pro video chip built on board. 

I ran into a problem, the industrial monitor I am using is not returning any DCC info and Ubuntu is limiting my max resolution to 800x600 on this 1024x768 monitor. To verify the problem I hooked up another monitor and restarted and it worked fine with all the resolutions shown, I selected 1024x768 and switched to that and it was happy. I then hot plugged the industrial monitor in and it ran just fine at the modeline the other monitor was running at.

So, I rebooted with the old monitor and used xrandr to try and set the resolution:

```
xrandr --newmode "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync xrandr --addmode default 1024x768

```

This brought up the 1024x768 option in the display properties, I click on it and hit apply and get a popup notification that says "The selected configuration for displays could not be applied CRTC 263" 

Argh!

Here is my xorg.0.log:

```
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
Current Operating System: Linux laser-welder 2.6.32-122-rtai #rtai SMP Tue Jul 27 12:44:07 CDT 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-122-rtai root=UUID=2db8cf1d-36c6-4fd6-8e30-f58424c08026 ro quiet splash
Build Date: 25 February 2012  06:59:39AM
xorg-server 2:1.7.6-2ubuntu7.11 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Aug 29 13:52:44 2013
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7


(--) PCI: (0:0:18:0) 1039:0300:1039:0300 Silicon Integrated Systems [SiS] 300/305 PCI/AGP VGA Display Adapter rev 144, Mem @ 0xd0000000/134217728, 0xe1000000/131072, I/O @ 0x0000e400/128, BIOS @ 0x????????/65536
(--) PCI:*(0:1:0:0) 1002:4742:0000:0040 ATI Technologies Inc 3D Rage Pro AGP 1X/2X rev 92, Mem @ 0xd8000000/16777216, 0xda000000/4096, I/O @ 0x0000d000/256, BIOS @ 0x????????/131072
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
(II) LoadModule: "mach64"
(II) Loading /usr/lib/xorg/modules/drivers/mach64_drv.so
(II) Module mach64: vendor="X.Org Foundation"
    compiled for 1.7.2, module version = 6.8.2
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
(II) MACH64: Driver for ATI Mach64 chipsets
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.0.2
    ABI class: X.Org Video Driver, version 6.0
(II) MACH64(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
(==) MACH64(0): Depth 24, (--) framebuffer bpp 32
(==) MACH64(0): Using XAA acceleration architecture
(II) MACH64: Mach64 in slot 1:0:0 detected.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Video Driver, version 6.0
(II) MACH64(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Video Driver, version 6.0
(II) MACH64(0): VESA BIOS detected
(II) MACH64(0): VESA VBE Version 2.0
(II) MACH64(0): VESA VBE Total Mem: 4096 kB
(II) MACH64(0): VESA VBE OEM: ATI MACH64
(II) MACH64(0): VESA VBE OEM Software Rev: 1.0
(II) MACH64(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) MACH64(0): VESA VBE OEM Product: MACH64GT
(II) MACH64(0): VESA VBE OEM Product Rev: 01.00
(II) MACH64(0): VESA VBE DDC supported
(II) MACH64(0): VESA VBE DDC Level none
(II) MACH64(0): VESA VBE DDC transfer in appr. 2 sec.
(II) MACH64(0): VESA VBE DDC read failed
(II) MACH64(0): BIOS Data:  BIOSSize=0x8000, ROMTable=0x00F4.
(II) MACH64(0): BIOS Data:  ClockTable=0x0700, FrequencyTable=0x0000.
(II) MACH64(0): BIOS Data:  LCDTable=0x0000.
(II) MACH64(0): BIOS Data:  VideoTable=0x0000, HardwareTable=0x013E.
(II) MACH64(0): BIOS Data:  I2CType=0x02, Tuner=0x00, Decoder=0x00, Audio=0x0F.
(--) MACH64(0): ATI 3D Rage Pro graphics controller detected.
(--) MACH64(0): Chip type 4742 "GB", version 4, foundry UMC, class 0, revision 0x01.
(--) MACH64(0): AGP bus interface detected;  block I/O base is 0xD000.
(--) MACH64(0): ATI Mach64 adapter detected.
(!!) MACH64(0): For information on using the multimedia capabilities
    of this adapter, please see http://gatos.sf.net.
(--) MACH64(0): Internal RAMDAC (subtype 1) detected.
(==) MACH64(0): RGB weight 888
(==) MACH64(0): Default visual is TrueColor
(==) MACH64(0): Using gamma correction (1.0, 1.0, 1.0)
(II) MACH64(0): Using Mach64 accelerator CRTC.
(II) MACH64(0): Storing hardware cursor image at 0xD83FFC00.
(II) MACH64(0): Using 8 MB linear aperture at 0xD8000000.
(!!) MACH64(0): Virtual resolutions will be limited to 4095 kB
 due to linear aperture size and/or placement of hardware cursor image area.
(II) MACH64(0): Using Block 0 MMIO aperture at 0xDA000400.
(II) MACH64(0): Using Block 1 MMIO aperture at 0xDA000000.
(II) MACH64(0): MMIO write caching enabled.
(--) MACH64(0): 4096 kB of SGRAM (1:1) detected (using 4095 kB).
(WW) MACH64(0): Cannot shadow an accelerated frame buffer.
(II) MACH64(0): Engine XCLK 99.765 MHz;  Refresh rate code 7.
(--) MACH64(0): Internal programmable clock generator detected.
(--) MACH64(0): Reference clock 157.5/11 (14.318) MHz.
(II) MACH64(0): <default monitor>: Using default hsync range of 31.50-37.90 kHz
(II) MACH64(0): <default monitor>: Using default vrefresh range of 50.00-70.00 Hz
(WW) MACH64(0): Unable to estimate virtual size
(II) MACH64(0): Maximum clock: 199.00 MHz
(II) MACH64(0): Not using default mode "640x350" (vrefresh out of range)
(II) MACH64(0): Not using default mode "320x175" (vrefresh out of range)
(II) MACH64(0): Not using default mode "640x400" (vrefresh out of range)
(II) MACH64(0): Not using default mode "320x200" (vrefresh out of range)
(II) MACH64(0): Not using default mode "720x400" (vrefresh out of range)
(II) MACH64(0): Not using default mode "360x200" (vrefresh out of range)
(II) MACH64(0): Not using default mode "640x480" (vrefresh out of range)
(II) MACH64(0): Not using default mode "320x240" (vrefresh out of range)
(II) MACH64(0): Not using default mode "640x480" (vrefresh out of range)
(II) MACH64(0): Not using default mode "320x240" (vrefresh out of range)
(II) MACH64(0): Not using default mode "640x480" (hsync out of range)
(II) MACH64(0): Not using default mode "320x240" (hsync out of range)
(II) MACH64(0): Not using default mode "800x600" (hsync out of range)
(II) MACH64(0): Not using default mode "400x300" (hsync out of range)
(II) MACH64(0): Not using default mode "800x600" (hsync out of range)
(II) MACH64(0): Not using default mode "400x300" (hsync out of range)
(II) MACH64(0): Not using default mode "800x600" (hsync out of range)
(II) MACH64(0): Not using default mode "400x300" (hsync out of range)
(II) MACH64(0): Not using default mode "1024x768" (vrefresh out of range)
(II) MACH64(0): Not using default mode "512x384" (vrefresh out of range)
(II) MACH64(0): Not using default mode "1024x768" (hsync out of range)
(II) MACH64(0): Not using default mode "512x384" (hsync out of range)
(II) MACH64(0): Not using default mode "1024x768" (hsync out of range)
(II) MACH64(0): Not using default mode "512x384" (hsync out of range)
(II) MACH64(0): Not using default mode "1024x768" (hsync out of range)
(II) MACH64(0): Not using default mode "512x384" (hsync out of range)
(II) MACH64(0): Not using default mode "1024x768" (hsync out of range)
(II) MACH64(0): Not using default mode "512x384" (hsync out of range)
(II) MACH64(0): Not using default mode "1152x864" (hsync out of range)
(II) MACH64(0): Not using default mode "576x432" (hsync out of range)
(II) MACH64(0): Not using default mode "1280x960" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "640x480" (hsync out of range)
(II) MACH64(0): Not using default mode "1280x960" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "640x480" (hsync out of range)
(II) MACH64(0): Not using default mode "1280x1024" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "640x512" (hsync out of range)
(II) MACH64(0): Not using default mode "1280x1024" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "640x512" (hsync out of range)
(II) MACH64(0): Not using default mode "1280x1024" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "640x512" (hsync out of range)
(II) MACH64(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "800x600" (hsync out of range)
(II) MACH64(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "800x600" (hsync out of range)
(II) MACH64(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "800x600" (hsync out of range)
(II) MACH64(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "800x600" (hsync out of range)
(II) MACH64(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "800x600" (hsync out of range)
(II) MACH64(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "896x672" (hsync out of range)
(II) MACH64(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "896x672" (hsync out of range)
(II) MACH64(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "928x696" (hsync out of range)
(II) MACH64(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "928x696" (hsync out of range)
(II) MACH64(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "960x720" (hsync out of range)
(II) MACH64(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "960x720" (hsync out of range)
(II) MACH64(0): Not using default mode "832x624" (hsync out of range)
(II) MACH64(0): Not using default mode "416x312" (hsync out of range)
(II) MACH64(0): Not using default mode "1152x864" (hsync out of range)
(II) MACH64(0): Not using default mode "576x432" (hsync out of range)
(II) MACH64(0): Not using default mode "1152x864" (hsync out of range)
(II) MACH64(0): Not using default mode "576x432" (hsync out of range)
(II) MACH64(0): Not using default mode "1152x864" (hsync out of range)
(II) MACH64(0): Not using default mode "576x432" (hsync out of range)
(II) MACH64(0): Not using default mode "1152x864" (hsync out of range)
(II) MACH64(0): Not using default mode "576x432" (hsync out of range)
(II) MACH64(0): Not using default mode "1152x864" (hsync out of range)
(II) MACH64(0): Not using default mode "576x432" (hsync out of range)
(II) MACH64(0): Not using default mode "1152x864" (hsync out of range)
(II) MACH64(0): Not using default mode "576x432" (hsync out of range)
(II) MACH64(0): Not using default mode "1360x768" (hsync out of range)
(II) MACH64(0): Not using default mode "680x384" (hsync out of range)
(II) MACH64(0): Not using default mode "1360x768" (hsync out of range)
(II) MACH64(0): Not using default mode "680x384" (hsync out of range)
(II) MACH64(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "700x525" (hsync out of range)
(II) MACH64(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "700x525" (hsync out of range)
(II) MACH64(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "700x525" (hsync out of range)
(II) MACH64(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "700x525" (hsync out of range)
(II) MACH64(0): Not using default mode "1440x900" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "720x450" (hsync out of range)
(II) MACH64(0): Not using default mode "1600x1024" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "800x512" (hsync out of range)
(II) MACH64(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "840x525" (hsync out of range)
(II) MACH64(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "840x525" (hsync out of range)
(II) MACH64(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "840x525" (hsync out of range)
(II) MACH64(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "840x525" (hsync out of range)
(II) MACH64(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "840x525" (hsync out of range)
(II) MACH64(0): Not using default mode "1920x1080" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "960x540" (hsync out of range)
(II) MACH64(0): Not using default mode "1920x1200" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "960x600" (hsync out of range)
(II) MACH64(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "960x720" (hsync out of range)
(II) MACH64(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1024x768" (hsync out of range)
(II) MACH64(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1024x768" (hsync out of range)
(II) MACH64(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1024x768" (hsync out of range)
(--) MACH64(0): Virtual size is 800x600 (pitch 800)
(**) MACH64(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) MACH64(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) MACH64(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) MACH64(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) MACH64(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) MACH64(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) MACH64(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) MACH64(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) MACH64(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) MACH64(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
(**) MACH64(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) MACH64(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(==) MACH64(0): DPI set to (96, 96)
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
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) MACH64(0): I2C bus "Mach64" initialized.
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(--) Depth 24 pixmap format is 32 bpp
(WW) MACH64(0): DRI static buffer allocation failed -- need at least 4687 kB video memory
(II) MACH64(0): Largest offscreen areas (with overlaps):
(II) MACH64(0):     800 x 710 rectangle at 0,600
(II) MACH64(0):     320 x 711 rectangle at 0,600
(II) MACH64(0): Using XFree86 Acceleration Architecture (XAA)
    Screen to screen bit blits
    Solid filled rectangles
    8x8 mono pattern filled rectangles
    Indirect CPU to Screen color expansion
    Solid Lines
    Setting up tile and stipple cache:
        30 128x128 slots
(==) MACH64(0): Backing store disabled
(==) MACH64(0): Silken mouse enabled
(==) MACH64(0): DPMS enabled
(II) MACH64(0): Direct rendering disabled
(==) RandR enabled
(II) Found 2 VGA devices: arbiter wrapping enabled
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
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Link keybd (/dev/input/event2)
(**) Link keybd: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Link keybd: always reports core events
(**) Link keybd: Device: "/dev/input/event2"
(II) Link keybd: Found keys
(II) Link keybd: Configuring as keyboard
(II) XINPUT: Adding extended input device "Link keybd" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Link keybd (/dev/input/event3)
(**) Link keybd: Applying InputClass "evdev pointer catchall"
(**) Link keybd: always reports core events
(**) Link keybd: Device: "/dev/input/event3"
(II) Link keybd: Found 3 mouse buttons
(II) Link keybd: Found relative axes
(II) Link keybd: Found x and y relative axes
(II) Link keybd: Configuring as mouse
(**) Link keybd: YAxisMapping: buttons 4 and 5
(**) Link keybd: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Link keybd" (type: MOUSE)
(II) Link keybd: initialized for relative axes.
(II) config/udev: Adding input device Link keybd (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event1)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event4)
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.2.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.2
(**) Option "Device" "/dev/input/event4"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event0)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
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

