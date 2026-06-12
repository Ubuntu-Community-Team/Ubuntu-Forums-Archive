---
title: "two keyboards, different layouts"
date: 2008-11-13
forum: Hardware
---

### Post by jvrodrigues on 2008-11-13
Hello.

I currently have a laptop with a portuguese keyboard layout and I'm trying to use it with a usb keyboard with usa layout

Right now, my xorg.conf has a section like this:

```
Section "InputDevice"
	Identifier	"keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"pt(basic),us(altgr-intl)"
	Option		"XkbOptions"	"grp:rshift_toggle"
EndSection
```

but when I press the right shift to to change to us layout, these three keys act strangely
1 becomes ¹
s becomes ß
d becomes ð

I discovered also that if I bring up a terminal and type
```
$ setxkbmap pt\(basic\),us\(altgr-intl\)
```
the keys go back to normal.

Is there something wrong with my xorg.conf or is this a bug?

---

