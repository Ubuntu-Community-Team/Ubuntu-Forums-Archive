---
title: "Ati X1650pro and Ubuntu 11.04 Resolution issue."
date: 2011-05-07
forum: Hardware
---

### Post by vtepes on 2011-05-07
Hello,
I have an Ati x1650 Pro pci-e display adapter and samsung 22" monitor which is supports 1680x1050 maximum resolution. My monitor cable is 5mt. 

There was no problem until I upgraded ubuntu to 11.04. For now i can only reach maximum 1360x768 resolution. ( I see maximum 1360x768 in the "Configure Display Settings" menu)


I tried to search about this issue on this forum and the others and of course in Google but not found.

I tried to install Ati Catalyst but it says there is no more support for X cards which is unfair. 

I also tried to add this resolution by this command: 
xrandr --addmode DVI-1 1680x1050
And said: 
xrandr: cannot find mode "1680x1050"


Here is the output of the Xorg.0.log :

[    23.109] (II) RADEON(0): Not using default mode "1792x1344" (hsync out of range)
[    23.109] (II) RADEON(0): Not using default mode "896x672" (hsync out of range)
[    23.109] (II) RADEON(0): Not using default mode "1792x1344" (vrefresh out of range)
[    23.109] (II) RADEON(0): Not using default mode "896x672" (vrefresh out of range)
[    23.110] (II) RADEON(0): Not using default mode "1856x1392" (hsync out of range)
[    23.110] (II) RADEON(0): Not using default mode "928x696" (hsync out of range)
[    23.110] (II) RADEON(0): Not using default mode "1856x1392" (vrefresh out of range)
[    23.110] (II) RADEON(0): Not using default mode "928x696" (vrefresh out of range)
[    23.110] (II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
[    23.110] (II) RADEON(0): Not using default mode "960x720" (hsync out of range)
[    23.110] (II) RADEON(0): Not using default mode "1920x1440" (vrefresh out of range)
[    23.110] (II) RADEON(0): Not using default mode "960x720" (vrefresh out of range)
[    23.110] (II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
[    23.110] (II) RADEON(0): Not using default mode "416x312" (vrefresh out of range)
[    23.110] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    23.110] (II) RADEON(0): Not using default mode "576x432" (vrefresh out of range)
[    23.110] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    23.110] (II) RADEON(0): Not using default mode "576x432" (vrefresh out of range)
[    23.110] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    23.110] (II) RADEON(0): Not using default mode "576x432" (vrefresh out of range)
[    23.110] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    23.110] (II) RADEON(0): Not using default mode "576x432" (vrefresh out of range)
[    23.110] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    23.110] (II) RADEON(0): Not using default mode "576x432" (vrefresh out of range)
[    23.110] (II) RADEON(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[    23.110] (II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
[    23.110] (II) RADEON(0): Not using default mode "700x525" (hsync out of range)
[    23.110] (II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
[    23.110] (II) RADEON(0): Not using default mode "700x525" (vrefresh out of range)
[    23.110] (II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
[    23.110] (II) RADEON(0): Not using default mode "700x525" (vrefresh out of range)
[    23.110] (II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
[    23.110] (II) RADEON(0): Not using default mode "700x525" (vrefresh out of range)
[    23.110] (II) RADEON(0): Not using default mode "1440x900" (hsync out of range)
[    23.110] (II) RADEON(0): Not using default mode "720x450" (hsync out of range)
[    23.110] (II) RADEON(0): Not using default mode "1600x1024" (hsync out of range)
[    23.110] (II) RADEON(0): Not using default mode "800x512" (hsync out of range)
[    23.110] (II) RADEON(0): Not using default mode "1680x1050" (hsync out of range)
[    23.110] (II) RADEON(0): Not using default mode "840x525" (hsync out of range)
[    23.110] (II) RADEON(0): Not using default mode "1680x1050" (hsync out of range)
[    23.110] (II) RADEON(0): Not using default mode "840x525" (hsync out of range)
[    23.110] (II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
[    23.110] (II) RADEON(0): Not using default mode "840x525" (vrefresh out of range)
[    23.110] (II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
[    23.110] (II) RADEON(0): Not using default mode "840x525" (vrefresh out of range)
[    23.110] (II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
[    23.110] (II) RADEON(0): Not using default mode "840x525" (vrefresh out of range)
[    23.110] (II) RADEON(0): Not using default mode "1920x1080" (hsync out of range)
[    23.110] (II) RADEON(0): Not using default mode "960x540" (hsync out of range)
[    23.110] (II) RADEON(0): Not using default mode "1920x1200" (hsync out of range)
[    23.110] (II) RADEON(0): Not using default mode "960x600" (hsync out of range)
[    23.110] (II) RADEON(0): Not using default mode "1920x1440" (vrefresh out of range)
[    23.110] (II) RADEON(0): Not using default mode "960x720" (vrefresh out of range)
[    23.110] (II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
[    23.110] (II) RADEON(0): Not using default mode "1024x768" (hsync out of range)
[    23.110] (II) RADEON(0): Not using default mode "2048x1536" (vrefresh out of range)
[    23.110] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[    23.110] (II) RADEON(0): Not using default mode "2048x1536" (vrefresh out of range)
[    23.110] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[    23.110] (II) RADEON(0): Printing probed modes for output DVI-1
[    23.110] (II) RADEON(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    23.110] (II) RADEON(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[    23.110] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    23.110] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    23.110] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    23.110] (II) RADEON(0): Modeline "680x384"x59.8   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz)
[    23.110] (II) RADEON(0): Modeline "680x384"x60.0   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz)
[    23.110] (II) RADEON(0): Modeline "576x432"x60.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz)
[    23.110] (II) RADEON(0): Modeline "512x384"x60.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz)
[    23.110] (II) RADEON(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
[    23.110] (II) RADEON(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)

How can i reach to 1680x1050 with this card? Is it possible?
Do i need to buy a new card?

Thank you for your help.

---

