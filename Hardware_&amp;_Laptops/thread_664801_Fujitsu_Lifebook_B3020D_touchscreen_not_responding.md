---
title: "Fujitsu Lifebook B3020D touchscreen not responding"
date: 2008-01-11
forum: Hardware &amp; Laptops
---

### Post by 13u11fr09 on 2008-01-11
Trying to get the touchscreen working on my Fujitsu Lifebook B3020D.

I've downloaded the evtouch driver by doing:
```

sudo apt-get install xserver-xorg-input-evtouch

```
and took the udev rules from the [http://www.conan.de/]("http://www.conan.de/") site.

I then added the following to my /etc/X11/xorg.conf:
```

Section "InputDevice"
    Identifier "touchscreen"
    Driver "evtouch"
    Option "Device" "/dev/input/evtouch_event"
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

Section "InputDevice"
    Identifier "dummy"
    Driver "void"
    Option "Device" "/dev/input/mice"
EndSection

```
and to my server layout:
```

    InputDevice "touchscreen" "CorePointer"
    InputDevice "dummy"

```

After restarting the laptop, I am still not getting the touchscreen to respond...  when I run 
```

sudo cat /dev/input/evtouch_event

```
and touch the screen with my finger, I don't get a response...

I keep thinking that I must be missing something really basic so any help would really be appreciated...

---

### Post by 13u11fr09 on 2008-01-12
bump?

---

### Post by 13u11fr09 on 2008-01-12
Update:  Can anyone tell me what this means?  I'm hoping it just means I need to wait for a kernel patch and not that my touchscreen is busted...

found this message in my dmesg output:

```

[   64.620000] psmouse.c: Lifebook TouchScreen at iso0060/serio4/input0 lost synchronization, throwing 1 bytes away.

```

---

### Post by bryancoe on 2008-01-26
I just installed 7.10 on a B3020D and, after installing the evtouch package, am seeing the same line in the dmesg output, so I don't think there is any issue with your hardware.  Unfortunately I haven't been able to get it working either.

---

