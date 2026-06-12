---
title: "Forgets my keyboard layout"
date: 2008-08-09
forum: General Help
---

### Post by Jojan on 2008-08-09
Ubuntu forgets my keyboard layout everytime I log out.

When I go to gnome-keyboard-properties it allways says the layout that I have choosen, but it does not apply it. I have to ad my layout again and remove the old one, even if they're the same. I use the regular Swedish layout.

---

### Post by svenbertil on 2008-08-09
I had the very same problem, turns out my xorg.conf was set to us layout.

This is what you do:
open a terminal window.
type:
```
sudo gedit /etc/X11/xorg.conf
```

Look for a line that says:
```
	Option		"XkbLayout"	"us"
```
It doesn't necessarily say "us", could be something else.  

Change that to:
```
	Option		"XkbLayout"	"se"
```

And you should be all set :)

---

### Post by Jojan on 2008-08-09
Tack så mycket! (Thank you very much!)

---

