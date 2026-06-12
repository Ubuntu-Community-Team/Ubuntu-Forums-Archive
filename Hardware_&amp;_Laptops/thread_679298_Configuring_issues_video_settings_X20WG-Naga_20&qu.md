---
title: "Configuring issues video settings X20WG-Naga 20&quot; 16:10 Wide LCD and X1950 ATI Video"
date: 2008-01-26
forum: Hardware &amp; Laptops
---

### Post by dalvon on 2008-01-26
Okay I am new to Ubuntu and linux being a windows user for years. I cannot get my video setting correct. I am not sure what to choose. So here are the specs for my monitor. 

Model
Brand SCEPTRE
Model X20WG-Naga
Cabinet Color Black
Display
Panel TFT LCD
Screen Size 20.1"
Widescreen Yes
Display Type WSXGA+
Maximum Resolution 1680 x 1050
Recommended Resolution 1680 x 1050
Viewing Angle 160°(H) / 160°(V)
Display Colors 16.2 Million
Brightness 300 cd/m2
Contrast Ratio 1000:1
Response Time 5ms (GTG)
Horizontal Refresh Rate Analog: 24kHz - 82kHz
Digital: 31kHz - 80kHz
Vertical Refresh Rate Analog: 50Hz - 75Hz
Digital: 50Hz - 75Hz
Connectivity
Input Video Compatibility Analog RGB, Digital
Connectors D-Sub, DVI
D-Sub 1
DVI 1
HDMI No
Power
Power Supply 100V - 240V AC @ 50/60 Hz
Power Consumption 80W (max.)
Convenience
User Controls Power on/off, OSD (On Screen Display), Contrast, Brightness, Clock, phase, H-Position, V-Position, H-Size, V-Size, Graph/Text Mode Selection, Auto-adjust, Color Temperature, Audio Volume, OSD H-Position, OSD V-Position, Display Mode Detection, Show Firmware Version, and Reset: Basic Setting, Position, Miscellaneous, & All Functions
Regulatory Approvals UL, FCC-B, EPA
Adjustable Stand Tilt Adjustments
Built in TV Tuner No
Built in Speakers 2W
Features •Flicker and Static Free
•PNP: DDC1/2B (Analog), DDC2B (Digital)
•Less Than VLMF Radiation Standard
•Panel & Neck detachable
•Factory presetting mode: 41
•Wall-Mount: VESA 100mm
Packaging
Package Contents X20WG-NAGA LCD Monitor
User Manual
Power Cable
VGA Cable
Audio Cable
Dimensions
Dimensions (W×H×D) 18.8" x 15.4" x 7.1"
Weight 18 lbs.
Manufacturer Warranty
Parts 1 year limited
Labor 1 year limited

[http://www.sceptre.com/Products/LCD/Specifications/spec_x20wg_Naga.htm](http://www.sceptre.com/Products/LCD/Specifications/spec_x20wg_Naga.htm)

I have a Sapphire X1950 PRO for my video card. Can anyone recommend what I should do to get these two working right in Ubuntu.

---

### Post by dalvon on 2008-01-27
I figured out my problem everything is working as it should now. I just recreated my xconf file

---

### Post by brainstuff on 2008-03-09
Hello there. I'm a Linux semin00b - had a couple of brief flings with Ubuntu, and I've just installed 7.10 on my amd64 system with x1950 (AGP) on a 20" LG L204WT monitor (1680x1050 native).  I tried installing the restricted x1950 driver that was offered... I tried doing the Synaptic install, the manual install, and the Envy install. All of them have resulted in black screen :( 

I'm guessing it's because of my monitor's resolution / refresh rates as opposed to the card itself not working, as it's similar to the problem I got with an old Thinkpad T21, where it hadn't put the correct horizontal and vertical refresh rates in during install, so I had to tweak the xorg.conf. That worked, but I don't know where to start on my desktop beastie. 

I've only succeeded in getting back to Vesa using nano from the recovery console, which made me feel fairly accomplished, but I wanna see those sexy compiz effects, and basic graphics mode really doesn't do my hardware any justice :) 

 I'll come back in a bit once I've done another Vesa reset, and post up my xorg.conf - any other bits of info useful?
cheers

---

