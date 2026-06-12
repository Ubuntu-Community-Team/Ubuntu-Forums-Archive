---
title: "aiptek tablet"
date: 2005-02-20
forum: Hardware &amp; Laptops
---

### Post by pomalin on 2005-02-20
Ok,without answers in hoary section I try here,I have an usb aiptek tablet 12000U, by reading, and reading the page of the aiptek driver project on sourceforge,  I find how to configure xorg.conf to make my tablet work with appropriate coordonates,  to make my tablet work I have to put this in xorg.conf :

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "keyboard"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "fr"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "Emulate3Buttons" "true"
Option "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
Identifier "pen"
Driver "aiptek"
Option "Device" "/dev/input/event3"
Option "Type" "stylus"
Option "Mode" "absolute"
Option "Cursor" "stylus"
Option "USB" "on"
Option "KeepShape" "on"
Option "debuglevel" "20"
EndSection

Section "InputDevice"
Identifier "cursor"
Driver "aiptek"
Option "Device" "/dev/input/event3"
Option "Type" "cursor"
Option "Mode" "absolute"
Option "Cursor" "puck"
Option "USB" "on"
Option "KeepShape" "on"
Option "debuglevel" "20"
EndSection

Section "InputDevice"
Identifier "eraser"
Driver "aiptek"
Option "Device" "/dev/input/event3"
Option "Type" "eraser"
Option "Mode" "absolute"
Option "Cursor" "stylus"
Option "USB" "on"
Option "KeepShape" "on"
Option "debuglevel" "20"
EndSection
.................................................. .........................................;
Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse" "CorePointer"
InputDevice "pen" "AlwaysCore"
InputDevice "cursor" "AlwaysCore"
InputDevice "eraser" "AlwaysCore"
EndSection



But, the /dev/input/eventnumber change on boot, and X crashes often at startup, so I must, if it crash, edit /sys/bus/usb/drivers/aiptek/2-1:1.0/input_path to see what number is, and edit xorg.conf, and at last do init 1. after that X run well and my tablet to,  with pressure and all options, but, how can i get it work at each boot without editing xorg.conf each time ???

---

### Post by xphil on 2005-04-17
try something like this:


```
#!/bin/bash
aiptekpath=$( sed -n '1p'  /sys/bus/usb/drivers/aiptek/2-1\:1.0/input_path)
ln -sf $aiptekpath /dev/input/aiptektablet
``` 


this will create a symlink to the current device of the tablet
you have to edit your xorg.conf like this:

```
Option "Device" "/dev/input/aiptektablet"
``` 

to autoexecute it on boot read this:
[http://www.ubuntulinux.org/wiki/UbuntuBootupHowto](http://www.ubuntulinux.org/wiki/UbuntuBootupHowto)

i hope this will help you

ps: sorry for my bad english

---

### Post by mcmuffy on 2005-08-21
I am looking into one of these tablets. Did you get it working in the end?

---

### Post by luopio on 2006-01-24
Judging from the mailing list at aiptektablet.sf.net some people have gotten it to work. I got gaiptek (the frontend) to work, but haven't been able to compile the xdriver (the pen works partially in absolute mode, but no pressure).. 

Btw, here's a udev rule for aiptek tablets. That'll put your tablet into /dev/input/aiptektablet without much hassle.

```
$ cat /etc/udev/rules.d/aiptektablet.rules
KERNEL=="event*", SYSFS{manufacturer}="AIPTEK International Inc.", NAME="input/aiptektablet", MODE="0644"
```

---

### Post by luopio on 2006-01-29
I made a **howto** on installing the newest drivers from CVS and you can find it [here]("http://www.ubuntuforums.org/showthread.php?t=122735"). That could solve your problems (the drivers in the current kernel and xserver are heavily outdated).

---

