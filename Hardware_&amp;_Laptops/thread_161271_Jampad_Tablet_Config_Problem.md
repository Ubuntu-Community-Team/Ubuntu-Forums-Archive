---
title: "Jampad Tablet Config Problem"
date: 2006-04-16
forum: Hardware &amp; Laptops
---

### Post by Rithkan on 2006-04-16
I'm trying to install a Jampad Tablet model KG-TAB1 on my machine.  The system auto-detects the tablet as a mouse but the mouse pointer will jump around if you pick up the stylus and set it down somewhere else.  I added this section to xorg.conf:

Section "InputDevice"
  Identifier "JamPad"
  Driver "js_x"
  Option "Device"   "/dev/ttyUSB0"
  Option "MaxX"  "8000"
  Option "MaxY"  "6000"
  Option "MinX"  "0"
  Option "MinY"  "0"
  Option "PressMax"  "127"
  Option "PressMin"  "0"
  Option "PressDiv"  "2"
EndSection

I also added InputDevice "JamPad" to the ServerLayout section of the file and then rebooted.
The mouse pointer still jumps if the stylus is picked up.  Does anyone know how to properly configure the pad?

---

### Post by Rithkan on 2006-04-16
Ok, I've found my main problem.  Apparently the version of Xorg I'm using doesn't have the js_x driver.  I'm currently using version 6.8.2 from February 9 2005.  Where do I download a newer version of Xorg?

---

