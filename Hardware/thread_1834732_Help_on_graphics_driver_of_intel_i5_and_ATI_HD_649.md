---
title: "Help on graphics driver of intel i5 and ATI HD 6490M"
date: 2011-08-28
forum: Hardware
---

### Post by wecing on 2011-08-28
Hello guys. In fact I'm currently using Debian, but I think the solution should make no difference.

I just bought a HP Pavilion dv7 6175us laptop. It has Intel i5 2410M and Radeon HD 6490M.

I tried running 'aticonfig', but it reports that "no supported adapters detected". Installing the official driver for 6490M will make the system unable to run X correctly.

However, I don't care the graphics very much. But the screen resolution is currently 1024x768, which is very unacceptable. I installed xserver-xorg-video-radeon, xserver-xorg-video-radeonhd and xserver-xorg-video-ati, but still it doesn't work.

Currently my xorg.conf is empty. Do I need to disable the radeon staff to make the Intel graphics driver runs correctly?

---

### Post by .... on 2011-08-28
You need to purge the proprietary ATI driver (Catalyst/fglrx) for the intel adapter to work correctly (unless you have a BIOS switch to disable the Intel graphics). See: [http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Removing_Catalyst.2Ffglrx)
Once you've done that, you may need to update some components (kernel/drm, mesa) to get the Intel GPU working properly depending on how old your Debian is. Finally, once you get the Intel working properly, you can experiment with vga_switcheroo to see if you can completely disable the radeon GPU to save power. I guess you could also switch to the radeon GPU, but I don't see much advantage to that.

---

### Post by wecing on 2011-08-28
I uninstalled it, and also have xserver-xorg-video-intel installed.
But it seems the driver is still not working.

You said that I could disable Intel graphics in BIOS... Well, can I disable the ATI cards in it?

And, do I need to remove or blacklist some kernel modules like radeon?

---

### Post by realzippy on 2011-08-28
Does the intel graphics not work correctly?
If so,which kernel do you run?

```
uname -r
```

---

### Post by wecing on 2011-08-28
Here it is:

> wecing@D5:~$ uname -r
2.6.32-5-amd64

---

### Post by .... on 2011-08-28
Oh, you're running lucid. That's too old for intel Sandy Bridge-based graphics.

---

### Post by realzippy on 2011-08-28
So that is your problem.
You need at least kernel 2.6.38.x...
Which ubuntu version?

Edit:
...forgot you are on debian.

---

### Post by wecing on 2011-08-28
I found this on Phoronix:

> With this code starting to live in the mainline repositories, the first bits of Intel Sandy Bridge support will arrive in the Linux 2.6.34 kernel for the DRM and in xf86-video-intel 2.11 for the DDX user-space side.

Does that means I have to update my kernel?

---

### Post by wecing on 2011-08-28
A-ha. I'm using Debian Squeeze. Bad.

Why at least 2.6.38? Is 2.6.34 not working?

---

### Post by wecing on 2011-08-28
> **wecing said:**
> Hello guys. [COLOR="Red"]In fact I'm currently using Debian[/COLOR], but I think the solution should make no difference.

I just bought a HP Pavilion dv7 6175us laptop. It has Intel i5 2410M and Radeon HD 6490M.

I tried running 'aticonfig', but it reports that "no supported adapters detected". Installing the official driver for 6490M will make the system unable to run X correctly.

However, I don't care the graphics very much. But the screen resolution is currently 1024x768, which is very unacceptable. I installed xserver-xorg-video-radeon, xserver-xorg-video-radeonhd and xserver-xorg-video-ati, but still it doesn't work.

Currently my xorg.conf is empty. Do I need to disable the radeon staff to make the Intel graphics driver runs correctly?

I'm a Debian spy. :)

---

### Post by SeijiSensei on 2011-08-28
Have you run Windows applications on this machine?  Do you know whether you can switch from Intel to ATI easily?

We just got my daughter an i5 dv6tse with the ATI 6770M graphics card.  When we started it up in Win7, we discovered that you couldn't switch directly from one to the other video adapter, even in Windows.  It did come with an application that allowed you to assign an adapter to specific applications, but no hot-switching ability.  

It turns out the initial HP [BIOS]("http://forum.notebookreview.com/hp-pavilion-notebooks/583203-dv6t-61xx-dv7t-61xx-switchable-graphics-discussion.html") for these Catalyst-based computers was the limiting factor.  Once I upgraded to the newer BIOS from [this page](http://forum.notebookreview.com/hp-pavilion-notebooks/595505-updated-hp-pavilion-bios-releases.html) ([F1.A]("ftp://ftp.hp.com/pub/softpaq/sp54001-54500/sp54024.html") in my case), I could switch to "fixed mode" in the BIOS during boot.  Kubuntu 11.04 then saw the ATI card and now uses the proprietary driver.  I haven't tried anything like vga_switcheroo to see if I can switch back to the Intel chip, and I can't test it out until she comes back from college.

She can also now switch directly from one video mode to the other in Windows.

You might want to consider upgrading the BIOS to see if it helps resolve your problems.

---

### Post by wecing on 2011-08-28
A huge thanks to you guys. The resolution is now perfect.
It seems that I'm now using the Intel graphics, without 3D acceleration.

And also thanks SeijiSensei, I will try it later. Lots of work to do... ;-P

---

### Post by realzippy on 2011-08-28
So 2.6.34 worked?

---

### Post by wecing on 2011-08-28
I don't know if it works. I just updated the kernel to 2.6.38. :-P

---

### Post by realzippy on 2011-08-29
Ok.
Please set thread as solved (threadtools),it helps others.
Have fun!

---

### Post by wecing on 2011-08-30
Well, I hope to do so, but new problems arose.

I updated my BIOS firmware and now able to make the BIOS to select video card to use dynamically(or fixed), and still using Intel graphics with no 3D acceleration. When I tried to play a video downloaded from the web with smplayer, my system got dead...

---

### Post by .... on 2011-08-30
Did you follow this?: [http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Removing_Catalyst.2Ffglrx)

If so, post /var/log/Xorg.0.log

---

### Post by wecing on 2011-08-30
Yes.

> 
X.Org X Server 1.7.7
Release Date: 2010-05-04
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.37-trunk-amd64 x86_64 Debian
Current Operating System: Linux D5 2.6.38-bpo.2-amd64 #1 SMP Mon Jun 6 15:24:02 UTC 2011 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-bpo.2-amd64 root=UUID=b373b7ea-debb-4ce8-bd4c-dcb0c19177c9 ro quiet
Build Date: 18 February 2011  08:27:24PM
xorg-server 2:1.7.7-13 (Cyril Brulebois <kibi@debian.org>) 
Current version of pixman: 0.16.4
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Aug 30 14:41:47 2011
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
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
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x7c8aa0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:0116:103c:1659 Intel Corporation Sandy Bridge Integrated Graphics Controller rev 9, Mem @ 0xc0000000/4194304, 0xb0000000/268435456, I/O @ 0x00006000/64
(--) PCI: (0:1:0:0) 1002:6760:103c:1659 ATI Technologies Inc NI Seymour [AMD Radeon HD 6470M] rev 0, Mem @ 0xa0000000/268435456, 0xc6500000/131072, I/O @ 0x00005000/256, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension SELinux
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
	compiled for 1.7.7, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.5.0, module version = 1.0.0
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched intel as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 2.13.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 2.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.7.6.901, module version = 0.4.2
	ABI class: X.Org Video Driver, version 6.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 0.0.2
	ABI class: X.Org Video Driver, version 6.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge
(--) intel(0): Chipset: "Sandybridge"
(**) intel(0): Tiling enabled
(**) intel(0): SwapBuffers wait disabled
(==) intel(0): video overlay key set to 0x101fe
(II) intel(0): Output LVDS1 has no monitor section
(II) intel(0): found backlight control interface /sys/class/backlight/acpi_video1
(II) intel(0): Output VGA1 has no monitor section
(II) intel(0): Output HDMI1 has no monitor section
(II) intel(0): Output DP1 has no monitor section
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: LGD  Model: 27a  Serial#: 0
(II) intel(0): Year: 2009  Week: 0
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 38  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.615 redY: 0.346   greenX: 0.314 greenY: 0.602
(II) intel(0): blueX: 0.151 blueY: 0.109   whiteX: 0.312 whiteY: 0.328
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 97.8 MHz   Image Size:  382 x 215 mm
(II) intel(0): h_active: 1600  h_sync: 1648  h_sync_end 1696 h_blank_end 1784 h_border: 0
(II) intel(0): v_active: 900  v_sync: 902  v_sync_end 905 v_blanking: 912 v_border: 0
(II) intel(0):  
(II) intel(0):  LP173WD1-TLC3
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff0030e47a0200000000
(II) intel(0): 	00130103802615780aa8c09d58509a26
(II) intel(0): 	1c505400000001010101010101010101
(II) intel(0): 	0101010101012f2640b860840c303030
(II) intel(0): 	23007ed7100000190000000000000000
(II) intel(0): 	00000000000000000000000000fe0000
(II) intel(0): 	00004c47446973706c61790a000000fe
(II) intel(0): 	004c503137335744312d544c433300c2
(II) intel(0): EDID vendor "LGD", prod id 634
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0   97.75  1600 1648 1696 1784  900 902 905 912 -hsync -vsync (54.8 kHz)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
(II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
(II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
(II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1600x900"x60.1   97.75  1600 1648 1696 1784  900 902 905 912 -hsync -vsync (54.8 kHz)
(II) intel(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
(II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output HDMI1
(II) intel(0): EDID for output DP1
(II) intel(0): Output LVDS1 connected
(II) intel(0): Output VGA1 disconnected
(II) intel(0): Output HDMI1 disconnected
(II) intel(0): Output DP1 disconnected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output LVDS1 using initial mode 1600x900
(II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(II) intel(0): Kernel page flipping support detected, enabling
(**) intel(0): Display dimensions: (380, 210) mm
(**) intel(0): DPI set to (106, 108)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(==) Depth 24 pixmap format is 32 bpp
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): [DRI2] Setup complete
(II) intel(0): Allocated new frame buffer 1600x900 stride 6656, tiled
(II) UXA(0): Driver registered support for the following operations:
(II)         solid
(II)         copy
(II)         composite (RENDER acceleration)
(II)         put_image
(II)         get_image
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(==) intel(0): DPMS enabled
(==) intel(0): Intel XvMC decoder enabled
(II) intel(0): Set up textured video
(II) intel(0): [XvMC] i965_xvmc driver initialized.
(II) intel(0): direct rendering: DRI2 Enabled
(--) RandR disabled
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
SELinux: Disabled on system, not enabling in X server
(EE) GLX error: Can not get required symbols.
(II) intel(0): Setting screen physical size to 423 x 238
(II) config/udev: Adding input device Power Button (/dev/input/event5)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6.901, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event5"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Video Bus (/dev/input/event10)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event10"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Lid Switch (/dev/input/event3)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Video Bus (/dev/input/event9)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event9"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Power Button (/dev/input/event4)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event4"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device HP TrueVision HD (/dev/input/event8)
(**) HP TrueVision HD: Applying InputClass "evdev keyboard catchall"
(**) HP TrueVision HD: always reports core events
(**) HP TrueVision HD: Device: "/dev/input/event8"
(II) HP TrueVision HD: Found keys
(II) HP TrueVision HD: Configuring as keyboard
(II) XINPUT: Adding extended input device "HP TrueVision HD" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event12)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel PCH Mic at Ext Front Jack (/dev/input/event13)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel PCH HP Out at Ext Front Jack (/dev/input/event14)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event1)
(**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event1"
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event2)
(**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
(**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event2"
(II) Logitech USB Receiver: Found 20 mouse buttons
(II) Logitech USB Receiver: Found scroll wheel(s)
(II) Logitech USB Receiver: Found relative axes
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Found absolute axes
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as mouse
(II) Logitech USB Receiver: Configuring as keyboard
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) Logitech USB Receiver: initialized for relative axes.
(WW) Logitech USB Receiver: ignoring absolute axes.
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event0)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event0"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.7.6.901, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.2
(**) Option "Device" "/dev/input/event7"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5756
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4868
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
(II) SynPS/2 Synaptics TouchPad: buttons: left right double triple
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
(II) Synaptics touchpad driver version 1.2.2
SynPS/2 Synaptics TouchPad no synaptics event device found
(**) Option "Device" "/dev/input/mouse1"
Query no Synaptics: 6003C8
(--) SynPS/2 Synaptics TouchPad: no supported touchpad found
(EE) SynPS/2 Synaptics TouchPad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "SynPS/2 Synaptics TouchPad"
(II) UnloadModule: "synaptics"
(II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/event11)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/js0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device ACPI Virtual Keyboard Device (/dev/input/event15)
(**) ACPI Virtual Keyboard Device: Applying InputClass "evdev keyboard catchall"
(**) ACPI Virtual Keyboard Device: always reports core events
(**) ACPI Virtual Keyboard Device: Device: "/dev/input/event15"
(II) ACPI Virtual Keyboard Device: Found keys
(II) ACPI Virtual Keyboard Device: Configuring as keyboard
(II) XINPUT: Adding extended input device "ACPI Virtual Keyboard Device" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event6)
(**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
(**) HP WMI hotkeys: always reports core events
(**) HP WMI hotkeys: Device: "/dev/input/event6"
(II) HP WMI hotkeys: Found keys
(II) HP WMI hotkeys: Configuring as keyboard
(II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) intel(0): EDID vendor "LGD", prod id 634
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0   97.75  1600 1648 1696 1784  900 902 905 912 -hsync -vsync (54.8 kHz)
(II) intel(0): EDID vendor "LGD", prod id 634
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0   97.75  1600 1648 1696 1784  900 902 905 912 -hsync -vsync (54.8 kHz)
(II) intel(0): EDID vendor "LGD", prod id 634
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0   97.75  1600 1648 1696 1784  900 902 905 912 -hsync -vsync (54.8 kHz)

---

### Post by wecing on 2011-08-30
and also hope this would help:
> wecing@D5:~$ sudo lshw -C video
[sudo] password for wecing: 
  *-display               
       description: VGA compatible controller
       product: NI Seymour [AMD Radeon HD 6470M]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:51 memory:a0000000-afffffff memory:c6500000-c651ffff ioport:5000(size=256) memory:c6520000-c653ffff
  *-display
       description: VGA compatible controller
       product: Sandy Bridge Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:49 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:6000(size=64)


---

### Post by wecing on 2011-08-30
This copy is the one when X break after I used mplayer.
> 
X.Org X Server 1.7.7
Release Date: 2010-05-04
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.37-trunk-amd64 x86_64 Debian
Current Operating System: Linux D5 2.6.38-bpo.2-amd64 #1 SMP Mon Jun 6 15:24:02 UTC 2011 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-bpo.2-amd64 root=UUID=b373b7ea-debb-4ce8-bd4c-dcb0c19177c9 ro quiet
Build Date: 18 February 2011  08:27:24PM
xorg-server 2:1.7.7-13 (Cyril Brulebois <kibi@debian.org>) 
Current version of pixman: 0.16.4
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Aug 30 16:42:52 2011
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
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
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x7c8aa0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 8

(--) PCI:*(0:0:2:0) 8086:0116:103c:1659 Intel Corporation Sandy Bridge Integrated Graphics Controller rev 9, Mem @ 0xc0000000/4194304, 0xb0000000/268435456, I/O @ 0x00006000/64
(--) PCI: (0:1:0:0) 1002:6760:103c:1659 ATI Technologies Inc NI Seymour [AMD Radeon HD 6470M] rev 0, Mem @ 0xa0000000/268435456, 0xc6500000/131072, I/O @ 0x00005000/256, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension SELinux
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
	compiled for 1.7.7, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched intel as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 2.13.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 2.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.7.6.901, module version = 0.4.2
	ABI class: X.Org Video Driver, version 6.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 0.0.2
	ABI class: X.Org Video Driver, version 6.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge
(--) intel(0): Chipset: "Sandybridge"
(**) intel(0): Tiling enabled
(**) intel(0): SwapBuffers wait disabled
(==) intel(0): video overlay key set to 0x101fe
(II) intel(0): Output LVDS1 has no monitor section
(II) intel(0): found backlight control interface /sys/class/backlight/acpi_video1
(II) intel(0): Output VGA1 has no monitor section
(II) intel(0): Output HDMI1 has no monitor section
(II) intel(0): Output DP1 has no monitor section
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: LGD  Model: 27a  Serial#: 0
(II) intel(0): Year: 2009  Week: 0
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 38  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.615 redY: 0.346   greenX: 0.314 greenY: 0.602
(II) intel(0): blueX: 0.151 blueY: 0.109   whiteX: 0.312 whiteY: 0.328
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 97.8 MHz   Image Size:  382 x 215 mm
(II) intel(0): h_active: 1600  h_sync: 1648  h_sync_end 1696 h_blank_end 1784 h_border: 0
(II) intel(0): v_active: 900  v_sync: 902  v_sync_end 905 v_blanking: 912 v_border: 0
(II) intel(0):  
(II) intel(0):  LP173WD1-TLC3
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff0030e47a0200000000
(II) intel(0): 	00130103802615780aa8c09d58509a26
(II) intel(0): 	1c505400000001010101010101010101
(II) intel(0): 	0101010101012f2640b860840c303030
(II) intel(0): 	23007ed7100000190000000000000000
(II) intel(0): 	00000000000000000000000000fe0000
(II) intel(0): 	00004c47446973706c61790a000000fe
(II) intel(0): 	004c503137335744312d544c433300c2
(II) intel(0): EDID vendor "LGD", prod id 634
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0   97.75  1600 1648 1696 1784  900 902 905 912 -hsync -vsync (54.8 kHz)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
(II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
(II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
(II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1600x900"x60.1   97.75  1600 1648 1696 1784  900 902 905 912 -hsync -vsync (54.8 kHz)
(II) intel(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
(II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output HDMI1
(II) intel(0): EDID for output DP1
(II) intel(0): Output LVDS1 connected
(II) intel(0): Output VGA1 disconnected
(II) intel(0): Output HDMI1 disconnected
(II) intel(0): Output DP1 disconnected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output LVDS1 using initial mode 1600x900
(II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(II) intel(0): Kernel page flipping support detected, enabling
(**) intel(0): Display dimensions: (380, 210) mm
(**) intel(0): DPI set to (106, 108)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(==) Depth 24 pixmap format is 32 bpp
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): [DRI2] Setup complete
(EE) intel(0): Failed to allocate framebuffer.
(EE) intel(0): Couldn't allocate initial framebuffer.

Fatal server error:
AddScreen/ScreenInit failed for driver 0


Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.


And It's wired that playing videos through the flash plugin in my browser is ok.
I'm using the beta version 64-bit Adobe flash player.

---

### Post by .... on 2011-08-30
> (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.5.0, module version = 1.0.0

You still have the proprietary ATI version of libglx.so as the default.

See if this helps:
```
sudo dpkg-divert --remove /usr/lib/xorg/modules/extensions/libglx.so
```

---

### Post by wecing on 2011-08-30
No...
> # dpkg-divert --remove /usr/lib/xorg/modules/extensions/libglx.so 
No diversion 'any diversion of /usr/lib/xorg/modules/extensions/libglx.so', none removed.

My X is not work now. I can neither use ctrl+alt+f1 to switch to the tty consoles. So I booted with a live cd, chrooted to the partion, called the command, but it seems not working. Bad luck. ;-P

===============================

Screw it. I reinstalled my Debian, but my video player is still not working.
The original problem got solved, and I will create a new thread.

Thank you all for your generous help on me.

---

### Post by realzippy on 2011-08-31
If anybody else ever should be interested,
```
sudo apt-get install --reinstall xserver-xorg-core
```
should kick the ati version of libglx.so

---

### Post by .... on 2011-08-31
> **realzippy said:**
> If anybody else ever should be interested,
```
sudo apt-get install --reinstall xserver-xorg-core
```should kick the ati version of libglx.so
Yeah, but s/he already did that. There was probably cruft left in the alternatives selection. That was my next step, but it's a moot point now....

---

### Post by bcschmerker on 2011-09-05
Thanks for a heads up on a potential problem.  I'm curently considering a video upgrade of my hybrid Everex® mid-tower with 500W Athena® PSU feeding an AMD®-CPU/chipset/VDA mobo, from the planar Radeon® HD 3200 to either an HD 3650 (viz., ATi® All-In-Wonder&#8482; HD, also useful for video input from digital cable TV) or an HD 6850 (can drive multiple displays, and I landed two used Asus® EAH6850DC/2DS/1GD5 VDA's on eBay® for the MSRP of one new, before shipping).  The 6850, being a bleeding-edge GPU, could easily force the use of Catalyst&#8482; Control Center (package: fglrx-amdcccle), while the open-source Radeon driver (package: xserver-xorg-radeonhd) should be able to handle the 3650 on the All-in-Wonder&#8482; HD as well as it does the planar 3200.

**Update:**  The Gigabyte® MA78GM-S2HP proved unable to properly control the HD 6850 during power-on self test, thereby ruling the EAH6850DC out of further consideration (barring a rebuild of the Everex®  around a late-model Asus®  micro-ATX board such as the M3A78-EM).

---

