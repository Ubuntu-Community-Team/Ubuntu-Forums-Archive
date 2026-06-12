---
title: "no direct redering intel 945GM"
date: 2010-02-27
forum: Hardware
---

### Post by schubber on 2010-02-27
Hello,

got display problems with Ubuntu 9.10 and my laptop. The laptop has integrated intel 945GM graphics. With Ubuntu 8.04 everything was fine. After installing Ubuntu 9.10, the screen did work only with the vesa driver. With the intel driver the screen stayed black. So i installed the older graphics driver from Ubuntu 8.10 by this howto [wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4]. Now the Laptop starts with the intel driver but performance ist extremly low. with an extern monitor everything is fine and performance ist very well.
In case i undestand the following part of my Xorg.0.log correctly, direct-rendering gets deactivated. That is because the intel driver thinks my Screen ist not dri capable. The complete Xorg.0.log ist included as an attachment. 
> 
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is off
(II) intel(0):   Display plane B is now disabled and connected to pipe A.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane A is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output LVDS is connected to pipe B
(II) intel(0):   Output TV is connected to pipe none
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): using SSC reference clock of 96 MHz
(II) intel(0): Selecting standard 18 bit TMDS pixel format.
(II) intel(0): DPMS enabled
(II) intel(0): Set up textured video
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: Failed
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
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) intel(0): Setting screen physical size to 270 x 203

I did not change anything in my xorg.conf.
> 
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"intel"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

glxinfo gives the following output (part). The complete output is included as an attachment:
> 
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.6
OpenGL shading language version string: 1.20

I think only software rendering is activated.

Perhaps i have to force direct-rendering, but how? Perhaps im wrong and the problem is somewhere else? 
I hope someone has some tips or an idea how to go on to get the screen working.

Thanks in advance!

---

