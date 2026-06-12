---
title: "I can't change keyboard layout at startup"
date: 2009-05-30
forum: Installation &amp; Upgrades
---

### Post by PalmTXfan on 2009-05-30
_box_: [COLOR="DarkOrchid"]**netbook ASUS eee pc 2G surf (700)**[/COLOR]

I've already installed ubuntu jaunty minimal cd,
wihtout any flavour to not waste precious space (SSD has only 2G)
and from there: xorg, gdm, lxde

The netbook has US keyboard layout, but is gonna be used by an spanish girl, then she wants to be easy to use "ñÑáéíóu"

The best solution is to change layout, and works with:
```
setxkbmap us -variant intl
```
but only stay for the session :(
[U]
Now the problem[/U]:
I've changed /etc/X11/xorg.conf (it was empty)
with something like this (only to know fast+easy the change)
to login with the correct layout ...
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver	"kbd"
	Option	"CoreKeyboard"
	Option	"XkbRules"	"xorg"
	Option	"XkbModel"	"pc104"
	Option	"XkbLayout"	"es"
EndSection
```
but the keyboard layout doesn't change (i was expecting "ñ" pressing ";")

I added at start of xorg.conf the following to know if is used:
```
Section	"ServerFlags"
	Option	"DontZap"	"false"
EndSection
```and to my surprise, it works

What i am doing wrong? :(

---

