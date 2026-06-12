---
title: "Where can I find xserver-xorg file?  Please help."
date: 2008-09-04
forum: General Help
---

### Post by Timberwolf5578 on 2008-09-04
Could someone please help me?  My monitor is not displaying the correct resolutions and refresh rates.  I have all the information for my monitor from the manual (below), but first I need to show you what my xserver.xorg file looks like, then could someone could look at my monitor information and let me know exactly how I should edit in the xserver.xorg file?  Please help.

**Monitor Information:**

Model Name SyncMaster 997DF
Picture Tube
Type 19"(48cm) DynaFlat (45.8cm viewable)
Deflection angle 90 °
Dot Pitch 0.20mm (Horizontal)
Screen type Aluminized tri-color phosphor dot trio with black matrix.
Anti-doming invar shadow mask.
Multi-layer coated with anti-static.
Maximum Resolution
1600 X 1200@ 76Hz
Active Display
Horizontal 352 ± 3 mm
Vertical 264 ± 3 mm
Synchronization
Horizontal 30 ~ 96 kHz
Vertical 50 ~ 160 Hz
Input Signal Definition
Video Signal RGB, Analog 0.7 Vpp positive at 75 ohms
Sync Signal Separate H/V sync, TTL level, positive or negative
Display Color
Unlimited
Maximum Pixel Clock
250 MHz
Power Supply
90 ~ 264VAC rms, 60/50 Hz ± 3Hz
Power Consumption
Less than 110W
Dimensions (WxDxH)
445 x 457.5 x 416mm (After installation of Stand)
Weight
18.2 kg
Environmental considerations
Operating Temperature 32°F ~ 104°F(0°C ~ 40°C)
Humidity 10% ~ 80%, non-condensing
Storage Temperature -4°F ~113°F (-20°C ~ 45°C)
Humidity 5% ~ 95%, non-condensing
Plug and Play Capability
This monitor can be installed on any Plug & Play compatible system. Interaction of the monitor and
computer systems will provide the best operating conditions and monitor settings. In most cases,
monitor installation will proceed automatically, unless the user wishes to select alternate settings.

Table 1. Preset Timing Modes
Display Mode
Horizontal
Frequency
(kHz)
Vertical
Frequency
(Hz)
Pixel Clock
(MHz)
Sync Polarity
(H/V)
VESA, 640 x 480 37.500 75.000 31.500 -/-
VESA, 1024 x 768 68.677 84.997 94.500 +/+
VESA, 1280 x 1024 91.146 85.024 157.50 +/+

---

### Post by zxscooby on 2008-09-04
/etc/X11/xorg.conf

try reading 
```
man xorg
man xorg.conf
```

---

### Post by Timberwolf5578 on 2008-09-04
**Ok, here is my xorg.conf file:**

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

---

### Post by Timberwolf5578 on 2008-09-04
> **zxscooby said:**
> /etc/X11/xorg.conf

try reading 
```
man xorg
man xorg.conf
```

I would rather just someone please give me the lines I need, because I don't wanna mess with the file and mess it up, because then I won't have a picture.

I am sure an experienced user could figure this out in a few min and just post the answer here.  Please help.

I would like my monitor to display at 1024X768 and the highest refresh rate possible.

Thanks.

---

### Post by zxscooby on 2008-09-04
First back up your config file!
and read this
[https://help.ubuntu.com/community/FixVideoResolutionHowto?highlight=%28xorg%5C.conf%29](https://help.ubuntu.com/community/FixVideoResolutionHowto?highlight=%28xorg%5C.conf%29)

Try editing your "Monitor" section to look like this.


```
Section "Monitor"
 Identifier "Configured Monitor"
HorizSync          30-96
VertRefresh        50-160

 EndSection

```


and add this screen section directly after the monitor section.

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "SyncMaster 997DF"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1600 X 1200"
        EndSubSection
EndSection
```

---

### Post by zxscooby on 2008-09-04
for 1024X768
it would be like this.

Section "Screen"
        Identifier      "Default Screen"
        Device          "SyncMaster 997DF"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1024X768"
        EndSubSection
EndSection

---

### Post by Timberwolf5578 on 2008-09-04
Thanks for all the suggestions.  I ended up only having to adjust the resolution in Nvidia settings.  But according to the monitor information I posted, what should be the max resolution I can display at 1024X768?  Anyone know?  Cause I think WinXP used to let me go up to 100hz but Nvidia Settings is only allowing 85hz.

Also why are all my screen fonts and icons fuzzy compared to Mandriva?  Can I adjust them?

---

### Post by rossjman1 on 2008-09-04
Instead of editing the file you can run
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by russu52 on 2009-01-25
thnks for this post. i managed to arrange the extended display on  my laptop.

---

