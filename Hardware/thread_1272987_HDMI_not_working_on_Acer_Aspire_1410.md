---
title: "HDMI not working on Acer Aspire 1410"
date: 2009-09-22
forum: Hardware
---

### Post by Ryan_Singer on 2009-09-22
Hi Everyone,

When I attach my Acer Aspire 1410 (running 9.04) to my TV (Olivia 232-T12) over HDMI it shows normally on the TV instead of the laptop screen during the boot process, but once X11 loads, the laptop screen works and the TV screen shows only an invalid format message.

How do I get this working?

---

### Post by blackened on 2009-09-22
Are you able to change the settings of the external display using the Display Properties dialog? System -> Preferences -> Display.

---

### Post by Ryan_Singer on 2009-09-22
Yes, the dialog shows both monitors, but changes in the settings don't change the TV, it still continues to be a blank black with the invalid format message.

---

### Post by blackened on 2009-09-23
Odd. What does xrandr show you?

```
xrandr --prop
```

---

### Post by Ryan_Singer on 2009-09-23
```
Screen 0: minimum 320 x 200, current 1360 x 768, maximum 2720 x 768
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1360x768+0+0 (normal left inverted right x axis y axis) 256mm x 144mm
	EDID_DATA:
		00ffffffffffff0006af5c2000000000
		01120103801a0e780a99859555569228
		22505400000001010101010101010101
		01010101010196195628500008301810
		24000090100000180000000f00000000
		00000000000000000020000000fe0041
		554f0a202020202020202020000000fe
		004231313658573032205630200a00f8
	PANEL_FITTING:	full_aspect
		supported: center       full_aspect  full        
	BACKLIGHT_CONTROL:	kernel
		supported: native       legacy       combination  kernel      
	BACKLIGHT: 9 (0x00000009)	range:  (0,9)
   1366x768       60.0 +
   1360x768       59.8* 
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
HDMI-1 connected 1360x768+0+0 (normal left inverted right x axis y axis) 710mm x 400mm
	EDID_DATA:
		00ffffffffffff004f2e4000f4030000
		23110103814728780b3f00a754469825
		11494b254a0081c00101010101010101
		010101010101201c50a0500016303020
		3500c6902100001ca91a00a050001630
		30207300c6902100001a000000fd0038
		4b0f3a08000a202020202020000000fc
		003233322d5431320a20202020200123
		02031971468502030406072309070783
		01000065030c001000011d8018711c17
		20582c2500c6902100009e011d007251
		d01e206e285500c6902100001e8c0ad0
		8a20e02d10103e9600c690210000188c
		0ad08a20e02d10103e96001490210000
		188c0aa01451f01600267c4300c69021
		00009800000000000000000000000084
   1360x768       60.0*+
   1280x768       60.0  
   1280x720       60.0  
   1024x768       75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     75.0     59.9  
HDMI-2 disconnected (normal left inverted right x axis y axis)
TV disconnected (normal left inverted right x axis y axis)
	BOTTOM: 37 (0x00000025)	range:  (0,100)
	RIGHT: 46 (0x0000002e)	range:  (0,100)
	TOP: 36 (0x00000024)	range:  (0,100)
	LEFT: 54 (0x00000036)	range:  (0,100)
	TV_FORMAT:	NTSC-M
		supported: NTSC-M       NTSC-443     NTSC-J       PAL-M       
		           PAL-N        PAL         

```

---

### Post by blackened on 2009-09-23
Gonna stop right here. After some poking around on google, apparently numerous people have reported problems connecting components to the HDMI ports on this and other Olevia TVs. If it's new, then I would take it back and get something else. Everything I've read says that there have been no firmware updates to fix these problems.

Judging by your xrandr output, you should have at least something on the display.

---

### Post by Ryan_Singer on 2009-09-23
That's too bad. I've had the Olivia TV for over a year now. My iMac exports to it over S-Video with no problems. My Laptop also has a VGA port, so I'll buy a VGA cable and try that.

---

### Post by blackened on 2009-09-23
> **Ryan_Singer said:**
> That's too bad. I've had the Olivia TV for over a year now. My iMac exports to it over S-Video with no problems. My Laptop also has a VGA port, so I'll buy a VGA cable and try that.

That's probably your best bet. I've seen a few reports of people experiencing the same problem over the VGA connection as well though. Best of luck to you.

---

### Post by Ryan_Singer on 2009-09-23
Thanks for your help, blackened. If you make it out to the SF Bay Area at some point, I owe you a beer!

---

