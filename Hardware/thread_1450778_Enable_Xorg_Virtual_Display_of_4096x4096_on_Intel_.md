---
title: "Enable Xorg Virtual Display of 4096x4096 on Intel 94x Graphics Card"
date: 2010-04-09
forum: Hardware
---

### Post by Jamie Jackson on 2010-04-09
A while back, I was able to use a virtual display of 4096x4096 (which would accommodate both my laptop screen and external monitor in dual head mode). I don't remember For many months, though, I haven't been able to replicate that (screens go black, and system locks up when I approach 2048 in width.

I am running running with a fully updated 9.10 on a Dell D620. (Detailed specs at the end of this post.)

I am also running without an xorg.conf, and suspect I need one to enable the increased virtual display dimensions. If so, please advise as to what the xorg.conf would need to be. I have included the relevant-seeming section of the Xorg.0.log immediately below.

Thanks,
Jamie

**Xorg.0.log snippet:**
```
(--) PCI:*(0:0:2:0) 8086:27a2:1028:01c2 Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xdff00000/524288, 0xc0000000/268435456, 0xdfec0000/262144, I/O @ 0x0000eff8/8
(==) Using default built-in configuration (39 lines)
(==) --- Start of built-in configuration ---
	Section "Device"
		Identifier	"Builtin Default intel Device 0"
		Driver	"intel"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default intel Screen 0"
		Device	"Builtin Default intel Device 0"
	EndSection
	Section "Device"
		Identifier	"Builtin Default i810 Device 0"
		Driver	"i810"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default i810 Screen 0"
		Device	"Builtin Default i810 Device 0"
	EndSection
	Section "Device"
		Identifier	"Builtin Default vesa Device 0"
		Driver	"vesa"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default vesa Screen 0"
		Device	"Builtin Default vesa Device 0"
	EndSection
	Section "Device"
		Identifier	"Builtin Default fbdev Device 0"
		Driver	"fbdev"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default fbdev Screen 0"
		Device	"Builtin Default fbdev Device 0"
	EndSection
	Section "ServerLayout"
		Identifier	"Builtin Default Layout"
		Screen	"Builtin Default intel Screen 0"
		Screen	"Builtin Default i810 Screen 0"
		Screen	"Builtin Default vesa Screen 0"
		Screen	"Builtin Default fbdev Screen 0"
	EndSection
(==) --- End of built-in configuration ---
(==) ServerLayout "Builtin Default Layout"
(**) |-->Screen "Builtin Default intel Screen 0" (0)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default intel Device 0"
(==) No monitor specified for screen "Builtin Default intel Screen 0".
	Using a default monitor configuration.
(**) |-->Screen "Builtin Default i810 Screen 0" (1)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default i810 Device 0"
(==) No monitor specified for screen "Builtin Default i810 Screen 0".
	Using a default monitor configuration.
(**) |-->Screen "Builtin Default vesa Screen 0" (2)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default vesa Device 0"
(==) No monitor specified for screen "Builtin Default vesa Screen 0".
	Using a default monitor configuration.
(**) |-->Screen "Builtin Default fbdev Screen 0" (3)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default fbdev Device 0"
(==) No monitor specified for screen "Builtin Default fbdev Screen 0".
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
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
```


**System Specs:**
```
jamie@mercury:~$ sudo lshw -C video
[sudo] password for jamie: 
  *-display:0             
       description: VGA compatible controller
       product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:dff00000-dff7ffff ioport:eff8(size=8) memory:c0000000-cfffffff(prefetchable) memory:dfec0000-dfefffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:dff80000-dfffffff
jamie@mercury:~$ uname -a
Linux mercury 2.6.31-21-generic #59-Ubuntu SMP Wed Mar 24 07:28:56 UTC 2010 i686 GNU/Linux

```

---

### Post by Jamie Jackson on 2010-04-10
Here's what worked:

First, I removed compiz with "sudo apt-get remove compiz-core", as getting rid of compiz (and its 3D effects, which are incompatible with intel virtual displays larger than 2048x2048 ) is what finally got the large virtual display working. I would rather have just disabled compiz, but I didn't know how. Please reply if you know how to disable it more elegantly.

Next, I created an /etc/init.d/xorg.conf file as follows:
```
Section "Device"
        Identifier "Intel Graphics Adapter"
        Driver     "intel"
EndSection

Section "Screen"
     Identifier      "Default Screen"
     Device          "Intel Graphics Adapter"
     SubSection "Display"
            Virtual         4096 4096
     EndSubSection
EndSection
```

After logging out and logging back in, I found that although I could finally use my monitors with a virtual display larger than 2048, my gnome was fairly hosed: My windows were missing their chrome (or whatever you call the border of a window that contains the minimize/close bar). I set gnome to its defaults by moving some hidden directories out of my home directory (like .gnome .gnome2 .gconf, etc.). This hosing of gnome is one reason why I'd like to know better how to disable compiz more gently than removing it. Still, I'm happy to finally have both monitors working at full res.

---

