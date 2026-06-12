---
title: "Having some problems with my keyboard layout"
date: 2008-08-21
forum: Hardware
---

### Post by bredin on 2008-08-21
Running ubuntu 8.04 64bit with xfce as DE on my thinkpad x61.

And I'm having problems with my keys. Like when I try to bind:
```

aumix -v+5

```
to the XF86AudioRaiser button it becomes blank. Same with the other XF86 buttons.  
But it works with like alt+a

In archlinux there were a special layout for the thinkpad60 series. And that made all hotkeys working. Media play&pause&next&previous and XF86AudioMute/Raise/Lower.

```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"thinkpad60"
	Option		"XkbLayout"	"se"
EndSection

```

Tried to use pc105 as XkbModel, didn't work. And changed layout in xfce to the thinkpad layout. And it still does not work. Worked before when I ran xfce4 with gnome installed. But now I've uninstalled gnome
```

sudo apt-get autoremove gnome*

```
So I might need a package. But what package?

And the XF86Audio button works if I have the VolumeControl in the taskbar. But I don't want it. I Want the buttons to bind directly to aumix.

---

