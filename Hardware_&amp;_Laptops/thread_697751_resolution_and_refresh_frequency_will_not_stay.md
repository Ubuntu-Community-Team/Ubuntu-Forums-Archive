---
title: "resolution and refresh frequency will not stay"
date: 2008-02-15
forum: Hardware &amp; Laptops
---

### Post by nilsA on 2008-02-15
For some reason the monitor I specify, using either nvidia-settings (as superuser) or SystemSettings -> Monitor&Display will not stay over reset. (Well, most of the time, anyway.) (Kubuntu 7.10)

The monitor, an old Nokia Multigraph 446Xpro, is in xorg.conf capable of up to these:

(Many lower omitted)
```
  modeline  "1600x1200@85" 229.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@75" 261.0 1792 1888 2104 2456 1344 1345 1348 1417 -hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
  modeline  "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
  modeline  "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
  modeline  "2048x1536@60" 266.95 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync
```

But when I do 

sudo xandr

I find:

```
Screen 0: minimum 320 x 175, current 1600 x 1200, maximum 1600 x 1200
default connected 1600x1200+0+0 0mm x 0mm
   1600x1200      50.0     51.0*    54.0     55.0     56.0     57.0
   1280x1024      52.0     66.0     67.0
   1024x768       53.0     77.0     78.0     79.0     80.0     81.0     82.0
   1600x1024      58.0
   1440x900       59.0
   1400x1050      60.0     61.0     62.0     63.0     64.0     65.0
   1280x960       68.0     69.0     70.0     71.0
   1280x800       72.0
   1280x768       73.0
   1152x864       74.0     75.0
   1152x768       76.0
   960x720        83.0
   960x600        84.0     85.0
```

(Many lower omitted).

It is clear that both the graphics card, Gainward GeForce 6800LE 128MB DDR, and the monitor is capable of doing the 1600x1200@85 I need. I can do the changes with nvidiia-settings quite without any problem. But, even though it saves just fine - the next time, back to 1600x1200@50.

I've tried all possible combinations of generating and editing the xorg.conf file, and tried Envy.

If I use the nv driver things seem ok, but many programs complain.
The nvidia and specific nvidia6800 drivers introduce the problem.

How can I get around this? It's annoying having to set the HZ rate every time I start the PC.

---

### Post by Yellow Pasque on 2008-02-15
Hmm, how did you get the modelines? Try a program called cvt (may already be installed).
See what this gives you:
```
sudo cvt -v 1600 1200 85.0Hz
```

Also, are you sure that your monitor is capable of that resolution/refresh at 24-bit color depth? Try looking at your /var/log/Xorg.0.log to see if it gives you any clues as to why it won't start in the desired resolution.

---

### Post by nilsA on 2008-02-16
> **Temüjin said:**
> Hmm, how did you get the modelines? Try a program called cvt (may already be installed).
See what this gives you:
```
sudo cvt -v 1600 1200 85.0Hz
```

Also, are you sure that your monitor is capable of that resolution/refresh at 24-bit color depth? Try looking at your /var/log/Xorg.0.log to see if it gives you any clues as to why it won't start in the desired resolution.

Thanks for helping - I am about to give up here.

```
 sudo cvt -v 1600 1200 85.0Hz
# 1600x1200 84.95 Hz (CVT 1.92M3) hsync: 107.21 kHz; pclk: 235.00 MHz
Modeline "1600x1200_85.00"  235.00  1600 1728 1896 2192  1200 1203 1207 1262 -hsync +vsync

```

And yes, I am sure the monitor can do 1600x1200@85HZ w/24-32colour - it does in Win2000 without any problem

A little below the middle of /var/log/xorg.0.log I find this:

```
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(**) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "1600x1200_85 +0+0; 1600x1200 +0+0; 1280x1024 +0+0; 1024x768 +0+0"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6800 LE (NV40) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 05.40.02.22.04
(II) NVIDIA(0): Detected AGP rate: 2X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6800 LE at PCI:1:0:0:
(--) NVIDIA(0):     Nokia 446Xpro (CRT-1)
(--) NVIDIA(0): Nokia 446Xpro (CRT-1): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-1
(II) NVIDIA(0): Validated modes:
(II) DRAVIDIAN(0):     "1600x1200_85+0+0"
(II) NVIDIA(0):     "1600x1200+0+0"
(II) NVIDIA(0):     "1280x1024+0+0"
(II) NVIDIA(0):     "1024x768+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200
(++) NVIDIA(0): DPI set to (74, 74); computed from -dpi X commandline option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
```

Then a list called "resource ranges ... followed by:

```
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Setting mode "1600x1200_85+0+0"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
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
(**) Option "CoreKeyboard"
```

A section regarding mouse and keyboard, and at the end:

```
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) NVIDIA(0): Setting mode "1600x1200@60"
(II) NVIDIA(0): Setting mode "1600x1200+0+0"
(WW) NVIDIA(0): Error while parsing panning domain in mode description
(WW) NVIDIA(0):     "1600x1200@75@1600x1200+0+0"
(WW) NVIDIA(0): Error while parsing panning domain in mode description
(WW) NVIDIA(0):     "1600x1200@70@1600x1200+0+0"
(WW) NVIDIA(0): Error while parsing panning domain in mode description
(WW) NVIDIA(0):     "1600x1200@65@1600x1200+0+0"
(WW) NVIDIA(0): Error while parsing panning domain in mode description
(WW) NVIDIA(0):     "1600x1200@60@1600x1200+0+0"
(WW) NVIDIA(0): Error while parsing panning domain in mode description
(WW) NVIDIA(0):     "1400x1050@75@1400x1050+0+0"
(WW) NVIDIA(0): Error while parsing panning domain in mode description
(WW) NVIDIA(0):     "1400x1050@60@1400x1050+0+0"
(WW) NVIDIA(0): Error while parsing panning domain in mode description
(WW) NVIDIA(0):     "1280x1024@75@1280x1024+0+0"
(WW) NVIDIA(0): Error while parsing panning domain in mode description
(WW) NVIDIA(0):     "1280x1024@60@1280x1024+0+0"
(WW) NVIDIA(0): Error while parsing panning domain in mode description
(WW) NVIDIA(0):     "1280x960@85@1280x960+0+0"
(WW) NVIDIA(0): Error while parsing panning domain in mode description
(WW) NVIDIA(0):     "1280x960@75@1280x960+0+0"
(WW) NVIDIA(0): Error while parsing panning domain in mode description
(WW) NVIDIA(0):     "1280x960@60@1280x960+0+0"
(WW) NVIDIA(0): Error while parsing panning domain in mode description
(WW) NVIDIA(0):     "1152x864@75@1152x864+0+0"
(WW) NVIDIA(0): Error while parsing panning domain in mode description
(WW) NVIDIA(0):     "1024x768@85@1024x768+0+0"
(WW) NVIDIA(0): Error while parsing panning domain in mode description
(WW) NVIDIA(0):     "1024x768@75@1024x768+0+0"
(WW) NVIDIA(0): Error while parsing panning domain in mode description
(WW) NVIDIA(0):     "1024x768@70@1024x768+0+0"
(WW) NVIDIA(0): Error while parsing panning domain in mode description
(WW) NVIDIA(0):     "1024x768@60@1024x768+0+0"
(WW) NVIDIA(0): Error while parsing panning domain in mode description
(WW) NVIDIA(0):     "1024x768@43@1024x768+0+0"
(WW) NVIDIA(0): Error while parsing panning domain in mode description
(WW) NVIDIA(0):     "832x624@75@832x624+0+0"
(WW) NVIDIA(0): Error while parsing panning domain in mode description
(WW) NVIDIA(0):     "800x600@85@800x600+0+0"
(WW) NVIDIA(0): Error while parsing panning domain in mode description
(WW) NVIDIA(0):     "800x600@75@800x600+0+0"
(WW) NVIDIA(0): Error while parsing panning domain in mode description
(WW) NVIDIA(0):     "800x600@72@800x600+0+0"
(WW) NVIDIA(0): Error while parsing panning domain in mode description
(WW) NVIDIA(0):     "800x600@60@800x600+0+0"
(WW) NVIDIA(0): Error while parsing panning domain in mode description
(WW) NVIDIA(0):     "800x600@56@800x600+0+0"
(WW) NVIDIA(0): Error while parsing panning domain in mode description
(WW) NVIDIA(0):     "640x480@85@640x480+0+0"
(WW) NVIDIA(0): Error while parsing panning domain in mode description
(WW) NVIDIA(0):     "640x480@75@640x480+0+0"
(WW) NVIDIA(0): Error while parsing panning domain in mode description
(WW) NVIDIA(0):     "640x480@72@640x480+0+0"
(WW) NVIDIA(0): Error while parsing panning domain in mode description
(WW) NVIDIA(0):     "640x480@60@640x480+0+0"
```

---

### Post by Blood.Omen on 2008-04-26
I also have the NOKIA Multigraph 446Xpro.
You are wrong on it's stats.
Maybe the thing can do more, but the official stats from Nokia are like this:

Technical Specification
446Xpro Nokia 19" Monitor


CRT SIZE , TYPE 	19"- FST
PHOSPHOR , DOT/MASK PITCH 	P22, medium short,
Trio: 0.26 mm (dot pitch)
Horz.: 0,21 mm (horiz mask pitch)
FACE PLATE TREATMENT, TRANSMISSION 	Spin coating
Light transmission 46%, dark tint
High-contrast ratio 1:4
FREQUENCY RANGE 	Horizontal: 30-107 kHz,
Vertical: 50-150 Hz
MAX DOT FREQUENCY 	230 MHz (fall and rise times
RESOLUTIONS, MAX PICTURE REFRESH RATE 	640 x 480: up to 150 Hz
800 x 600: up to 150 Hz
1024 X 768: up to 130 Hz
1280 x 1024: up to 99 Hz
1600 x 1200: up to 85 Hz
1600 x 1280: up to 80 Hz
CONVERGENCE DISTORTION 	A-area = to 0,25 mm,
B-area = to 0,35 mm (typical)
Using static convergence correction
A-area = Center circle diameter of 270 mm,
B-area = is rest area

so 1600 x 1280 @ 80Hz is MAXIMUM!!!

Source: Nokia Pressrelease and Nokia Tech Specs.
[http://www.atkkierratys.com/techspecsfor446Xpro.html](http://www.atkkierratys.com/techspecsfor446Xpro.html)
[http://press.nokia.com/PR/199710/776645_5.html](http://press.nokia.com/PR/199710/776645_5.html)

cheers!

ps. a helpful tool under windows is REFORCE.
(RefreshForce V1.10)
It can edit out all invalid frequencies for your monitor with it.

---

