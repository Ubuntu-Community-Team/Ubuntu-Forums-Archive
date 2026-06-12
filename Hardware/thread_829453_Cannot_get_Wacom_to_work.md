---
title: "Cannot get Wacom to work"
date: 2008-06-14
forum: Hardware
---

### Post by moredhel on 2008-06-14
Running on Ubuntu 8.04. I did have this working before on the same laptop on 7.10.

I've added all the necessary lines to my xorg.conf that I know. Those being:

```
Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"USB"		"on"
	Option 		"Mode" 		"Absolute"
EndSection
```

and 

```
	InputDevice     "stylus"	"SendCoreEvents"
```

to serverlayout

Is there anything more I need to do? This is a wacom volito 2 by the way (in europe only). The pen does not have an eraser or mouse etc which is why I only pu the stylus section in.

EDIT: Also, doing sudo cat /dev/s=input/wacom then moving my stylus around does make lots of stuff happen, but it also works with the dev entry "/dev/input/tablet-volito2-4x5".

Any help is /very/ appreciated.

EDIT: just to clarify, the pen does work as in responds and I can click etc, but I do not get pressure sensitivity and it is not listed as a device in gimp/inkscape/krita.

---

### Post by moredhel on 2008-06-15
bump...

---

