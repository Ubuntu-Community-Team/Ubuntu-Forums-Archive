---
title: "keyboard layout woe"
date: 2007-11-04
forum: Hardware &amp; Laptops
---

### Post by martbab on 2007-11-04
I have also problem with my keyboard layout switching..

I'm using hp6110nx laptop with Xubuntu 7.10/WinXP

Couple of days ago my X server had some compatibility issue with graphics drivers and I had to reinstall X and gdm and generate new xorg.conf to solve the problem.

From that day I can't make my keyboard to work properly.

I previously used the us and Slovak QWERTY layout

So I tried to add Slovak QWERTY layout (sk_qwerty) to xorg.conf, nothing happened

I tried ```
setxkbmap sk_qwerty
``` but setxkbmap reported and error when loading the layout, so I had to use Slovak QWERTZ layout (sk), which is bit confusing for me.

Then I tried to add layout switching to xorg.conf, but none of the entries (like "grp:alt_shift_toggle" etc.) worked and I have to change it via setxkbmap.

this is my keyboard setup in xorg.conf

```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us,sk"
	Option		"XkbOptions" "grp:shifts_toggle,grp_led:scroll"
EndSection
 
```

I'd be happy if someone helped me solve this. :confused:

---

### Post by martbab on 2007-11-05
Anyone?

---

