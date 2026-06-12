---
title: "Flash, XOrg and Radeon 2600"
date: 2012-04-07
forum: Hardware
---

### Post by prpl on 2012-04-07
Hey guys

I'm using a laptop with a Radeon Mobility 2600 graphics card and I've had some problems with it. There is no driver for it in ubuntu so I've tried using no drivers (I believe ubuntu just uses some standard vesa drivers without any GPU acceleration support then?), I've tried using the driver that System->Administration->Hardware Drivers suggests, and I've tried using a driver from the amd website ([http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)). All of these have their own problems. I am on a 32bit architecture and I'm on 10.04 Lucid Lynx.

When I use the driver that ubuntu suggests, I have problems with resizing, maximizing, minimizing, and opening new windows, it takes 10 seconds for those actions during which everything freezes, even just to open a new gnome-terminal or nautilus window.

When I used the driver that I get from the amd website, I don't have those problems but instead I have problems with flash player. When I use youtube or twitch.tv, XOrg suddenly starts to eat up my CPU, sometimes eating up 50% (an entire core). Additionally, the sound glitches all the time (but the video is okay).

Without any drivers, nothing really works any well.

I have the glxinfo and the xorg.conf file for both configurations (both the drivers) but I'm not sure if those are relevant though.

I'd post the entire glxinfo but it's quite big so here's the difference.

glxinfo with the amd site driver has this:
```
client glx extensions:
    GLX_EXT_swap_control, GLX_MESA_copy_sub_buffer, GLX_AMD_gpu_association
OpenGL version string: 2.1 (3.3.11566 Compatibility Profile Context)
OpenGL shading language version string: (null)
    GL_ARB_vertex_buffer_object, GL_ARB_shader_objects, 
    GL_ARB_vertex_shader, GL_ARB_fragment_shader, GL_ARB_framebuffer_object, 
    GL_ARB_geometry_shader4,GL_EXT_histogram, GL_EXT_framebuffer_blit,
    GL_EXT_framebuffer_multisample, GL_EXT_geometry_shader4, GL_EXT_gpu_shader4
```

glxinfo with the driver Hardware Drivers suggested has this:
```
OpenGL version string: 1.4 (3.2.9756 Compatibility Profile Context)
```

Both of them have a ton of other stuff, but they have all that stuff in common.

After I install the driver from the amd site xorg.conf looks like this:
```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

After I install the driver the Hardware Drivers suggests xorg.conf looks like this:

```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"fglrx"
EndSection
```

I'm wondering if you have any advice? I'd like to have both flash player work and windows open and resize instantly and not freeze the system for 10 seconds.

Thank you for your help

---

### Post by dandnsmith on 2012-04-08
I don't know at what point you tried various things.
The default with Ub10.04 is to not have an xorg.conf, as the stuff is all done on the fly.
I'm using several Radeon cards of different models with several PC's, and have no delay problems on any of them using default drivers (which are not vesa for me).
Only other thing I can think of is that, via a vga connection to the monitor I am restricted as to the resolutions available, and whether they fill the screen - but DVI connections don't seem to have this problem (for me).
I note that I have different drivers in use when running under Mint11 (which I quite like), and they seem to work well too.

---

