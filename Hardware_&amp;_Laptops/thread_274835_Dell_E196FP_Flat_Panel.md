---
title: "Dell E196FP Flat Panel"
date: 2006-10-10
forum: Hardware &amp; Laptops
---

### Post by MepisReign on 2006-10-10
Hello guys:
Maybe somebody here could give me hand with my problem, I own a Dell XPS 400 and I'm a Mepis user, currently my system is running the latest kernel version 2.6.15-27-686 (MEPIS) and I have the 8774 NVIDIA driver properly installed the problem is that I can not increase the color depth from thousands of colors to millions of colors, therefore Enemy Territory runs (yeah, I know that game is old) but with crappy graphics, is there a way to configure Xorg in order to get millions of colors displayed?
I did all the procedure of the installation in the proper way and the latest NVIDIA driver from their site (8774) is up and running. Now I just realized that the problem is not the driver but my FLAT PANEL :(. It's a DELL 19 inches E196FP (not digital). The problem seems to be with the color depth, it only takes thousands of colors instead of millions of colors, any ideas?

This is the Xorg log:

WW) NVIDIA(0): Invalid ConnectedMonitor request; request was for 'DFP-0,
(WW) NVIDIA(0): DFP-1', but the valid display devices are 'CRT-0, CRT-1,
(WW) NVIDIA(0): DFP-0, TV-0'.
(II) NVIDIA(0): NVIDIA GPU GeForce 7300 LE at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.72.22.41.31
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7300 LE at PCI:1:0:0:
(--) NVIDIA(0): Dell E196FP (CRT-1)
(--) NVIDIA(0): Dell E196FP (CRT-1): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0): "1280x1024"
(II) NVIDIA(0): "1024x768"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option
(II) do I need RAC? No, I don't.

***********************************************

(II) NVIDIA(0): Setting mode "1280x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "SecondMonitorVendorName" is not used
(WW) NVIDIA(0): Option "SecondMonitorModelName" is not used
(WW) NVIDIA(0): Option "UseInternalAGPGART" is not used
(WW) NVIDIA(0): Option "DmaMode" is not used
(WW) NVIDIA(0): Option "FlatPanelProperties" is not used
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX

***********************************************

I think the problem may be that the system is not recognizing the monitor as a Flat Panel but a CRT. I mean this particular model is Analog not digital but even in that case I should be able to change from thousands of colors to millions of colors, am I right?

Regards,

MepisReign

---

### Post by MepisReign on 2006-10-10
Anyone?

---

### Post by foxhound89 on 2006-11-18
I found this very helpful with getting my 196 up and running (never did figure out how to set the resolution, but it's running good enough) [<CLICK>]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")

I'm using the same monitor on my Dimension E510. Hope this helps and keep it in the wind.

---

