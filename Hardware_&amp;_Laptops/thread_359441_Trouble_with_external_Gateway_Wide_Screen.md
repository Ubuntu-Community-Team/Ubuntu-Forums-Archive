---
title: "Trouble with external Gateway Wide Screen"
date: 2007-02-12
forum: Hardware &amp; Laptops
---

### Post by sandolamb on 2007-02-12
First let me assure you that I have read and tried every post I could find to solve the problem, so I believe I have something new - well, certainly something I can't solve in several hours of trying.

I just can't get my Gateway FPD2275W monitor to work with Ubuntu/Gnome.  Here's what I know so far:

The monitor works windows in Dual-head mode (You can extend the desktop)
The monitor works with a friends Dell and Ubuntu (but a different Dell model)
There's the hardware information from the log

Video Card:

[FONT="Courier New"]
(II) I810(0): Integrated Graphics Chipset: Intel(R) unknown chipset
(--) I810(0): Chipset: "945GM"
(--) I810(0): Linear framebuffer at 0xC0000000
(--) I810(0): IO registers at addr 0xDFF00000
(II) I810(0): 2 display pipes available.
(II) I810(0): detected 7932 kB stolen memory.
(II) I810(0): Kernel reported 488960 total, 1 used
(II) I810(0): Checking Available AGP Memory: 1955836 kB available (total 1955840 kB, used 4 kB)
(II) I810(0): Monitoring connected displays enabled

...

(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 12288 kB
(II) I810(0): VESA VBE OEM: Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r) 82945GM Chipset Family Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): BIOS now sees 12288 kB VideoRAM




[/FONT]


Extra Monitor
[FONT="Courier New"]
(II) I810(0): Manufacturer: GWY  Model: 8ed  Serial#: 0
(II) I810(0): Year: 2007  Week: 1
(II) I810(0): EDID Version: 1.3
(II) I810(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) I810(0): Sync:  Separate
(II) I810(0): Max H-Image Size [cm]: horiz.: 48  vert.: 30
(II) I810(0): Gamma: 2.20
(II) I810(0): DPMS capabilities: Off; RGB/Color Display
(II) I810(0): First detailed timing is preferred mode
(II) I810(0): redX: 0.644 redY: 0.333   greenX: 0.286 greenY: 0.603
(II) I810(0): blueX: 0.152 blueY: 0.079   whiteX: 0.313 whiteY: 0.329
(II) I810(0): Supported VESA Video Modes:
(II) I810(0): 720x400@70Hz
(II) I810(0): 640x480@60Hz
(II) I810(0): 640x480@72Hz
(II) I810(0): 640x480@75Hz
(II) I810(0): 800x600@56Hz
(II) I810(0): 800x600@60Hz
(II) I810(0): 800x600@72Hz
(II) I810(0): 800x600@75Hz
(II) I810(0): 1024x768@60Hz
(II) I810(0): 1024x768@70Hz
(II) I810(0): 1024x768@75Hz
(II) I810(0): 1280x1024@75Hz
(II) I810(0): Manufacturer's mask: 0
(II) I810(0): Supported Future Video Modes:
(II) I810(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) I810(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) I810(0): #2: hsize: 1400  vsize 1050  refresh: 60  vid: 16528
(II) I810(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) I810(0): #4: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) I810(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) I810(0): #6: hsize: 1680  vsize 1050  refresh: 75  vid: 4019
(II) I810(0): Supported additional Video Mode:
(II) I810(0): clock: 146.2 MHz   Image Size:  473 x 296 mm
(II) I810(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) I810(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) I810(0): Monitor name: FPD2275W
(II) I810(0): Ranges: V min: 56  V max: 76 Hz, H min: 31  H max: 83 kHz, PixClock max 190 MHz
(II) I810(0): Serial No: MGK71D0C02856
(--) I810(0): A non-CRT device is attached to pipe B.
	No refresh rate overrides will be attempted.
(--) I810(0): Maximum space available for video modes: 12288 kByte
(II) I810(0): Using detected DDC timings
(II) I810(0): 	HorizSync 31-83
(II) I810(0): 	VertRefresh 56-76

[/FONT]

That all looks just fine.  Here's some symptoms

If I start gnome and set the resolution to 1600x1200, I can Fn-F8 and run the external monitor above it's rating and it scales the image.  It look yucky, but works fine.

However, 1680x1050 (the native resolution) doesn't appear.  So I used 915resolution and added an entry.  Now I can select 1680x1050 and the laptop screen shows it.

I press Fn-F8 and the monitor displays "sync is out of range"

Next I add a mode line to xorg.conf to match the EDID information exactly (Also this matches the settings that my friends laptop picked for the screen automatically.) I restart everything, select the resolution, check the settings with xvidtune, everything is perfect.

[FONT="Courier New"]
    Modeline "1680x1050_59.95"  146.25 1680 1784 1960 2240  1050 1053 1059 1089 +HSync`
[/FONT]

Press Fn-F8 and the external monitor says it's out of sync range - again.

I'm at a loss and will provide any information (or money) you need to help me.

Please.....

---

### Post by sandolamb on 2007-02-12
Ping

---

### Post by sandolamb on 2007-02-13
Well try as I might to get the monitor to respond to Linux at the correct resolution it was a no go.  It worked with Windows; it worked at non-standard resolutions.  It just wouldn't run at the correct one.

So,  I took it back.

Thanks anyway.

---

### Post by bogdanmarian on 2007-03-22
that's too bad, this is a nice monitor at a decent price point.  i'm currently running it at 1920x1200 on an old geforce4 440mx card. the DPI at 1680x1050 for a 22" lcd is too low to produce clear fonts (your mileage may vary of course)

for anyone who may be wondering, the Gateway FPD2275W does work just fine with linux (i don't actually use ubuntu, but xorg is xorg and drivers are drivers, regardless of your distro)

---

### Post by VxJasonxV on 2007-07-08
Could you enlighten a poor soul and tell me how exactly?

---

