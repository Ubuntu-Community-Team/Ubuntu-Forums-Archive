---
title: "Monitor shuts off every few min"
date: 2008-01-08
forum: Hardware &amp; Laptops
---

### Post by dhaus111 on 2008-01-08
Hello all, 

I've got a gateway mx6959 that is being a real pain in my ****.  I installed gutsy on it a few weeks ago and lately Its been shutting off the screen every few min, completely off not just blanked,  I can turn it back on by adjusting the brightness either up for down a few notches (FN+up or FN+down).  Then I've got a few min to wait until it does it again. There is no idle time require, it happens while I'm working on it.  my Xorg.log shows this: 

```
(II) intel(0): Output TV disconnected
(II) intel(0): EDID for output TV
(II) intel(0): Output VGA disconnected
(II) intel(0): EDID for output VGA
(II) intel(0): Output LVDS connected
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID for output LVDS
(II) intel(0): Manufacturer: SEC  Model: 3445  Serial#: 0
(II) intel(0): Year: 2005  Week: 0
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max H-Image Size [cm]: horiz.: 33  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) intel(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) intel(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(II) intel(0):  SAMSUNG
(II) intel(0):  LTN154X3-L03
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff004ca3453400000000
(II) intel(0): 	000f0103802115780a87f594574f8c27
(II) intel(0): 	27505400000001010101010101010101
(II) intel(0): 	010101010101ee1a0080502010301030
(II) intel(0): 	13004bcf100000190000000f00000000
(II) intel(0): 	00000000002387026400000000fe0053
(II) intel(0): 	414d53554e470a2020202020000000fe
(II) intel(0): 	004c544e31353458332d4c30330a0065
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync
(II) intel(0): EDID vendor "SEC", prod id 13381
(II) intel(0): Not using default mode "640x350" (vrefresh out of range)
(II) intel(0): Not using default mode "640x400" (vrefresh out of range)
(II) intel(0): Not using default mode "720x400" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x960" (hsync out of range)
(II) intel(0): Not using default mode "1280x960" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "832x624" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1440x900" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Printing probed modes for output LVDS
(II) intel(0): Modeline "1280x800"x60.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) intel(0): Modeline "1280x800"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 (49.7 kHz)
(II) intel(0): Modeline "1280x768"x60.0   80.14  1280 1344 1480 1680  768 769 772 795 (47.7 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Output TV disconnected
(II) intel(0): EDID for output TV
```


Its got an intel 945GM chipset with integrated video if that helps.

I've looked around at some posts regarding dimming, and timing out of the monitor due to inactivity and had a look at some of the mentioned settings, But i'm pretty stumped on this one. Any suggestions?

---

### Post by dhaus111 on 2008-01-11
anybodies?

---

### Post by Yellow Pasque on 2008-01-12
Try this:
[http://ubuntuforums.org/showpost.php?p=4069397&postcount=2](http://ubuntuforums.org/showpost.php?p=4069397&postcount=2)

---

