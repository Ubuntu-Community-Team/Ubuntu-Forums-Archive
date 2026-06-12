---
title: "Display Shifted 4 Pixels to Right (Portege 3500)"
date: 2005-09-07
forum: Hardware &amp; Laptops
---

### Post by chuvisco on 2005-09-07
After installing Ubuntu on a Toshiba Portege 3500, the display is shifted 4 pixels to the right.  So there is a black column on the left (4 pixels wide) and the last 4 pixels on the right are off the screen.  I've been working on this for a few days (I'm new to Linux) without success.  The graphics card is a Trident CyberALADDiN-T.  I found an option in xorg.conf called HSkew that I thought might solve my problem, but it doesn't seem to have any effect.  I've also tried reconfiguring the x-server.

The display is working well otherwise, and there is no shift or anything in Windows.  Here is part of my xorg.conf:

```
Section "Module"
 Load "bitmap"
 Load "dbe"
 Load "ddc"
 Load "dri"
 Load "extmod"
 Load "freetype"
 Load "glx"
 Load "int10"
 Load "record"
 Load "type1"
 Load "vbe"
EndSection

Section "Device"
 Identifier "Trident Microsystems CyberBlade XPAi1"
 Driver  "trident"
 BusID  "PCI:1:0:0" 
EndSection

Section "Monitor"
 Identifier "Generic Monitor"
 Option  "DPMS"
 HorizSync 28-49
 VertRefresh 43-72
EndSection

Section "Screen"
 Identifier "Default Screen"
 Device  "Trident Microsystems CyberBlade XPAi1"
 Monitor  "Generic Monitor"
 DefaultDepth 16
 SubSection "Display"
  Depth  1
  Modes  "1024x768"
 EndSubSection
 SubSection "Display"
  Depth  4
  Modes  "1024x768"
 EndSubSection
 SubSection "Display"
  Depth  8
  Modes  "1024x768"
 EndSubSection
 SubSection "Display"
  Depth  15
  Modes  "1024x768"
 EndSubSection
 SubSection "Display"
  Depth  16
  Modes  "1024x768"
 EndSubSection
 SubSection "Display"
  Depth  24
  Modes  "1024x768"
 EndSubSection
EndSection

Section "ServerLayout"
 Identifier "Default Layout"
 Screen  "Default Screen"
 InputDevice "Generic Keyboard"
 InputDevice "Configured Mouse"
 InputDevice "Synaptics Touchpad"
EndSection

Section "DRI"
 Mode 0666
EndSection
```

So does anyone have any ideas?

---

### Post by codejunkie on 2005-09-15
[QUOTE=chuvisco]After installing Ubuntu on a Toshiba Portege 3500, the display is shifted 4 pixels to the right.  So there is a black column on the left (4 pixels wide) and the last 4 pixels on the right are off the screen.  I've been working on this for a few days (I'm new to Linux) without success.  The graphics card is a Trident CyberALADDiN-T.  I found an option in xorg.conf called HSkew that I thought might solve my problem, but it doesn't seem to have any effect.  I've also tried reconfiguring the x-server.

The display is working well otherwise, and there is no shift or anything in Windows.  Here is part of my xorg.conf:

```
Section "Module"
 Load "bitmap"
 Load "dbe"
 Load "ddc"
 Load "dri"
 Load "extmod"
 Load "freetype"
 Load "glx"
 Load "int10"
 Load "record"
 Load "type1"
 Load "vbe"
EndSection

Section "Device"
 Identifier "Trident Microsystems CyberBlade XPAi1"
 Driver  "trident"
 BusID  "PCI:1:0:0" 
EndSection

Section "Monitor"
 Identifier "Generic Monitor"
 Option  "DPMS"
 HorizSync 28-49
 VertRefresh 43-72
EndSection

Section "Screen"
 Identifier "Default Screen"
 Device  "Trident Microsystems CyberBlade XPAi1"
 Monitor  "Generic Monitor"
 DefaultDepth 16
 SubSection "Display"
  Depth  1
  Modes  "1024x768"
 EndSubSection
 SubSection "Display"
  Depth  4
  Modes  "1024x768"
 EndSubSection
 SubSection "Display"
  Depth  8
  Modes  "1024x768"
 EndSubSection
 SubSection "Display"
  Depth  15
  Modes  "1024x768"
 EndSubSection
 SubSection "Display"
  Depth  16
  Modes  "1024x768"
 EndSubSection
 SubSection "Display"
  Depth  24
  Modes  "1024x768"
 EndSubSection
EndSection

Section "ServerLayout"
 Identifier "Default Layout"
 Screen  "Default Screen"
 InputDevice "Generic Keyboard"
 InputDevice "Configured Mouse"
 InputDevice "Synaptics Touchpad"
EndSection

Section "DRI"
 Mode 0666
EndSection
```

So does anyone have any ideas?[/QUOTE]
have you tried changing the driver from "trident" to "vesa" don't know for sure if this will help but vesa should work being that it's a generic driver.

---

### Post by jeremytaylor on 2005-09-15
You could try using **xvidtune** to work out a modeline that places your display in the right position...

jeremy

---

### Post by chuvisco on 2005-09-17
I tried xvidtune, but the modelines it gave me didn't seem to change anything.  I also tried the vesa driver, but then X wouldn't start at all.  I did figure out that the display corrects itself when I press [Fn][F5] (hotkey cycles through LCD > LCD + CRT > CRT).  I have played around with **vbetool vbestate restore**, but it does some weird things.

---

### Post by tuxd00d on 2006-06-18
I also have a 3500 with the image off to the right by a few pixels.  You're not going crazy.  Thanks for the fnF5 tip.

---

### Post by chuvisco on 2006-06-30
Disable display stretch in the BIOS and you will not have the shift.

---

### Post by Sefianix on 2007-11-29
I have an old Toshiba Satellite 1800-S204 and going into the BIOS and disabling "LCD display stretch" solved it for me too.  Thanks for the answer!!

---

