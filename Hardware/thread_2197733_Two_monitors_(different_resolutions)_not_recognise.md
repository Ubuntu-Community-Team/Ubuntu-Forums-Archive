---
title: "Two monitors (different resolutions) not recognised on 13.04"
date: 2014-01-05
forum: Hardware
---

### Post by cj2008 on 2014-01-05
I recently bought a second monitor for my 13.04 desktop. The resolution of the new monitor is different from my previous one - 1920x1080 vs 1680x1050.

On their own, each monitor is recognised and works well out of the box, but when I try running them both at the same time I get a corrupted EDID error on start-up, an "Unknown" monitor in Settings > Display and really low resolution on both of the monitors (much lower than the smallest one).

I suspect the different resolutions is the problem. Does anyone know of any good guides on how to configure different resolution monitors?

(A lot of posts I've read talk about adjusting xorg.conf, but I can't find this file in /etc/X11 or /usr/share/X11 on 13.04, so I'm not sure where to look.)

Thanks in advance.

---

### Post by mörgæs on 2014-01-05
[http://blog.bodhizazen.net/linux/use-xrandr-to-set-a-screen-resolution/](http://blog.bodhizazen.net/linux/use-xrandr-to-set-a-screen-resolution/)

Besides, I would begin with installing 13.10, as 13.04 has only a few weeks of support left.

---

### Post by cj2008 on 2014-01-07
Thanks for the response.

Unfortunately xrandr is still only picking up one monitor, so it can't help me configure them. 

chris@chris-desktop:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 32767 x 32767
VGA1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1920x1080      60.0* 
   1024x768       60.0  
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
chris@chris-desktop:~$ xrandr --auto --output VGA1 --mode 1920x1080 --left-of VGA2
xrandr: cannot find output "VGA2"

Is there a way to fix the corrupt EDID issue I reported on start-up? Is that preventing the system from seeing the second monitor?

---

### Post by cj2008 on 2014-01-11
OK. I've upgraded to 13.10.

After much head-banging I've realized my school-boy error in thinking that I could just use a VGA splitter on my (single output) graphics card to connect two monitors. Of course you can't do this as VGA splitters are for mirroring displays and don't handle two independent displays. It also explains the EDID checksum problem, because the two monitors were returning conflicting data.

So I invested in a cheap graphics card (nVidia GeForce 200) with a VGA and a DVI output and connected my monitors to those. Then the pain started all over again...

- All of the various nvidia packages (331, 319 and 304) from xorg-edgers ppa fail with a "failed to load NVIDIA kernel module" error.
- Nouveau works but is failing to recognise the correct screen resolution for either of the screens, leaving me with low resolution.

I added a config file under /usr/share/X11/xorg.conf.d to try to "educate" X server on my setup but it doesn't make a difference. That config files and the Xorg.0.log are pasted below.

Can anyone see the problem? Should I be trying to use Nouveau or should I focus on trying to get nvidia drivers working?

Thanks in advance...

```
Section "Device"
	Identifier	"Graphics Card"
	Driver		"nouveau"
EndSection

Section "Monitor"
	Identifier	"Dell"
	DisplaySize	1680 1050
	Modeline 	"1680x1050@60" 154.20 1680 1712 2296 2328 1050 1071 1081 1103
EndSection

Section "Screen"
	Identifier	"Dell Mapping"
	Device		"Graphics Card"
	Monitor 	"Dell"
EndSection
```


```
[   860.913] 
X.Org X Server 1.14.5
Release Date: 2013-12-12
[   860.913] X Protocol Version 11, Revision 0
[   860.913] Build Operating System: Linux 3.2.0-54-generic i686 Ubuntu
[   860.913] Current Operating System: Linux chris-desktop 3.11.0-15-generic #23-Ubuntu SMP Mon Dec 9 18:16:27 UTC 2013 i686
[   860.914] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-15-generic root=UUID=eae98412-2165-4303-a548-7557b5db6d77 ro recovery nomodeset
[   860.914] Build Date: 17 December 2013  10:03:52AM
[   860.914] xorg-server 2:1.14.5-1ubuntu2~saucy1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[   860.914] Current version of pixman: 0.30.2
[   860.914] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[   860.914] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   860.914] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Jan 11 22:48:03 2014
[   861.013] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   861.494] (==) No Layout section.  Using the first Screen section.
[   861.494] (**) |-->Screen "Dell Mapping" (0)
[   861.494] (**) |   |-->Monitor "Dell"
[   861.494] (**) |   |-->Device "Graphics Card"
[   861.494] (==) Automatically adding devices
[   861.494] (==) Automatically enabling devices
[   861.494] (==) Automatically adding GPU devices
[   861.494] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   861.494] 	Entry deleted from font path.
[   861.494] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   861.494] 	Entry deleted from font path.
[   861.494] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   861.494] 	Entry deleted from font path.
[   861.494] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   861.494] 	Entry deleted from font path.
[   861.494] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   861.494] 	Entry deleted from font path.
[   861.494] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[   861.495] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   861.495] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[   861.495] (II) Loader magic: 0xb777c6a0
[   861.495] (II) Module ABI versions:
[   861.495] 	X.Org ANSI C Emulation: 0.4
[   861.495] 	X.Org Video Driver: 14.1
[   861.495] 	X.Org XInput driver : 19.1
[   861.495] 	X.Org Server Extension : 7.0
[   861.496] (--) PCI:*(0:1:0:0) 10de:0a65:3842:1313 rev 162, Mem @ 0xfb000000/16777216, 0xb0000000/268435456, 0xce000000/33554432, I/O @ 0x0000af00/128, BIOS @ 0x????????/524288
[   861.496] (II) Open ACPI successful (/var/run/acpid.socket)
[   861.514] Initializing built-in extension Generic Event Extension
[   861.514] Initializing built-in extension SHAPE
[   861.514] Initializing built-in extension MIT-SHM
[   861.514] Initializing built-in extension XInputExtension
[   861.514] Initializing built-in extension XTEST
[   861.514] Initializing built-in extension BIG-REQUESTS
[   861.514] Initializing built-in extension SYNC
[   861.514] Initializing built-in extension XKEYBOARD
[   861.514] Initializing built-in extension XC-MISC
[   861.514] Initializing built-in extension SECURITY
[   861.514] Initializing built-in extension XINERAMA
[   861.514] Initializing built-in extension XFIXES
[   861.514] Initializing built-in extension RENDER
[   861.514] Initializing built-in extension RANDR
[   861.514] Initializing built-in extension COMPOSITE
[   861.514] Initializing built-in extension DAMAGE
[   861.514] Initializing built-in extension MIT-SCREEN-SAVER
[   861.514] Initializing built-in extension DOUBLE-BUFFER
[   861.514] Initializing built-in extension RECORD
[   861.514] Initializing built-in extension DPMS
[   861.514] Initializing built-in extension X-Resource
[   861.514] Initializing built-in extension XVideo
[   861.514] Initializing built-in extension XVideo-MotionCompensation
[   861.514] Initializing built-in extension SELinux
[   861.514] Initializing built-in extension XFree86-VidModeExtension
[   861.514] Initializing built-in extension XFree86-DGA
[   861.514] Initializing built-in extension XFree86-DRI
[   861.514] Initializing built-in extension DRI2
[   861.514] (II) "glx" will be loaded by default.
[   861.514] (WW) "xmir" is not to be loaded by default. Skipping.
[   861.514] (II) LoadModule: "dri2"
[   861.514] (II) Module "dri2" already built-in
[   861.514] (II) LoadModule: "glamoregl"
[   861.515] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[   863.966] (II) Module glamoregl: vendor="X.Org Foundation"
[   863.966] 	compiled for 1.14.4.901, module version = 0.5.1
[   863.966] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   863.966] (II) LoadModule: "glx"
[   863.967] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   864.212] (II) Module glx: vendor="X.Org Foundation"
[   864.212] 	compiled for 1.14.5, module version = 1.0.0
[   864.212] 	ABI class: X.Org Server Extension, version 7.0
[   864.212] (==) AIGLX enabled
[   864.228] Loading extension GLX
[   864.228] (II) LoadModule: "nouveau"
[   864.228] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   864.485] (II) Module nouveau: vendor="X.Org Foundation"
[   864.485] 	compiled for 1.14.2, module version = 1.0.9
[   864.485] 	Module class: X.Org Video Driver
[   864.485] 	ABI class: X.Org Video Driver, version 14.1
[   864.485] (II) NOUVEAU driver 
[   864.485] (II) NOUVEAU driver for NVIDIA chipset families :
[   864.485] 	RIVA TNT        (NV04)
[   864.485] 	RIVA TNT2       (NV05)
[   864.485] 	GeForce 256     (NV10)
[   864.485] 	GeForce 2       (NV11, NV15)
[   864.485] 	GeForce 4MX     (NV17, NV18)
[   864.485] 	GeForce 3       (NV20)
[   864.485] 	GeForce 4Ti     (NV25, NV28)
[   864.485] 	GeForce FX      (NV3x)
[   864.485] 	GeForce 6       (NV4x)
[   864.485] 	GeForce 7       (G7x)
[   864.485] 	GeForce 8       (G8x)
[   864.485] 	GeForce GTX 200 (NVA0)
[   864.485] 	GeForce GTX 400 (NVC0)
[   864.485] (++) using VT number 7

[   864.487] (EE) [drm] KMS not enabled
[   864.487] (EE) No devices detected.
[   864.487] (==) Matched nvidia as autoconfigured driver 0
[   864.487] (==) Matched nouveau as autoconfigured driver 1
[   864.487] (==) Matched vesa as autoconfigured driver 2
[   864.487] (==) Matched modesetting as autoconfigured driver 3
[   864.487] (==) Matched fbdev as autoconfigured driver 4
[   864.487] (==) Assigned the driver to the xf86ConfigLayout
[   864.487] (II) LoadModule: "nvidia"
[   864.489] (WW) Warning, couldn't open module nvidia
[   864.489] (II) UnloadModule: "nvidia"
[   864.489] (II) Unloading nvidia
[   864.489] (EE) Failed to load module "nvidia" (module does not exist, 0)
[   864.489] (II) LoadModule: "nouveau"
[   864.489] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   864.489] (II) Module nouveau: vendor="X.Org Foundation"
[   864.489] 	compiled for 1.14.2, module version = 1.0.9
[   864.489] 	Module class: X.Org Video Driver
[   864.489] 	ABI class: X.Org Video Driver, version 14.1
[   864.489] (II) UnloadModule: "nouveau"
[   864.489] (II) Unloading nouveau
[   864.489] (II) Failed to load module "nouveau" (already loaded, 0)
[   864.489] (II) LoadModule: "vesa"
[   864.489] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   864.517] (II) Module vesa: vendor="X.Org Foundation"
[   864.517] 	compiled for 1.14.1, module version = 2.3.2
[   864.517] 	Module class: X.Org Video Driver
[   864.517] 	ABI class: X.Org Video Driver, version 14.1
[   864.518] (II) LoadModule: "modesetting"
[   864.518] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   864.585] (II) Module modesetting: vendor="X.Org Foundation"
[   864.585] 	compiled for 1.14.1, module version = 0.8.0
[   864.585] 	Module class: X.Org Video Driver
[   864.585] 	ABI class: X.Org Video Driver, version 14.1
[   864.585] (II) LoadModule: "fbdev"
[   864.585] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   864.656] (II) Module fbdev: vendor="X.Org Foundation"
[   864.656] 	compiled for 1.14.1, module version = 0.4.3
[   864.656] 	Module class: X.Org Video Driver
[   864.656] 	ABI class: X.Org Video Driver, version 14.1
[   864.656] (II) NOUVEAU driver 
[   864.656] (II) NOUVEAU driver for NVIDIA chipset families :
[   864.656] 	RIVA TNT        (NV04)
[   864.656] 	RIVA TNT2       (NV05)
[   864.656] 	GeForce 256     (NV10)
[   864.656] 	GeForce 2       (NV11, NV15)
[   864.656] 	GeForce 4MX     (NV17, NV18)
[   864.656] 	GeForce 3       (NV20)
[   864.656] 	GeForce 4Ti     (NV25, NV28)
[   864.656] 	GeForce FX      (NV3x)
[   864.656] 	GeForce 6       (NV4x)
[   864.656] 	GeForce 7       (G7x)
[   864.656] 	GeForce 8       (G8x)
[   864.656] 	GeForce GTX 200 (NVA0)
[   864.656] 	GeForce GTX 400 (NVC0)
[   864.656] (II) VESA: driver for VESA chipsets: vesa
[   864.656] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   864.656] (II) FBDEV: driver for framebuffer: fbdev
[   864.656] (++) using VT number 7

[   864.656] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[   864.656] (WW) xf86OpenConsole: setsid failed: Operation not permitted
[   864.657] (EE) [drm] KMS not enabled
[   864.657] (WW) Falling back to old probe method for modesetting
[   864.657] (EE) open /dev/dri/card0: No such file or directory
[   864.657] (WW) Falling back to old probe method for fbdev
[   864.657] (II) Loading sub module "fbdevhw"
[   864.657] (II) LoadModule: "fbdevhw"
[   864.657] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   864.698] (II) Module fbdevhw: vendor="X.Org Foundation"
[   864.698] 	compiled for 1.14.5, module version = 0.0.2
[   864.698] 	ABI class: X.Org Video Driver, version 14.1
[   864.698] (EE) open /dev/fb0: No such file or directory
[   864.698] (II) Loading sub module "vbe"
[   864.698] (II) LoadModule: "vbe"
[   864.699] (II) Loading /usr/lib/xorg/modules/libvbe.so
[   864.741] (II) Module vbe: vendor="X.Org Foundation"
[   864.741] 	compiled for 1.14.5, module version = 1.1.0
[   864.741] 	ABI class: X.Org Video Driver, version 14.1
[   864.741] (II) Loading sub module "int10"
[   864.741] (II) LoadModule: "int10"
[   864.741] (II) Loading /usr/lib/xorg/modules/libint10.so
[   864.823] (II) Module int10: vendor="X.Org Foundation"
[   864.823] 	compiled for 1.14.5, module version = 1.0.0
[   864.823] 	ABI class: X.Org Video Driver, version 14.1
[   864.823] (II) VESA(0): initializing int10
[   864.865] (II) VESA(0): Bad V_BIOS checksum
[   864.865] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[   864.895] (II) VESA(0): VESA BIOS detected
[   864.895] (II) VESA(0): VESA VBE Version 3.0
[   864.895] (II) VESA(0): VESA VBE Total Mem: 14336 kB
[   864.895] (II) VESA(0): VESA VBE OEM: NVIDIA
[   864.895] (II) VESA(0): VESA VBE OEM Software Rev: 112.24
[   864.895] (II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
[   864.895] (II) VESA(0): VESA VBE OEM Product: GT218 Board - 08730000
[   864.895] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
[   864.960] (II) VESA(0): Creating default Display subsection in Screen section
	"Dell Mapping" for depth/fbbpp 24/32
[   864.960] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[   864.960] (==) VESA(0): RGB weight 888
[   864.960] (==) VESA(0): Default visual is TrueColor
[   864.960] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[   864.960] (II) Loading sub module "ddc"
[   864.960] (II) LoadModule: "ddc"
[   864.960] (II) Module "ddc" already built-in
[   864.963] (II) VESA(0): VESA VBE DDC supported
[   864.963] (II) VESA(0): VESA VBE DDC Level none
[   864.963] (II) VESA(0): VESA VBE DDC transfer in appr. 0 sec.
[   865.128] (II) VESA(0): VESA VBE DDC read failed
[   865.128] (II) VESA(0): Searching for matching VESA mode(s):
[   865.130] Mode: 100 (640x400)

[…DETAIL REMOVED TO SAVE SPACE…]

[   865.177] (II) VESA(0): Total Memory: 224 64KB banks (14336kB)
[   865.177] (II) VESA(0): Dell: Using default hsync range of 31.50-48.00 kHz
[   865.177] (II) VESA(0): Dell: Using default vrefresh range of 50.00-70.00 Hz
[   865.177] (II) VESA(0): Dell: Using default maximum pixel clock of 65.00 MHz
[   865.177] (WW) VESA(0): Unable to estimate virtual size
[   865.177] (II) VESA(0): Not using built-in mode "1600x1200" (no mode of this name)
[   865.177] (II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
[   865.177] (II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
[   865.177] (II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
[   865.177] (II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
[   865.177] (II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
[   865.177] (II) VESA(0): Not using built-in mode "320x400" (no mode of this name)
[   865.177] (II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
[   865.177] (II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
[   865.177] (WW) VESA(0): No valid modes left. Trying less strict filter...
[   865.177] (II) VESA(0): Dell: Using hsync range of 31.50-48.00 kHz
[   865.177] (II) VESA(0): Dell: Using vrefresh range of 50.00-70.00 Hz
[   865.177] (II) VESA(0): Dell: Using maximum pixel clock of 65.00 MHz
[   865.177] (WW) VESA(0): Unable to estimate virtual size
[   865.177] (II) VESA(0): Not using built-in mode "1600x1200" (hsync out of range)
[   865.177] (II) VESA(0): Not using built-in mode "1280x1024" (hsync out of range)
[   865.177] (II) VESA(0): Not using built-in mode "640x400" (hsync out of range)
[   865.177] (II) VESA(0): Not using built-in mode "320x400" (hsync out of range)
[   865.177] (II) VESA(0): Not using built-in mode "320x240" (illegal horizontal timings)
[   865.177] (II) VESA(0): Not using built-in mode "320x200" (illegal horizontal timings)
[   865.177] (--) VESA(0): Virtual size is 1024x768 (pitch 1024)
[   865.177] (**) VESA(0): *Built-in mode "1024x768"
[   865.177] (**) VESA(0): *Built-in mode "800x600"
[   865.178] (**) VESA(0): *Built-in mode "640x480"
[   865.178] (**) VESA(0): Display dimensions: (1680, 1050) mm
[   865.178] (**) VESA(0): DPI set to (15, 18)
[   865.178] (II) VESA(0): Attempting to use 60Hz refresh for mode "1024x768" (118)
[   865.178] (II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (115)
[   865.179] (II) VESA(0): Attempting to use 60Hz refresh for mode "640x480" (112)
[   865.180] (**) VESA(0): Using "Shadow Framebuffer"
[   865.180] (II) Loading sub module "shadow"
[   865.180] (II) LoadModule: "shadow"
[   865.180] (II) Loading /usr/lib/xorg/modules/libshadow.so
[   865.242] (II) Module shadow: vendor="X.Org Foundation"
[   865.242] 	compiled for 1.14.5, module version = 1.1.0
[   865.242] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   865.242] (II) Loading sub module "fb"
[   865.242] (II) LoadModule: "fb"
[   865.242] (II) Loading /usr/lib/xorg/modules/libfb.so
[   865.371] (II) Module fb: vendor="X.Org Foundation"
[   865.371] 	compiled for 1.14.5, module version = 1.0.0
[   865.371] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   865.371] (II) UnloadModule: "modesetting"
[   865.371] (II) Unloading modesetting
[   865.371] (II) UnloadModule: "fbdev"
[   865.371] (II) Unloading fbdev
[   865.371] (II) UnloadSubModule: "fbdevhw"
[   865.371] (II) Unloading fbdevhw
[   865.371] (==) Depth 24 pixmap format is 32 bpp
[   865.371] (II) Loading sub module "int10"
[   865.371] (II) LoadModule: "int10"
[   865.372] (II) Loading /usr/lib/xorg/modules/libint10.so
[   865.372] (II) Module int10: vendor="X.Org Foundation"
[   865.372] 	compiled for 1.14.5, module version = 1.0.0
[   865.372] 	ABI class: X.Org Video Driver, version 14.1
[   865.372] (II) VESA(0): initializing int10
[   865.372] (II) VESA(0): Bad V_BIOS checksum
[   865.372] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[   865.404] (II) VESA(0): VESA BIOS detected
[   865.404] (II) VESA(0): VESA VBE Version 3.0
[   865.404] (II) VESA(0): VESA VBE Total Mem: 14336 kB
[   865.404] (II) VESA(0): VESA VBE OEM: NVIDIA
[   865.404] (II) VESA(0): VESA VBE OEM Software Rev: 112.24
[   865.404] (II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
[   865.404] (II) VESA(0): VESA VBE OEM Product: GT218 Board - 08730000
[   865.404] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
[   865.404] (II) VESA(0): virtual address = 0xb5c77000,
	physical address = 0xcf000000, size = 14680064
[   865.429] (II) VESA(0): Setting up VESA Mode 0x118 (1024x768)
[   865.571] (==) VESA(0): Default visual is TrueColor
[   865.598] (==) VESA(0): Backing store disabled
[   865.598] (==) VESA(0): DPMS enabled
[   865.619] (==) RandR enabled
[   865.647] (II) SELinux: Disabled on system
[   865.671] (II) AIGLX: Screen 0 is not DRI2 capable
[   865.671] (II) AIGLX: Screen 0 is not DRI capable
[   869.525] (II) AIGLX: Loaded and initialized swrast
[   869.525] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[   869.682] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
```

---

