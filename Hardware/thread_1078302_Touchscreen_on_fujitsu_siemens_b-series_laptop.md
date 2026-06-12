---
title: "Touchscreen on fujitsu siemens b-series laptop"
date: 2009-02-23
forum: Hardware
---

### Post by damnedvirus on 2009-02-23
Hi, 
I'm trying to get the xserver to use the evtouch driver, for my touchscreen.

And the documentation says to put this in xorg.conf

Section "InputDevice"
    Identifier "touchscreen"
    Driver "evtouch"
    Option "Device" "/dev/input/event1"
    Option "DeviceName" "touchscreen"
    Option "MinX" "98"
    Option "MinY" "43"
    Option "MaxX" "940"
    Option "MaxY" "925"
    Option "ReportingMode" "Raw"
    Option "Emulate3Buttons"
    Option "Emulate3Timeout" "50"
    Option "SendCoreEvents" "On"
EndSection

I have done this,
But I also need to put 

InputDevice "touchscreen" "CorePointer"

in the serverlayout section, but it doesn't exist.
Does anyone know what I can do?

Thanks

---

### Post by karlitoes on 2009-03-06
Hi there,

I'm facing the same problem -- on almost the same laptop -- and I think it has to do with the newest version of the x-server system.  I am dual-booting with TinyME OS, which apparently uses an older version of x without the hardware abstraction layer (I don't know if I'm mixing metaphors here so bear with me).  With HAL, there are some elements of xorg.conf that are ignored, having been configured in the background by HAL.  I haven't figured out yet how to outsmart the HAL.  Under TinyME, I can get the touchscreen working just fine...(but I haven't yet gotten an on-screen keyboard working).

So, I don't have a solution but maybe this gives you or someone a clue as to next step...

Karl

---

