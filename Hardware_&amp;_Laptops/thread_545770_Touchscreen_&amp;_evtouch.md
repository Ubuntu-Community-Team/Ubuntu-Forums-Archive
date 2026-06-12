---
title: "Touchscreen &amp; evtouch"
date: 2007-09-08
forum: Hardware &amp; Laptops
---

### Post by phenolholic on 2007-09-08
hello. i have a problem with my touchscreen. it responds, but it doesnt work like it should. when i touch my touchscreen, it automatically positions the cursor to the center of the screen, and not where i touch. obviously, its responding to my touch, but not the correct way. my touchscreen is an eGalax touchscreen that comes with HP Pavilion TX1000 model notebooks. i linked evtouch_event in /dev/input with whichever event the touchscreen loads up on. my xorg entry for the touchscreen device is:
Section "InputDevice"
Identifier "touchscreen"
Driver "evtouch"
Option "Device" "/dev/input/evtouch_event"
Option "DeviceName" "touchscreen"
Option "MinX" "48"
Option "MinY" "110"
Option "MaxX" "4006"
Option "MaxY" "4002"
Option "x0" "-1"
Option "y0" "-3"
Option "x1" "-6"
Option "y1" "-4"
Option "x2" "-2"
Option "y2" "-6"
Option "x3" "-2"
Option "y3" "-3"
Option "x4" "-4"
Option "y4" "-3"
Option "x5" "2"
Option "y5" "-1"
Option "x6" "-5"
Option "y6" "-3"
Option "x7" "-2"
Option "y7" "1"
Option "x8" "5"
Option "y8" "2"
Option "TapTimer" "0"
Option "LongTouchTimer" "250"
Option "ReportingMode" "Raw"
Option "SendCoreEvents" "On"
EndSection


i also put the following in Section "ServerLayout"
InputDevice "touchscreen" "CorePointer"

any info would be appreciated. thanks

---

### Post by v.cecchetto on 2007-09-10
Welcome in tx1000 community! :)

You have to calibrate your touchscreen.

For this and other problem solutions related to tx1000 read this 

[http://ubuntuforums.org/showthread.php?t=442483&highlight=tx1000](http://ubuntuforums.org/showthread.php?t=442483&highlight=tx1000)

Hope you find it useful.

---

### Post by jcdx on 2007-10-14
Hi!

I have the same notebook (tx1020ea). I have also problems with the calibration. When I touch the screen, the cursor jumps to the right bottom corner. 

I am using kubuntu 7.10 with kernel 2.6.22-14 and als things are worse than before. When I now touch the screen the x-server simply crashes.

I have installed the evtouch driver from the repository and the driver is installed in 
/usr/lib/xorg/modules/input/evtouch_drv.so

I installed evtouch-0.8.0 and evtouch-0.8.7 by hand and tried the calibration as reported in 
[http://wikifisch.homelinux.org/wikifisch/index.php/Carpc#Touchscreen_Konfiguration](http://wikifisch.homelinux.org/wikifisch/index.php/Carpc#Touchscreen_Konfiguration)

but nothing works. The ev_calibrate crashes with an error.

Did you compile the evtouch and the driver by hand? Any packages I have to install or remove? 

I am really frustrated because I like the notebook and linux but I want a working touchscreen. 

Thanks you for any help!

P.S. For some reason I can not pipe within the x-server because AltGr+< does not work. Any idea about this ;)

---

