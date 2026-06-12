---
title: "Installing External mouse on Laptop"
date: 2005-10-22
forum: Hardware &amp; Laptops
---

### Post by Frogfoot on 2005-10-22
Hi All,

Some weeks ago tried to install an External mouse on my laptop, but I do not get it to work.
Then it was on a development release of Breezer. Now I have tried it on the official release, but still it does not work.

I read /dev/input/mice receives all communication of all the mice connected to the laptop. In the xorg.conf I have set the line Protocol to auto. Also I have set in /etc/modules the line psmouse to psmouse proto=bare. But this did not work either

The specs of the laptop and the mouse:
* Compaq Armade 7400
* Logitech Trackman Marble.

Can anyone give me some guidlines how to install the external mouse? 

Already thanks

---

### Post by ranf on 2005-10-22
[QUOTE=Frogfoot]
I read /dev/input/mice receives all communication of all the mice connected to the laptop. In the xorg.conf I have set the line Protocol to auto. Also I have set in /etc/modules the line psmouse to psmouse proto=bare. But this did not work either

The specs of the laptop and the mouse:
* Compaq Armade 7400
* Logitech Trackman Marble.
[/QUOTE]
I also have a Trackman. Here are the relevant parts of my xorg.conf:
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

```
Hmm, my "protocol" option looks different from yours.

---

