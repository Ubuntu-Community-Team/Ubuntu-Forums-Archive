---
title: "fglrx driver fails with external monitor"
date: 2008-02-06
forum: Hardware &amp; Laptops
---

### Post by robmacg on 2008-02-06
I know there are a lot of posts with this kind of problem, but I have not seen that exactly match, so here goes (I also posted this on the beginners forum, but this seems a more appropriate place).

I am trying to connect a projector to my Thinkpad T60 (ATI graphics card, using the fglrx driver).

Firstly - I have to restart X to get the projector to be active at all. It seems that the Function-F7 key to activate an external monitor is not implemented (I've looked at KeyTouch, but that does not list it as a possible combination).

Then - when X starts with the projector plugged in I get a message saying that X has hit an error and will operate in low resolution mode. This dialog allows you to set the resolution, but the only option available is 1400x1050 at 61Hz (this is the resolution of my laptop screen, although the 61Hz is a bit odd).

The system then comes up at 1400x1050, with the projector active (yippee). However, most projectors are very unhappy at such a high resolution, so I try to change it to 1024x768. BUT, the Screen Resolution option under Preferences has only one option - 1400x1050!

On investigating a bit more, it seems the fglrx driver is crashing during startup and that is what drives the system into the weird "low resolution mode" thing. The Xorg.9.log file shows this failure and a backtrace. I've copied the end of the log below. This looks like an fglrx bug - can anyone suggest how to pursue it further?

Here is the tail of Xorg.9.log:


[FONT="Courier New"](II) fglrx(0): EDID (in hex):
(II) fglrx(0): 00ffffffffffff0030ae224000000000
(II) fglrx(0): 15110103801d1578ea6f959c544c8726
(II) fglrx(0): 21505400000001010101010101010101
(II) fglrx(0): 010101010101302a7820511a10403070
(II) fglrx(0): 13001fd71000001825237820511a1040
(II) fglrx(0): 307013001fd7100000180000000f0090
(II) fglrx(0): 43329043280f010030640055000000fe
(II) fglrx(0): 004c5444313431454e39420a20200004
(II) fglrx(0): End of Display2 EDID data --------------------
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Secondary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000008
(II) fglrx(0): POWERplay version 3. 5 power states available:
(II) fglrx(0): 1. 446/351MHz @ 60Hz [enable load balancing]
(II) fglrx(0): 2. 128/135MHz @ 60Hz [low voltage, enable sleep]
(II) fglrx(0): 3. 209/135MHz @ 60Hz [low voltage, enable sleep]
(II) fglrx(0): 4. 324/135MHz @ 60Hz [enable sleep]
(II) fglrx(0): 5. 398/351MHz @ 60Hz [enable sleep, thermal diode mode]
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 2
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0): PseudoColor visuals disabled
(**) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled
(==) fglrx(0): TMDS coherent mode is enabled
(II) fglrx(0): Total of 6 modes found for primary display.
(--) fglrx(0): Virtual size is 640x480 (pitch 0)
(**) fglrx(0): *Mode "640x480@60": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480@60" 108.00 640 1448 1560 1688 480 1051 1054 1066 +hsync +vsync
(**) fglrx(0): Default mode "640x400": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400" 108.00 640 1448 1560 1688 400 1051 1054 1066 +hsync +vsync
(**) fglrx(0): Default mode "512x384": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384" 108.00 512 1448 1560 1688 384 1051 1054 1066 +hsync +vsync
(**) fglrx(0): Default mode "400x300": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300" 108.00 400 1448 1560 1688 300 1051 1054 1066 +hsync +vsync
(**) fglrx(0): Default mode "320x240": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240" 108.00 320 1448 1560 1688 240 1051 1054 1066 +hsync +vsync
(**) fglrx(0): Default mode "320x200": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200" 108.00 320 1448 1560 1688 200 1051 1054 1066 +hsync +vsync

Backtrace:
0: /usr/X11R6/bin/Xorg(xf86SigHandler+0x81) [0x80c95d1]
1: [0xffffe420]
2: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0xb7a1e064]
3: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddx PreInit+0x98 [0xb7a18a48]
4: /usr/X11R6/bin/Xorg(InitOutput+0x9a4) [0x80a8ea4]
5: /usr/X11R6/bin/Xorg(main+0x27b) [0x8076ceb]
6: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe 0) [0xb7dfe050]
7: /usr/X11R6/bin/Xorg(FontFileCompleteXLFD+0x1e1) [0x8076241]

Fatal server error:
Caught signal 11. Server aborting[/FONT]

---

