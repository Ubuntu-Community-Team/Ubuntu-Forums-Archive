---
title: "Keyboard Layout Switching"
date: 2008-08-14
forum: General Help
---

### Post by Inventech on 2008-08-14
The keyboard shortcut for switching my keyboard layout isn't working. It is supposed to be switching from Englgish to Russian but it stays in English no matter what I do.

---

### Post by fridaythe14th on 2008-08-14
Yeah, it's broken I believe. I had the same problem and a bunch of other ones after "upgrading" to hardy, and I've seen other people commenting as well.

If you know what xorg.conf is you could try editing it.
If you don't I strongly suggest you don't, because it's easy to mess things up.

If you do, look for a section like this one:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection
```

and change XkbLayout from "us" to "ru" or add it if you don't have it.

**And always remember to backup xorg.conf no matter how small changes you make**

---

### Post by Archimedes0212 on 2008-08-15
as a little added measure, you may need to change the value of

Option "XkbVariant" "some_value_here"

if it still doesn't work properly after modifying xkblayout

---

