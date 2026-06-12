---
title: "could not get the right resolution on a widescreen LCD with video-intel driver"
date: 2008-11-03
forum: Hardware
---

### Post by diony on 2008-11-03
i am using xserver-xorg-video-intel driver, lspci said my onboard video card is :

```

00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 0e)

```

and the xrandr -q said:
```

Screen 0: minimum 320 x 200, current 1152 x 864, maximum 1360 x 1360
VGA connected 1152x864+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1152x864       60.0* 
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  

```

i have tried manually adding resolution modes to xorg.conf, like this:
```

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	16	
	SubSection	"Display"
		Depth	16	
		Modes	"1680x1050" "1440x900" "1280x800" "1024x768" "800x600"
	EndSubSection
	SubSection	"Display"
		Depth	24
		Modes	"1680x1050" "1440x900" "1280x800" "1024x768" "800x600"
	EndSubSection
EndSection

```

but it doesn't help. i can't get 1680x1050 work.

any suggestion?:(

---

### Post by mwgrient on 2008-11-03
try this at the prompt, without X running:

X -configure

and then try your new configuration with:
X -config /root/xorg.conf.new

---

### Post by diony on 2008-11-03
tried "X -configure", but it only show me a blank&black screen. after a very long time waiting, i pressed alt+f1 go back, and got something like this
```

X:symbol lookup error: /usr/lib/xorg/modules/drivers/vga_drv.so: undefined symbol:xf86GetPciVideoInfo

```

and i didn't get the file xorg.conf.new.

---

### Post by diony on 2008-11-04
after remove the vga and another driver, i can do X -configure now. but the new xorg.conf doesn't help. still i can not get 1680x1050 mode working.

i have checked the /var/log/Xorg.0.log, and grep all lines include "intel"

```

diony@diony-minipc:~$ grep intel /var/log/Xorg.0.log
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
(**) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 915G
(--) intel(0): Chipset: "915G"
(--) intel(0): Linear framebuffer at 0xC0000000
(--) intel(0): IO registers at addr 0xD0200000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using EXA for acceleration
(II) intel(0): initializing int10
(WW) intel(0): Bad V_BIOS checksum
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 7872 kB
(II) intel(0): VESA VBE OEM: Intel(r)915G/915GV/910GL Graphics Chip Accelerated VGA BIOS
(II) intel(0): VESA VBE OEM Software Rev: 1.0
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: Intel(r)915G/915GV/910GL Graphics Controller
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) intel(0): Output VGA using monitor section Monitor0
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): Output VGA connected
(II) intel(0): Using fuzzy aspect match for initial modes
(II) intel(0): Output VGA using initial mode 1152x864
(II) intel(0): detected 256 kB GTT.
(II) intel(0): detected 7932 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Intel XvMC decoder disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(II) intel(0): Comparing regs from server start up to After PreInit
(II) intel(0): Kernel reported 238848 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 955388 kB available
(II) intel(0): [drm] Using the DRM lock SAREA also for drawables.
(II) intel(0): [drm] framebuffer mapped by ddx driver
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) intel(0): [drm] Registers = 0xd0200000
(II) intel(0): [drm] ring buffer = 0xc0000000
(II) intel(0): [drm] mapped front buffer at 0xc1000000, handle = 0xc1000000
(II) intel(0): [drm] mapped back buffer at 0xc4000000, handle = 0xc4000000
(II) intel(0): [drm] mapped depth buffer at 0xc5000000, handle = 0xc5000000
(II) intel(0): [drm] mapped classic textures at 0xc6000000, handle = 0xc6000000
(II) intel(0): [drm] Initialized kernel agp heap manager, 33554432
(II) intel(0): [dri] visual configs initialized
(II) intel(0): Page Flipping disabled
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): [DRI] installation complete
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x01000000 (pgoffset 4096)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x02000000 (pgoffset 8192)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x04000000 (pgoffset 16384)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x05000000 (pgoffset 20480)
(II) intel(0): xf86BindGARTMemory: bind key 4 at 0x06000000 (pgoffset 24576)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x00029fff: HW cursors (40 kB, 0x000000003f820000 physical
(II) intel(0): 0x0002a000-0x00031fff: logical 3D context (32 kB)
(II) intel(0): 0x00032000-0x00032fff: overlay registers (4 kB, 0x000000003f832000 physical
(II) intel(0): 0x007bf000:            end of stolen memory
(II) intel(0): 0x01000000-0x01ffffff: front buffer (10880 kB) X tiled
(II) intel(0): 0x02000000-0x03fdffff: exa offscreen (32640 kB)
(II) intel(0): 0x04000000-0x04ffffff: back buffer (10880 kB) X tiled
(II) intel(0): 0x05000000-0x05ffffff: depth buffer (10880 kB) X tiled
(II) intel(0): 0x06000000-0x07ffffff: classic textures (32768 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is on
(II) intel(0):   Display plane A is now enabled and connected to pipe A.
(II) intel(0):   Pipe B is off
(II) intel(0):   Display plane B is now disabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe A
(II) intel(0): [drm] dma control initialized, using IRQ 16
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): DPMS enabled
(II) intel(0): Set up textured video
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: Enabled
(II) intel(0): Setting screen physical size to 304 x 228
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.

```

---

### Post by ZennouRyuu on 2008-11-10
Having the same issue with my Lenovo T500 with Intel graphics.....

Strange thing is, 1600x1050 was working great before i tried to hook up an external monitor to my laptop and then it all went to hell.

Anyone have any ideas on how to get the native resolution back, looking at this screen is really making me sick :shock:

---

### Post by ZennouRyuu on 2008-11-10
Okay so this seems for me at least to be a user level problem, I created a new user and my resolution was back to normal. I cant seem to figure out which file actually controls this, but I imagine one could just delete it and get back to normal.


Good luck though, I have to go get some asprin now that I have been staring at a terribly fuzzy screen for five hours....

---

