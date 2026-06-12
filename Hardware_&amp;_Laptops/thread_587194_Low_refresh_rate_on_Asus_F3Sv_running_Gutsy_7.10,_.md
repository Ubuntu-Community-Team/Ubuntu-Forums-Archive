---
title: "Low refresh rate on Asus F3Sv running Gutsy 7.10, LCD Manufacturer unknown"
date: 2007-10-22
forum: Hardware &amp; Laptops
---

### Post by 0graham0 on 2007-10-22
Hi,

I've been working on an Asus F3Sv laptop with a nVIDIA GeForce 8600M GS GPU. When the computer arrived it was running vista and the refresh rate for the monitor was somewhere between 65 and 75 Hz. However in Ubuntu 7.10 I'm not sure what model monitor to enter into the Screens and Graphics config (or the xorg.conf for that matter)...the highest refresh rate I've been able to get for 1680 x 1050 is 55 Hz.

Searches for the manufacturer of the LCD screen have not been fruitful. Can anyone verify the refresh rate they receive in Vista vs. Ubuntu? Any suggestions on how to get it higher? 

PS It wouldn't be that big of a deal but this computer is intended for a friend who is unable to have a monitor with a low refresh rate  due to health problems. Any help is greatly appreciated...

---

### Post by Insightfill on 2007-10-23
Have you really checked out the LCD screen running at 55Hz?  Remember: the rules on screen refresh are different for LCD than they were for CRT.  Generally, the higher the refresh on a CRT the better, with different people having different thresholds of detection (less than 75 really bugs me and can hurt after a while.).  On an LCD, the slower repaint and the general design mean a much lower number is adequate; I've got two panels running at 60Hz all day and can't even tell.

[http://en.wikipedia.org/wiki/Refresh_rate#LCD_displays](http://en.wikipedia.org/wiki/Refresh_rate#LCD_displays)

The above article also indicates that the default refresh may vary with the OS, but if the number itself still annoys you, I suppose you could always go into the config file and just hack it to 65!

---

### Post by Fittersman on 2007-11-03
im pretty sure the max is 60 isnt it? (not between 65-75)

so, 55 isnt really that terrible, your only down 5 from what it can do (myself as well)

---

