---
title: "Trident CyberBlade i1 on Compaq Presario 1200 = No graphic acceleration... HELP"
date: 2009-06-29
forum: Hardware
---

### Post by Gaming4JC on 2009-06-29
Hello All,
I'm currently trying to configure Ubuntu 9.04 for some one running a Compaq Presario 1200, the graphics card is a Trident Microsystem's CyberBlade i1 which uses OpenGL. It worked fine on the Windows ME which was previously installed on this older laptop. The Windows drivers can be found here:
[http://members.driverguide.com/driver/detail.php?driverid=55770](http://members.driverguide.com/driver/detail.php?driverid=55770)

Currently Ubuntu is running on default drivers which means no graphic acceleration, no compiz, no 3d, and laggy 2d. I was also told Karmic may have newer trident drivers which are currently not on jaunty, but I still have doubts as to whether or not it would work.

I have already done some research on the IRC, and it seems to be either a graphic driver bug, or no one knows. The following are the specs which I was requested to give on the IRC:
[http://pastebin.ubuntu.com/206341/](http://pastebin.ubuntu.com/206341/)
[http://pastebin.ubuntu.com/206342/](http://pastebin.ubuntu.com/206342/)

I also was told to run a command which found out it was Direct Rendering capable, which left some folks confused...l
[quote=irc]
(11:55:00 AM) Incarus: Halitech, he said "direct rendering: Yes" but it is: "(II) AIGLX: Screen 0 is not DRI capable"
[/quote]


If anyone has any information on the subject please post as soon as possible. Thanks. :)

---

### Post by Tonyr63 on 2009-07-02
I have a related issue with a Compaq Presario Laptop where I got no display at all until I added Driver = Vesa into the Xorg.conf file.  Now I can just get a small screen at 800x600 and I have made numerious different edits to the xorg.conf file trying to find a modeline that will just give me 1024x768 with no luck.

I have tried many variables in the xorg.conf to try to tell Ubuntu that my laptop has the capability to display at 1024x768 however despite several hours I cannot seem to work out what to put in the file.  The video has 8MB enabled in the BIOS.  I get a good quality display as a box filling only 70% of the screen size.  Ubuntu's "configure display settings" gives me no option to increase the resolution to adjust display showing only 800x600 at 61Hz or 640x480

This is what I have currently in the xorg.conf:

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"1024x768 @ 60 Hz hsync: 48.4 kHz
ModeLine "1024x768@60"  65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Subsection "Display"
	Depth	24
	Modes "1024x768_60.00"
	EndSubsection
	
EndSection


Here is what the relevent section of the log file produces:

(II) VESA(0): Total Memory: 128 64KB banks (8192kB)
(II) VESA(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz
(II) VESA(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
(II) VESA(0): Not using mode "1024x768_75.00" (no mode of this name)
(II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
(II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
(WW) VESA(0): No valid modes left. Trying less strict filter...
(II) VESA(0): Configured Monitor: Using hsync range of 31.50-37.90 kHz
(II) VESA(0): Configured Monitor: Using vrefresh range of 50.00-70.00 Hz
(II) VESA(0): Not using mode "1024x768_75.00" (no mode of this name)
(II) VESA(0): Not using built-in mode "1024x768" (hsync out of range)
(--) VESA(0): Virtual size is 800x600 (pitch 800)
(**) VESA(0):  Built-in mode "800x600"
(**) VESA(0):  Built-in mode "640x480"
(==) VESA(0): DPI set to (96, 96)
(II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (115)
(II) VESA(0): Attempting to use 60Hz refresh for mode "640x480" (112)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 2.0
(II) VESA(0): VESA VBE Total Mem: 8192 kB
(II) VESA(0): VESA VBE OEM: Copyright 1998 TRIDENT MICROSYSTEMS INC.
(II) VESA(0): VESA VBE OEM Software Rev: 0.0
(II) VESA(0): VESA VBE OEM Vendor: 
(II) VESA(0): VESA VBE OEM Product: 
(II) VESA(0): VESA VBE OEM Product Rev: 
(II) VESA(0): virtual address = 0xb6e6a000,
	physical address = 0xf5000000, size = 8388608
(II) VESA(0): VBESetVBEMode failed...Tried again without customized values.
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(II) VESA(0): DPMS enabled
(==) RandR enabled

I'm not clear why having entered the mode 1024x768 explicitly I do not get this option and when the laptop run Windows it always worked at he higher display setting.


Can someone advise the settings I need in the xorg.conf file  to get a full screen display?
:KS

---

### Post by Zimmer on 2009-07-07
> **Tonyr63 said:**
> 

This is what I have currently in the xorg.conf:

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"1024x768 @ 60 Hz hsync: 48.4 kHz
ModeLine "1024x768@60"  65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Subsection "Display"
	Depth	24
	Modes "1024x768_60.00"
	EndSubsection
	
EndSection



(II) VESA(0): Not using mode "1024x768_75.00" (no mode of this name)
(


Can someone advise the settings I need in the xorg.conf file  to get a full screen display?
:KS
The error message says it all....

ModeLine "1024x768@60"
The line..
Modes "1024x768_60.00" is not valid,this should mirror the modeline name you created in the config

ie  should be Modes "1024x768@60" .
as long as the modeline is valid that should do the trick..

---

### Post by Cams on 2009-07-08
Did not work for Tiny A440 with Trident Cyberblade i1 (stuck at 800x600)

---

### Post by Tonyr63 on 2009-07-09
Zimmer
 
Thanks for your suggstion with is most appreciated.
 
Prior to reading your post I resolved the problem by removing the modeline completely and running with a simpler xorg.conf
 
In the monitor section i put:
 option "DPMS" "True"
Horizsync 30.0-60.0
VertRefresh 50.0-70.0
 
The screens section has thge ususal dept stuff and just
 
Modes "1024x768" "800x600"
 
Luckly it starts up with 1024x768.
 
It seem that it was looking for a Horiz and Vert sync range explicitly set which is surprising as the range I specified is quite standard and rather broad.  I canot understand why Ubuntu would not have been able to start the Vesa driver without this board setting explicitly set in a config file.  Then again when I finished the install it started with a completly BLANK display and dd not even have teh Driver = Vesa set??
 
It makes one wonder what was going on during the setup program which run for nearly 2 hours and reported diddly sqwat about have difficulties with what is a common display adapter on a named brand laptop (compaq) with a standard LCD monitor.  Its'nt SETUP supposed to set you up for operation of the device?
 
I think there is a case to answer here.
 
I am delighted to have a full display in any case and the 2001 laptop is quite functional to the extent that i plan to max out its memory to 320 MB from its current 188 Mb as I think it will notice the difference.
 
Great to see the old girl get some new life.
 
Kind Regards
 
 
Anthony

---

### Post by Zimmer on 2009-07-09
The problem(s) started for me with the new versions of xorg which attempt to use the EDID info from the monitor to set up the video. If there are problems reading the data or it is corrupt (can be corrupted by poor connecting leads or video extension cables!) then the default seems to be 800x600. The errors,warnings , etc. are in the xorg.0.log, but few people seem to go and have a look.... :) 
CAMS problem from the log is
(--) TRIDENT(0): TFT Panel 800x600 found
(--) TRIDENT(0): Memory Clock is 57.27 MHz
(==) TRIDENT(0): Min pixel clock is 12 MHz
(--) TRIDENT(0): Max pixel clock is 115 MHz
xorg reckons he has a 800x600 screen so it will not allow a better resolution.
Cams reckons his screen is capable of 1024x768 (and has been in the past).
IF we knew the correct Horizsynch and Vertrefresh ranges for the screen we could put those in the xorg.conf along with a statement to tell xorg to ignore the EDID info.
It might be worth trying your solution....  in the hope the ranges for your screen matches his...

---

### Post by Tonyr63 on 2009-07-09
I agree that getting the right Hsinc & Vsinc "range" should fix a problem like this as Linux is cautious to not pick a random setting and fry your monitor.  It is not always easy to find out these specification for a monitor as I know 2 of my laptops manuals did not provide these specs so you have to trawl the web and see if you can find out someone else with a similar device.  It is worth searching for xorg.conf & Monitor type or Graphic card type and see if you can get a sample file that will give you the H & V sync ranges that might work.
 
In my case i never found out the monitor type - I mean it is a Compaq Persario 1200 12XL 512 but no where have I see the monitor defined.  It took me a good while to find out that it most likely had a Trident Cyberblade 1i from someone else with a similar model which remindde me what used to be in the device manager of Windows ME.  I was sorry I did not print out the windows sysinfo before upgrading to Ubuntu.
 
It is a bit of a hit and miss and far from ideal.

---

### Post by Gaming4JC on 2010-02-09
This is still an issue, even on Karmic.

> 
ubuntu@ubuntu:~$ lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. VT8601 [Apollo ProMedia] (rev 05)
	Flags: bus master, medium devsel, latency 0
	Memory at f8000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-via
	Kernel modules: via-agp

00:01.0 PCI bridge: VIA Technologies, Inc. VT8601 [Apollo ProMedia AGP]
	Flags: bus master, 66MHz, medium devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: f4100000-f57fffff
	Prefetchable memory behind bridge: 1c000000-1c0fffff
	Kernel modules: shpchp

00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
	Subsystem: VIA Technologies, Inc. Device 0000
	Flags: bus master, stepping, medium devsel, latency 0
	Kernel driver in use: parport_pc
	Kernel modules: parport_pc

00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10) (prog-if 8a [Master SecP PriP])
	Flags: bus master, medium devsel, latency 64
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	I/O ports at 1420 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_via

00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
	Subsystem: First International Computer, Inc. Device 1234
	Flags: bus master, medium devsel, latency 64, IRQ 11
	I/O ports at 1400 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:07.4 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
	Flags: medium devsel, IRQ 10
	Capabilities: <access denied>
	Kernel modules: via686a, i2c-viapro

00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 20)
	Subsystem: Compaq Computer Corporation Device b194
	Flags: medium devsel, IRQ 9
	I/O ports at 1000 [size=256]
	I/O ports at 1434 [size=4]
	I/O ports at 1430 [size=4]
	Capabilities: <access denied>
	Kernel driver in use: VIA 82xx Audio
	Kernel modules: snd-via82xx

00:09.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem (rev 01)
	Subsystem: Compaq Computer Corporation Device b195
	Flags: medium devsel, IRQ 11
	Memory at f4000000 (32-bit, non-prefetchable) [size=64K]
	I/O ports at 1438 [size=8]
	Capabilities: <access denied>

00:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
	Subsystem: Compaq Computer Corporation Device b103
	Flags: bus master, medium devsel, latency 168, IRQ 9
	Memory at 1c100000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
	Memory window 0: 14000000-17fff000 (prefetchable)
	Memory window 1: 18000000-1bfff000
	I/O window 0: 00001800-000018ff
	I/O window 1: 00001c00-00001cff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

01:00.0 VGA compatible controller: Trident Microsystems CyberBlade i1 (rev 6a)
	Subsystem: Compaq Computer Corporation Device b16e
	Flags: bus master, fast Back2Back, 66MHz, medium devsel, latency 64, IRQ 9
	Memory at f5000000 (32-bit, non-prefetchable) [size=8M]
	Memory at f4100000 (32-bit, non-prefetchable) [size=128K]
	Memory at f4800000 (32-bit, non-prefetchable) [size=8M]
	[virtual] Expansion ROM at 1c000000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel modules: tridentfb

ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ gnome-appearance-properties %F

(gnome-appearance-properties:2915): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
There is no available graphics driver for your system which supports the composite extension, or the current one already supports it.
Checking for Xgl: 
(gnome-appearance-properties:2915): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:2915): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:2915): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
not present. 

(gnome-appearance-properties:2915): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:2915): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

(gnome-appearance-properties:2915): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:2915): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:2915): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:2915): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:2915): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:2915): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:2915): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:2915): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:2915): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:2915): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:2915): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:2915): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:2915): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
ubuntu@ubuntu:~$ 


As you can see, it's not allowing me to enable graphics acceleration and fails to detect card capabilities.

---

### Post by Gaming4JC on 2011-04-12
FYI, there's graphic acceleration on Windows. So I know some one over at MESSA dev or similar should be able to fix this... :(

---

