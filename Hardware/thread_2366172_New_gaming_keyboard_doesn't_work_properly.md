---
title: "New gaming keyboard doesn't work properly"
date: 2017-07-14
forum: Hardware
---

### Post by fleetwood1970 on 2017-07-14
Hello Forum
I got a gaming keyboard with nice lights and macros, the brand is NISUTA NSKBGZ2 (its not a very expensive keyboard of course).-
And seems like the keyboard has problems with the layout.
The keys CTRL L - ALT L - ALT GR (in the right side) y SHIFT L and R don't work like they should.
I can't use ALT GR to type "@" (need to copy and paste).-
Another problem is that I can't do CTRL+C and CTRL+V to copy and paste easy.-
Of course macro keys don't work (it has 3 M keys and 5 G keys).-
Would be great to make it work completly but I know maybe I'll have to forget about the macro keys.-
What I did noticed, when I see the layout (mine is Spanish - Latin American but the whole system is in english), is that when I press any of those problematic keys all of them hit SHIFT L.-
I think the problem is the layout, maybe I can fix it somehow or create a custom layout to be able to use it. 
Advices and tutorials are very welcomed. 

Info about my computer

Processor : 2x AMD A6-7400K Radeon R5, 6 Compute Cores 2C+4G
Memory : 8112MB (1934MB used)
Operating System : Ubuntu 14.04.5 LTS
User Name : fleetwood (Fleetwood)
Date/Time : sáb 18 mar 2017 14:56:41 ART
-Display-
Resolution : 1440x900 pixels
OpenGL Renderer : GeForce GT 610/PCIe/SSE2
X11 Vendor : The X.Org Foundation
-Multimedia-
Audio Adapter : HDA-Intel - HD-Audio Generic
Audio Adapter : USB-Audio - FaceCam 310
Audio Adapter : HDA-Intel - HDA NVidia
-Input Devices-
Power Button
Power Button
SiliconWin mouse
SEMICO USB Keyboard
SEMICO USB Keyboard
Video Bus
FaceCam 310
HD-Audio Generic Rear Mic
HD-Audio Generic Line
HD-Audio Generic Line Out
HDA NVidia HDMI/DP,pcm : 3=
HDA NVidia HDMI/DP,pcm : 7=
-Printers-
No printers found
-SCSI Disks-
ATA ST500LT012-1DG14
TSSTcorp CDDVDW SH-S223F
Myson CS8819A2-113 0
Myson CS8819A2-113 1
Myson CS8819A2-113 2
Myson CS8819A2-113 3
Hitachi HTS545050B9A300

Info about the keyboard NISUTA NSKBGZ2

5x3 Programable keys for macros
6 Multimedia Quick Access Keys
26 Antighosting keys
Optional gaming mode (Blocks Windows Key)
Keys A/W/S/D and 4 directional arrows are interchangeable (?) That's what google translator says:lolflag:
DOESN'T BRING DRIVERS AND IS USB

Thanks in advance for the help and for reading my post
Lorena

---

### Post by Autodave on 2017-07-14
The first thing I would try would be to download a newer version of Ubintu. 16.04 is a long term release and would be my first choice. Burn it to a DVD or to a USB stick and boot from that and see if your keyboard works properly. If it does, time to upgrade. If 16.04 doesn't work, 17.04 could also be tried, but keep in mind that that is a short term release and you will have to upgrade in a few months when 17.10 comes out.

---

### Post by efflandt on 2017-07-15
How keyboard keys are recognized depends upon what is in /etc/default/keyboard (at least for terminal or terminal window), not necessarily what is marked on keys themselves. So you need to modify that keyboard file if your keyboard is different than that file says. In a terminal see: [B]man keyboard

[/B]Note that in terminals certain keys like Ctrl+C and Ctrl+V that work for copy/paste in X apps (similar to "the" Windows) can have special meaning or are used by certain terminal programs. For a terminal window I typically copy with the mouse, and you can paste with Ctrl+Shift+V, right mouse button, Edit > Paste from menu, or the old fashion X way is to highlight what you want to copy and paste it with middle mouse button (or both mouse buttons on 2-button mouse).

There may be other ways to modify keys or key combinations in X which may depend upon the window manager, but the keyboard file should also apply to defaults for X. In Ubuntu with default Unity, Compiz Config Settings Manager (if you install it) can add/set key combinations to do certain things, or change key combinations that do things like window switching.

---

