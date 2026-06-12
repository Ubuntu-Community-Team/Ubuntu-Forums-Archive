---
title: "[SOLVED] Egalax Touchscreen Gutsy Calibration"
date: 2008-03-18
forum: Hardware &amp; Laptops
---

### Post by treb0r on 2008-03-18
Hi All,

I have a Protouch touchscreen monitor, and I have managed to get as far as having it sense 'clicks', but not X or Y coordinates.

losource@dell-desktop:~$ grep egalax /var/log/Xorg.0.log
(II) LoadModule: "egalax"
(II) Loading /usr/lib/xorg/modules/input//egalax_drv.so
(II) Module egalax: vendor="X.Org Foundation"
(**) egalax: always reports core events
(**) egalax X device name: egalax
(**) egalaxHistroSize=10
(**) egalax associated screen: 0
(**) egalax associated screen: 0
(**) egalaxParameter=/etc/egalax.cal
(II) XINPUT: Adding extended input device "egalax" (type: egalax)

losource@dell-desktop:~$ lsusb
Bus 008 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 413c:2003 Dell Computer Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 0461:4d15 Primax Electronics, Ltd 
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

Section "InputDevice"
    Identifier "EETI"
    Driver     "egalax"
    Option     "Device"     "hiddev"
    Option     "Parameters" "/etc/egalax.cal"
    Option     "ScreenNo"   "0"
 EndSection

As you can see, the screen is visible, and accepting input (for clicks only), I just need to know how to configure the x and y axis.

Thanks in advance!

---

### Post by treb0r on 2008-03-18
Hi All,

Just so you know, I got it working by following the instructions PROPERLY!

That means that Protouch touch screens work with Ubuntu out of the box, as long as you tell them you want the Linux drivers when you purchase the screen.

[http://www.protouch.co.uk/](http://www.protouch.co.uk/)

treb0r

---

### Post by stuporglue on 2008-05-23
treb0r, 

Which directions did you follow? I've got an eGalax touchscreen I bought off ebay and am having the click-only issue you mentioned in your first post. 

Any pointers greatly appreciated. 

Thanks, 
Stuporglue

---

