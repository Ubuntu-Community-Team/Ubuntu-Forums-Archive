---
title: "multiple HP Pavilion ze4401us(ze4400) issues"
date: 2008-06-18
forum: Hardware
---

### Post by maaltan on 2008-06-18
I have been searching the forums and the internet for a while now trying to fix multiple issues configuring my laptop to work with Ubuntu without luck.

I am using a new install of hardy heron.

In brief these are:
[LIST=1]
[*]External monitor for ati 320m
[*]Hibernate issues
[*]shutdown issues
[*]Evolution: corrupted mbox
[/LIST]

1.  3d acceleration worked out of the box(I think) with hardy. I get about 200fps with glxgears.  (although I've read a couple of posts of people getting 600.  Is there a way to tell if acceleration is active?) compiz runs pretty well.  i get several artifacts at times, but I had to force the driver to work so i can live with that.

The biggest problem I have right now is no external monitor support. I would prefer dual but one step at a time.  In the xorg log it appears that the external monitor (1080p tv) is queried properly, but it will never enable the display.  It worked fine in windows as does the boot screens in ubuntu. I would not be opposed to having to write/run a script that changes drivers around so I can use the external display if i could find a driver that works.

here is my xorg log when i detect displays from monitor resolutions.```
enable montype: 2
enable montype: 2
enable montype: 1
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: WDE  Model: 13f6  Serial#: 0
(II) RADEON(0): Year: 2006  Week: 25
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 104  vert.: 58
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.637 redY: 0.343   greenX: 0.277 greenY: 0.611
(II) RADEON(0): blueX: 0.146 blueY: 0.062   whiteX: 0.277 whiteY: 0.292
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #2: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 148.5 MHz   Image Size:  930 x 398 mm
(II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) RADEON(0): Ranges: V min: 60  V max: 75 Hz, H min: 30  H max: 80 kHz, PixClock max 150 MHz
(II) RADEON(0): Monitor name: WESTINGHOUSE
(II) RADEON(0): Monitor name: TX-47F430S
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff005c85f61300000000
(II) RADEON(0): 	1910010308683a782a3273a357479c25
(II) RADEON(0): 	0f474aadcf008100818081c001010101
(II) RADEON(0): 	010101010101023a801871382d40582c
(II) RADEON(0): 	4500a28e3100001e000000fd003c4b1e
(II) RADEON(0): 	500f0000000000000000000000fc0057
(II) RADEON(0): 	455354494e47484f55534520000000fc
(II) RADEON(0): 	0054582d343746343330530a20200065
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "WDE", prod id 5110
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "LVDS:ddc2" removed.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: WDE  Model: 13f6  Serial#: 0
(II) RADEON(0): Year: 2006  Week: 25
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 104  vert.: 58
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.637 redY: 0.343   greenX: 0.277 greenY: 0.611
(II) RADEON(0): blueX: 0.146 blueY: 0.062   whiteX: 0.277 whiteY: 0.292
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #2: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 148.5 MHz   Image Size:  930 x 398 mm
(II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) RADEON(0): Ranges: V min: 60  V max: 75 Hz, H min: 30  H max: 80 kHz, PixClock max 150 MHz
(II) RADEON(0): Monitor name: WESTINGHOUSE
(II) RADEON(0): Monitor name: TX-47F430S
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff005c85f61300000000
(II) RADEON(0): 	1910010308683a782a3273a357479c25
(II) RADEON(0): 	0f474aadcf008100818081c001010101
(II) RADEON(0): 	010101010101023a801871382d40582c
(II) RADEON(0): 	4500a28e3100001e000000fd003c4b1e
(II) RADEON(0): 	500f0000000000000000000000fc0057
(II) RADEON(0): 	455354494e47484f55534520000000fc
(II) RADEON(0): 	0054582d343746343330530a20200065
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "WDE", prod id 5110
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "LVDS:ddc2" removed.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
```

2. I can not hibernate more than once.   The first time works.  When I restore i get a "Computer did not hibernate properly" warning about 10% of the time, even though everything seems ok.  the second time it freezes up.  There is nothing on the screen and there is nothing in the logs.

  I found a bug reported in the linux kernel that sounds EXACTLY like this.  Something about shutting down IDE channels too early when in a "restored from a power save" state.  The fix was committed to the kernel code about Jan 2008. I can't find the post again.  Assuming I can find that huge commit ID, how can I find out if this fix is in the hardy kernel.

3. Shutdown seems a bit brutal. When I logout/shutdown it seems like all programs are killed instead of being allowed to gracefully terminate. Firefox always gives me the 'last session terminated unexpectedly' dialog.  Same thing with evolution.  A Couple of other programs have lost my preference changes when i had them open when I shut down.  Is this normal behavior for Linux.  It just doesn't seem proper to me.

4:  I get a message saying something about mbox being corrupt or a bad header field.  I suspect this was caused by issue #3.  According to searching google, this issue was fixed quite a while ago. 

Let me know if you need any more logs/etc.
Thanks for your help.

---

