---
title: "5-button USB mouse"
date: 2006-10-18
forum: Hardware &amp; Laptops
---

### Post by voided3 on 2006-10-18
Hello all. I use a USB 5-button Microsoft Intellimouse Explorer and it is recognized exactly as that in device manager, but the two side buttons are (under windows) forward and back buttons for web browsing, whereas in ubuntu they seem to function as left and right click. Is there any way I can change their functionality? Thanks!

---

### Post by xyz on 2006-10-18
How about this link?
[5-button]("http://ubuntuforums.org/archive/index.php/t-28374.html")

---

### Post by pliktrologos on 2006-11-24
I'm using this one: Microsoft 5-Button Mouse with IntelliEye (usb)

I changed the ```
/etc/X11/xorg.conf
``` section:

> Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

to this one:

> Section "InputDevice"
  Identifier "Configured Mouse"
  Driver "mouse"
  option "CorePointer"
  option "Device" "/dev/input/mice"
  option "Protocol" "ExplorerPS/2"
  option "ZAxisMapping" "4 5"
  option "ButtonMapping" "1 2 3 6 7"
  option "Emulate3Buttons" "true"
EndSection

The "4" and "5" are for the up/down scrollbar and the "6" and "7" for the back/forward buttons.
The back/forward buttons are working perfectly in my FireFox Mozilla but not in the Konqueror :-(

---

