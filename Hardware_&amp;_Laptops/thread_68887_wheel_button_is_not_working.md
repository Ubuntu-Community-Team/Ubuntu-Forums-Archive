---
title: "wheel button is not working"
date: 2005-09-24
forum: Hardware &amp; Laptops
---

### Post by hiperactive on 2005-09-24
This is my problem: my mouse has 2 buttons and a clickable scroll wheel. I am able to use all buttons except the wheel button (the scrolling function is working fine).

Here is my  /etc/X11/xorg.conf

```
Section "InputDevice"
Identifier "Configured Mouse"
Driver  "mouse"
Option  "CorePointer"
Option  "Device"  "/dev/input/mice"
Option  "Protocol"  "ImPS/2"
Option  "ZAxisMapping"  "4 5"
EndSection
```

After reading some posts, I have already tried this and did not succeed:
-$ sudo dpkg-reconfigure xserver-xorg
-adding Option  "Emulate3Buttons" "true"
-adding Option  "Emulate3Buttons" "false"
-changing protocol to ExplorerPS/2
It all gives me the same results on xev: button 1,3,4,5 are working but not the wheel button (button 2).

Any help?? Thanks in advance.

EDIT: Sorry, missed the right forum  ](*,)  ](*,)  ](*,)  I dont know how to delete this thread, sorry again

---

### Post by graigsmith on 2005-09-25
try this.  comment the one commands out with the # symbol, just like. i showed below.
```
	#Option		"Protocol"		"ImPS/2"
	#Option		"Emulate3Buttons"	"true"
	#Option		"ZAxisMapping"		"4 5"
	Option "Protocol" "ExplorerPS/2"
	Option "Buttons" "7"
	Option "ZAxisMapping" "4 5"
``` 

those 3 options should enable all the good stuff.  works great on my logitech mouse.

---

