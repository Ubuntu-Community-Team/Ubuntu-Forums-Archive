---
title: "Sony Vaio VPCS12M9E"
date: 2010-08-28
forum: Hardware
---

### Post by zecapistolas on 2010-08-28
Hello, this is my first post on forum....

Recently i buy new laptop, **Sony Vaio VPCS12M9E** but most hardware on this laptop does not work with Ubuntu 10.10 Maverick.... :(

What work out-of-box:
[LIST]
[*]Ethernet
[*]Wireless
[*]Bluetooth
[*]Sound
[*]VGA
[/LIST]

What does not work:
[LIST]
[*]Graphics, this laptop have a **GeForce 310M**. I follow this [tutorial]("http://www.sucka.net/2010/04/how-to-install-nvidia-video-driver-in-10-04-lucid-lynx/") but does not work
[*]Trackpad
[*]SD Reader (Ricoh)
[/LIST]

Please, help me on this hard work.... ;-)

---

### Post by an0dos on 2010-08-28
For your nvidia graphics-
try disabling KMS. There are instructions [here]("https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture").

---

### Post by zecapistolas on 2010-08-28
> **an0dos said:**
> For your nvidia graphics-
try disabling KMS. There are instructions [here]("https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture").

It's the same....

I was trying this [tutorial]("http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html"), the graphics work, but don't work perfectly... I can not change resolution, plug other device to VGA....
When i run *nvidia-setting* appears pop-up said "run `nvidia-xconfig` as root", then i restart laptop but does not starts X... :(

---

### Post by zecapistolas on 2010-08-28
I have also tried [this]("http://ubuntuforums.org/showthread.php?t=1392766&highlight=310M#9"), but don't work...

If i have /etc/X11/xorg.conf file, the X does not start.... :(

---

### Post by zecapistolas on 2010-08-28
_Without_ /etc/X11/xorg.conf file:
```

$ cat /var/log/Xorg.0.log
[    15.121] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    15.121] X Protocol Version 11, Revision 0
[    15.121] Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
[    15.121] Current Operating System: Linux zecarlos-laptop 2.6.35-19-generic #26-Ubuntu SMP Thu Aug 26 19:13:05 UTC 2010 i686
[    15.121] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-19-generic root=UUID=bf2171de-9d92-4c11-b0d0-a42602de101d ro quiet splash
[    15.121] Build Date: 24 August 2010  09:14:22AM
[    15.121] xorg-server 2:1.9.0-0ubuntu1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    15.121] Current version of pixman: 0.18.2
[    15.121] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    15.121] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    15.121] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Aug 28 16:25:15 2010
[    15.157] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    15.165] (==) No Layout section.  Using the first Screen section.
[    15.165] (==) No screen section available. Using defaults.
[    15.165] (**) |-->Screen "Default Screen Section" (0)
[    15.165] (**) |   |-->Monitor "<default monitor>"
[    15.166] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    15.166] (==) Automatically adding devices
[    15.166] (==) Automatically enabling devices
[    15.166] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    15.166] 	Entry deleted from font path.
[    15.166] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    15.166] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    15.166] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    15.166] (II) Loader magic: 0x81f8e00
[    15.166] (II) Module ABI versions:
[    15.166] 	X.Org ANSI C Emulation: 0.4
[    15.166] 	X.Org Video Driver: 8.0
[    15.166] 	X.Org XInput driver : 11.0
[    15.166] 	X.Org Server Extension : 4.0
[    15.167] (--) PCI:*(0:1:0:0) 10de:0a75:104d:9069 rev 162, Mem @ 0xd2000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00007000/128, BIOS @ 0x????????/524288
[    15.167] (II) Open ACPI successful (/var/run/acpid.socket)
[    15.167] (II) LoadModule: "extmod"
[    15.168] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    15.168] (II) Module extmod: vendor="X.Org Foundation"
[    15.168] 	compiled for 1.9.0, module version = 1.0.0
[    15.168] 	Module class: X.Org Server Extension
[    15.168] 	ABI class: X.Org Server Extension, version 4.0
[    15.168] (II) Loading extension MIT-SCREEN-SAVER
[    15.168] (II) Loading extension XFree86-VidModeExtension
[    15.168] (II) Loading extension XFree86-DGA
[    15.168] (II) Loading extension DPMS
[    15.168] (II) Loading extension XVideo
[    15.168] (II) Loading extension XVideo-MotionCompensation
[    15.168] (II) Loading extension X-Resource
[    15.168] (II) LoadModule: "dbe"
[    15.168] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    15.168] (II) Module dbe: vendor="X.Org Foundation"
[    15.168] 	compiled for 1.9.0, module version = 1.0.0
[    15.168] 	Module class: X.Org Server Extension
[    15.168] 	ABI class: X.Org Server Extension, version 4.0
[    15.168] (II) Loading extension DOUBLE-BUFFER
[    15.168] (II) LoadModule: "glx"
[    15.168] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    15.183] (II) Module glx: vendor="NVIDIA Corporation"
[    15.183] 	compiled for 4.0.2, module version = 1.0.0
[    15.183] 	Module class: X.Org Server Extension
[    15.183] (II) NVIDIA GLX Module  256.44  Thu Jul 29 01:55:11 PDT 2010
[    15.183] (II) Loading extension GLX
[    15.183] (II) LoadModule: "record"
[    15.183] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    15.183] (II) Module record: vendor="X.Org Foundation"
[    15.183] 	compiled for 1.9.0, module version = 1.13.0
[    15.183] 	Module class: X.Org Server Extension
[    15.183] 	ABI class: X.Org Server Extension, version 4.0
[    15.183] (II) Loading extension RECORD
[    15.183] (II) LoadModule: "dri"
[    15.183] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    15.183] (II) Module dri: vendor="X.Org Foundation"
[    15.183] 	compiled for 1.9.0, module version = 1.0.0
[    15.183] 	ABI class: X.Org Server Extension, version 4.0
[    15.183] (II) Loading extension XFree86-DRI
[    15.183] (II) LoadModule: "dri2"
[    15.184] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    15.184] (II) Module dri2: vendor="X.Org Foundation"
[    15.184] 	compiled for 1.9.0, module version = 1.2.0
[    15.184] 	ABI class: X.Org Server Extension, version 4.0
[    15.184] (II) Loading extension DRI2
[    15.184] (==) Matched nouveau as autoconfigured driver 0
[    15.184] (==) Matched nv as autoconfigured driver 1
[    15.184] (==) Matched vesa as autoconfigured driver 2
[    15.184] (==) Matched fbdev as autoconfigured driver 3
[    15.184] (==) Assigned the driver to the xf86ConfigLayout
[    15.184] (II) LoadModule: "nouveau"
[    15.234] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    15.244] (II) Module nouveau: vendor="X.Org Foundation"
[    15.244] 	compiled for 1.8.99.905, module version = 0.0.16
[    15.244] 	Module class: X.Org Video Driver
[    15.245] 	ABI class: X.Org Video Driver, version 8.0
[    15.245] (II) LoadModule: "nv"
[    15.245] (II) Loading /usr/lib/xorg/modules/drivers/nv_drv.so
[    15.245] (II) Module nv: vendor="X.Org Foundation"
[    15.245] 	compiled for 1.8.99.905, module version = 2.1.17
[    15.245] 	Module class: X.Org Video Driver
[    15.245] 	ABI class: X.Org Video Driver, version 8.0
[    15.245] (II) LoadModule: "vesa"
[    15.245] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    15.245] (II) Module vesa: vendor="X.Org Foundation"
[    15.245] 	compiled for 1.8.99.905, module version = 2.3.0
[    15.245] 	Module class: X.Org Video Driver
[    15.245] 	ABI class: X.Org Video Driver, version 8.0
[    15.245] (II) LoadModule: "fbdev"
[    15.246] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    15.246] (II) Module fbdev: vendor="X.Org Foundation"
[    15.246] 	compiled for 1.8.99.905, module version = 0.4.2
[    15.246] 	ABI class: X.Org Video Driver, version 8.0
[    15.246] (II) NOUVEAU driver Date:   Thu Aug 5 00:40:40 2010 +0200
[    15.246] (II) NOUVEAU driver for NVIDIA chipset families :
[    15.246] 	RIVA TNT    (NV04)
[    15.246] 	RIVA TNT2   (NV05)
[    15.246] 	GeForce 256 (NV10)
[    15.246] 	GeForce 2   (NV11, NV15)
[    15.246] 	GeForce 4MX (NV17, NV18)
[    15.246] 	GeForce 3   (NV20)
[    15.246] 	GeForce 4Ti (NV25, NV28)
[    15.246] 	GeForce FX  (NV3x)
[    15.246] 	GeForce 6   (NV4x)
[    15.246] 	GeForce 7   (G7x)
[    15.246] 	GeForce 8   (G8x)
[    15.246] (II) NOUVEAU driver Date:   Thu Aug 5 00:40:40 2010 +0200
[    15.246] (II) NOUVEAU driver for NVIDIA chipset families :
[    15.246] 	RIVA TNT    (NV04)
[    15.246] 	RIVA TNT2   (NV05)
[    15.246] 	GeForce 256 (NV10)
[    15.246] 	GeForce 2   (NV11, NV15)
[    15.246] 	GeForce 4MX (NV17, NV18)
[    15.246] 	GeForce 3   (NV20)
[    15.246] 	GeForce 4Ti (NV25, NV28)
[    15.246] 	GeForce FX  (NV3x)
[    15.246] 	GeForce 6   (NV4x)
[    15.246] 	GeForce 7   (G7x)
[    15.246] 	GeForce 8   (G8x)
[    15.246] (II) VESA: driver for VESA chipsets: vesa
[    15.246] (II) FBDEV: driver for framebuffer: fbdev
[    15.246] (++) using VT number 7

[    15.249] drmOpenDevice: node name is /dev/dri/card0
[    15.307] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    15.307] drmOpenDevice: node name is /dev/dri/card0
[    15.311] drmOpenByBusid: drmOpenMinor returns -1
[    15.311] drmOpenDevice: node name is /dev/dri/card1
[    15.316] drmOpenByBusid: drmOpenMinor returns -1
[    15.316] drmOpenDevice: node name is /dev/dri/card2
[    15.320] drmOpenByBusid: drmOpenMinor returns -1
[    15.320] drmOpenDevice: node name is /dev/dri/card3
[    15.324] drmOpenByBusid: drmOpenMinor returns -1
[    15.324] drmOpenDevice: node name is /dev/dri/card4
[    15.328] drmOpenByBusid: drmOpenMinor returns -1
[    15.328] drmOpenDevice: node name is /dev/dri/card5
[    15.332] drmOpenByBusid: drmOpenMinor returns -1
[    15.332] drmOpenDevice: node name is /dev/dri/card6
[    15.337] drmOpenByBusid: drmOpenMinor returns -1
[    15.337] drmOpenDevice: node name is /dev/dri/card7
[    15.341] drmOpenByBusid: drmOpenMinor returns -1
[    15.341] drmOpenDevice: node name is /dev/dri/card8
[    15.345] drmOpenByBusid: drmOpenMinor returns -1
[    15.345] drmOpenDevice: node name is /dev/dri/card9
[    15.349] drmOpenByBusid: drmOpenMinor returns -1
[    15.349] drmOpenDevice: node name is /dev/dri/card10
[    15.353] drmOpenByBusid: drmOpenMinor returns -1
[    15.353] drmOpenDevice: node name is /dev/dri/card11
[    15.357] drmOpenByBusid: drmOpenMinor returns -1
[    15.358] drmOpenDevice: node name is /dev/dri/card12
[    15.362] drmOpenByBusid: drmOpenMinor returns -1
[    15.362] drmOpenDevice: node name is /dev/dri/card13
[    15.366] drmOpenByBusid: drmOpenMinor returns -1
[    15.366] drmOpenDevice: node name is /dev/dri/card14
[    15.370] drmOpenByBusid: drmOpenMinor returns -1
[    15.370] drmOpenDevice: node name is /dev/dri/card15
[    15.374] drmOpenByBusid: drmOpenMinor returns -1
[    15.374] drmOpenDevice: node name is /dev/dri/card0
[    15.381] drmOpenDevice: node name is /dev/dri/card0
[    15.385] drmOpenDevice: node name is /dev/dri/card1
[    15.389] drmOpenDevice: node name is /dev/dri/card2
[    15.393] drmOpenDevice: node name is /dev/dri/card3
[    15.397] drmOpenDevice: node name is /dev/dri/card4
[    15.402] drmOpenDevice: node name is /dev/dri/card5
[    15.406] drmOpenDevice: node name is /dev/dri/card6
[    15.410] drmOpenDevice: node name is /dev/dri/card7
[    15.415] drmOpenDevice: node name is /dev/dri/card8
[    15.419] drmOpenDevice: node name is /dev/dri/card9
[    15.423] drmOpenDevice: node name is /dev/dri/card10
[    15.427] drmOpenDevice: node name is /dev/dri/card11
[    15.431] drmOpenDevice: node name is /dev/dri/card12
[    15.435] drmOpenDevice: node name is /dev/dri/card13
[    15.440] drmOpenDevice: node name is /dev/dri/card14
[    15.444] drmOpenDevice: node name is /dev/dri/card15
[    15.448] (EE) [drm] failed to open device
[    15.448] (WW) Falling back to old probe method for fbdev
[    15.448] (II) Loading sub module "fbdevhw"
[    15.448] (II) LoadModule: "fbdevhw"
[    15.448] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    15.449] (II) Module fbdevhw: vendor="X.Org Foundation"
[    15.449] 	compiled for 1.9.0, module version = 0.0.2
[    15.449] 	ABI class: X.Org Video Driver, version 8.0
[    15.449] (EE) open /dev/fb0: No such file or directory
[    15.449] (II) Loading sub module "vbe"
[    15.449] (II) LoadModule: "vbe"
[    15.449] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    15.449] (II) Module vbe: vendor="X.Org Foundation"
[    15.449] 	compiled for 1.9.0, module version = 1.1.0
[    15.449] 	ABI class: X.Org Video Driver, version 8.0
[    15.449] (II) Loading sub module "int10"
[    15.449] (II) LoadModule: "int10"
[    15.449] (II) Loading /usr/lib/xorg/modules/libint10.so
[    15.449] (II) Module int10: vendor="X.Org Foundation"
[    15.449] 	compiled for 1.9.0, module version = 1.0.0
[    15.449] 	ABI class: X.Org Video Driver, version 8.0
[    15.449] (II) VESA(0): initializing int10
[    15.450] (II) VESA(0): Bad V_BIOS checksum
[    15.450] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    15.562] (II) VESA(0): VESA BIOS detected
[    15.562] (II) VESA(0): VESA VBE Version 3.0
[    15.562] (II) VESA(0): VESA VBE Total Mem: 14336 kB
[    15.562] (II) VESA(0): VESA VBE OEM: NVIDIA
[    15.562] (II) VESA(0): VESA VBE OEM Software Rev: 112.24
[    15.562] (II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
[    15.562] (II) VESA(0): VESA VBE OEM Product: GT218 Board - 0696a750
[    15.562] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
[    15.748] (II) VESA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    15.748] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[    15.748] (==) VESA(0): RGB weight 888
[    15.748] (==) VESA(0): Default visual is TrueColor
[    15.748] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[    15.748] (II) Loading sub module "ddc"
[    15.748] (II) LoadModule: "ddc"
[    15.748] (II) Module "ddc" already built-in
[    15.751] (II) VESA(0): VESA VBE DDC supported
[    15.751] (II) VESA(0): VESA VBE DDC Level 2
[    15.751] (II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
[    15.878] (II) VESA(0): VESA VBE DDC read successfully
[    15.878] (II) VESA(0): Manufacturer: SAM  Model: 88  Serial#: 1297035573
[    15.878] (II) VESA(0): Year: 2003  Week: 5
[    15.878] (II) VESA(0): EDID Version: 1.3
[    15.878] (II) VESA(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    15.878] (II) VESA(0): Sync:  Separate  Composite
[    15.878] (II) VESA(0): Max Image Size [cm]: horiz.: 30  vert.: 23
[    15.878] (II) VESA(0): Gamma: 1.97
[    15.878] (II) VESA(0): DPMS capabilities: Off; RGB/Color Display
[    15.878] (II) VESA(0): First detailed timing is preferred mode
[    15.878] (II) VESA(0): redX: 0.601 redY: 0.335   greenX: 0.304 greenY: 0.593
[    15.878] (II) VESA(0): blueX: 0.149 blueY: 0.106   whiteX: 0.295 whiteY: 0.310
[    15.878] (II) VESA(0): Supported established timings:
[    15.878] (II) VESA(0): 720x400@70Hz
[    15.878] (II) VESA(0): 640x480@60Hz
[    15.878] (II) VESA(0): 640x480@67Hz
[    15.878] (II) VESA(0): 640x480@75Hz
[    15.878] (II) VESA(0): 800x600@56Hz
[    15.878] (II) VESA(0): 800x600@60Hz
[    15.878] (II) VESA(0): 800x600@75Hz
[    15.878] (II) VESA(0): 832x624@75Hz
[    15.878] (II) VESA(0): 1024x768@60Hz
[    15.878] (II) VESA(0): 1024x768@70Hz
[    15.878] (II) VESA(0): 1024x768@75Hz
[    15.878] (II) VESA(0): Manufacturer's mask: 0
[    15.878] (II) VESA(0): Supported standard timings:
[    15.878] (II) VESA(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
[    15.878] (II) VESA(0): #1: hsize: 800  vsize 600  refresh: 60  vid: 16453
[    15.878] (II) VESA(0): #2: hsize: 1024  vsize 768  refresh: 60  vid: 16481
[    15.878] (II) VESA(0): #3: hsize: 640  vsize 480  refresh: 75  vid: 20273
[    15.878] (II) VESA(0): #4: hsize: 800  vsize 600  refresh: 75  vid: 20293
[    15.878] (II) VESA(0): #5: hsize: 1024  vsize 768  refresh: 75  vid: 20321
[    15.878] (II) VESA(0): Supported detailed timing:
[    15.878] (II) VESA(0): clock: 65.0 MHz   Image Size:  304 x 228 mm
[    15.878] (II) VESA(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
[    15.878] (II) VESA(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
[    15.878] (II) VESA(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 61 kHz, PixClock max 85 MHz
[    15.878] (II) VESA(0): Monitor name: SyncMaster
[    15.878] (II) VESA(0): Serial No: HMFW105243
[    15.878] (II) VESA(0): EDID (in hex):
[    15.878] (II) VESA(0): 	00ffffffffffff004c2d880035314f4d
[    15.878] (II) VESA(0): 	050d01030c1e17612aff5999554d9726
[    15.878] (II) VESA(0): 	1b4b4fb76e00314045406140314f454f
[    15.878] (II) VESA(0): 	614f0101010164190040410026301888
[    15.878] (II) VESA(0): 	360030e410000018000000fd00384b1e
[    15.878] (II) VESA(0): 	3d08000a202020202020000000fc0053
[    15.878] (II) VESA(0): 	796e634d61737465720a2020000000ff
[    15.878] (II) VESA(0): 	00484d46573130353234330a2020008c
[    15.878] (II) VESA(0): EDID vendor "SAM", prod id 136
[    15.878] (II) VESA(0): Using EDID range info for horizontal sync
[    15.878] (II) VESA(0): Using EDID range info for vertical refresh
[    15.878] (II) VESA(0): Printing DDC gathered Modelines:
[    15.878] (II) VESA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    15.878] (II) VESA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    15.878] (II) VESA(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    15.878] (II) VESA(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    15.879] (II) VESA(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    15.879] (II) VESA(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    15.879] (II) VESA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    15.879] (II) VESA(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    15.879] (II) VESA(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    15.879] (II) VESA(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    15.879] (II) VESA(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    15.879] (II) VESA(0): Searching for matching VESA mode(s):
[    15.881] Mode: 100 (640x400)
[    15.881] 	ModeAttributes: 0x3bf
[    15.881] 	WinAAttributes: 0x7
[    15.881] 	WinBAttributes: 0x0
[    15.881] 	WinGranularity: 64
[    15.881] 	WinSize: 64
[    15.881] 	WinASegment: 0xa000
[    15.881] 	WinBSegment: 0x0
[    15.881] 	WinFuncPtr: 0xc000687b
[    15.881] 	BytesPerScanline: 640
[    15.881] 	XResolution: 640
[    15.881] 	YResolution: 400
[    15.881] 	XCharSize: 8
[    15.881] 	YCharSize: 16
[    15.881] 	NumberOfPlanes: 1
[    15.881] 	BitsPerPixel: 8
[    15.881] 	NumberOfBanks: 1
[    15.881] 	MemoryModel: 4
[    15.881] 	BankSize: 0
[    15.881] 	NumberOfImages: 14
[    15.881] 	RedMaskSize: 0
[    15.881] 	RedFieldPosition: 0
[    15.881] 	GreenMaskSize: 0
[    15.881] 	GreenFieldPosition: 0
[    15.881] 	BlueMaskSize: 0
[    15.881] 	BlueFieldPosition: 0
[    15.881] 	RsvdMaskSize: 0
[    15.881] 	RsvdFieldPosition: 0
[    15.881] 	DirectColorModeInfo: 0
[    15.881] 	PhysBasePtr: 0xd1000000
[    15.881] 	LinBytesPerScanLine: 640
[    15.881] 	BnkNumberOfImagePages: 14
[    15.881] 	LinNumberOfImagePages: 14
[    15.881] 	LinRedMaskSize: 0
[    15.881] 	LinRedFieldPosition: 0
[    15.881] 	LinGreenMaskSize: 0
[    15.881] 	LinGreenFieldPosition: 0
[    15.881] 	LinBlueMaskSize: 0
[    15.882] 	LinBlueFieldPosition: 0
[    15.882] 	LinRsvdMaskSize: 0
[    15.882] 	LinRsvdFieldPosition: 0
[    15.882] 	MaxPixelClock: 229500000
[    15.884] Mode: 101 (640x480)
[    15.884] 	ModeAttributes: 0x3bf
[    15.884] 	WinAAttributes: 0x7
[    15.884] 	WinBAttributes: 0x0
[    15.884] 	WinGranularity: 64
[    15.884] 	WinSize: 64
[    15.884] 	WinASegment: 0xa000
[    15.884] 	WinBSegment: 0x0
[    15.884] 	WinFuncPtr: 0xc000687b
[    15.884] 	BytesPerScanline: 640
[    15.884] 	XResolution: 640
[    15.884] 	YResolution: 480
[    15.884] 	XCharSize: 8
[    15.884] 	YCharSize: 16
[    15.884] 	NumberOfPlanes: 1
[    15.884] 	BitsPerPixel: 8
[    15.884] 	NumberOfBanks: 1
[    15.884] 	MemoryModel: 4
[    15.884] 	BankSize: 0
[    15.884] 	NumberOfImages: 10
[    15.884] 	RedMaskSize: 0
[    15.884] 	RedFieldPosition: 0
[    15.884] 	GreenMaskSize: 0
[    15.884] 	GreenFieldPosition: 0
[    15.884] 	BlueMaskSize: 0
[    15.884] 	BlueFieldPosition: 0
[    15.884] 	RsvdMaskSize: 0
[    15.884] 	RsvdFieldPosition: 0
[    15.884] 	DirectColorModeInfo: 0
[    15.884] 	PhysBasePtr: 0xd1000000
[    15.884] 	LinBytesPerScanLine: 640
[    15.884] 	BnkNumberOfImagePages: 10
[    15.884] 	LinNumberOfImagePages: 10
[    15.884] 	LinRedMaskSize: 0
[    15.884] 	LinRedFieldPosition: 0
[    15.884] 	LinGreenMaskSize: 0
[    15.884] 	LinGreenFieldPosition: 0
[    15.884] 	LinBlueMaskSize: 0
[    15.884] 	LinBlueFieldPosition: 0
[    15.884] 	LinRsvdMaskSize: 0
[    15.884] 	LinRsvdFieldPosition: 0
[    15.884] 	MaxPixelClock: 229500000
[    15.887] Mode: 102 (800x600)
[    15.887] 	ModeAttributes: 0x33f
[    15.887] 	WinAAttributes: 0x7
[    15.887] 	WinBAttributes: 0x0
[    15.887] 	WinGranularity: 64
[    15.887] 	WinSize: 64
[    15.887] 	WinASegment: 0xa000
[    15.887] 	WinBSegment: 0x0
[    15.887] 	WinFuncPtr: 0xc000687b
[    15.887] 	BytesPerScanline: 100
[    15.887] 	XResolution: 800
[    15.887] 	YResolution: 600
[    15.887] 	XCharSize: 8
[    15.887] 	YCharSize: 16
[    15.887] 	NumberOfPlanes: 4
[    15.887] 	BitsPerPixel: 4
[    15.887] 	NumberOfBanks: 1
[    15.887] 	MemoryModel: 3
[    15.887] 	BankSize: 0
[    15.887] 	NumberOfImages: 2
[    15.887] 	RedMaskSize: 0
[    15.887] 	RedFieldPosition: 0
[    15.887] 	GreenMaskSize: 0
[    15.887] 	GreenFieldPosition: 0
[    15.887] 	BlueMaskSize: 0
[    15.887] 	BlueFieldPosition: 0
[    15.887] 	RsvdMaskSize: 0
[    15.887] 	RsvdFieldPosition: 0
[    15.887] 	DirectColorModeInfo: 0
[    15.887] 	PhysBasePtr: 0x0
[    15.887] 	LinBytesPerScanLine: 100
[    15.887] 	BnkNumberOfImagePages: 2
[    15.887] 	LinNumberOfImagePages: 2
[    15.887] 	LinRedMaskSize: 0
[    15.887] 	LinRedFieldPosition: 0
[    15.887] 	LinGreenMaskSize: 0
[    15.887] 	LinGreenFieldPosition: 0
[    15.887] 	LinBlueMaskSize: 0
[    15.887] 	LinBlueFieldPosition: 0
[    15.887] 	LinRsvdMaskSize: 0
[    15.887] 	LinRsvdFieldPosition: 0
[    15.887] 	MaxPixelClock: 108500000
[    15.890] Mode: 103 (800x600)
[    15.890] 	ModeAttributes: 0x3bf
[    15.890] 	WinAAttributes: 0x7
[    15.890] 	WinBAttributes: 0x0
[    15.890] 	WinGranularity: 64
[    15.890] 	WinSize: 64
[    15.890] 	WinASegment: 0xa000
[    15.890] 	WinBSegment: 0x0
[    15.890] 	WinFuncPtr: 0xc000687b
[    15.890] 	BytesPerScanline: 800
[    15.890] 	XResolution: 800
[    15.890] 	YResolution: 600
[    15.890] 	XCharSize: 8
[    15.890] 	YCharSize: 16
[    15.890] 	NumberOfPlanes: 1
[    15.890] 	BitsPerPixel: 8
[    15.890] 	NumberOfBanks: 1
[    15.890] 	MemoryModel: 4
[    15.890] 	BankSize: 0
[    15.890] 	NumberOfImages: 6
[    15.890] 	RedMaskSize: 0
[    15.890] 	RedFieldPosition: 0
[    15.890] 	GreenMaskSize: 0
[    15.890] 	GreenFieldPosition: 0
[    15.890] 	BlueMaskSize: 0
[    15.890] 	BlueFieldPosition: 0
[    15.890] 	RsvdMaskSize: 0
[    15.890] 	RsvdFieldPosition: 0
[    15.890] 	DirectColorModeInfo: 0
[    15.890] 	PhysBasePtr: 0xd1000000
[    15.890] 	LinBytesPerScanLine: 800
[    15.890] 	BnkNumberOfImagePages: 6
[    15.890] 	LinNumberOfImagePages: 6
[    15.890] 	LinRedMaskSize: 0
[    15.890] 	LinRedFieldPosition: 0
[    15.890] 	LinGreenMaskSize: 0
[    15.890] 	LinGreenFieldPosition: 0
[    15.890] 	LinBlueMaskSize: 0
[    15.890] 	LinBlueFieldPosition: 0
[    15.890] 	LinRsvdMaskSize: 0
[    15.890] 	LinRsvdFieldPosition: 0
[    15.890] 	MaxPixelClock: 229500000
[    15.893] Mode: 104 (1024x768)
[    15.893] 	ModeAttributes: 0x33f
[    15.893] 	WinAAttributes: 0x7
[    15.893] 	WinBAttributes: 0x0
[    15.893] 	WinGranularity: 64
[    15.893] 	WinSize: 64
[    15.893] 	WinASegment: 0xa000
[    15.893] 	WinBSegment: 0x0
[    15.893] 	WinFuncPtr: 0xc000687b
[    15.893] 	BytesPerScanline: 128
[    15.893] 	XResolution: 1024
[    15.893] 	YResolution: 768
[    15.893] 	XCharSize: 8
[    15.893] 	YCharSize: 16
[    15.893] 	NumberOfPlanes: 4
[    15.893] 	BitsPerPixel: 4
[    15.893] 	NumberOfBanks: 1
[    15.893] 	MemoryModel: 3
[    15.893] 	BankSize: 0
[    15.893] 	NumberOfImages: 1
[    15.893] 	RedMaskSize: 0
[    15.893] 	RedFieldPosition: 0
[    15.893] 	GreenMaskSize: 0
[    15.893] 	GreenFieldPosition: 0
[    15.893] 	BlueMaskSize: 0
[    15.893] 	BlueFieldPosition: 0
[    15.893] 	RsvdMaskSize: 0
[    15.893] 	RsvdFieldPosition: 0
[    15.893] 	DirectColorModeInfo: 0
[    15.893] 	PhysBasePtr: 0x0
[    15.893] 	LinBytesPerScanLine: 128
[    15.893] 	BnkNumberOfImagePages: 1
[    15.893] 	LinNumberOfImagePages: 1
[    15.893] 	LinRedMaskSize: 0
[    15.893] 	LinRedFieldPosition: 0
[    15.893] 	LinGreenMaskSize: 0
[    15.893] 	LinGreenFieldPosition: 0
[    15.893] 	LinBlueMaskSize: 0
[    15.893] 	LinBlueFieldPosition: 0
[    15.893] 	LinRsvdMaskSize: 0
[    15.893] 	LinRsvdFieldPosition: 0
[    15.893] 	MaxPixelClock: 108500000
[    15.896] Mode: 105 (1024x768)
[    15.896] 	ModeAttributes: 0x3bf
[    15.896] 	WinAAttributes: 0x7
[    15.896] 	WinBAttributes: 0x0
[    15.896] 	WinGranularity: 64
[    15.896] 	WinSize: 64
[    15.896] 	WinASegment: 0xa000
[    15.896] 	WinBSegment: 0x0
[    15.896] 	WinFuncPtr: 0xc000687b
[    15.896] 	BytesPerScanline: 1024
[    15.896] 	XResolution: 1024
[    15.896] 	YResolution: 768
[    15.896] 	XCharSize: 8
[    15.896] 	YCharSize: 16
[    15.896] 	NumberOfPlanes: 1
[    15.896] 	BitsPerPixel: 8
[    15.896] 	NumberOfBanks: 1
[    15.896] 	MemoryModel: 4
[    15.896] 	BankSize: 0
[    15.896] 	NumberOfImages: 3
[    15.896] 	RedMaskSize: 0
[    15.896] 	RedFieldPosition: 0
[    15.896] 	GreenMaskSize: 0
[    15.896] 	GreenFieldPosition: 0
[    15.896] 	BlueMaskSize: 0
[    15.896] 	BlueFieldPosition: 0
[    15.896] 	RsvdMaskSize: 0
[    15.896] 	RsvdFieldPosition: 0
[    15.896] 	DirectColorModeInfo: 0
[    15.896] 	PhysBasePtr: 0xd1000000
[    15.896] 	LinBytesPerScanLine: 1024
[    15.896] 	BnkNumberOfImagePages: 3
[    15.896] 	LinNumberOfImagePages: 3
[    15.896] 	LinRedMaskSize: 0
[    15.896] 	LinRedFieldPosition: 0
[    15.896] 	LinGreenMaskSize: 0
[    15.896] 	LinGreenFieldPosition: 0
[    15.896] 	LinBlueMaskSize: 0
[    15.896] 	LinBlueFieldPosition: 0
[    15.896] 	LinRsvdMaskSize: 0
[    15.896] 	LinRsvdFieldPosition: 0
[    15.896] 	MaxPixelClock: 229500000
[    15.899] Mode: 10e (320x200)
[    15.899] 	ModeAttributes: 0x3bf
[    15.899] 	WinAAttributes: 0x7
[    15.899] 	WinBAttributes: 0x0
[    15.899] 	WinGranularity: 64
[    15.899] 	WinSize: 64
[    15.899] 	WinASegment: 0xa000
[    15.899] 	WinBSegment: 0x0
[    15.899] 	WinFuncPtr: 0xc000687b
[    15.899] 	BytesPerScanline: 640
[    15.899] 	XResolution: 320
[    15.899] 	YResolution: 200
[    15.899] 	XCharSize: 8
[    15.899] 	YCharSize: 8
[    15.899] 	NumberOfPlanes: 1
[    15.899] 	BitsPerPixel: 16
[    15.899] 	NumberOfBanks: 1
[    15.899] 	MemoryModel: 6
[    15.899] 	BankSize: 0
[    15.899] 	NumberOfImages: 30
[    15.899] 	RedMaskSize: 5
[    15.899] 	RedFieldPosition: 11
[    15.899] 	GreenMaskSize: 6
[    15.899] 	GreenFieldPosition: 5
[    15.899] 	BlueMaskSize: 5
[    15.899] 	BlueFieldPosition: 0
[    15.899] 	RsvdMaskSize: 0
[    15.899] 	RsvdFieldPosition: 0
[    15.899] 	DirectColorModeInfo: 0
[    15.899] 	PhysBasePtr: 0xd1000000
[    15.899] 	LinBytesPerScanLine: 640
[    15.899] 	BnkNumberOfImagePages: 30
[    15.899] 	LinNumberOfImagePages: 30
[    15.899] 	LinRedMaskSize: 5
[    15.899] 	LinRedFieldPosition: 11
[    15.899] 	LinGreenMaskSize: 6
[    15.899] 	LinGreenFieldPosition: 5
[    15.899] 	LinBlueMaskSize: 5
[    15.899] 	LinBlueFieldPosition: 0
[    15.899] 	LinRsvdMaskSize: 0
[    15.899] 	LinRsvdFieldPosition: 0
[    15.899] 	MaxPixelClock: 229500000
[    15.901] *Mode: 10f (320x200)
[    15.901] 	ModeAttributes: 0x3bf
[    15.901] 	WinAAttributes: 0x7
[    15.901] 	WinBAttributes: 0x0
[    15.901] 	WinGranularity: 64
[    15.901] 	WinSize: 64
[    15.901] 	WinASegment: 0xa000
[    15.901] 	WinBSegment: 0x0
[    15.901] 	WinFuncPtr: 0xc000687b
[    15.901] 	BytesPerScanline: 1280
[    15.902] 	XResolution: 320
[    15.902] 	YResolution: 200
[    15.902] 	XCharSize: 8
[    15.902] 	YCharSize: 8
[    15.902] 	NumberOfPlanes: 1
[    15.902] 	BitsPerPixel: 32
[    15.902] 	NumberOfBanks: 1
[    15.902] 	MemoryModel: 6
[    15.902] 	BankSize: 0
[    15.902] 	NumberOfImages: 14
[    15.902] 	RedMaskSize: 8
[    15.902] 	RedFieldPosition: 16
[    15.902] 	GreenMaskSize: 8
[    15.902] 	GreenFieldPosition: 8
[    15.902] 	BlueMaskSize: 8
[    15.902] 	BlueFieldPosition: 0
[    15.902] 	RsvdMaskSize: 8
[    15.902] 	RsvdFieldPosition: 24
[    15.902] 	DirectColorModeInfo: 0
[    15.902] 	PhysBasePtr: 0xd1000000
[    15.902] 	LinBytesPerScanLine: 1280
[    15.902] 	BnkNumberOfImagePages: 14
[    15.902] 	LinNumberOfImagePages: 14
[    15.902] 	LinRedMaskSize: 8
[    15.902] 	LinRedFieldPosition: 16
[    15.902] 	LinGreenMaskSize: 8
[    15.902] 	LinGreenFieldPosition: 8
[    15.902] 	LinBlueMaskSize: 8
[    15.902] 	LinBlueFieldPosition: 0
[    15.902] 	LinRsvdMaskSize: 8
[    15.902] 	LinRsvdFieldPosition: 24
[    15.902] 	MaxPixelClock: 229500000
[    15.904] Mode: 111 (640x480)
[    15.904] 	ModeAttributes: 0x3bf
[    15.904] 	WinAAttributes: 0x7
[    15.904] 	WinBAttributes: 0x0
[    15.904] 	WinGranularity: 64
[    15.904] 	WinSize: 64
[    15.904] 	WinASegment: 0xa000
[    15.904] 	WinBSegment: 0x0
[    15.904] 	WinFuncPtr: 0xc000687b
[    15.904] 	BytesPerScanline: 1280
[    15.904] 	XResolution: 640
[    15.904] 	YResolution: 480
[    15.904] 	XCharSize: 8
[    15.904] 	YCharSize: 16
[    15.904] 	NumberOfPlanes: 1
[    15.904] 	BitsPerPixel: 16
[    15.904] 	NumberOfBanks: 1
[    15.904] 	MemoryModel: 6
[    15.904] 	BankSize: 0
[    15.904] 	NumberOfImages: 4
[    15.905] 	RedMaskSize: 5
[    15.905] 	RedFieldPosition: 11
[    15.905] 	GreenMaskSize: 6
[    15.905] 	GreenFieldPosition: 5
[    15.905] 	BlueMaskSize: 5
[    15.905] 	BlueFieldPosition: 0
[    15.905] 	RsvdMaskSize: 0
[    15.905] 	RsvdFieldPosition: 0
[    15.905] 	DirectColorModeInfo: 0
[    15.905] 	PhysBasePtr: 0xd1000000
[    15.905] 	LinBytesPerScanLine: 1280
[    15.905] 	BnkNumberOfImagePages: 4
[    15.905] 	LinNumberOfImagePages: 4
[    15.905] 	LinRedMaskSize: 5
[    15.905] 	LinRedFieldPosition: 11
[    15.905] 	LinGreenMaskSize: 6
[    15.905] 	LinGreenFieldPosition: 5
[    15.905] 	LinBlueMaskSize: 5
[    15.905] 	LinBlueFieldPosition: 0
[    15.905] 	LinRsvdMaskSize: 0
[    15.905] 	LinRsvdFieldPosition: 0
[    15.905] 	MaxPixelClock: 229500000
[    15.907] *Mode: 112 (640x480)
[    15.907] 	ModeAttributes: 0x3bf
[    15.907] 	WinAAttributes: 0x7
[    15.907] 	WinBAttributes: 0x0
[    15.907] 	WinGranularity: 64
[    15.907] 	WinSize: 64
[    15.907] 	WinASegment: 0xa000
[    15.907] 	WinBSegment: 0x0
[    15.907] 	WinFuncPtr: 0xc000687b
[    15.907] 	BytesPerScanline: 2560
[    15.907] 	XResolution: 640
[    15.907] 	YResolution: 480
[    15.907] 	XCharSize: 8
[    15.907] 	YCharSize: 16
[    15.907] 	NumberOfPlanes: 1
[    15.907] 	BitsPerPixel: 32
[    15.907] 	NumberOfBanks: 1
[    15.907] 	MemoryModel: 6
[    15.907] 	BankSize: 0
[    15.907] 	NumberOfImages: 1
[    15.907] 	RedMaskSize: 8
[    15.907] 	RedFieldPosition: 16
[    15.907] 	GreenMaskSize: 8
[    15.907] 	GreenFieldPosition: 8
[    15.907] 	BlueMaskSize: 8
[    15.907] 	BlueFieldPosition: 0
[    15.907] 	RsvdMaskSize: 8
[    15.907] 	RsvdFieldPosition: 24
[    15.907] 	DirectColorModeInfo: 0
[    15.907] 	PhysBasePtr: 0xd1000000
[    15.907] 	LinBytesPerScanLine: 2560
[    15.907] 	BnkNumberOfImagePages: 1
[    15.907] 	LinNumberOfImagePages: 1
[    15.907] 	LinRedMaskSize: 8
[    15.907] 	LinRedFieldPosition: 16
[    15.907] 	LinGreenMaskSize: 8
[    15.907] 	LinGreenFieldPosition: 8
[    15.907] 	LinBlueMaskSize: 8
[    15.907] 	LinBlueFieldPosition: 0
[    15.907] 	LinRsvdMaskSize: 8
[    15.907] 	LinRsvdFieldPosition: 24
[    15.907] 	MaxPixelClock: 229500000
[    15.911] Mode: 114 (800x600)
[    15.911] 	ModeAttributes: 0x3bf
[    15.911] 	WinAAttributes: 0x7
[    15.911] 	WinBAttributes: 0x0
[    15.911] 	WinGranularity: 64
[    15.911] 	WinSize: 64
[    15.911] 	WinASegment: 0xa000
[    15.911] 	WinBSegment: 0x0
[    15.911] 	WinFuncPtr: 0xc000687b
[    15.911] 	BytesPerScanline: 1600
[    15.911] 	XResolution: 800
[    15.911] 	YResolution: 600
[    15.911] 	XCharSize: 8
[    15.911] 	YCharSize: 16
[    15.911] 	NumberOfPlanes: 1
[    15.911] 	BitsPerPixel: 16
[    15.911] 	NumberOfBanks: 1
[    15.911] 	MemoryModel: 6
[    15.911] 	BankSize: 0
[    15.911] 	NumberOfImages: 2
[    15.911] 	RedMaskSize: 5
[    15.911] 	RedFieldPosition: 11
[    15.911] 	GreenMaskSize: 6
[    15.911] 	GreenFieldPosition: 5
[    15.911] 	BlueMaskSize: 5
[    15.911] 	BlueFieldPosition: 0
[    15.911] 	RsvdMaskSize: 0
[    15.911] 	RsvdFieldPosition: 0
[    15.911] 	DirectColorModeInfo: 0
[    15.911] 	PhysBasePtr: 0xd1000000
[    15.911] 	LinBytesPerScanLine: 1600
[    15.911] 	BnkNumberOfImagePages: 2
[    15.911] 	LinNumberOfImagePages: 2
[    15.911] 	LinRedMaskSize: 5
[    15.911] 	LinRedFieldPosition: 11
[    15.911] 	LinGreenMaskSize: 6
[    15.911] 	LinGreenFieldPosition: 5
[    15.911] 	LinBlueMaskSize: 5
[    15.911] 	LinBlueFieldPosition: 0
[    15.911] 	LinRsvdMaskSize: 0
[    15.911] 	LinRsvdFieldPosition: 0
[    15.911] 	MaxPixelClock: 229500000
[    15.913] *Mode: 115 (800x600)
[    15.913] 	ModeAttributes: 0x3bf
[    15.913] 	WinAAttributes: 0x7
[    15.913] 	WinBAttributes: 0x0
[    15.913] 	WinGranularity: 64
[    15.913] 	WinSize: 64
[    15.913] 	WinASegment: 0xa000
[    15.913] 	WinBSegment: 0x0
[    15.913] 	WinFuncPtr: 0xc000687b
[    15.913] 	BytesPerScanline: 3200
[    15.913] 	XResolution: 800
[    15.913] 	YResolution: 600
[    15.913] 	XCharSize: 8
[    15.913] 	YCharSize: 16
[    15.914] 	NumberOfPlanes: 1
[    15.914] 	BitsPerPixel: 32
[    15.914] 	NumberOfBanks: 1
[    15.914] 	MemoryModel: 6
[    15.914] 	BankSize: 0
[    15.914] 	NumberOfImages: 1
[    15.914] 	RedMaskSize: 8
[    15.914] 	RedFieldPosition: 16
[    15.914] 	GreenMaskSize: 8
[    15.914] 	GreenFieldPosition: 8
[    15.914] 	BlueMaskSize: 8
[    15.914] 	BlueFieldPosition: 0
[    15.914] 	RsvdMaskSize: 8
[    15.914] 	RsvdFieldPosition: 24
[    15.914] 	DirectColorModeInfo: 0
[    15.914] 	PhysBasePtr: 0xd1000000
[    15.914] 	LinBytesPerScanLine: 3200
[    15.914] 	BnkNumberOfImagePages: 1
[    15.914] 	LinNumberOfImagePages: 1
[    15.914] 	LinRedMaskSize: 8
[    15.914] 	LinRedFieldPosition: 16
[    15.914] 	LinGreenMaskSize: 8
[    15.914] 	LinGreenFieldPosition: 8
[    15.914] 	LinBlueMaskSize: 8
[    15.914] 	LinBlueFieldPosition: 0
[    15.914] 	LinRsvdMaskSize: 8
[    15.914] 	LinRsvdFieldPosition: 24
[    15.914] 	MaxPixelClock: 229500000
[    15.916] Mode: 117 (1024x768)
[    15.916] 	ModeAttributes: 0x3bf
[    15.916] 	WinAAttributes: 0x7
[    15.916] 	WinBAttributes: 0x0
[    15.916] 	WinGranularity: 64
[    15.916] 	WinSize: 64
[    15.916] 	WinASegment: 0xa000
[    15.916] 	WinBSegment: 0x0
[    15.916] 	WinFuncPtr: 0xc000687b
[    15.916] 	BytesPerScanline: 2048
[    15.916] 	XResolution: 1024
[    15.916] 	YResolution: 768
[    15.916] 	XCharSize: 8
[    15.916] 	YCharSize: 16
[    15.916] 	NumberOfPlanes: 1
[    15.916] 	BitsPerPixel: 16
[    15.916] 	NumberOfBanks: 1
[    15.916] 	MemoryModel: 6
[    15.916] 	BankSize: 0
[    15.916] 	NumberOfImages: 1
[    15.916] 	RedMaskSize: 5
[    15.916] 	RedFieldPosition: 11
[    15.916] 	GreenMaskSize: 6
[    15.916] 	GreenFieldPosition: 5
[    15.916] 	BlueMaskSize: 5
[    15.916] 	BlueFieldPosition: 0
[    15.917] 	RsvdMaskSize: 0
[    15.917] 	RsvdFieldPosition: 0
[    15.917] 	DirectColorModeInfo: 0
[    15.917] 	PhysBasePtr: 0xd1000000
[    15.917] 	LinBytesPerScanLine: 2048
[    15.917] 	BnkNumberOfImagePages: 1
[    15.917] 	LinNumberOfImagePages: 1
[    15.917] 	LinRedMaskSize: 5
[    15.917] 	LinRedFieldPosition: 11
[    15.917] 	LinGreenMaskSize: 6
[    15.917] 	LinGreenFieldPosition: 5
[    15.917] 	LinBlueMaskSize: 5
[    15.917] 	LinBlueFieldPosition: 0
[    15.917] 	LinRsvdMaskSize: 0
[    15.917] 	LinRsvdFieldPosition: 0
[    15.917] 	MaxPixelClock: 229500000
[    15.919] *Mode: 118 (1024x768)
[    15.919] 	ModeAttributes: 0x3bf
[    15.919] 	WinAAttributes: 0x7
[    15.919] 	WinBAttributes: 0x0
[    15.919] 	WinGranularity: 64
[    15.919] 	WinSize: 64
[    15.919] 	WinASegment: 0xa000
[    15.919] 	WinBSegment: 0x0
[    15.919] 	WinFuncPtr: 0xc000687b
[    15.919] 	BytesPerScanline: 4096
[    15.919] 	XResolution: 1024
[    15.919] 	YResolution: 768
[    15.919] 	XCharSize: 8
[    15.919] 	YCharSize: 16
[    15.919] 	NumberOfPlanes: 1
[    15.919] 	BitsPerPixel: 32
[    15.919] 	NumberOfBanks: 1
[    15.919] 	MemoryModel: 6
[    15.919] 	BankSize: 0
[    15.919] 	NumberOfImages: 1
[    15.919] 	RedMaskSize: 8
[    15.919] 	RedFieldPosition: 16
[    15.919] 	GreenMaskSize: 8
[    15.919] 	GreenFieldPosition: 8
[    15.919] 	BlueMaskSize: 8
[    15.919] 	BlueFieldPosition: 0
[    15.919] 	RsvdMaskSize: 8
[    15.919] 	RsvdFieldPosition: 24
[    15.919] 	DirectColorModeInfo: 0
[    15.919] 	PhysBasePtr: 0xd1000000
[    15.919] 	LinBytesPerScanLine: 4096
[    15.919] 	BnkNumberOfImagePages: 1
[    15.919] 	LinNumberOfImagePages: 1
[    15.919] 	LinRedMaskSize: 8
[    15.919] 	LinRedFieldPosition: 16
[    15.919] 	LinGreenMaskSize: 8
[    15.919] 	LinGreenFieldPosition: 8
[    15.919] 	LinBlueMaskSize: 8
[    15.919] 	LinBlueFieldPosition: 0
[    15.919] 	LinRsvdMaskSize: 8
[    15.919] 	LinRsvdFieldPosition: 24
[    15.919] 	MaxPixelClock: 229500000
[    15.922] Mode: 130 (320x200)
[    15.922] 	ModeAttributes: 0x3bf
[    15.922] 	WinAAttributes: 0x7
[    15.922] 	WinBAttributes: 0x0
[    15.922] 	WinGranularity: 64
[    15.922] 	WinSize: 64
[    15.922] 	WinASegment: 0xa000
[    15.922] 	WinBSegment: 0x0
[    15.922] 	WinFuncPtr: 0xc000687b
[    15.922] 	BytesPerScanline: 320
[    15.922] 	XResolution: 320
[    15.922] 	YResolution: 200
[    15.922] 	XCharSize: 8
[    15.922] 	YCharSize: 8
[    15.922] 	NumberOfPlanes: 1
[    15.922] 	BitsPerPixel: 8
[    15.922] 	NumberOfBanks: 1
[    15.922] 	MemoryModel: 4
[    15.922] 	BankSize: 0
[    15.922] 	NumberOfImages: 62
[    15.922] 	RedMaskSize: 0
[    15.922] 	RedFieldPosition: 0
[    15.922] 	GreenMaskSize: 0
[    15.922] 	GreenFieldPosition: 0
[    15.922] 	BlueMaskSize: 0
[    15.922] 	BlueFieldPosition: 0
[    15.922] 	RsvdMaskSize: 0
[    15.922] 	RsvdFieldPosition: 0
[    15.922] 	DirectColorModeInfo: 0
[    15.922] 	PhysBasePtr: 0xd1000000
[    15.922] 	LinBytesPerScanLine: 320
[    15.922] 	BnkNumberOfImagePages: 62
[    15.922] 	LinNumberOfImagePages: 62
[    15.922] 	LinRedMaskSize: 0
[    15.922] 	LinRedFieldPosition: 0
[    15.922] 	LinGreenMaskSize: 0
[    15.922] 	LinGreenFieldPosition: 0
[    15.922] 	LinBlueMaskSize: 0
[    15.922] 	LinBlueFieldPosition: 0
[    15.922] 	LinRsvdMaskSize: 0
[    15.922] 	LinRsvdFieldPosition: 0
[    15.922] 	MaxPixelClock: 229500000
[    15.925] Mode: 131 (320x400)
[    15.925] 	ModeAttributes: 0x3bf
[    15.925] 	WinAAttributes: 0x7
[    15.925] 	WinBAttributes: 0x0
[    15.925] 	WinGranularity: 64
[    15.925] 	WinSize: 64
[    15.925] 	WinASegment: 0xa000
[    15.925] 	WinBSegment: 0x0
[    15.925] 	WinFuncPtr: 0xc000687b
[    15.925] 	BytesPerScanline: 320
[    15.925] 	XResolution: 320
[    15.925] 	YResolution: 400
[    15.925] 	XCharSize: 8
[    15.925] 	YCharSize: 16
[    15.925] 	NumberOfPlanes: 1
[    15.925] 	BitsPerPixel: 8
[    15.925] 	NumberOfBanks: 1
[    15.925] 	MemoryModel: 4
[    15.925] 	BankSize: 0
[    15.925] 	NumberOfImages: 30
[    15.925] 	RedMaskSize: 0
[    15.925] 	RedFieldPosition: 0
[    15.925] 	GreenMaskSize: 0
[    15.925] 	GreenFieldPosition: 0
[    15.925] 	BlueMaskSize: 0
[    15.925] 	BlueFieldPosition: 0
[    15.925] 	RsvdMaskSize: 0
[    15.925] 	RsvdFieldPosition: 0
[    15.925] 	DirectColorModeInfo: 0
[    15.925] 	PhysBasePtr: 0xd1000000
[    15.925] 	LinBytesPerScanLine: 320
[    15.925] 	BnkNumberOfImagePages: 30
[    15.925] 	LinNumberOfImagePages: 30
[    15.925] 	LinRedMaskSize: 0
[    15.925] 	LinRedFieldPosition: 0
[    15.925] 	LinGreenMaskSize: 0
[    15.925] 	LinGreenFieldPosition: 0
[    15.925] 	LinBlueMaskSize: 0
[    15.925] 	LinBlueFieldPosition: 0
[    15.925] 	LinRsvdMaskSize: 0
[    15.925] 	LinRsvdFieldPosition: 0
[    15.925] 	MaxPixelClock: 229500000
[    15.928] Mode: 132 (320x400)
[    15.928] 	ModeAttributes: 0x3bf
[    15.928] 	WinAAttributes: 0x7
[    15.928] 	WinBAttributes: 0x0
[    15.928] 	WinGranularity: 64
[    15.928] 	WinSize: 64
[    15.928] 	WinASegment: 0xa000
[    15.928] 	WinBSegment: 0x0
[    15.928] 	WinFuncPtr: 0xc000687b
[    15.928] 	BytesPerScanline: 640
[    15.928] 	XResolution: 320
[    15.928] 	YResolution: 400
[    15.928] 	XCharSize: 8
[    15.928] 	YCharSize: 16
[    15.928] 	NumberOfPlanes: 1
[    15.928] 	BitsPerPixel: 16
[    15.928] 	NumberOfBanks: 1
[    15.928] 	MemoryModel: 6
[    15.928] 	BankSize: 0
[    15.928] 	NumberOfImages: 14
[    15.928] 	RedMaskSize: 5
[    15.928] 	RedFieldPosition: 11
[    15.928] 	GreenMaskSize: 6
[    15.928] 	GreenFieldPosition: 5
[    15.928] 	BlueMaskSize: 5
[    15.928] 	BlueFieldPosition: 0
[    15.928] 	RsvdMaskSize: 0
[    15.928] 	RsvdFieldPosition: 0
[    15.928] 	DirectColorModeInfo: 0
[    15.928] 	PhysBasePtr: 0xd1000000
[    15.928] 	LinBytesPerScanLine: 640
[    15.928] 	BnkNumberOfImagePages: 14
[    15.928] 	LinNumberOfImagePages: 14
[    15.928] 	LinRedMaskSize: 5
[    15.928] 	LinRedFieldPosition: 11
[    15.928] 	LinGreenMaskSize: 6
[    15.928] 	LinGreenFieldPosition: 5
[    15.928] 	LinBlueMaskSize: 5
[    15.928] 	LinBlueFieldPosition: 0
[    15.928] 	LinRsvdMaskSize: 0
[    15.928] 	LinRsvdFieldPosition: 0
[    15.928] 	MaxPixelClock: 229500000
[    15.930] *Mode: 133 (320x400)
[    15.930] 	ModeAttributes: 0x3bf
[    15.930] 	WinAAttributes: 0x7
[    15.930] 	WinBAttributes: 0x0
[    15.930] 	WinGranularity: 64
[    15.930] 	WinSize: 64
[    15.930] 	WinASegment: 0xa000
[    15.930] 	WinBSegment: 0x0
[    15.930] 	WinFuncPtr: 0xc000687b
[    15.930] 	BytesPerScanline: 1280
[    15.930] 	XResolution: 320
[    15.930] 	YResolution: 400
[    15.930] 	XCharSize: 8
[    15.930] 	YCharSize: 16
[    15.930] 	NumberOfPlanes: 1
[    15.930] 	BitsPerPixel: 32
[    15.930] 	NumberOfBanks: 1
[    15.930] 	MemoryModel: 6
[    15.931] 	BankSize: 0
[    15.931] 	NumberOfImages: 6
[    15.931] 	RedMaskSize: 8
[    15.931] 	RedFieldPosition: 16
[    15.931] 	GreenMaskSize: 8
[    15.931] 	GreenFieldPosition: 8
[    15.931] 	BlueMaskSize: 8
[    15.931] 	BlueFieldPosition: 0
[    15.931] 	RsvdMaskSize: 8
[    15.931] 	RsvdFieldPosition: 24
[    15.931] 	DirectColorModeInfo: 0
[    15.931] 	PhysBasePtr: 0xd1000000
[    15.931] 	LinBytesPerScanLine: 1280
[    15.931] 	BnkNumberOfImagePages: 6
[    15.931] 	LinNumberOfImagePages: 6
[    15.931] 	LinRedMaskSize: 8
[    15.931] 	LinRedFieldPosition: 16
[    15.931] 	LinGreenMaskSize: 8
[    15.931] 	LinGreenFieldPosition: 8
[    15.931] 	LinBlueMaskSize: 8
[    15.931] 	LinBlueFieldPosition: 0
[    15.931] 	LinRsvdMaskSize: 8
[    15.931] 	LinRsvdFieldPosition: 24
[    15.931] 	MaxPixelClock: 229500000
[    15.933] Mode: 134 (320x240)
[    15.933] 	ModeAttributes: 0x3bf
[    15.933] 	WinAAttributes: 0x7
[    15.933] 	WinBAttributes: 0x0
[    15.933] 	WinGranularity: 64
[    15.933] 	WinSize: 64
[    15.933] 	WinASegment: 0xa000
[    15.933] 	WinBSegment: 0x0
[    15.933] 	WinFuncPtr: 0xc000687b
[    15.933] 	BytesPerScanline: 320
[    15.933] 	XResolution: 320
[    15.933] 	YResolution: 240
[    15.933] 	XCharSize: 8
[    15.933] 	YCharSize: 8
[    15.933] 	NumberOfPlanes: 1
[    15.933] 	BitsPerPixel: 8
[    15.933] 	NumberOfBanks: 1
[    15.933] 	MemoryModel: 4
[    15.933] 	BankSize: 0
[    15.933] 	NumberOfImages: 30
[    15.933] 	RedMaskSize: 0
[    15.933] 	RedFieldPosition: 0
[    15.933] 	GreenMaskSize: 0
[    15.933] 	GreenFieldPosition: 0
[    15.933] 	BlueMaskSize: 0
[    15.933] 	BlueFieldPosition: 0
[    15.933] 	RsvdMaskSize: 0
[    15.933] 	RsvdFieldPosition: 0
[    15.933] 	DirectColorModeInfo: 0
[    15.933] 	PhysBasePtr: 0xd1000000
[    15.933] 	LinBytesPerScanLine: 320
[    15.933] 	BnkNumberOfImagePages: 30
[    15.933] 	LinNumberOfImagePages: 30
[    15.933] 	LinRedMaskSize: 0
[    15.933] 	LinRedFieldPosition: 0
[    15.933] 	LinGreenMaskSize: 0
[    15.933] 	LinGreenFieldPosition: 0
[    15.933] 	LinBlueMaskSize: 0
[    15.933] 	LinBlueFieldPosition: 0
[    15.933] 	LinRsvdMaskSize: 0
[    15.933] 	LinRsvdFieldPosition: 0
[    15.933] 	MaxPixelClock: 229500000
[    15.936] Mode: 135 (320x240)
[    15.936] 	ModeAttributes: 0x3bf
[    15.936] 	WinAAttributes: 0x7
[    15.936] 	WinBAttributes: 0x0
[    15.936] 	WinGranularity: 64
[    15.936] 	WinSize: 64
[    15.936] 	WinASegment: 0xa000
[    15.936] 	WinBSegment: 0x0
[    15.936] 	WinFuncPtr: 0xc000687b
[    15.936] 	BytesPerScanline: 640
[    15.936] 	XResolution: 320
[    15.936] 	YResolution: 240
[    15.936] 	XCharSize: 8
[    15.936] 	YCharSize: 8
[    15.936] 	NumberOfPlanes: 1
[    15.936] 	BitsPerPixel: 16
[    15.936] 	NumberOfBanks: 1
[    15.936] 	MemoryModel: 6
[    15.936] 	BankSize: 0
[    15.936] 	NumberOfImages: 19
[    15.936] 	RedMaskSize: 5
[    15.936] 	RedFieldPosition: 11
[    15.936] 	GreenMaskSize: 6
[    15.936] 	GreenFieldPosition: 5
[    15.936] 	BlueMaskSize: 5
[    15.936] 	BlueFieldPosition: 0
[    15.936] 	RsvdMaskSize: 0
[    15.936] 	RsvdFieldPosition: 0
[    15.936] 	DirectColorModeInfo: 0
[    15.936] 	PhysBasePtr: 0xd1000000
[    15.936] 	LinBytesPerScanLine: 640
[    15.936] 	BnkNumberOfImagePages: 19
[    15.936] 	LinNumberOfImagePages: 19
[    15.936] 	LinRedMaskSize: 5
[    15.936] 	LinRedFieldPosition: 11
[    15.936] 	LinGreenMaskSize: 6
[    15.936] 	LinGreenFieldPosition: 5
[    15.936] 	LinBlueMaskSize: 5
[    15.936] 	LinBlueFieldPosition: 0
[    15.936] 	LinRsvdMaskSize: 0
[    15.936] 	LinRsvdFieldPosition: 0
[    15.936] 	MaxPixelClock: 229500000
[    15.939] *Mode: 136 (320x240)
[    15.939] 	ModeAttributes: 0x3bf
[    15.939] 	WinAAttributes: 0x7
[    15.939] 	WinBAttributes: 0x0
[    15.939] 	WinGranularity: 64
[    15.939] 	WinSize: 64
[    15.939] 	WinASegment: 0xa000
[    15.939] 	WinBSegment: 0x0
[    15.939] 	WinFuncPtr: 0xc000687b
[    15.939] 	BytesPerScanline: 1280
[    15.939] 	XResolution: 320
[    15.939] 	YResolution: 240
[    15.939] 	XCharSize: 8
[    15.939] 	YCharSize: 8
[    15.939] 	NumberOfPlanes: 1
[    15.939] 	BitsPerPixel: 32
[    15.939] 	NumberOfBanks: 1
[    15.939] 	MemoryModel: 6
[    15.939] 	BankSize: 0
[    15.939] 	NumberOfImages: 10
[    15.939] 	RedMaskSize: 8
[    15.939] 	RedFieldPosition: 16
[    15.939] 	GreenMaskSize: 8
[    15.939] 	GreenFieldPosition: 8
[    15.939] 	BlueMaskSize: 8
[    15.939] 	BlueFieldPosition: 0
[    15.939] 	RsvdMaskSize: 8
[    15.939] 	RsvdFieldPosition: 24
[    15.939] 	DirectColorModeInfo: 0
[    15.939] 	PhysBasePtr: 0xd1000000
[    15.939] 	LinBytesPerScanLine: 1280
[    15.939] 	BnkNumberOfImagePages: 10
[    15.939] 	LinNumberOfImagePages: 10
[    15.939] 	LinRedMaskSize: 8
[    15.939] 	LinRedFieldPosition: 16
[    15.939] 	LinGreenMaskSize: 8
[    15.939] 	LinGreenFieldPosition: 8
[    15.939] 	LinBlueMaskSize: 8
[    15.939] 	LinBlueFieldPosition: 0
[    15.939] 	LinRsvdMaskSize: 8
[    15.939] 	LinRsvdFieldPosition: 24
[    15.939] 	MaxPixelClock: 229500000
[    15.942] Mode: 13d (640x400)
[    15.942] 	ModeAttributes: 0x3bf
[    15.942] 	WinAAttributes: 0x7
[    15.942] 	WinBAttributes: 0x0
[    15.942] 	WinGranularity: 64
[    15.942] 	WinSize: 64
[    15.942] 	WinASegment: 0xa000
[    15.942] 	WinBSegment: 0x0
[    15.942] 	WinFuncPtr: 0xc000687b
[    15.942] 	BytesPerScanline: 1280
[    15.942] 	XResolution: 640
[    15.942] 	YResolution: 400
[    15.942] 	XCharSize: 8
[    15.942] 	YCharSize: 16
[    15.942] 	NumberOfPlanes: 1
[    15.942] 	BitsPerPixel: 16
[    15.942] 	NumberOfBanks: 1
[    15.942] 	MemoryModel: 6
[    15.942] 	BankSize: 0
[    15.942] 	NumberOfImages: 6
[    15.942] 	RedMaskSize: 5
[    15.942] 	RedFieldPosition: 11
[    15.942] 	GreenMaskSize: 6
[    15.942] 	GreenFieldPosition: 5
[    15.942] 	BlueMaskSize: 5
[    15.942] 	BlueFieldPosition: 0
[    15.942] 	RsvdMaskSize: 0
[    15.942] 	RsvdFieldPosition: 0
[    15.942] 	DirectColorModeInfo: 0
[    15.942] 	PhysBasePtr: 0xd1000000
[    15.942] 	LinBytesPerScanLine: 1280
[    15.942] 	BnkNumberOfImagePages: 6
[    15.942] 	LinNumberOfImagePages: 6
[    15.942] 	LinRedMaskSize: 5
[    15.942] 	LinRedFieldPosition: 11
[    15.942] 	LinGreenMaskSize: 6
[    15.942] 	LinGreenFieldPosition: 5
[    15.942] 	LinBlueMaskSize: 5
[    15.942] 	LinBlueFieldPosition: 0
[    15.942] 	LinRsvdMaskSize: 0
[    15.942] 	LinRsvdFieldPosition: 0
[    15.942] 	MaxPixelClock: 229500000
[    15.944] *Mode: 13e (640x400)
[    15.944] 	ModeAttributes: 0x3bf
[    15.945] 	WinAAttributes: 0x7
[    15.945] 	WinBAttributes: 0x0
[    15.945] 	WinGranularity: 64
[    15.945] 	WinSize: 64
[    15.945] 	WinASegment: 0xa000
[    15.945] 	WinBSegment: 0x0
[    15.945] 	WinFuncPtr: 0xc000687b
[    15.945] 	BytesPerScanline: 2560
[    15.945] 	XResolution: 640
[    15.945] 	YResolution: 400
[    15.945] 	XCharSize: 8
[    15.945] 	YCharSize: 16
[    15.945] 	NumberOfPlanes: 1
[    15.945] 	BitsPerPixel: 32
[    15.945] 	NumberOfBanks: 1
[    15.945] 	MemoryModel: 6
[    15.945] 	BankSize: 0
[    15.945] 	NumberOfImages: 2
[    15.945] 	RedMaskSize: 8
[    15.945] 	RedFieldPosition: 16
[    15.945] 	GreenMaskSize: 8
[    15.945] 	GreenFieldPosition: 8
[    15.945] 	BlueMaskSize: 8
[    15.945] 	BlueFieldPosition: 0
[    15.945] 	RsvdMaskSize: 8
[    15.945] 	RsvdFieldPosition: 24
[    15.945] 	DirectColorModeInfo: 0
[    15.945] 	PhysBasePtr: 0xd1000000
[    15.945] 	LinBytesPerScanLine: 2560
[    15.945] 	BnkNumberOfImagePages: 2
[    15.945] 	LinNumberOfImagePages: 2
[    15.945] 	LinRedMaskSize: 8
[    15.945] 	LinRedFieldPosition: 16
[    15.945] 	LinGreenMaskSize: 8
[    15.945] 	LinGreenFieldPosition: 8
[    15.945] 	LinBlueMaskSize: 8
[    15.945] 	LinBlueFieldPosition: 0
[    15.945] 	LinRsvdMaskSize: 8
[    15.945] 	LinRsvdFieldPosition: 24
[    15.945] 	MaxPixelClock: 229500000
[    15.947] Mode: 14b (1360x768)
[    15.947] 	ModeAttributes: 0x3bf
[    15.947] 	WinAAttributes: 0x7
[    15.947] 	WinBAttributes: 0x0
[    15.947] 	WinGranularity: 64
[    15.947] 	WinSize: 64
[    15.947] 	WinASegment: 0xa000
[    15.947] 	WinBSegment: 0x0
[    15.947] 	WinFuncPtr: 0xc000687b
[    15.947] 	BytesPerScanline: 1360
[    15.947] 	XResolution: 1360
[    15.947] 	YResolution: 768
[    15.947] 	XCharSize: 8
[    15.947] 	YCharSize: 16
[    15.947] 	NumberOfPlanes: 1
[    15.947] 	BitsPerPixel: 8
[    15.947] 	NumberOfBanks: 1
[    15.947] 	MemoryModel: 4
[    15.947] 	BankSize: 0
[    15.947] 	NumberOfImages: 1
[    15.947] 	RedMaskSize: 0
[    15.947] 	RedFieldPosition: 0
[    15.947] 	GreenMaskSize: 0
[    15.947] 	GreenFieldPosition: 0
[    15.948] 	BlueMaskSize: 0
[    15.948] 	BlueFieldPosition: 0
[    15.948] 	RsvdMaskSize: 0
[    15.948] 	RsvdFieldPosition: 0
[    15.948] 	DirectColorModeInfo: 0
[    15.948] 	PhysBasePtr: 0xd1000000
[    15.948] 	LinBytesPerScanLine: 1360
[    15.948] 	BnkNumberOfImagePages: 1
[    15.948] 	LinNumberOfImagePages: 1
[    15.948] 	LinRedMaskSize: 0
[    15.948] 	LinRedFieldPosition: 0
[    15.948] 	LinGreenMaskSize: 0
[    15.948] 	LinGreenFieldPosition: 0
[    15.948] 	LinBlueMaskSize: 0
[    15.948] 	LinBlueFieldPosition: 0
[    15.948] 	LinRsvdMaskSize: 0
[    15.948] 	LinRsvdFieldPosition: 0
[    15.948] 	MaxPixelClock: 229500000
[    15.950] Mode: 14c (1360x768)
[    15.950] 	ModeAttributes: 0x3bf
[    15.950] 	WinAAttributes: 0x7
[    15.950] 	WinBAttributes: 0x0
[    15.950] 	WinGranularity: 64
[    15.950] 	WinSize: 64
[    15.950] 	WinASegment: 0xa000
[    15.950] 	WinBSegment: 0x0
[    15.950] 	WinFuncPtr: 0xc000687b
[    15.950] 	BytesPerScanline: 2720
[    15.950] 	XResolution: 1360
[    15.950] 	YResolution: 768
[    15.950] 	XCharSize: 8
[    15.950] 	YCharSize: 16
[    15.950] 	NumberOfPlanes: 1
[    15.950] 	BitsPerPixel: 16
[    15.950] 	NumberOfBanks: 1
[    15.950] 	MemoryModel: 6
[    15.950] 	BankSize: 0
[    15.950] 	NumberOfImages: 1
[    15.950] 	RedMaskSize: 5
[    15.950] 	RedFieldPosition: 11
[    15.950] 	GreenMaskSize: 6
[    15.950] 	GreenFieldPosition: 5
[    15.950] 	BlueMaskSize: 5
[    15.950] 	BlueFieldPosition: 0
[    15.950] 	RsvdMaskSize: 0
[    15.950] 	RsvdFieldPosition: 0
[    15.950] 	DirectColorModeInfo: 0
[    15.950] 	PhysBasePtr: 0xd1000000
[    15.950] 	LinBytesPerScanLine: 2720
[    15.950] 	BnkNumberOfImagePages: 1
[    15.950] 	LinNumberOfImagePages: 1
[    15.950] 	LinRedMaskSize: 5
[    15.950] 	LinRedFieldPosition: 11
[    15.950] 	LinGreenMaskSize: 6
[    15.950] 	LinGreenFieldPosition: 5
[    15.950] 	LinBlueMaskSize: 5
[    15.950] 	LinBlueFieldPosition: 0
[    15.950] 	LinRsvdMaskSize: 0
[    15.950] 	LinRsvdFieldPosition: 0
[    15.950] 	MaxPixelClock: 229500000
[    15.953] *Mode: 14d (1360x768)
[    15.953] 	ModeAttributes: 0x3bf
[    15.953] 	WinAAttributes: 0x7
[    15.953] 	WinBAttributes: 0x0
[    15.953] 	WinGranularity: 64
[    15.953] 	WinSize: 64
[    15.953] 	WinASegment: 0xa000
[    15.953] 	WinBSegment: 0x0
[    15.953] 	WinFuncPtr: 0xc000687b
[    15.953] 	BytesPerScanline: 5440
[    15.953] 	XResolution: 1360
[    15.953] 	YResolution: 768
[    15.953] 	XCharSize: 8
[    15.953] 	YCharSize: 16
[    15.953] 	NumberOfPlanes: 1
[    15.953] 	BitsPerPixel: 32
[    15.953] 	NumberOfBanks: 1
[    15.953] 	MemoryModel: 6
[    15.953] 	BankSize: 0
[    15.953] 	NumberOfImages: 1
[    15.953] 	RedMaskSize: 8
[    15.953] 	RedFieldPosition: 16
[    15.953] 	GreenMaskSize: 8
[    15.953] 	GreenFieldPosition: 8
[    15.953] 	BlueMaskSize: 8
[    15.953] 	BlueFieldPosition: 0
[    15.953] 	RsvdMaskSize: 8
[    15.953] 	RsvdFieldPosition: 24
[    15.953] 	DirectColorModeInfo: 0
[    15.953] 	PhysBasePtr: 0xd1000000
[    15.953] 	LinBytesPerScanLine: 5440
[    15.953] 	BnkNumberOfImagePages: 1
[    15.953] 	LinNumberOfImagePages: 1
[    15.953] 	LinRedMaskSize: 8
[    15.953] 	LinRedFieldPosition: 16
[    15.953] 	LinGreenMaskSize: 8
[    15.953] 	LinGreenFieldPosition: 8
[    15.953] 	LinBlueMaskSize: 8
[    15.953] 	LinBlueFieldPosition: 0
[    15.953] 	LinRsvdMaskSize: 8
[    15.953] 	LinRsvdFieldPosition: 24
[    15.953] 	MaxPixelClock: 229500000
[    15.956] Mode: 162 (768x480)
[    15.956] 	ModeAttributes: 0x3bf
[    15.956] 	WinAAttributes: 0x7
[    15.956] 	WinBAttributes: 0x0
[    15.956] 	WinGranularity: 64
[    15.956] 	WinSize: 64
[    15.956] 	WinASegment: 0xa000
[    15.956] 	WinBSegment: 0x0
[    15.956] 	WinFuncPtr: 0xc000687b
[    15.956] 	BytesPerScanline: 768
[    15.956] 	XResolution: 768
[    15.956] 	YResolution: 480
[    15.956] 	XCharSize: 8
[    15.956] 	YCharSize: 16
[    15.956] 	NumberOfPlanes: 1
[    15.956] 	BitsPerPixel: 8
[    15.956] 	NumberOfBanks: 1
[    15.956] 	MemoryModel: 4
[    15.956] 	BankSize: 0
[    15.956] 	NumberOfImages: 8
[    15.956] 	RedMaskSize: 0
[    15.956] 	RedFieldPosition: 0
[    15.956] 	GreenMaskSize: 0
[    15.956] 	GreenFieldPosition: 0
[    15.956] 	BlueMaskSize: 0
[    15.956] 	BlueFieldPosition: 0
[    15.956] 	RsvdMaskSize: 0
[    15.956] 	RsvdFieldPosition: 0
[    15.956] 	DirectColorModeInfo: 0
[    15.956] 	PhysBasePtr: 0xd1000000
[    15.956] 	LinBytesPerScanLine: 768
[    15.956] 	BnkNumberOfImagePages: 8
[    15.956] 	LinNumberOfImagePages: 8
[    15.956] 	LinRedMaskSize: 0
[    15.956] 	LinRedFieldPosition: 0
[    15.956] 	LinGreenMaskSize: 0
[    15.956] 	LinGreenFieldPosition: 0
[    15.956] 	LinBlueMaskSize: 0
[    15.956] 	LinBlueFieldPosition: 0
[    15.956] 	LinRsvdMaskSize: 0
[    15.956] 	LinRsvdFieldPosition: 0
[    15.956] 	MaxPixelClock: 229500000
[    15.959] *Mode: 17b (1280x720)
[    15.959] 	ModeAttributes: 0x3bf
[    15.959] 	WinAAttributes: 0x7
[    15.959] 	WinBAttributes: 0x0
[    15.959] 	WinGranularity: 64
[    15.959] 	WinSize: 64
[    15.959] 	WinASegment: 0xa000
[    15.959] 	WinBSegment: 0x0
[    15.959] 	WinFuncPtr: 0xc000687b
[    15.959] 	BytesPerScanline: 5120
[    15.959] 	XResolution: 1280
[    15.959] 	YResolution: 720
[    15.959] 	XCharSize: 8
[    15.959] 	YCharSize: 16
[    15.959] 	NumberOfPlanes: 1
[    15.959] 	BitsPerPixel: 32
[    15.959] 	NumberOfBanks: 1
[    15.959] 	MemoryModel: 6
[    15.959] 	BankSize: 0
[    15.959] 	NumberOfImages: 1
[    15.959] 	RedMaskSize: 8
[    15.959] 	RedFieldPosition: 16
[    15.959] 	GreenMaskSize: 8
[    15.959] 	GreenFieldPosition: 8
[    15.959] 	BlueMaskSize: 8
[    15.959] 	BlueFieldPosition: 0
[    15.959] 	RsvdMaskSize: 8
[    15.959] 	RsvdFieldPosition: 24
[    15.959] 	DirectColorModeInfo: 0
[    15.959] 	PhysBasePtr: 0xd1000000
[    15.959] 	LinBytesPerScanLine: 5120
[    15.959] 	BnkNumberOfImagePages: 1
[    15.959] 	LinNumberOfImagePages: 1
[    15.959] 	LinRedMaskSize: 8
[    15.959] 	LinRedFieldPosition: 16
[    15.959] 	LinGreenMaskSize: 8
[    15.959] 	LinGreenFieldPosition: 8
[    15.959] 	LinBlueMaskSize: 8
[    15.959] 	LinBlueFieldPosition: 0
[    15.959] 	LinRsvdMaskSize: 8
[    15.959] 	LinRsvdFieldPosition: 24
[    15.959] 	MaxPixelClock: 229500000
[    15.959] 
[    15.959] (II) VESA(0): Total Memory: 224 64KB banks (14336kB)
[    15.959] (II) VESA(0): <default monitor>: Using hsync range of 30.00-61.00 kHz
[    15.959] (II) VESA(0): <default monitor>: Using vrefresh range of 56.00-75.00 Hz
[    15.959] (II) VESA(0): <default monitor>: Using maximum pixel clock of 85.00 MHz
[    15.959] (WW) VESA(0): Unable to estimate virtual size
[    15.959] (II) VESA(0): Not using built-in mode "1360x768" (no mode of this name)
[    15.959] (II) VESA(0): Not using built-in mode "1280x720" (no mode of this name)
[    15.962] (II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
[    15.962] (II) VESA(0): Not using built-in mode "320x400" (no mode of this name)
[    15.962] (II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
[    15.962] (II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
[    15.962] (--) VESA(0): Virtual size is 1024x768 (pitch 1024)
[    15.962] (**) VESA(0): *Built-in mode "1024x768"
[    15.962] (**) VESA(0): *Built-in mode "800x600"
[    15.962] (**) VESA(0): *Built-in mode "640x480"
[    15.962] (**) VESA(0): Display dimensions: (300, 230) mm
[    15.962] (**) VESA(0): DPI set to (86, 84)
[    15.962] (**) VESA(0): Using "Shadow Framebuffer"
[    15.962] (II) Loading sub module "shadow"
[    15.962] (II) LoadModule: "shadow"
[    15.963] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    15.963] (II) Module shadow: vendor="X.Org Foundation"
[    15.963] 	compiled for 1.9.0, module version = 1.1.0
[    15.963] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    15.963] (II) Loading sub module "fb"
[    15.963] (II) LoadModule: "fb"
[    15.963] (II) Loading /usr/lib/xorg/modules/libfb.so
[    15.963] (II) Module fb: vendor="X.Org Foundation"
[    15.963] 	compiled for 1.9.0, module version = 1.0.0
[    15.963] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    15.963] (II) UnloadModule: "nv"
[    15.963] (II) Unloading /usr/lib/xorg/modules/drivers/nv_drv.so
[    15.963] (II) UnloadModule: "fbdev"
[    15.963] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    15.963] (II) UnloadModule: "fbdevhw"
[    15.963] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    15.963] (==) Depth 24 pixmap format is 32 bpp
[    15.963] (II) Loading sub module "int10"
[    15.963] (II) LoadModule: "int10"
[    15.964] (II) Reloading /usr/lib/xorg/modules/libint10.so
[    15.964] (II) VESA(0): initializing int10
[    15.964] (II) VESA(0): Bad V_BIOS checksum
[    15.964] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    16.075] (II) VESA(0): VESA BIOS detected
[    16.075] (II) VESA(0): VESA VBE Version 3.0
[    16.075] (II) VESA(0): VESA VBE Total Mem: 14336 kB
[    16.075] (II) VESA(0): VESA VBE OEM: NVIDIA
[    16.075] (II) VESA(0): VESA VBE OEM Software Rev: 112.24
[    16.075] (II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
[    16.075] (II) VESA(0): VESA VBE OEM Product: GT218 Board - 0696a750
[    16.075] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
[    16.078] (II) VESA(0): virtual address = 0xb67a5000,
	physical address = 0xd1000000, size = 14680064
[    16.115] (II) VESA(0): Setting up VESA Mode 0x118 (1024x768)
[    16.292] (==) VESA(0): Default visual is TrueColor
[    16.292] (==) VESA(0): Backing store disabled
[    16.292] (==) VESA(0): DPMS enabled
[    16.292] (==) RandR enabled
[    16.292] (II) Initializing built-in extension Generic Event Extension
[    16.292] (II) Initializing built-in extension SHAPE
[    16.292] (II) Initializing built-in extension MIT-SHM
[    16.292] (II) Initializing built-in extension XInputExtension
[    16.292] (II) Initializing built-in extension XTEST
[    16.292] (II) Initializing built-in extension BIG-REQUESTS
[    16.292] (II) Initializing built-in extension SYNC
[    16.292] (II) Initializing built-in extension XKEYBOARD
[    16.292] (II) Initializing built-in extension XC-MISC
[    16.292] (II) Initializing built-in extension SECURITY
[    16.292] (II) Initializing built-in extension XINERAMA
[    16.292] (II) Initializing built-in extension XFIXES
[    16.292] (II) Initializing built-in extension RENDER
[    16.292] (II) Initializing built-in extension RANDR
[    16.292] (II) Initializing built-in extension COMPOSITE
[    16.292] (II) Initializing built-in extension DAMAGE
[    16.292] (II) Initializing built-in extension GESTURE
[    16.295] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    16.320] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    16.327] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    16.327] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.327] (II) LoadModule: "evdev"
[    16.327] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.328] (II) Module evdev: vendor="X.Org Foundation"
[    16.328] 	compiled for 1.9.0, module version = 2.3.2
[    16.328] 	Module class: X.Org XInput Driver
[    16.328] 	ABI class: X.Org XInput driver, version 11.0
[    16.328] (**) Power Button: always reports core events
[    16.328] (**) Power Button: Device: "/dev/input/event2"
[    16.352] (II) Power Button: Found keys
[    16.352] (II) Power Button: Configuring as keyboard
[    16.352] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    16.352] (**) Option "xkb_rules" "evdev"
[    16.352] (**) Option "xkb_model" "pc105"
[    16.352] (**) Option "xkb_layout" "pt"
[    16.354] (II) XKB: reuse xkmfile /var/lib/xkb/server-8F12297C8ADF2DCAF94655EF02F153CE34CF92F1.xkm
[    16.356] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    16.356] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    16.356] (**) Video Bus: always reports core events
[    16.356] (**) Video Bus: Device: "/dev/input/event6"
[    16.384] (II) Video Bus: Found keys
[    16.384] (II) Video Bus: Configuring as keyboard
[    16.384] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    16.384] (**) Option "xkb_rules" "evdev"
[    16.384] (**) Option "xkb_model" "pc105"
[    16.384] (**) Option "xkb_layout" "pt"
[    16.385] (II) config/udev: Adding input device Sony Vaio Keys (/dev/input/event7)
[    16.385] (**) Sony Vaio Keys: Applying InputClass "evdev keyboard catchall"
[    16.385] (**) Sony Vaio Keys: always reports core events
[    16.385] (**) Sony Vaio Keys: Device: "/dev/input/event7"
[    16.416] (II) Sony Vaio Keys: Found keys
[    16.416] (II) Sony Vaio Keys: Configuring as keyboard
[    16.416] (II) XINPUT: Adding extended input device "Sony Vaio Keys" (type: KEYBOARD)
[    16.416] (**) Option "xkb_rules" "evdev"
[    16.416] (**) Option "xkb_model" "pc105"
[    16.416] (**) Option "xkb_layout" "pt"
[    16.418] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    16.418] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.418] (**) Power Button: always reports core events
[    16.418] (**) Power Button: Device: "/dev/input/event0"
[    16.448] (II) Power Button: Found keys
[    16.448] (II) Power Button: Configuring as keyboard
[    16.448] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    16.448] (**) Option "xkb_rules" "evdev"
[    16.448] (**) Option "xkb_model" "pc105"
[    16.448] (**) Option "xkb_layout" "pt"
[    16.449] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    16.449] (II) No input driver/identifier specified (ignoring)
[    16.450] (II) config/udev: Adding input device UVC Camera (05ca:18b7) (/dev/input/event5)
[    16.450] (**) UVC Camera (05ca:18b7): Applying InputClass "evdev keyboard catchall"
[    16.450] (**) UVC Camera (05ca:18b7): always reports core events
[    16.450] (**) UVC Camera (05ca:18b7): Device: "/dev/input/event5"
[    16.480] (II) UVC Camera (05ca:18b7): Found keys
[    16.480] (II) UVC Camera (05ca:18b7): Configuring as keyboard
[    16.480] (II) XINPUT: Adding extended input device "UVC Camera (05ca:18b7)" (type: KEYBOARD)
[    16.480] (**) Option "xkb_rules" "evdev"
[    16.480] (**) Option "xkb_model" "pc105"
[    16.480] (**) Option "xkb_layout" "pt"
[    16.482] (II) config/udev: Adding input device Logitech USB RECEIVER (/dev/input/event4)
[    16.482] (**) Logitech USB RECEIVER: Applying InputClass "evdev pointer catchall"
[    16.482] (**) Logitech USB RECEIVER: always reports core events
[    16.482] (**) Logitech USB RECEIVER: Device: "/dev/input/event4"
[    16.512] (II) Logitech USB RECEIVER: Found 20 mouse buttons
[    16.512] (II) Logitech USB RECEIVER: Found scroll wheel(s)
[    16.512] (II) Logitech USB RECEIVER: Found relative axes
[    16.512] (II) Logitech USB RECEIVER: Found x and y relative axes
[    16.512] (II) Logitech USB RECEIVER: Configuring as mouse
[    16.512] (**) Logitech USB RECEIVER: YAxisMapping: buttons 4 and 5
[    16.512] (**) Logitech USB RECEIVER: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    16.512] (II) XINPUT: Adding extended input device "Logitech USB RECEIVER" (type: MOUSE)
[    16.512] (II) Logitech USB RECEIVER: initialized for relative axes.
[    16.513] (II) config/udev: Adding input device Logitech USB RECEIVER (/dev/input/mouse0)
[    16.513] (II) No input driver/identifier specified (ignoring)
[    16.514] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    16.514] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    16.514] (**) AT Translated Set 2 keyboard: always reports core events
[    16.514] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    16.544] (II) AT Translated Set 2 keyboard: Found keys
[    16.544] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    16.544] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    16.544] (**) Option "xkb_rules" "evdev"
[    16.544] (**) Option "xkb_model" "pc105"
[    16.544] (**) Option "xkb_layout" "pt"
[    16.547] (II) config/udev: Adding input device Sony Vaio Jogdial (/dev/input/event8)
[    16.547] (II) No input driver/identifier specified (ignoring)
[    16.547] (II) config/udev: Adding input device Sony Vaio Jogdial (/dev/input/mouse1)
[    16.547] (II) No input driver/identifier specified (ignoring)

```

_With_ /etc/X11/xorg.conf file:
```

$ cat /var/log/Xorg.0.log
[    15.098] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    15.098] X Protocol Version 11, Revision 0
[    15.098] Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
[    15.098] Current Operating System: Linux zecarlos-laptop 2.6.35-19-generic #26-Ubuntu SMP Thu Aug 26 19:13:05 UTC 2010 i686
[    15.098] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-19-generic root=UUID=bf2171de-9d92-4c11-b0d0-a42602de101d ro quiet splash
[    15.098] Build Date: 24 August 2010  09:14:22AM
[    15.098] xorg-server 2:1.9.0-0ubuntu1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    15.098] Current version of pixman: 0.18.2
[    15.098] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    15.098] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    15.098] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Aug 28 16:30:12 2010
[    15.098] (==) Using config file: "/etc/X11/xorg.conf"
[    15.098] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    15.152] (==) ServerLayout "Layout0"
[    15.152] (**) |-->Screen "Screen0" (0)
[    15.152] (**) |   |-->Monitor "Monitor0"
[    15.152] (**) |   |-->Device "Device0"
[    15.152] (**) |-->Input Device "Keyboard0"
[    15.152] (**) |-->Input Device "Mouse0"
[    15.152] (==) Automatically adding devices
[    15.152] (==) Automatically enabling devices
[    15.152] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    15.152] 	Entry deleted from font path.
[    15.152] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    15.152] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    15.152] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    15.152] (WW) Disabling Keyboard0
[    15.152] (WW) Disabling Mouse0
[    15.152] (II) Loader magic: 0x81f8e00
[    15.152] (II) Module ABI versions:
[    15.152] 	X.Org ANSI C Emulation: 0.4
[    15.152] 	X.Org Video Driver: 8.0
[    15.152] 	X.Org XInput driver : 11.0
[    15.152] 	X.Org Server Extension : 4.0
[    15.153] (--) PCI:*(0:1:0:0) 10de:0a75:104d:9069 rev 162, Mem @ 0xd2000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00007000/128, BIOS @ 0x????????/524288
[    15.154] (II) Open ACPI successful (/var/run/acpid.socket)
[    15.154] (II) LoadModule: "extmod"
[    15.154] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    15.154] (II) Module extmod: vendor="X.Org Foundation"
[    15.154] 	compiled for 1.9.0, module version = 1.0.0
[    15.154] 	Module class: X.Org Server Extension
[    15.154] 	ABI class: X.Org Server Extension, version 4.0
[    15.154] (II) Loading extension MIT-SCREEN-SAVER
[    15.154] (II) Loading extension XFree86-VidModeExtension
[    15.154] (II) Loading extension XFree86-DGA
[    15.154] (II) Loading extension DPMS
[    15.154] (II) Loading extension XVideo
[    15.154] (II) Loading extension XVideo-MotionCompensation
[    15.154] (II) Loading extension X-Resource
[    15.154] (II) LoadModule: "dbe"
[    15.154] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    15.154] (II) Module dbe: vendor="X.Org Foundation"
[    15.154] 	compiled for 1.9.0, module version = 1.0.0
[    15.154] 	Module class: X.Org Server Extension
[    15.154] 	ABI class: X.Org Server Extension, version 4.0
[    15.154] (II) Loading extension DOUBLE-BUFFER
[    15.154] (II) LoadModule: "glx"
[    15.155] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    15.169] (II) Module glx: vendor="NVIDIA Corporation"
[    15.169] 	compiled for 4.0.2, module version = 1.0.0
[    15.169] 	Module class: X.Org Server Extension
[    15.169] (II) NVIDIA GLX Module  256.44  Thu Jul 29 01:55:11 PDT 2010
[    15.169] (II) Loading extension GLX
[    15.169] (II) LoadModule: "record"
[    15.169] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    15.169] (II) Module record: vendor="X.Org Foundation"
[    15.169] 	compiled for 1.9.0, module version = 1.13.0
[    15.169] 	Module class: X.Org Server Extension
[    15.169] 	ABI class: X.Org Server Extension, version 4.0
[    15.169] (II) Loading extension RECORD
[    15.169] (II) LoadModule: "dri"
[    15.169] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    15.170] (II) Module dri: vendor="X.Org Foundation"
[    15.170] 	compiled for 1.9.0, module version = 1.0.0
[    15.170] 	ABI class: X.Org Server Extension, version 4.0
[    15.170] (II) Loading extension XFree86-DRI
[    15.170] (II) LoadModule: "dri2"
[    15.170] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    15.170] (II) Module dri2: vendor="X.Org Foundation"
[    15.170] 	compiled for 1.9.0, module version = 1.2.0
[    15.170] 	ABI class: X.Org Server Extension, version 4.0
[    15.170] (II) Loading extension DRI2
[    15.170] (II) LoadModule: "nvidia"
[    15.170] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    15.296] (II) Module nvidia: vendor="NVIDIA Corporation"
[    15.296] 	compiled for 4.0.2, module version = 1.0.0
[    15.296] 	Module class: X.Org Video Driver
[    15.296] ================ WARNING WARNING WARNING WARNING ================
[    15.296] This server has a video driver ABI version of 8.0 that this
driver does not officially support.  Please check
[http://www.nvidia.com/](http://www.nvidia.com/) for driver updates or downgrade to an X
server with a supported driver ABI.
[    15.296] =================================================================
[    15.296] (EE) NVIDIA: Use the -ignoreABI option to override this check.
[    15.296] (II) UnloadModule: "nvidia"
[    15.296] (II) Unloading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    15.296] (EE) Failed to load module "nvidia" (module requirement mismatch, 0)
[    15.296] (EE) No drivers available.
[    15.296] 
Fatal server error:
[    15.296] no screens found
[    15.296] 
Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[    15.296] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    15.296] 

```

```

$ cat /etc/X11/xorg.conf
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 256.44  (buildmeister@builder97.nvidia.com)  Thu Jul 29 02:00:07 PDT 2010


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "ConnectedMonitor" "DFP-0,DFP-1,CRT"
    Option         "CustomEDID" "DFP-0:/etc/X11/sonyedid.raw"
    Option         "RegistryDwords" "EnableBrightnessControl=1"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by zecapistolas on 2010-08-30
Hello,

The graphics of my laptop now work fine....

1. #apt-get --purge remove nvidia-*

2. Install [NVidia driver 256.52]("ftp://download.nvidia.com/XFree86/Linux-x86/256.52/") and add:
```

Option         "ConnectedMonitor" "DFP-0,DFP-1,CRT"
Option         "CustomEDID" "DFP-0:/etc/X11/sonyedid.raw"
Option         "RegistryDwords" "EnableBrightnessControl=1"

```
to _/etc/X11/xorg.conf_ and voilá....

So, now **I need help** to put the touchpad to work. I follow [this]("http://ubuntuforums.org/showthread.php?t=1511797") and [this]("http://wiki.archlinux.org/index.php/Touchpad_Synaptics") but does not work....

In _Xorg.0.log_ appears this:
```

[    17.440] (II) Synaptics touchpad driver version 1.2.2
[    19.440] SynapticsTouchpad no synaptics event device found
[    19.440] (**) Option "Device" "/dev/psaux"
[    19.472] (**) Option "SHMConfig" "on"
[    19.493] Query no Synaptics: 6003C8
[    19.493] (--) SynapticsTouchpad: no supported touchpad found
[    19.493] (EE) SynapticsTouchpad Unable to query/initialize Synaptics hardware.
[    19.556] (EE) PreInit failed for input device "SynapticsTouchpad"
[    19.556] (II) UnloadModule: "synaptics"

```

;)

---

### Post by zecapistolas on 2010-09-01
For the problem of TouchPad i found [this]("https://wiki.ubuntu.com/DebuggingTouchpadDetection") and in section _In case your touchpad doesn't work at all (No response from the touchpad)_ appears this:
> 
If you do not find a Touchpad in you /proc/bus/inpus/devices, in that case the bug is in the kernel itself


And now?! I report the bug to who or where?! :(

---

### Post by zecapistolas on 2010-09-03
I upgraded the kernel on my system, but the bug continues, the **Synaptics TouchPad** is not recognized by the system.... :icon_frown:

I need help....

---

### Post by Tony Baines on 2010-09-04
The solution in [this forum]("http://ubuntuforums.org/showthread.php?t=1150077") works for me

> Here's the fix:

1. Edit /etc/default/grub to include GRUB_CMDLINE_LINUX="i8042.nopnp"
2. Run: sudo update-grub
3. Reboot.
~Tony

---

### Post by zecapistolas on 2010-09-06
> **Tony Baines said:**
> The solution in [this forum]("http://ubuntuforums.org/showthread.php?t=1150077") works for me

~Tony

Tony, many thank's.... The Touchpad work perfect :KS ....

Next step put the _card reader_ to work and _micro_...

1. SD Card read works great, but **MemoryStickPRODuo** does not detected by system, I think the card reader is Ricoh....
2. Sound works great, but internal micro does not....

---

### Post by zecapistolas on 2010-09-10
My version of Realtek is ALC275, and the bug with internal micro was corrected on kernel image 2.6.36... :KS

Next, SD Card read works great, but **MemoryStickPRODu**o does not detected by system, I think the card reader is Ricoh....

---

### Post by Grunghar on 2010-10-23
Hello folks,

first of all: many thank for that helpful thread. I can now "work" with my Vaio (S12V9E) but there are still a few things missing:

I had to install Nvidia driver 256.xx to get the display working, but my brightness control is not working.
Due to [http://code.google.com/p/vaio-f11-linux/wiki/DisplayBacklight](http://code.google.com/p/vaio-f11-linux/wiki/DisplayBacklight) (essentially using acpi_listen and creating the corresponding files) I am now able to capture the ACPI events, but I do not know how to alter the backlight :-(

The other thing is the keyboard backlight and the backlight sensor (are these thing glued together?!). How do I get them to work?

Many thanks in advance!

---

### Post by zecapistolas on 2010-10-24
> **Grunghar said:**
> Hello folks,

first of all: many thank for that helpful thread. I can now "work" with my Vaio (S12V9E) but there are still a few things missing:

I had to install Nvidia driver 256.xx to get the display working, but my brightness control is not working.
Due to [http://code.google.com/p/vaio-f11-linux/wiki/DisplayBacklight](http://code.google.com/p/vaio-f11-linux/wiki/DisplayBacklight) (essentially using acpi_listen and creating the corresponding files) I am now able to capture the ACPI events, but I do not know how to alter the backlight :-(

The other thing is the keyboard backlight and the backlight sensor (are these thing glued together?!). How do I get them to work?

Many thanks in advance!

Hello,

For _brightness control_ what i do?

```

$ cat /etc/X11/xorg.conf
...
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0"
    Option         "ConnectedMonitor" "DFP-0,DFP-1,CRT"
    Option         "CustomEDID" "DFP-0:/etc/X11/sonyedid.raw"
    [COLOR="Red"]Option         "RegistryDwords" "EnableBrightnessControl=1"[/COLOR]
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
...

```

```

$ cat /etc/default/grub
...
GRUB_CMDLINE_LINUX="i8042.nopnp acpi_backlight=vendor"
...

```

i8042.nopnp -> For touchpad
acpi_backlight=vendor -> For brightness control

And **sudo update-grub** to update grub....

My model, VPCS12M9E does not have _keyboard backlight_ so i cannot help you....

:D

---

### Post by greenyfrog on 2010-11-13
zecapistolas, 

could you, please, post a copy of your EDID file ? I have the same model, but i can't get an EDID file for it :( :(

thank you

---

