---
title: "Resolution stuck at 800x600 - need driver help"
date: 2010-07-07
forum: Hardware
---

### Post by ZaphodFJ on 2010-07-07
Hi,

I posted this on the 'Absolute Beginner Talk' forum a few days ago - but thanks to all the new stuff posted there, I doubt if anyone will see it now!

In brief - my system is not identifying the graphics hardware properly.  Or, if it is, thinks it cannot do above 800x600.

To avoid cross-posting, please look at the original post/reply/my follow-up, at:

[http://ubuntuforums.org/showthread.php?t=1524659](http://ubuntuforums.org/showthread.php?t=1524659)

Thanks in advance!
ZFJ

---

### Post by Yellow Pasque on 2010-07-07
Post or pastebin your /var/log/Xorg.0.log file (use [ code ][ /code ] tags or better yet, use [http://ubuntu.pastebin.com/](http://ubuntu.pastebin.com/) and just link to it).

---

### Post by ZaphodFJ on 2010-07-08
Thanks.  It says:

<script  src="http://pastebin.com/embed_js.php?i=7ASTkMck"></script>

---

### Post by ZaphodFJ on 2010-07-08
Oops - let's try that again

```


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux zaphod-desktop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-23-generic root=UUID=f24d017a-4066-4a9b-8fd6-3b652e4da297 ro quiet splash
Build Date: 16 June 2010  09:31:32AM
xorg-server 2:1.7.6-2ubuntu7.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Jul  7 16:56:24 2010
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

(--) PCI:*(0:1:0:0) 5333:8d04:1462:7870 S3 Inc. VT8375 [ProSavage8 KM266/KL266] rev 0, Mem @ 0xed000000/524288, 0xe0000000/134217728, BIOS @ 0x????????/65536
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
(==) Matched savage as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "savage"
(II) Loading /usr/lib/xorg/modules/drivers/savage_drv.so
(II) Module savage: vendor="X.Org Foundation"
    compiled for 1.7.2, module version = 2.3.1
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
(II) SAVAGE: driver (version 2.3.1) for S3 Savage chipsets: Savage4,
    Savage3D, Savage3D-MV, Savage2000, Savage/MX-MV, Savage/MX,
    Savage/IX-MV, Savage/IX, ProSavage PM133, ProSavage KM133,
    Twister PN133, Twister KN133, SuperSavage/MX 128, SuperSavage/MX 64,
    SuperSavage/MX 64C, SuperSavage/IX 128, SuperSavage/IX 128,
    SuperSavage/IX 64, SuperSavage/IX 64, SuperSavage/IXC 64,
    SuperSavage/IXC 64, ProSavage DDR, ProSavage DDR-K
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
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.1.0
    ABI class: X.Org Video Driver, version 6.0
(II) SAVAGE(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 16/16
(==) SAVAGE(0): Depth 16, (--) framebuffer bpp 16
(==) SAVAGE(0): RGB weight 565
(==) SAVAGE(0): Default visual is TrueColor
(II) SAVAGE(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) SAVAGE(0): Using XAA acceleration architecture
(==) SAVAGE(0): Using HW cursor
(==) SAVAGE(0): Using video BIOS to set modes
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Video Driver, version 6.0
(II) SAVAGE(0): initializing int10
(II) SAVAGE(0): Primary V_BIOS segment is: 0xc000
(II) SAVAGE(0): VESA BIOS detected
(II) SAVAGE(0): VESA VBE Version 3.0
(II) SAVAGE(0): VESA VBE Total Mem: 31680 kB
(II) SAVAGE(0): VESA VBE OEM: S3 Graphics ProSavage DDR Family BIOS
(II) SAVAGE(0): VESA VBE OEM Software Rev: 2.0
(II) SAVAGE(0): VESA VBE OEM Vendor: S3 Garphics Incorporated.
(II) SAVAGE(0): VESA VBE OEM Product: VBE 3.0
(II) SAVAGE(0): VESA VBE OEM Product Rev: Rev 0.0
(--) SAVAGE(0): Chip: id 8d04, "ProSavage DDR-K"
(--) SAVAGE(0): Engine: "ProSavageDDR"
(--) SAVAGE(0): AGP card detected
(==) SAVAGE(0): Using BusType PCI by default
(==) SAVAGE(0): Using PCI DMA
(==) SAVAGE(0): Will try command and vertex DMA mode
(==) SAVAGE(0): Using gamma correction (1.0, 1.0, 1.0)
(--) SAVAGE(0): probed videoram:  32768k
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(--) SAVAGE(0): No DDC signal
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) SAVAGE(0): I2C bus "I2C bus" initialized.
(II) SAVAGE(0): I2C device "I2C bus:ddc2" registered at address 0xA0.
(--) SAVAGE(0): Detected current MCLK value of 14.318 MHz
(--) SAVAGE(0): 1904x2042 TFT LCD panel detected but not active
(--) SAVAGE(0): Found 5 modes at this depth:
    [111] 640 x 480, 60Hz, 75Hz, 85Hz, 100Hz, 160Hz
    [114] 800 x 600, 60Hz, 75Hz, 85Hz
    [117] 1024 x 768, 60Hz, 70Hz, 75Hz, 85Hz, 100Hz, 130Hz
    [11a] 1280 x 1024, 60Hz, 75Hz, 85Hz, 100Hz
    [122] 1600 x 1200, 60Hz
(II) SAVAGE(0): <default monitor>: Using default hsync range of 31.50-37.90 kHz
(II) SAVAGE(0): <default monitor>: Using default vrefresh range of 50.00-70.00 Hz
(WW) SAVAGE(0): Unable to estimate virtual size
(II) SAVAGE(0): Clock range:  10.00 to 250.00 MHz
(--) SAVAGE(0): No suitable BIOS mode found for 640x350 85Hz.
(II) SAVAGE(0): Not using default mode "640x350" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 320x175 85Hz.
(II) SAVAGE(0): Not using default mode "320x175" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 640x400 85Hz.
(II) SAVAGE(0): Not using default mode "640x400" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 320x200 85Hz.
(II) SAVAGE(0): Not using default mode "320x200" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 720x400 85Hz.
(II) SAVAGE(0): Not using default mode "720x400" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 360x200 85Hz.
(II) SAVAGE(0): Not using default mode "360x200" (no mode of this name)
(--) SAVAGE(0): Chose mode 111 at 60Hz.
(--) SAVAGE(0): No suitable BIOS mode found for 320x240 60Hz.
(II) SAVAGE(0): Not using default mode "320x240" (no mode of this name)
(--) SAVAGE(0): Chose mode 111 at 75Hz.
(II) SAVAGE(0): Not using default mode "640x480" (vrefresh out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 320x240 72Hz.
(II) SAVAGE(0): Not using default mode "320x240" (no mode of this name)
(--) SAVAGE(0): Chose mode 111 at 75Hz.
(II) SAVAGE(0): Not using default mode "640x480" (vrefresh out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 320x240 75Hz.
(II) SAVAGE(0): Not using default mode "320x240" (no mode of this name)
(--) SAVAGE(0): Chose mode 111 at 85Hz.
(II) SAVAGE(0): Not using default mode "640x480" (hsync out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 320x240 85Hz.
(II) SAVAGE(0): Not using default mode "320x240" (no mode of this name)
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(--) SAVAGE(0): No suitable BIOS mode found for 400x300 56Hz.
(II) SAVAGE(0): Not using default mode "400x300" (no mode of this name)
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(--) SAVAGE(0): No suitable BIOS mode found for 400x300 60Hz.
(II) SAVAGE(0): Not using default mode "400x300" (no mode of this name)
(--) SAVAGE(0): Chose mode 114 at 75Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 400x300 72Hz.
(II) SAVAGE(0): Not using default mode "400x300" (no mode of this name)
(--) SAVAGE(0): Chose mode 114 at 75Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 400x300 75Hz.
(II) SAVAGE(0): Not using default mode "400x300" (no mode of this name)
(--) SAVAGE(0): Chose mode 114 at 85Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 400x300 85Hz.
(II) SAVAGE(0): Not using default mode "400x300" (no mode of this name)
(--) SAVAGE(0): Chose mode 117 at 85Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (vrefresh out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 512x384 87Hz.
(II) SAVAGE(0): Not using default mode "512x384" (no mode of this name)
(--) SAVAGE(0): Chose mode 117 at 60Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 512x384 60Hz.
(II) SAVAGE(0): Not using default mode "512x384" (no mode of this name)
(--) SAVAGE(0): Chose mode 117 at 70Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 512x384 70Hz.
(II) SAVAGE(0): Not using default mode "512x384" (no mode of this name)
(--) SAVAGE(0): Chose mode 117 at 75Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 512x384 75Hz.
(II) SAVAGE(0): Not using default mode "512x384" (no mode of this name)
(--) SAVAGE(0): Chose mode 117 at 85Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 512x384 84Hz.
(II) SAVAGE(0): Not using default mode "512x384" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1152x864 75Hz.
(II) SAVAGE(0): Not using default mode "1152x864" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 75Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1280x960 60Hz.
(II) SAVAGE(0): Not using default mode "1280x960" (no mode of this name)
(--) SAVAGE(0): Chose mode 111 at 60Hz.
(II) SAVAGE(0): Not using default mode "640x480" (hsync out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 1280x960 85Hz.
(II) SAVAGE(0): Not using default mode "1280x960" (no mode of this name)
(--) SAVAGE(0): Chose mode 111 at 85Hz.
(II) SAVAGE(0): Not using default mode "640x480" (hsync out of range)
(--) SAVAGE(0): Chose mode 11a at 60Hz.
(II) SAVAGE(0): Not using default mode "1280x1024" (hsync out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 640x512 60Hz.
(II) SAVAGE(0): Not using default mode "640x512" (no mode of this name)
(--) SAVAGE(0): Chose mode 11a at 75Hz.
(II) SAVAGE(0): Not using default mode "1280x1024" (hsync out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 640x512 75Hz.
(II) SAVAGE(0): Not using default mode "640x512" (no mode of this name)
(--) SAVAGE(0): Chose mode 11a at 85Hz.
(II) SAVAGE(0): Not using default mode "1280x1024" (hsync out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 640x512 85Hz.
(II) SAVAGE(0): Not using default mode "640x512" (no mode of this name)
(--) SAVAGE(0): Chose mode 122 at 60Hz.
(II) SAVAGE(0): Not using default mode "1600x1200" (hsync out of range)
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(--) SAVAGE(0): Chose mode 122 at 60Hz.
(II) SAVAGE(0): Not using default mode "1600x1200" (hsync out of range)
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(--) SAVAGE(0): Chose mode 122 at 60Hz.
(II) SAVAGE(0): Not using default mode "1600x1200" (hsync out of range)
(--) SAVAGE(0): Chose mode 114 at 75Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(--) SAVAGE(0): Chose mode 122 at 60Hz.
(II) SAVAGE(0): Not using default mode "1600x1200" (hsync out of range)
(--) SAVAGE(0): Chose mode 114 at 75Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(--) SAVAGE(0): Chose mode 122 at 60Hz.
(II) SAVAGE(0): Not using default mode "1600x1200" (hsync out of range)
(--) SAVAGE(0): Chose mode 114 at 85Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 1792x1344 60Hz.
(II) SAVAGE(0): Not using default mode "1792x1344" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 896x672 60Hz.
(II) SAVAGE(0): Not using default mode "896x672" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(--) SAVAGE(0): No suitable BIOS mode found for 896x672 75Hz.
(II) SAVAGE(0): Not using default mode "896x672" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1856x1392 60Hz.
(II) SAVAGE(0): Not using default mode "1856x1392" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 928x696 60Hz.
(II) SAVAGE(0): Not using default mode "928x696" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(--) SAVAGE(0): No suitable BIOS mode found for 928x696 75Hz.
(II) SAVAGE(0): Not using default mode "928x696" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1920x1440 60Hz.
(II) SAVAGE(0): Not using default mode "1920x1440" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 960x720 60Hz.
(II) SAVAGE(0): Not using default mode "960x720" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(--) SAVAGE(0): No suitable BIOS mode found for 960x720 75Hz.
(II) SAVAGE(0): Not using default mode "960x720" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 832x624 74Hz.
(II) SAVAGE(0): Not using default mode "832x624" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 416x312 74Hz.
(II) SAVAGE(0): Not using default mode "416x312" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1152x864 59Hz.
(II) SAVAGE(0): Not using default mode "1152x864" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 60Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1152x864 70Hz.
(II) SAVAGE(0): Not using default mode "1152x864" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 70Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1152x864 74Hz.
(II) SAVAGE(0): Not using default mode "1152x864" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 74Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1152x864 84Hz.
(II) SAVAGE(0): Not using default mode "1152x864" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 85Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1152x864 85Hz.
(II) SAVAGE(0): Not using default mode "1152x864" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 85Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1152x864 99Hz.
(II) SAVAGE(0): Not using default mode "1152x864" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 100Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1360x768 59Hz.
(II) SAVAGE(0): Not using default mode "1360x768" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 680x384 59Hz.
(II) SAVAGE(0): Not using default mode "680x384" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1360x768 59Hz.
(II) SAVAGE(0): Not using default mode "1360x768" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 680x384 59Hz.
(II) SAVAGE(0): Not using default mode "680x384" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1400x1050 59Hz.
(II) SAVAGE(0): Not using default mode "1400x1050" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 700x525 59Hz.
(II) SAVAGE(0): Not using default mode "700x525" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1400x1050 69Hz.
(II) SAVAGE(0): Not using default mode "1400x1050" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 700x525 70Hz.
(II) SAVAGE(0): Not using default mode "700x525" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1400x1050 74Hz.
(II) SAVAGE(0): Not using default mode "1400x1050" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 700x525 74Hz.
(II) SAVAGE(0): Not using default mode "700x525" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1400x1050 85Hz.
(II) SAVAGE(0): Not using default mode "1400x1050" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 700x525 85Hz.
(II) SAVAGE(0): Not using default mode "700x525" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1440x900 59Hz.
(II) SAVAGE(0): Not using default mode "1440x900" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 720x450 59Hz.
(II) SAVAGE(0): Not using default mode "720x450" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1600x1024 60Hz.
(II) SAVAGE(0): Not using default mode "1600x1024" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 800x512 60Hz.
(II) SAVAGE(0): Not using default mode "800x512" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1680x1050 59Hz.
(II) SAVAGE(0): Not using default mode "1680x1050" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 840x525 59Hz.
(II) SAVAGE(0): Not using default mode "840x525" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1680x1050 59Hz.
(II) SAVAGE(0): Not using default mode "1680x1050" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 840x525 60Hz.
(II) SAVAGE(0): Not using default mode "840x525" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1680x1050 69Hz.
(II) SAVAGE(0): Not using default mode "1680x1050" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 840x525 69Hz.
(II) SAVAGE(0): Not using default mode "840x525" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1680x1050 74Hz.
(II) SAVAGE(0): Not using default mode "1680x1050" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 840x525 74Hz.
(II) SAVAGE(0): Not using default mode "840x525" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1680x1050 84Hz.
(II) SAVAGE(0): Not using default mode "1680x1050" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 840x525 85Hz.
(II) SAVAGE(0): Not using default mode "840x525" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1920x1080 59Hz.
(II) SAVAGE(0): Not using default mode "1920x1080" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 960x540 59Hz.
(II) SAVAGE(0): Not using default mode "960x540" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1920x1200 59Hz.
(II) SAVAGE(0): Not using default mode "1920x1200" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 960x600 59Hz.
(II) SAVAGE(0): Not using default mode "960x600" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(--) SAVAGE(0): No suitable BIOS mode found for 960x720 85Hz.
(II) SAVAGE(0): Not using default mode "960x720" (no mode of this name)
(II) SAVAGE(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(--) SAVAGE(0): Chose mode 117 at 60Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(II) SAVAGE(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(--) SAVAGE(0): Chose mode 117 at 75Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(II) SAVAGE(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(--) SAVAGE(0): Chose mode 117 at 85Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(--) SAVAGE(0): Chose mode 111 at 60Hz.
(--) SAVAGE(0): Virtual size is 800x600 (pitch 800)
(**) SAVAGE(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) SAVAGE(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) SAVAGE(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) SAVAGE(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) SAVAGE(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) SAVAGE(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(==) SAVAGE(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.2.1
    ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) SAVAGE(0): initializing int10
(II) SAVAGE(0): Primary V_BIOS segment is: 0xc000
(II) SAVAGE(0): VESA BIOS detected
(II) SAVAGE(0): VESA VBE Version 3.0
(II) SAVAGE(0): VESA VBE Total Mem: 31680 kB
(II) SAVAGE(0): VESA VBE OEM: S3 Graphics ProSavage DDR Family BIOS
(II) SAVAGE(0): VESA VBE OEM Software Rev: 2.0
(II) SAVAGE(0): VESA VBE OEM Vendor: S3 Garphics Incorporated.
(II) SAVAGE(0): VESA VBE OEM Product: VBE 3.0
(II) SAVAGE(0): VESA VBE OEM Product Rev: Rev 0.0
(WW) SAVAGE(0): Cannot read colourmap from VGA.  Will restore with default
(II) SAVAGE(0): 3096 kB of Videoram needed for 3D; 32768 kB of Videoram available
(II) SAVAGE(0): Sufficient Videoram available for 3D
(II) SAVAGE(0): [drm] bpp: 16 depth: 16
(II) SAVAGE(0): [drm] Sarea 2200+284: 2484
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] loaded kernel module for "savage" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) SAVAGE(0): [drm] Using the DRM lock SAREA also for drawables.
(II) SAVAGE(0): [drm] framebuffer handle = 0xe0000000
(II) SAVAGE(0): [drm] added 1 reserved context for kernel
(II) SAVAGE(0): X context handle = 0x1
(II) SAVAGE(0): [drm] installed DRM signal handler
(II) SAVAGE(0): [drm] aperture handle = 0xe0000000
(II) SAVAGE(0): [drm] PCI command DMA handle = 0x34300000
(II) SAVAGE(0): [drm] Enabling ShadowStatus for DRI.
(II) SAVAGE(0): [drm] Status handle = 0x3423e000
(II) SAVAGE(0): [drm] Status page mapped at 0xb77f9000
(II) SAVAGE(0): [dri] visual configs initialized
(**) SAVAGE(0): DRI is enabled
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(II) SAVAGE(0): virtualX:800,virtualY:600
(II) SAVAGE(0): bpp:16,tiledwidthBytes:1664,tiledBufferSize:1011712 
(II) SAVAGE(0): bpp:16,widthBytes:1664,BufferSize:999424 
(II) SAVAGE(0): videoRambytes:0x02000000 
(II) SAVAGE(0): textureSize:0x01afd000 
(II) SAVAGE(0): textureSize:0x01afd000 
(II) SAVAGE(0): textureOffset:0x004e2000 
(II) SAVAGE(0): depthOffset:0x003eb000,depthPitch:1664
(II) SAVAGE(0): backOffset:0x002f4000,backPitch:1664
(II) SAVAGE(0): Reserved back buffer at offset 0x2f4000
(II) SAVAGE(0): Reserved depth buffer at offset 0x3eb000
(II) SAVAGE(0): Reserved 27636 kb for textures at offset 0x4e2000
(II) SAVAGE(0): Using 1259 lines for offscreen memory.
(II) SAVAGE(0): Using XFree86 Acceleration Architecture (XAA)
    Screen to screen bit blits
    Solid filled rectangles
    8x8 mono pattern filled rectangles
    Indirect CPU to Screen color expansion
    Solid Lines
    Image Writes
    Setting up tile and stipple cache:
        30 128x128 slots
        6 256x256 slots
(==) SAVAGE(0): Backing store disabled
(==) SAVAGE(0): DPMS enabled
(II) SAVAGE(0): [DRI] installation complete
(II) SAVAGE(0): [junkers]pSAVAGEDRIServer:
(II) SAVAGE(0): [junkers]    reserved_map_agpstart:0x00000000
(II) SAVAGE(0): [junkers]    reserved_map_idx:0x00000000
(II) SAVAGE(0): [junkers]    sarea_priv_offset:0x00000000
(II) SAVAGE(0): [junkers]    chipset:0x00000000
(II) SAVAGE(0): [junkers]    sgram:0x00000000
(II) SAVAGE(0): [junkers]    frontbufferSize:0x000f4000
(II) SAVAGE(0): [junkers]    frontOffset:0x00000000
(II) SAVAGE(0): [junkers]    frontPitch:0x00000680
(II) SAVAGE(0): [junkers]    backbufferSize:0x000f7000
(II) SAVAGE(0): [junkers]    backOffset:0x002f4000
(II) SAVAGE(0): [junkers]    backPitch:0x00000680
(II) SAVAGE(0): [junkers]    depthbufferSize:0x000f7000
(II) SAVAGE(0): [junkers]    depthOffset:0x003eb000
(II) SAVAGE(0): [junkers]    depthPitch:0x00000680
(II) SAVAGE(0): [junkers]    textureOffset:0x004e2000
(II) SAVAGE(0): [junkers]    textureSize:0x01afd000
(II) SAVAGE(0): [junkers]    textureSize:0x01afd000
(II) SAVAGE(0): [junkers]    logTextureGranularity:0x00000000
(II) SAVAGE(0): [junkers]    agp:handle:0x00000000
(II) SAVAGE(0): [junkers]    agp:offset:0x00000000
(II) SAVAGE(0): [junkers]    agp:size:0x00000000
(II) SAVAGE(0): [junkers]    agp:map:0x00000000
(II) SAVAGE(0): [junkers]    registers:handle:0xed000000
(II) SAVAGE(0): [junkers]    registers:offset:0x00000000
(II) SAVAGE(0): [junkers]    registers:size:0x00080000
(II) SAVAGE(0): [junkers]    registers:map:0x00000000
(II) SAVAGE(0): [junkers]    status:handle:0x3423e000
(II) SAVAGE(0): [junkers]    status:offset:0x00000000
(II) SAVAGE(0): [junkers]    status:size:0x00001000
(II) SAVAGE(0): [junkers]    status:map:0xb77f9000
(II) SAVAGE(0): [junkers]    agpTextures:handle:0x00000000
(II) SAVAGE(0): [junkers]    agpTextures:offset:0x00000000
(II) SAVAGE(0): [junkers]    agpTextures:size:0x00000000
(II) SAVAGE(0): [junkers]    apgTextures:map:0x00000000
(II) SAVAGE(0): [junkers]    logAgpTextureGranularity:0x00000000
(II) SAVAGE(0): [junkers]    cmdDma:handle:0x34300000
(II) SAVAGE(0): [junkers]    cmdDma:offset:0x00000000
(II) SAVAGE(0): [junkers]    cmdDma:size:0x00100000
(II) SAVAGE(0): [junkers]    cmdDma:map:0x00000000
(II) SAVAGE(0): [junkers]pSAVAGEDRI:
(II) SAVAGE(0): [junkers]    chipset:0x00000006
(II) SAVAGE(0): [junkers]    width:0x00000320
(II) SAVAGE(0): [junkers]    height:0x00000258
(II) SAVAGE(0): [junkers]    mem:0x02000000
(II) SAVAGE(0): [junkers]    cpp:2
(II) SAVAGE(0): [junkers]    zpp:2
(II) SAVAGE(0): [junkers]    agpMode:0
(II) SAVAGE(0): [junkers]    bufferSize:65536
(II) SAVAGE(0): [junkers]    frontbufferSize:0x000f4000
(II) SAVAGE(0): [junkers]    frontOffset:0x00000000
(II) SAVAGE(0): [junkers]    backbufferSize:0x000f7000
(II) SAVAGE(0): [junkers]    backOffset:0x002f4000
(II) SAVAGE(0): [junkers]    depthbufferSize:0x000f7000
(II) SAVAGE(0): [junkers]    depthOffset:0x003eb000
(II) SAVAGE(0): [junkers]    textureOffset:0x004e2000
(II) SAVAGE(0): [junkers]    textureSize:0x01a00000
(II) SAVAGE(0): [junkers]    logTextureGranularity:0x00000015
(II) SAVAGE(0): [junkers]    agpTextureHandle:0x00000000
(II) SAVAGE(0): [junkers]    agpTextureSize:0x00000000
(II) SAVAGE(0): [junkers]    logAgpTextureGranularity:0x00000020
(II) SAVAGE(0): [junkers]    apertureHandle:0xe0000000
(II) SAVAGE(0): [junkers]    apertureSize:0x05000000
(II) SAVAGE(0): [junkers]    aperturePitch:0x00001000
(II) SAVAGE(0): [junkers]    statusHandle:0x3423e000
(II) SAVAGE(0): [junkers]    statusSize:0x00001000
(II) SAVAGE(0): [junkers]    sarea_priv_offset:0x00000898
(II) SAVAGE(0): Direct rendering enabled
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
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: drmOpenMinor returns 12
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: Loaded and initialized /usr/lib/dri/savage_dri.so
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
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(**) Option "xkb_variant" "extd"
(II) XKB: reuse xkmfile /var/lib/xkb/server-1529D616753195EAEFADABC0A5076611C127C014.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(**) Option "xkb_variant" "extd"
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(**) Option "xkb_variant" "extd"
(II) config/udev: Adding input device ImExPS/2 Generic Explorer Mouse (/dev/input/event4)
(**) ImExPS/2 Generic Explorer Mouse: Applying InputClass "evdev pointer catchall"
(**) ImExPS/2 Generic Explorer Mouse: always reports core events
(**) ImExPS/2 Generic Explorer Mouse: Device: "/dev/input/event4"
(II) ImExPS/2 Generic Explorer Mouse: Found 9 mouse buttons
(II) ImExPS/2 Generic Explorer Mouse: Found scroll wheel(s)
(II) ImExPS/2 Generic Explorer Mouse: Found relative axes
(II) ImExPS/2 Generic Explorer Mouse: Found x and y relative axes
(II) ImExPS/2 Generic Explorer Mouse: Configuring as mouse
(**) ImExPS/2 Generic Explorer Mouse: YAxisMapping: buttons 4 and 5
(**) ImExPS/2 Generic Explorer Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImExPS/2 Generic Explorer Mouse" (type: MOUSE)
(II) ImExPS/2 Generic Explorer Mouse: initialized for relative axes.
(II) config/udev: Adding input device ImExPS/2 Generic Explorer Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
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
(II) AIGLX: Suspending AIGLX clients for VT switch
(II) Open ACPI successful (/var/run/acpid.socket)
(II) AIGLX: Resuming AIGLX clients after VT switch
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(II) Power Button: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) ImExPS/2 Generic Explorer Mouse: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.

```

---

### Post by Yellow Pasque on 2010-07-08
First, generate a mode line with cvt:
```
cvt -v 1024 768 60.0Hz
```

The output will look something like this:
```
# 1024x768 59.92 Hz (CVT 0.79M3) **hsync: 47.82 kHz**; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
```
The number you need is the Horizontal Sync (hsync). Now you can create an /etc/X11/xorg.conf file since X is failing to auto-detect your monitor's EDID.

```
gksu gedit /etc/X11/xorg.conf
```

Copy/paste this, replacing <some number> with a number slightly greater than the hsync number you got from cvt:
```
Section "Device"
	Identifier	"Configured Video"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync       31-<some number>
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video"
EndSection
```
Save the file. Quit gedit and log out to restart X.

---

### Post by ZaphodFJ on 2010-07-08
I used 58 in place of <some number> and it worked a treat, thanks!

For the benefit of anyone reading this at a later stage:
- I logged out
- The login screen was 1024x768
- I logged on
- My session was 800x600, as it has been before
- I now had the option (in System>Prefs>Monitors) of 1024x768.
- My desktop wallpaper was lost when I changed the resolution, but this is hardly a problem!

Z

---

