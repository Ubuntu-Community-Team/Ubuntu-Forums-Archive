---
title: "keyboard shortcuts and the &quot;Home&quot; key on a dell 1420n"
date: 2008-02-18
forum: Hardware &amp; Laptops
---

### Post by nbubis on 2008-02-18
Hi all,

I'm having a problem with my keyboard shortcuts after upgrading to hardy.

The keyboard shortcut for my home folder used to be the "Home" button on the keyboard, and now it doesn't seem to do anything, although it does appear as "0xed".Now It also seems that changing any of the keyboard shortcuts to anything different then what they previously were has absolutely no affect.

Has anyone else experienced this? I'm not sure whether this a Xconf problem, a GNOME problem or some combo of both.

my xorg.conf:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
```


Thanks for any help,
Nathaniel

---

