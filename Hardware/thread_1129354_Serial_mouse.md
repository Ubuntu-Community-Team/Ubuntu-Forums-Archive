---
title: "Serial mouse?"
date: 2009-04-18
forum: Hardware
---

### Post by B4RR13N705 on 2009-04-18
Hi, i was doing my own terminatorX turntable with a mouse. I found an old mouse, but is a serial mouse, that connects trough the serial port.
I connected to the PC but ubuntu did not reconized. Is a way to make it function, with a driver or something?

---

### Post by B4RR13N705 on 2009-04-18
I edited the /etc/X11/Xorg.conf
and i added this:

```

Section "InputDevice"
        Identifier      "Serial Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option "Device" "/dev/ttyS0"
        Option "Protocol" "auto"
        Option "ZAxisMapping" "4 5"

```

I restarted Xorg but still nothing :(
Can anybody help???

---

### Post by B4RR13N705 on 2009-05-16
I connected and reconnected the serial mouse.
I ran "dmesg" and i get this:
> 
[   30.985855] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input7

Any idea?
I will appreciate that somebody answer.

---

