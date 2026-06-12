---
title: "Logitech V270 Bluetooth Mouse Does Not Scroll"
date: 2007-04-08
forum: Hardware &amp; Laptops
---

### Post by mistermix on 2007-04-08
I am running Feisty Beta on a Dell m1210 laptop.  I was able to get a Logitech v270 Bluetooth mouse to connect without any problems, but the scroll wheel does not scroll.  Pressing on the scroll wheel is recognized as a middle button press, but that's all the scroll wheel will do.

I'm using the standard xorg.conf with the following mouse input:

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

I've tried messing around with the ZAxisMapping ("6 7", "4 5 6 7"), and that doesn't work.  When I use xev to view events, I don't see any events being generated when I turn the scroll wheel.

I also have a Belkin USB mouse with scroll wheel that scrolls fine.

Any help would be appreciated.  Thanks.

---

### Post by mistermix on 2007-04-08
The issue seems to be that the mouse is treated as a "generic" mouse after reboot or suspend/resume.

I'm able to get it to work each time by pressing reset on the mouse and issuing these commands:

hciconfig hci0 reset
hidd --search

The mouse is then picked up as a Logitech Mouse, and scrolling works.

---

### Post by cleatsupkeep on 2007-04-24
Is there a less hackish way? I mean - this works, and it's good to fidn a fix since I am having the same problem, but is there something in the xorg.conf or any other file that is predicating this behavior?

---

### Post by milanmm on 2008-01-04
I have the same problem. There has to be more elegant way how to fix it. If somebody has the Logitech V270 wheel scrolling working right after boot, please let us know.

---

