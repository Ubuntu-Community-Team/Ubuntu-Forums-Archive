---
title: "Problem with Desktop effects Hardy 8.04"
date: 2008-09-21
forum: General Help
---

### Post by chanfle on 2008-09-21
hello all...
yesterday I buyed a new PC, Dell inspiron 530s, Pentium 1.8ghz dual core, 3 gigas ram, 250 hdd, Integrated Intel Graphics Media Accelerator 3100.
when i created a new user, the 2 accounts work very fine desktop effects, but when i logon with other user the desktop effects disable are disable, and I try enable and  appear me the next message: "Desktop effects could not be enable"
But with my user the effects is enable....
How i can fix this issue...???

I waiting your responses....
Regards...

---

### Post by Squish on 2008-09-21
Check restricted drivers to see if you have your proprietary video driver enabled

---

### Post by chanfle on 2008-09-21
> **Squish said:**
> Check restricted drivers to see if you have your proprietary video driver enabled

squish,
thanks for you replay....
on this moment i checked,
system >> administration >> hardware drivers
i type my password, and the little window and not appear nothing the drivers...
but with other user it's work the desktop effects

comments..???

---

### Post by Kevbert on 2008-09-21
Removed...

---

### Post by chanfle on 2008-09-21
> **Kevbert said:**
> What graphics adapter do you have ?  If it's Intel, ATI or nVidia based you can use Advanced Desktop Effects.

i have Intel adapter....but open advance desktop, i active cube effects and do not nothing

---

### Post by chanfle on 2008-09-21
any comments...????

---

### Post by chanfle on 2008-09-21
> **chanfle said:**
> any comments...????

?????????????????

---

### Post by chanfle on 2008-09-22
second call....
??????????

---

### Post by glotz on 2008-09-22
Perhaps you should start over in your native language.

---

### Post by chanfle on 2008-09-22
> **glotz said:**
> Perhaps you should start over in your native language.

So....anybody help me???

---

### Post by chanfle on 2008-09-22
hello...
this is my xorg.conf
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
```

i don't see anything about "Integrated Intel Graphics Media Accelerator 3100"
maybe this is more information about my issue....
how i can install the real intel drivers...???
thanks

---

