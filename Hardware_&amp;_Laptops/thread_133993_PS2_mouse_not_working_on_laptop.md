---
title: "PS2 mouse not working on laptop"
date: 2006-02-21
forum: Hardware &amp; Laptops
---

### Post by bdavids on 2006-02-21
Hi,

Installed Breezy on Compaq Presario 1800XL laptop. How do I get the PS2 or USB mouse to work instead of the touch-pad?

Thanks

---

### Post by florizs on 2006-02-21
[QUOTE=bdavids]Hi,

Installed Breezy on Compaq Presario 1800XL laptop. How do I get the PS2 or USB mouse to work instead of the touch-pad?

Thanks[/QUOTE]

you should try enabling the ps2 mouse in your XORG settings.

open a terminal

backup your xorg.conf file

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.backup

then edit your xorg.conf


sudo gedit /etc/X11/xorg.conf

look for the section InputDevice and enter this sectioni

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "Emulate3Buttons" "true"
Option "ZAxisMapping" "4 5"
EndSection

---

### Post by bdavids on 2006-02-22
Thanks Florizs, but these settings are in xorg.conf already. Any thing else I should check?
:-|

---

### Post by florizs on 2006-03-02
what kind of mouse do you have? usb or ps2?

if its an USB try typing: lsusb
and see if it shows up.

---

### Post by afx on 2006-03-06
question: what should be listed in xorg.conf if i had an usb mouse.
i used to have ps/2 one, but it seemed not to work well with touchpad (i have a portable) and it had a unusual habbit to jump around and click randomly, so i switched it with an usb model. should i change my xorg.conf because there's still an ps/2 mouse listed.

---

