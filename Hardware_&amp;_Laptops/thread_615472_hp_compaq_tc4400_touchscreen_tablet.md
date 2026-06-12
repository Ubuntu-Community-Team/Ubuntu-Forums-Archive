---
title: "hp compaq tc4400 touchscreen tablet"
date: 2007-11-17
forum: Hardware &amp; Laptops
---

### Post by crozar on 2007-11-17
greetings , my problem is the Touch Screen , it doesnt work
its not a finger touchscreen but it must be used with a pen
its a compaq tc4400
hp , and its wacom i think,

i have installed wacom-tools and evtouch from synaptic then restarted and still didnt help

i thought wacom is very supported and touch screen these days are important like the high end cards are important for some ;)
thanks for the help.

---

### Post by popch on 2007-11-18
There is a very detailed [thread about another hp tablet PC]("http://ubuntuforums.org/showthread.php?t=563736"), the tc1100. While I do not presume that everything fits your PC, some of it just might apply.

---

### Post by Borfo on 2008-06-29
I just got a HP TC4400 to work under Hardy after a bit of fussing around...

If the output of 
```
grep -i wacom /var/log/Xorg.0.log
```
looks like

```

(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
(II) UnloadModule: "wacom"
(II) Unloading /usr/lib/xorg/modules/input//wacom_drv.so
(EE) Failed to load module "wacom" (module requirement mismatch, 0)
(EE) No Input driver matching `wacom'

```

You may need to recompile the driver (wacom_drv.so) - apparently the prebuilt version doesn't work with hardy or something.



...making the driver:  (cribbed from [this thread](http://ubuntuforums.org/showthread.php?t=765915) - just follow steps 3-7)
**3.** ```
mkdir wacom
cd wacom
```

**4.** ```
sudo apt-get update
sudo apt-get install linux-headers-`uname -r` build-essential x11proto-core-dev libxau-dev libxdmcp-dev x11proto-input-dev x11proto-kb-dev xtrans-dev libx11-dev x11proto-xext-dev libxext-dev libxi-dev linux-libc-dev libc6-dev libncurses5-dev xserver-xorg-dev tk-dev tcl-dev -y
```

**5.** ```
wget http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.0.tar.bz2
tar xjf linuxwacom-0.8.0.tar.bz2
cd linuxwacom-0.8.0
```

**6.** (this fixes some symlinks that are broken in hardy for some reason) ```
sudo ln -s /usr/include/pixman-1/pixman.h /usr/include/pixman.h
sudo ln -s /usr/include/pixman-1/pixman-version.h /usr/include/pixman-version.h
```

**7.** ```
./configure --enable-wacom
make
sudo make install
```





...then make sure your xorg.conf is set up ok...  Mine looks like this:
```

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

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom"          # SERIAL ONLY
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
  Option        "Mode"          "Absolute"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom"          # SERIAL ONLY
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
  Option        "Mode"          "Absolute"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/wacom"          # SERIAL ONLY
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
  Option        "Mode"          "Absolute"
EndSection



Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
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
        InputDevice    "stylus"    "SendCoreEvents"
        InputDevice    "eraser"    "SendCoreEvents"
        InputDevice    "cursor"    "SendCoreEvents"    # For non-LCD tablets only
EndSection


```


...then, ctrl-alt-backspace to restart X, and hopefully everything works.


#####################

if it doesn't work, make sure /dev/input/wacom is a symlink to your tablet - mine is on com 1 - /dev/ttyS0  (you could also replace /dev/input/wacom with /dev/ttyS0 so you don't have to worry about the symlink)

...to check what com port your tablet is on, you can cat ttyS0, ttyS1, ttyS2, etc, and run your pen over the tablet - if you get output, the tablet's on that com port:```
cat /dev/ttyS0
```

To get useful wacdump output you have to force wacdump into tcp mode
```
sudo wacdump -f tpc /dev/ttyS0
```
See also:
[http://linuxwacom.sourceforge.net/index.php/howto/wacdump](http://linuxwacom.sourceforge.net/index.php/howto/wacdump)




The Linux Wacom Project documentation is generally pretty good:
[http://linuxwacom.sourceforge.net/index.php/howto/main](http://linuxwacom.sourceforge.net/index.php/howto/main)

---

