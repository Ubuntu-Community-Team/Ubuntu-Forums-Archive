---
title: "screen: black border"
date: 2006-06-30
forum: Hardware &amp; Laptops
---

### Post by thire on 2006-06-30
I installed 6.06 on my acer 630 notebook.
The starting splashscreen is nice, but then Ubuntu just uses the center of my screen and a border of 5cm stays black. If I change the resolution to a lower level, the black border gets even braoder.
Here some (relavant) content of my xorg.conf. I cannot choose the resolution "1200x900" even after restarting.

[FONT="Microsoft Sans Serif"]Section "Screen"
Identifier "Default Screen"
Device "NVIDIA Corporation NV11 [GeForce2 Go]"
Monitor "Standardbildschirm"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1200x900" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1200x900" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1200x900" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1200x900" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1200x900" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1600x1200" "1024x768" "800x600" "640x480"
EndSubSection
EndSection[/FONT]

---

