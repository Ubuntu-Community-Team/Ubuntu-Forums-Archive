---
title: "MX700 Scroll up Problem"
date: 2008-03-10
forum: Hardware &amp; Laptops
---

### Post by pbbd86 on 2008-03-10
I have a MX700 (USB) mouse and I am trying to get the buttons to work. The side buttons go back and forward. And the button (for scroll down works), but the scrollup button goes back a page. Can anyone help?

Here is what my xorg.conf file has


Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "Protocol" "ExplorerPS/2"
Option "Dev Name" "Logitech USB Receiver"
Option "Dev Phys" "0000:00:02.0-1/input0"
Option "Device" "/dev/input/mice"
Option "Buttons" "10"
Option "ZAxisMapping" "4 5"
Option "ButtonMapping" "1 2 3 6 7 "
Option "Resolution" "800"
EndSection 

Thanks

---

