---
title: "keyboard problem"
date: 2005-06-18
forum: Hardware &amp; Laptops
---

### Post by cullan on 2005-06-18
I have a MS Digital Media Pro keyboard. When I press some of the keys they produce a different result randomly.

I opened xev to see what was happening.

The delete key alternates randomly between sending this:
keycode 51 (keysym 0x5c, backslash)
and this:
keycode 107 (keysym 0xffff, Delete)

The up arrow key:
keycode 98 (keysym 0xff52, Up)
and:
keycode 48 (keysym 0x27, apostrophe)

Left shift:
keycode 50 (keysym 0xffe1, Shift_L)
and:
keycode 164 (keysym 0x0, NoSymbol)

The other keys seem to be working fine. I tried using the USB connector and the
PS/2 adapter and the same thing happens.

Any help would be greatly appreciated.

---

### Post by Mez on 2005-06-18
can you copy and paste the section of your /etc/X11/xorg.conf that looks similar to this

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection
```

to this thread please?

---

