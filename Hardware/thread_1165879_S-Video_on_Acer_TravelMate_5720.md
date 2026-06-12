---
title: "S-Video on Acer TravelMate 5720"
date: 2009-05-21
forum: Hardware
---

### Post by tuxuday on 2009-05-21
Hello All,

Greetings to everyone, i am new here.

I couldn't get S-Video out working on my TravelMate 5720. I tried the options in other posts but no joy.

```

root@Linus:~# lspci -v
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
        Subsystem: Acer Incorporated [ALI] Unknown device 011f
    Flags: bus master, fast devsel, latency 0
    Memory at fc100000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: [d0] Power Management version 3

root@Linus:/etc/X11# uname -a
Linux Linus.com 2.6.24-23-generic #1 SMP Wed Apr 1 21:47:28 UTC 2009 i686 GNU/Linux
root@Linus:/etc/X11# cat /etc/issue
Ubuntu 8.04.2 \n \l


```

```

root@Linus:/etc/X11# cat xorg.conf
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
#Option          "monitor-TV"   "TV"
        Option "monitor-VGA" "VGA"
        Option "monitor-TV" "TV"
        Option "monitor-LVCD" "LVCD"
        Option "MonitorLayout" "CRT,LFP"
        Option "Clone" "true"
        Option "DevicePresence" "true"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Monitor"
        Identifier      "VGA"
        Option "Ignore" "true"
EndSection

Section "Monitor"
        Identifier      "LVCD"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "TV"
        Option  "Ignore" "false"
        Option "TV_FORMAT" "PAL"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Synaptics Touchpad"
EndSection
```

Thx.
Uday.

---

### Post by tuxuday on 2009-06-17
Hello All,

An update on getting s-video working on Hardy, Acer TravelMate 5720.

```

root@Linus:~# xrandr
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+   60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV disconnected (normal left inverted right x axis y axis)
root@Linus:~# xrandr --output TV --set load_detection 1
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  156 (RANDR)
  Minor opcode of failed request:  11 ()
  Serial number of failed request:  18
  Current serial number in output stream:  18
root@Linus:~# 

```Any clue as to why it should shout on setting the load detection? Does it mean that there is no driver support?

Thx.
Uday.

---

