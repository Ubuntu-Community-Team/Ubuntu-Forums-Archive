---
title: "dual monitors, Microtouch touchscreens with Ubuntu 9.04"
date: 2010-03-21
forum: Hardware
---

### Post by grackleman on 2010-03-21
Hi

I haven't bothered with the Microtouch MT7build5 software. I found that if the touchscreens are calibrated with the Microtouch software in windows or Ubuntu 8.04 then they work perfectly with 9.04 or 9.10. Ubuntu 9.10, however, doesn't always seam to recognize both of them when you boot, but does after logging out and back in. The Microtouch controller stores the calibration info in the controller itself.

Mutouch will work with serial or USB to serial converters. Converters using the Prolific Technology PL2303 chip do not need a driver installed. For serial use /dev/ttySx and for USB use /dev/ttyUSBx.

This should be added to /etc/X11/xorg.conf

For 1 monitor use:

Section "ServerLayout" 
    Identifier     "Default Layout" 
    InputDevice    "TouchScreen0" 
EndSection 
 
Section "InputDevice" 
    Identifier "TouchScreen0" 
    Driver "mutouch" 
    Option "Type" "finger" 
    Option "Device" "/dev/ttyS0" 
    Option "MinX" "0" 
    Option "MaxX" "16383" 
    Option "MinY" "16383" 
    Option "MaxY" "0" 
    Option "SendCoreEvents" "yes" 
EndSection

For 2 monitors set up in twinview or widescreen use:

Section "ServerLayout" 
    Identifier     "Default Layout" 
    InputDevice    "TouchScreen0" 
    InputDevice    "TouchScreen1" 
EndSection

Section "InputDevice" 
    Identifier "TouchScreen0" 
    Driver "mutouch" 
    Option "Type" "finger" 
    Option "Device" "/dev/ttyUSB0" 
    Option "MinX" "0" 
    Option "MaxX" "32766" 
    Option "MinY" "16383" 
    Option "MaxY" "0" 
    Option "SendCoreEvents" "yes" 
EndSection 
 
Section "InputDevice" 
    Identifier "TouchScreen1" 
    Driver "mutouch" 
    Option "Type" "finger" 
    Option "Device" "/dev/ttyUSB1" 
    Option "MinX" "-16383" 
    Option "MaxX" "16383" 
    Option "MinY" "16383" 
    Option "MaxY" "0" 
    Option "SendCoreEvents" "yes" 
EndSection 
 
If the xorg.conf file has a 'Server Layout' section already then just add the part about the touchscreens.

I hope this helps.

Regards
Peter

---

