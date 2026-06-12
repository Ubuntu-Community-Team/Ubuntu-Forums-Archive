---
title: "Stuck in command line interface"
date: 2011-01-06
forum: Hardware
---

### Post by Art Gibbens on 2011-01-06
Howdy gang,

I did a fresh install of Xubuntu 10.10 on an older HP Pavilion N3390 with 256 RAM and a 40 Gig hard drive on Monday. All went fine until the first fire-up. I have no GUI. Here's what I've done: if I run the lspci command I get this: 01:00.0 VGA compatible controller: Silicon Motion, Inc. SM720 Lynx3DM (rev b1) 

If I issue the startx command I get a ton of stuff which may help someone help me out, I'll try to pick out the relevant stuff = "error setting MTRR ... Invalid argument; not enough video memory for the configured screen size (1024 x 1024) ((which seems an odd size to me)) and color depth; screens found, but none have a usable configuration; Fatal server error: no screen found; No such file or directory; unable to connect to X server; No such process; Server Error."

If I take a gander into /etc/X11 I don't see an xorg.conf file to edit. I've googled for help and searched in this forum and found lots of similar issues that folks have with no GUI popping up after an install, but none have given me a clear step by step diagnostic process to verify just what is not working exactly. I'm not as comfortable with command line but know it's necessary to get some stuff to work in Linux.

So, what steps do I need to do in what sequence to figure out just why this laptop has no GUI now? 

PS. It had Win98 on it before I started and the GUI worked fine so I know the screen is ok.
PSS. I used the same install CD with a couple of old Dells and they fired the GUI right away.

Thanx for any help and/or insight any of you might lend to help me out of this pickle,

Art

---

### Post by Fafler on 2011-01-06
To create a Xorg.conf:
```
sudo service gdm stop   sudo Xorg -configure
   sudo mv xorg.conf /etc/X11/xorg.conf
  
```


Edit the file and try the vesa driver instead of siliconmotion.


You could also include your complete /var/log/Xorg.0.log

---

### Post by Art Gibbens on 2011-01-07
When I did the sudo Xorg -configure I got a lot of errors on the screen as well.

[    28.942] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    28.942] X Protocol Version 11, Revision 0
[    28.942] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    28.942] Current Operating System: Linux buyer3 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 i686
[    28.942] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-24-generic root=UUID=9333931f-6159-4dec-b0b8-9d00b9727164 ro quiet splash
[    28.942] Build Date: 16 September 2010  05:39:22PM
[    28.942] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    28.943] Current version of pixman: 0.18.4
[    28.943]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    28.943] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    28.943] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jan  7 12:17:51 2011
[    28.958] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    28.959] (==) No Layout section.  Using the first Screen section.
[    28.959] (==) No screen section available. Using defaults.
[    28.959] (**) |-->Screen "Default Screen Section" (0)
[    28.960] (**) |   |-->Monitor "<default monitor>"
[    28.961] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    28.961] (==) Automatically adding devices
[    28.961] (==) Automatically enabling devices
[    29.036] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    29.036]     Entry deleted from font path.
[    29.375] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    29.375] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    29.375] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    29.375] (II) Loader magic: 0x81f8e00
[    29.375] (II) Module ABI versions:
[    29.375]     X.Org ANSI C Emulation: 0.4
[    29.375]     X.Org Video Driver: 8.0
[    29.375]     X.Org XInput driver : 11.0
[    29.376]     X.Org Server Extension : 4.0
[    29.377] (--) PCI:*(0:1:0:0) 126f:0720:103c:0015 rev 177, Mem @ 0xf8000000/67108864
[    29.379] (II) Open ACPI successful (/var/run/acpid.socket)
[    29.379] (II) LoadModule: "extmod"
[    29.521] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    29.521] (II) Module extmod: vendor="X.Org Foundation"
[    29.521]     compiled for 1.9.0, module version = 1.0.0
[    29.522]     Module class: X.Org Server Extension
[    29.522]     ABI class: X.Org Server Extension, version 4.0
[    29.522] (II) Loading extension MIT-SCREEN-SAVER
[    29.522] (II) Loading extension XFree86-VidModeExtension
[    29.522] (II) Loading extension XFree86-DGA
[    29.522] (II) Loading extension DPMS
[    29.522] (II) Loading extension XVideo
[    29.522] (II) Loading extension XVideo-MotionCompensation
[    29.522] (II) Loading extension X-Resource
[    29.522] (II) LoadModule: "dbe"
[    29.524] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    29.524] (II) Module dbe: vendor="X.Org Foundation"
[    29.524]     compiled for 1.9.0, module version = 1.0.0
[    29.524]     Module class: X.Org Server Extension
[    29.525]     ABI class: X.Org Server Extension, version 4.0
[    29.525] (II) Loading extension DOUBLE-BUFFER
[    29.525] (II) LoadModule: "glx"
[    29.526] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    29.527] (II) Module glx: vendor="X.Org Foundation"
[    29.527]     compiled for 1.9.0, module version = 1.0.0
[    29.527]     ABI class: X.Org Server Extension, version 4.0
[    29.527] (==) AIGLX enabled
[    29.527] (II) Loading extension GLX
[    29.527] (II) LoadModule: "record"
[    29.529] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    29.530] (II) Module record: vendor="X.Org Foundation"
[    29.530]     compiled for 1.9.0, module version = 1.13.0
[    29.530]     Module class: X.Org Server Extension
[    29.530]     ABI class: X.Org Server Extension, version 4.0
[    29.530] (II) Loading extension RECORD
[    29.530] (II) LoadModule: "dri"
[    29.532] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    29.533] (II) Module dri: vendor="X.Org Foundation"
[    29.533]     compiled for 1.9.0, module version = 1.0.0
[    29.533]     ABI class: X.Org Server Extension, version 4.0
[    29.533] (II) Loading extension XFree86-DRI
[    29.533] (II) LoadModule: "dri2"
[    29.535] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    29.535] (II) Module dri2: vendor="X.Org Foundation"
[    29.535]     compiled for 1.9.0, module version = 1.2.0
[    29.535]     ABI class: X.Org Server Extension, version 4.0
[    29.535] (II) Loading extension DRI2
[    29.535] (==) Matched siliconmotion as autoconfigured driver 0
[    29.535] (==) Matched vesa as autoconfigured driver 1
[    29.536] (==) Matched fbdev as autoconfigured driver 2
[    29.536] (==) Assigned the driver to the xf86ConfigLayout
[    29.536] (II) LoadModule: "siliconmotion"
[    29.537] (II) Loading /usr/lib/xorg/modules/drivers/siliconmotion_drv.so
[    29.538] (II) Module siliconmotion: vendor="X.Org Foundation"
[    29.538]     compiled for 1.8.99.905, module version = 1.7.4
[    29.538]     Module class: X.Org Video Driver
[    29.538]     ABI class: X.Org Video Driver, version 8.0
[    29.538] (II) LoadModule: "vesa"
[    29.539] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    29.539] (II) Module vesa: vendor="X.Org Foundation"
[    29.540]     compiled for 1.8.99.905, module version = 2.3.0
[    29.540]     Module class: X.Org Video Driver
[    29.540]     ABI class: X.Org Video Driver, version 8.0
[    29.540] (II) LoadModule: "fbdev"
[    29.541] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    29.542] (II) Module fbdev: vendor="X.Org Foundation"
[    29.542]     compiled for 1.8.99.905, module version = 0.4.2
[    29.542]     ABI class: X.Org Video Driver, version 8.0
[    29.542] (II) SMI: driver (version 1.7.4) for Silicon Motion Lynx chipsets: Lynx,
    LynxE, Lynx3D, LynxEM, LynxEM+, Lynx3DM, Cougar3DR, MSOC
[    29.543] (II) VESA: driver for VESA chipsets: vesa
[    29.543] (II) FBDEV: driver for framebuffer: fbdev
[    29.543] (++) using VT number 7

[    29.545] (WW) Falling back to old probe method for siliconmotion
[    29.545] (--) Assigning device section with no busID to primary device
[    29.545] (--) Chipset Lynx3DM found
[    29.545] (WW) Falling back to old probe method for vesa
[    29.545] (WW) Falling back to old probe method for fbdev
[    29.545] (II) Loading sub module "fbdevhw"
[    29.545] (II) LoadModule: "fbdevhw"
[    29.546] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    29.546] (II) Module fbdevhw: vendor="X.Org Foundation"
[    29.547]     compiled for 1.9.0, module version = 0.0.2
[    29.547]     ABI class: X.Org Video Driver, version 8.0
[    29.547] (EE) open /dev/fb0: No such file or directory
[    29.547] (II) Loading sub module "vgahw"
[    29.547] (II) LoadModule: "vgahw"
[    29.548] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    29.548] (II) Module vgahw: vendor="X.Org Foundation"
[    29.548]     compiled for 1.9.0, module version = 0.1.0
[    29.549]     ABI class: X.Org Video Driver, version 8.0
[    29.549] (II) SMI(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    29.549] (==) SMI(0): Depth 24, (--) framebuffer bpp 32
[    29.549] (==) SMI(0): RGB weight 888
[    29.549] (==) SMI(0): Default visual is TrueColor
[    29.549] (==) SMI(0): PCI Burst enabled
[    29.549] (==) SMI(0): PCI Retry enabled
[    29.549] (==) SMI(0): Using Hardware Cursor
[    29.549] (--) SMI(0): Chipset: "Lynx3DM"
[    29.549] (==) SMI(0): Dual head disabled
[    29.549] (==) SMI(0): Using XAA acceleration architecture
[    29.550] (--) SMI(0): videoram: 4096kB
[    29.555] (II) SMI(0): Cursor Offset: 003FFC00
[    29.555] (II) SMI(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[    29.556] (II) SMI(0): Reserved: 003FF800
[    29.557] (II) SMI(0): TFT Panel Size = 1024x768
[    29.557] (II) Loading sub module "i2c"
[    29.557] (II) LoadModule: "i2c"
[    29.557] (II) Module "i2c" already built-in
[    29.557] (II) SMI(0): I2C bus "I2C bus" initialized.
[    29.557] (II) Loading sub module "ddc"
[    29.557] (II) LoadModule: "ddc"
[    29.557] (II) Module "ddc" already built-in
[    29.557] (==) SMI(0): Using gamma correction (1.0, 1.0, 1.0)
[    29.557] (II) SMI(0): MCLK = 100.227
[    29.558] (II) SMI(0): Output LVDS has no monitor section
[    29.559] (II) SMI(0): Not using default mode "640x350" (vrefresh out of range)
[    29.559] (II) SMI(0): Not using default mode "320x175" (doublescan mode not supported)
[    29.559] (II) SMI(0): Not using default mode "640x400" (vrefresh out of range)
[    29.559] (II) SMI(0): Not using default mode "320x200" (doublescan mode not supported)
[    29.559] (II) SMI(0): Not using default mode "720x400" (vrefresh out of range)
[    29.559] (II) SMI(0): Not using default mode "360x200" (doublescan mode not supported)
[    29.559] (II) SMI(0): Not using default mode "640x480" (exceeds panel dimensions)
[    29.559] (II) SMI(0): Not using default mode "320x240" (doublescan mode not supported)
[    29.559] (II) SMI(0): Not using default mode "640x480" (vrefresh out of range)
[    29.559] (II) SMI(0): Not using default mode "320x240" (doublescan mode not supported)
[    29.559] (II) SMI(0): Not using default mode "640x480" (vrefresh out of range)
[    29.559] (II) SMI(0): Not using default mode "320x240" (doublescan mode not supported)
[    29.559] (II) SMI(0): Not using default mode "640x480" (vrefresh out of range)
[    29.560] (II) SMI(0): Not using default mode "320x240" (doublescan mode not supported)
[    29.560] (II) SMI(0): Not using default mode "800x600" (vrefresh out of range)
[    29.560] (II) SMI(0): Not using default mode "400x300" (doublescan mode not supported)
[    29.560] (II) SMI(0): Not using default mode "800x600" (exceeds panel dimensions)
[    29.560] (II) SMI(0): Not using default mode "400x300" (doublescan mode not supported)
[    29.560] (II) SMI(0): Not using default mode "800x600" (vrefresh out of range)
[    29.560] (II) SMI(0): Not using default mode "400x300" (doublescan mode not supported)
[    29.560] (II) SMI(0): Not using default mode "800x600" (vrefresh out of range)
[    29.560] (II) SMI(0): Not using default mode "400x300" (doublescan mode not supported)
[    29.560] (II) SMI(0): Not using default mode "800x600" (vrefresh out of range)
[    29.560] (II) SMI(0): Not using default mode "400x300" (doublescan mode not supported)
[    29.560] (II) SMI(0): Not using default mode "1024x768i" (interlace mode not supported)
[    29.561] (II) SMI(0): Not using default mode "512x384i" (doublescan mode not supported)
[    29.561] (II) SMI(0): Not using default mode "1024x768" (hsync out of range)
[    29.561] (II) SMI(0): Not using default mode "512x384" (doublescan mode not supported)
[    29.561] (II) SMI(0): Not using default mode "1024x768" (vrefresh out of range)
[    29.561] (II) SMI(0): Not using default mode "512x384" (doublescan mode not supported)
[    29.561] (II) SMI(0): Not using default mode "1024x768" (vrefresh out of range)
[    29.561] (II) SMI(0): Not using default mode "512x384" (doublescan mode not supported)
[    29.561] (II) SMI(0): Not using default mode "1024x768" (vrefresh out of range)
[    29.561] (II) SMI(0): Not using default mode "512x384" (doublescan mode not supported)
[    29.561] (II) SMI(0): Not using default mode "1152x864" (vrefresh out of range)
[    29.561] (II) SMI(0): Not using default mode "576x432" (doublescan mode not supported)
[    29.561] (II) SMI(0): Not using default mode "1280x960" (hsync out of range)
[    29.561] (II) SMI(0): Not using default mode "640x480" (doublescan mode not supported)
[    29.561] (II) SMI(0): Not using default mode "1280x960" (vrefresh out of range)
[    29.562] (II) SMI(0): Not using default mode "640x480" (doublescan mode not supported)
[    29.562] (II) SMI(0): Not using default mode "1280x1024" (hsync out of range)
[    29.562] (II) SMI(0): Not using default mode "640x512" (doublescan mode not supported)
[    29.562] (II) SMI(0): Not using default mode "1280x1024" (vrefresh out of range)
[    29.562] (II) SMI(0): Not using default mode "640x512" (doublescan mode not supported)
[    29.562] (II) SMI(0): Not using default mode "1280x1024" (vrefresh out of range)
[    29.562] (II) SMI(0): Not using default mode "640x512" (doublescan mode not supported)
[    29.562] (II) SMI(0): Not using default mode "1600x1200" (hsync out of range)
[    29.562] (II) SMI(0): Not using default mode "800x600" (doublescan mode not supported)
[    29.562] (II) SMI(0): Not using default mode "1600x1200" (vrefresh out of range)
[    29.562] (II) SMI(0): Not using default mode "800x600" (doublescan mode not supported)
[    29.563] (II) SMI(0): Not using default mode "1600x1200" (vrefresh out of range)
[    29.563] (II) SMI(0): Not using default mode "800x600" (doublescan mode not supported)
[    29.563] (II) SMI(0): Not using default mode "1600x1200" (vrefresh out of range)
[    29.563] (II) SMI(0): Not using default mode "800x600" (doublescan mode not supported)
[    29.563] (II) SMI(0): Not using default mode "1600x1200" (vrefresh out of range)
[    29.563] (II) SMI(0): Not using default mode "800x600" (doublescan mode not supported)
[    29.563] (II) SMI(0): Not using default mode "1792x1344" (hsync out of range)
[    29.563] (II) SMI(0): Not using default mode "896x672" (doublescan mode not supported)
[    29.563] (II) SMI(0): Not using default mode "1792x1344" (vrefresh out of range)
[    29.563] (II) SMI(0): Not using default mode "896x672" (doublescan mode not supported)
[    29.563] (II) SMI(0): Not using default mode "1856x1392" (hsync out of range)
[    29.563] (II) SMI(0): Not using default mode "928x696" (doublescan mode not supported)
[    29.563] (II) SMI(0): Not using default mode "1856x1392" (vrefresh out of range)
[    29.563] (II) SMI(0): Not using default mode "928x696" (doublescan mode not supported)
[    29.564] (II) SMI(0): Not using default mode "1920x1440" (hsync out of range)
[    29.564] (II) SMI(0): Not using default mode "960x720" (doublescan mode not supported)
[    29.564] (II) SMI(0): Not using default mode "1920x1440" (vrefresh out of range)
[    29.564] (II) SMI(0): Not using default mode "960x720" (doublescan mode not supported)
[    29.564] (II) SMI(0): Not using default mode "832x624" (vrefresh out of range)
[    29.564] (II) SMI(0): Not using default mode "416x312" (doublescan mode not supported)
[    29.564] (II) SMI(0): Not using default mode "1152x864" (hsync out of range)
[    29.564] (II) SMI(0): Not using default mode "576x432" (doublescan mode not supported)
[    29.564] (II) SMI(0): Not using default mode "1152x864" (vrefresh out of range)
[    29.564] (II) SMI(0): Not using default mode "576x432" (doublescan mode not supported)
[    29.564] (II) SMI(0): Not using default mode "1152x864" (vrefresh out of range)
[    29.564] (II) SMI(0): Not using default mode "576x432" (doublescan mode not supported)
[    29.564] (II) SMI(0): Not using default mode "1152x864" (vrefresh out of range)
[    29.564] (II) SMI(0): Not using default mode "576x432" (doublescan mode not supported)
[    29.565] (II) SMI(0): Not using default mode "1152x864" (vrefresh out of range)
[    29.565] (II) SMI(0): Not using default mode "576x432" (doublescan mode not supported)
[    29.565] (II) SMI(0): Not using default mode "1152x864" (vrefresh out of range)
[    29.565] (II) SMI(0): Not using default mode "576x432" (doublescan mode not supported)
[    29.565] (II) SMI(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[    29.565] (II) SMI(0): Not using default mode "680x384" (doublescan mode not supported)
[    29.565] (II) SMI(0): Not using default mode "1360x768" (exceeds panel dimensions)
[    29.565] (II) SMI(0): Not using default mode "680x384" (doublescan mode not supported)
[    29.565] (II) SMI(0): Not using default mode "1400x1050" (hsync out of range)
[    29.565] (II) SMI(0): Not using default mode "700x525" (doublescan mode not supported)
[    29.565] (II) SMI(0): Not using default mode "1400x1050" (vrefresh out of range)
[    29.565] (II) SMI(0): Not using default mode "700x525" (doublescan mode not supported)
[    29.565] (II) SMI(0): Not using default mode "1400x1050" (vrefresh out of range)
[    29.566] (II) SMI(0): Not using default mode "700x525" (doublescan mode not supported)
[    29.566] (II) SMI(0): Not using default mode "1400x1050" (vrefresh out of range)
[    29.566] (II) SMI(0): Not using default mode "700x525" (doublescan mode not supported)
[    29.566] (II) SMI(0): Not using default mode "1440x900" (hsync out of range)
[    29.566] (II) SMI(0): Not using default mode "720x450" (doublescan mode not supported)
[    29.566] (II) SMI(0): Not using default mode "1600x1024" (hsync out of range)
[    29.566] (II) SMI(0): Not using default mode "800x512" (doublescan mode not supported)
[    29.566] (II) SMI(0): Not using default mode "1680x1050" (hsync out of range)
[    29.566] (II) SMI(0): Not using default mode "840x525" (doublescan mode not supported)
[    29.566] (II) SMI(0): Not using default mode "1680x1050" (hsync out of range)
[    29.566] (II) SMI(0): Not using default mode "840x525" (doublescan mode not supported)
[    29.566] (II) SMI(0): Not using default mode "1680x1050" (vrefresh out of range)
[    29.566] (II) SMI(0): Not using default mode "840x525" (doublescan mode not supported)
[    29.566] (II) SMI(0): Not using default mode "1680x1050" (vrefresh out of range)
[    29.567] (II) SMI(0): Not using default mode "840x525" (doublescan mode not supported)
[    29.567] (II) SMI(0): Not using default mode "1680x1050" (vrefresh out of range)
[    29.567] (II) SMI(0): Not using default mode "840x525" (doublescan mode not supported)
[    29.567] (II) SMI(0): Not using default mode "1920x1080" (hsync out of range)
[    29.567] (II) SMI(0): Not using default mode "960x540" (doublescan mode not supported)
[    29.567] (II) SMI(0): Not using default mode "1920x1200" (hsync out of range)
[    29.567] (II) SMI(0): Not using default mode "960x600" (doublescan mode not supported)
[    29.567] (II) SMI(0): Not using default mode "1920x1440" (vrefresh out of range)
[    29.567] (II) SMI(0): Not using default mode "960x720" (doublescan mode not supported)
[    29.567] (II) SMI(0): Not using default mode "2048x1536" (hsync out of range)
[    29.568] (II) SMI(0): Not using default mode "1024x768" (doublescan mode not supported)
[    29.568] (II) SMI(0): Not using default mode "2048x1536" (vrefresh out of range)
[    29.568] (II) SMI(0): Not using default mode "1024x768" (doublescan mode not supported)
[    29.568] (II) SMI(0): Not using default mode "2048x1536" (vrefresh out of range)
[    29.568] (II) SMI(0): Not using default mode "1024x768" (doublescan mode not supported)
[    29.568] (II) SMI(0): Printing probed modes for output LVDS
[    29.568] (II) SMI(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[    29.568] (II) SMI(0): Output LVDS connected
[    29.568] (II) SMI(0): Using fuzzy aspect match for initial modes
[    29.568] (II) SMI(0): Output LVDS using initial mode 1024x768
[    29.569] (II) SMI(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    29.569] (EE) SMI(0): Not enough video memory for the configured screen size (1024x1024) and color depth.
[    29.571] (II) UnloadModule: "siliconmotion"
[    29.571] (II) UnloadModule: "vgahw"
[    29.571] (II) Unloading /usr/lib/xorg/modules/libvgahw.so
[    29.571] (EE) Screen(s) found, but none have a usable configuration.
[    29.572] 
Fatal server error:
[    29.572] no screens found
[    29.572] 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[    29.572] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    29.572] 
[    29.573]  ddxSigGiveUp: Closing log

---

### Post by Fafler on 2011-01-08
It finds 4 mb memory and says it's not enough to do 1024x786 at 32 bit. Try setting it to 16 bit on your xorg.conf. You won't notice anything on that LCD anyway.

---

### Post by Art Gibbens on 2011-01-12
Fafler,

Sorry about the delay - had a backup server crash and it had to be restored. When I run the second command to configure Xorg - it fails so I do not have xorg.conf in my /etc/X11 folder. The end of the warning message says to look at the  /var/log/Xorg.0.log     which I have already submitted. (Unless you want a different one, I noticed that there are a number of them in the folder.)

Art

---

### Post by Art Gibbens on 2011-01-20
Resolved. I installed Fedora 11 and now have GUI. I tried Fedora 14 Live and Fedora 14 XFCE and neither of them would install. I guess older equipment doesn't get the latest OSes with updates. Oh well.

---

