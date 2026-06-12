---
title: "Logitech MX510 scroll button"
date: 2005-05-07
forum: Hardware &amp; Laptops
---

### Post by the_clown on 2005-05-07
I have a Logitech MX510 mouse.  I have installed imwheel and followed the instructions [here](http://www.ubuntulinux.org/wiki/IntellimouseMousemanBackForwardButtons).
The back and forward buttons on my mouse are working but the scroll up, cruise button, is takiing me back to previous pages.


current xorg.conf:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Buttons"	        "10"
	Option		"ZAxisMapping"		"9 10"
	Option		"Resolution"		"800"
EndSection
```

current startup script:
```
#!/bin/sh
exec xmodmap -e "pointer = 1 2 3 6 7 8 9 10 4 5" &
exec imwheel -k -b "67" &
exec $REALSTARTUP
```

---

