---
title: "M150 Touchscreen Setup Notes"
date: 2007-07-11
forum: Hardware &amp; Laptops
---

### Post by teich on 2007-07-11
Hi,

This post is meant as helpful notes for anyone attempting to configure a 3M, M150 Touchscreen with Ubuntu 7.04.   We were recently successful after a bit of fiddling.

Start with the instructions at:
[http://stz-softwaretechnik.com/~ke/touchscreen/evtouch.html](http://stz-softwaretechnik.com/~ke/touchscreen/evtouch.html)
Then, use evtest to determine which device the touchscreen is and the min and max values.  The input device is different depending on your machine, so you will probably have to try the following and touch the screen a bit for each to see which input device it is.
> evtest /dev/input/event1
evtest /dev/input/event2
evtest /dev/input/event3
evtest /dev/input/event4
...


The InputDevice section for the touchscreen should be updated with the device, min, and max values.  Adding the line Option "TapTimer" "50" seems to make the screen respond faster.  

When a mouse is used as well, double clicks sometimes occur when they are unwanted.  To fix this, comment out the line ...
>   InputDevice "Configured Mouse"
... in Section "ServerLayout".  

Our InputDevice section in the xorg.conf file is shown below.  
> 
Section "InputDevice"
   Identifier "touchscreen"
   Driver "evtouch"
   Option "Device" "/dev/input/event3"
   Option "DeviceName" "touchscreen"
   Option "MinX" "14650"
   Option "MinY" "1930"
   Option "MaxX" "1882"
   Option "MaxY" "14500"
   Option "ReportingMode" "Raw"
#   Option "Emulate3Buttons"
#   Option "Emulate3Timeout" "50"
   Option "SendCoreEvents" "On"
   Option "TapTimer" "50"
EndSection

.. and the ServerLayout section:
> 
Section "ServerLayout"
  Identifier   "Default Layout"
  Screen  "Default Screen"
#  InputDevice "Configured Mouse"
  InputDevice "Generic Keyboard"
  InputDevice "touchscreen" "CorePointer"
  InputDevice "dummy"
EndSection 

Note that MinX and MaxX are reversed to fix the x axis inversion that occurs otherwise.

There is a virtual keyboard in ubuntu at System->Preferences->Accessibility->Assistive Technology Preferences.  However, it is fairly slow and annoying to use.  A physical keyboard is important if much typing is necessary.

There are still problems with double-tab -- the cursor sometimes flies around the screen seemingly at random.  This has not been resolved.

---

