---
title: "Setting up your Logitech MX500"
date: 2005-09-09
forum: Hardware &amp; Laptops
---

### Post by zurn on 2005-09-09
This tweak will get the left side buttons working

sudo gedit /etc/X11/xorg.conf

Edit the following lines:

Section "InputDevice"
Identifier"Configured Mouse"
Driver"mouse"
Option"CorePointer"
Option"Device""/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "Buttons" "7"
Option "ZAxisMapping" "4 5"
EndSection

Save the file then open Synaptic and install IMWheel.

Restart Ununtu and your good to go.

---

