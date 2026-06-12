---
title: "Problem with fglrx drivers"
date: 2011-10-23
forum: Hardware
---

### Post by pajn on 2011-10-23
I don't seem to have any 3d acceleration with the fglrx drivers (everything is very laggy with compiz)

glxinfo
```
rasmus@Rasmus-Ubuntu:~$ glxinfo | head
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: ATI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group

```

xorg.conf
```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
	Load  "glx"
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
	Identifier "Default Screen"
	DefaultDepth     24
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

glxgears works.

glxheads
```
rasmus@Rasmus-Ubuntu:~$ glxheads 
glxheads: exercise multiple GLX connections (any key = exit)
Usage:
  glxheads xdisplayname ...
Example:
  glxheads :0 mars:0 venus:1
Name: :0.0
  Display:     0x1dac340
  Window:      0x5200002
  Context:     0x1df2a40
  GL_VERSION:  4.1.11005 Compatibility Profile Context
  GL_VENDOR:   ATI Technologies Inc.
  GL_RENDERER: AMD Radeon HD 6800 Series

```

My hardware is 2 6870 in crossfire, singe screen.
And i run 11.10

---

