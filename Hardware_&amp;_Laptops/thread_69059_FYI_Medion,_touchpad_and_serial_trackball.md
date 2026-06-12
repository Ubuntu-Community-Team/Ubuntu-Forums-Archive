---
title: "FYI: Medion, touchpad and serial trackball"
date: 2005-09-25
forum: Hardware &amp; Laptops
---

### Post by mathiasv on 2005-09-25
This is only meant as information, as I am now satisfied with how my hardware works  with my Medion laptop: 
Medion
Model no.: FID 2010 Notebook pc
MD6081

I load the kernel in /boot/grub/menu.lst like this, where the nomux option is necessary for the touchpad:
```
kernel          /boot/vmlinuz-2.6.10 root=/dev/hda1 ro quiet splash i8042.nomux
```

PS/2-mouse: Without the nomux option it is only detected if plugged in after startup. With the nomux-option I could not get the PS/2-mouse to work neither in the PS/2-port nor in the serial port with an adapter. 

Logitech Trackman Marble (3 button, no wheel): With the nomux-option it works fine through an adapter in the serial port (??), but not in the PS/2 port. I did not get the middle button to work for scrolling, but I will just let it stay so. I tried several options in /etc/X11/xorg.conf but this worked, while other mentioned options prevented X (I think) from running:

```
Section "InputDevice"
        Identifier      "Serial Trackball"
        Driver          "mouse"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/ttyS0"
        Option          "Protocol"              "Microsoft"
        Option          "ZAxisMapping"          "4 5"
        Option "Buttons" "3"
EndSection

```

Hopefully this will be of benefit to someone.
Mathias

---

