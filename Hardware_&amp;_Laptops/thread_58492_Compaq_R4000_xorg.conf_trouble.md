---
title: "Compaq R4000 xorg.conf trouble"
date: 2005-08-20
forum: Hardware &amp; Laptops
---

### Post by ltracy on 2005-08-20
I installed Ubuntu on a Compaq Presario R4000 with the fglrx ati proprietary drivers.  For some reason I have been unable to get any resolution above 1024x768, and during bootup, I can't see any console text at all.  I just get a blank screen until the login screen.  I am fairly sure the problem is in my xorg.conf.  I just used the fglrxconfig command to create a xorg.conf file, and then added a ModeLine for 1280x800.

Here is what my Xorg.0.log file is showing:  
(II) fglrx(0): Connected Display1: LCD on internal LVDS
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: LPL  Model: 0  Serial#: 0
(II) fglrx(0): Year: 2004  Week: 0
(II) fglrx(0): EDID Version: 1.2
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 33  vert.: 21
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): No DPMS capabilities specified; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.590 redY: 0.344   greenX: 0.323 greenY: 0.534
(II) fglrx(0): blueX: 0.156 blueY: 0.138   whiteX: 0.312 whiteY: 0.328
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 71.2 MHz   Image Size:  289 x 21 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) fglrx(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(II) fglrx(0):  LGPhilipsLCD
(II) fglrx(0):  LP154W01-A5
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Specified desktop setup not supported: 8
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000004
(**) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(**) fglrx(0): Center Mode is disabled
(==) fglrx(0): TMDS coherent mode is enabled
(II) fglrx(0): Total of 12 modes found for primary display.
(--) fglrx(0): Virtual size is 1024x768 (pitch 1024)
(**) fglrx(0): *Mode "1024x768": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   71.25  1024 1200 1232 1440  768 786 792 823(**) fglrx(0): *Mode "800x600": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz


I see that a lot of people around are using this laptop with the same drivers, so if somebody with this laptop could post their xorg.conf, that'd be great.  Or if someone can tell me what I'm doin wrong, that'd be just as good :).

---

### Post by alexi on 2005-08-25
I have a compaq presario r4100 with the ATI Radeon Express 200M card so hopefully this xorg.conf works for you as it did for me. I'm using kernel 2.6.11 with ATI's 8.13.6 driver. I tried their latest driver (8.16.20) but it didnt work for me. Hopes this helps...

---

### Post by azcrumpty on 2005-12-09
The ATI driver installed the 1280 modeline commented out in the file when I did it.  Perhaps you should check if you 1280 line is commented.  It did this even tho I told it I wanted 1280x800.

---

