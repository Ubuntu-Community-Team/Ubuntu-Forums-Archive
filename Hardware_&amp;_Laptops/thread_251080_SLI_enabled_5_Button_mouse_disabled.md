---
title: "SLI enabled 5 Button mouse disabled"
date: 2006-09-04
forum: Hardware &amp; Laptops
---

### Post by mipstien on 2006-09-04
I finally got around to enabling SLI and it works great, except for WoW now crashes in wine but everything else runs in wine just fine....
i went to start surfing the net and my forward and back buttons aren't working in firefox now.


Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "mouse"
	Option "CorePointer"
	Option "Protocol" "ExplorerPS/2"
	Option "Emulate3Buttons"       "true"
	Option "Buttons" "7"
 	Option "ButtonMapping" "1 2 3 6 7"
EndSection

ill post my whole xorg file if you need to see it, but as i can tell everyting ELSE works fine.

---

### Post by mipstien on 2006-09-04
guess i just spoke too soon i went back through my old backup xorg files and found htis and it works

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option	   "Emulate3Buttons"	"false"
    Option	   "Buttons"		"7"
    Option	   "ButtonMapping"		"1 2 3 6 7"
EndSection

---

