---
title: "dell mouse freezes randomly"
date: 2007-10-01
forum: Hardware &amp; Laptops
---

### Post by rodriguezmf on 2007-10-01
here are my settings, i have no idea what might be going on can anyone help?
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection
```

thanks

---

### Post by Leviel on 2007-10-19
Try the solutions [here]("http://ubuntuforums.org/showthread.php?p=3475370#post3475370") or [here]("http://swik.net/Linux/YALB/Dell+E521,+Linux,+Freezing+USB+Mouse+Problem+Resolved/uo3x") - perhaps you'll get lucky.

---

