---
title: "Strange modifycation of the screen resolution"
date: 2010-02-01
forum: Hardware
---

### Post by Arnaudo.M on 2010-02-01
Hello everybody,
i have installed ubuntu 9.10 on my ThinkCentre without any big problem.

The annoying thing is that if i launch Ubuntu from the live cd i can use a 1440x900 (16:9) resolution, but if i launch Ubuntu from the hard disk i have only a 800x600 (4:3) resolution, and i can not change it...

In the Lenovo ThinkCentre there is a video card Intel 946GZ, and my monitor is a Samsung SyncMaster 932mw.

Can you help me to understand why it happens and how to resolve it?

Best regards
Massimo

---

### Post by Jive Turkey on 2010-02-03
You'll need to specify the correct resolution in the Monitor section of your xorg.conf file.  Also, determine if the correct video driver is specified there.

If you post the output of this command, people will be able to give you more detailed help:

```
cat /etc/X11/xorg.conf
```

if there is a lot of text, you could limit it to just the Device, Screen, and Monitor sections of the file.

---

### Post by Arnaudo.M on 2010-02-03
Hello,
yesterday i have changed for a test, in according with [http://wiki.ubuntu-it.org/Hardware/Video/ConfigurareXorg](http://wiki.ubuntu-it.org/Hardware/Video/ConfigurareXorg) (italian version), the file. I have tested the values 1440x900 and all worked fine!
But when i rebooted i coudn't view anything...

My file is:

Section "Device"
    Identifier    "Generic Monitor"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Samsung SyncMaster 932mw"
    ModeLine    "1440x900" 106,560 1440 1520 1672 1904 900 903 909 934 -hsync +vsync
EndSection

Section "Screen"
    Identifier    "Generic Monitor"
    Monitor        "Samsung SyncMaster 932mw"
    SubSection    "Display"
    Modes        "1440x900"
    EndSubsection
EndSection

and the permission are:
ubuntu@ubuntu:~$ ls -l /media/8c6a65ed-8693-4014-99a9-c47d100d2ec8/etc/X11/xorg.conf
-rw-r--r-- 1 root root 1160 2010-02-02 21:15 /media/8c6a65ed-8693-4014-99a9-c47d100d2ec8/etc/X11/xorg.conf

Thanks in advance!

Massimo

---

### Post by Jive Turkey on 2010-02-03
Maybe change```
ModeLine "1440x900" 106,560 1440 1520 1672 1904 900 903 909 934 -hsync +vsync
```
to:```
ModeLine "1440x900"
```
There are also some notes at the bottom of the man page for the vesa driver that might help you```
man vesa
```
I also thing that```
Section "Device"
Identifier "Generic Monitor"
Driver "vesa"
EndSection
```
may be an error to have ```
Identifier "Generic Monitor"
``` in that section.  I'm not sure though.

---

### Post by Arnaudo.M on 2010-02-05
Hello,
i have resolved and now my xorg.conf is:

Section "Device"
    Identifier    "Intel 946gz"
    Driver        "intel"
EndSection

Section "Monitor"
    Identifier    "Samsung SyncMaster 932mw"
#    Modeline "1024x768"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
    Modeline "1280x720"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
EndSection

Section "Screen"
    Identifier    "Ris.1280x720"
    Device        "Intel 946gz"
    Monitor        "Samsung SyncMaster 932mw"
    SubSection    "Display"
    Modes        "1280x720"
    EndSubsection
EndSection

---

