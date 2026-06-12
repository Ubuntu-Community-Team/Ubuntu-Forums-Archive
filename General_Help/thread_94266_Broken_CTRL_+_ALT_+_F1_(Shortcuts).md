---
title: "Broken CTRL + ALT + F1 (Shortcuts)"
date: 2005-11-23
forum: General Help
---

### Post by JustRandomName on 2005-11-23
Hi,

I think I have somehow broken the keyboard shortcuts for changing to consol to console
i.e.
ctrl+alt+F1

When I try the combination nothing happens, however if I am in GNOME and have the focus on a gnome-terminal and I attempt it I get some weird results.

F1 to F4 echos the alphabet starting at P e.g.

F1 = P
F2 = Q
F3 = R
F4 = S

However, the rest of the Fx's output the following to the console:

;7~

I think the solution is to delete the GNOME keyboard shortcuts file (anyone know where that is?) hoping that GNOME will just generate a new one (confirmation anyone?)

So my questions are thus;

Does anyone else know of a way to fix this?
Will the above solution work?
Where is the shortcut file, and will it automagiclly remake itself?

Thanks for your time,

---

### Post by JustRandomName on 2005-11-23
Ok, a little update

I have been searching around the interweb and I came accross someone with a similar problem, who found the problem to be in the xorg.config file.

I have had a look at the relevant section for mine, and as far as I can tell everything looks good.

Please find enclosed the relevant sections of my xorg.config.
```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbVariant"	"gb"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

```

---

### Post by Ozor Mox on 2007-10-23
Since updating to Gutsy I now have the same problem. Ctrl+Alt+Backspace still restarts the X server as normal, but Ctrl+Alt+F1-F8 no longer take me to the command line, when logged in nor from GDM.

Does anyone know how to re-enable these shortcuts?

---

