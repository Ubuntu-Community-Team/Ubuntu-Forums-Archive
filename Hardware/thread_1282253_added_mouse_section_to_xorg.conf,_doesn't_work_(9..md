---
title: "added mouse section to xorg.conf, doesn't work (9.04)"
date: 2009-10-04
forum: Hardware
---

### Post by stoupa on 2009-10-04
Hello,
I wanted to remap the buttons on my Evoluent mouse, so I added following section to the xorg.conf:

```

Section "InputDevice"
	Identifier 	"Configured Mouse"
	Driver 		"mouse"
	Option 		"Protocol" 		"auto"
	Option 		"Device" 		"/dev/input/mice"	
	Option		"Buttons"		"7"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"false"
	Option 		"ButtonMapping" 	"1 2 3 6 7"
EndSection

```

The problem is that this section never gets used. When i run *xev*, I still see events for buttons 8 a 9.
Does anyone have any ideas what am I doing wrong?

---

