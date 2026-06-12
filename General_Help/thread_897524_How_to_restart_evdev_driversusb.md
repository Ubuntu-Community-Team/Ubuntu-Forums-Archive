---
title: "How to restart evdev drivers/usb"
date: 2008-08-22
forum: General Help
---

### Post by Uriziel on 2008-08-22
My mouse is broken, sometimes it's going down for a half second. On windows everything is ok. On 'mouse' drivers everything is ok. With evdev drivers after going down mouse pointer stops and I can't do anything other than restart pc. I found something like that:
```
http://ubuntuforums.org/showthread.php?t=241396
``` 
But this solutions don't work. (Second solution stops my mouse pointer too (with evdev only))

---

### Post by Uriziel on 2008-08-22
refresh

---

### Post by Uriziel on 2008-08-22
refresh

---

### Post by LateNiteTV on 2008-08-22
pleaes post the contents of xorg.conf

---

### Post by LateNiteTV on 2008-08-22
[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2007-September/001788.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2007-September/001788.html)

---

### Post by Uriziel on 2008-08-23
```
Section "InputDevice"
	Identifier	"Mouse0"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Name"	"Logitech USB Gaming Mouse"
	Option		"ZAxisMapping"	"4 5"
	Option		"YAxisMapping"	"8 9"
	Option		"Device"	"/dev/input/event2"
	Option		"Emulate3Buttons"	"false"
	Option		"SampleRate"	"1000"
EndSection
```

---

### Post by Uriziel on 2008-08-23
ref?

---

