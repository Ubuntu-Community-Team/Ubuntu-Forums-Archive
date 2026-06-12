---
title: "How Do I Stop This From Happening?"
date: 2008-11-04
forum: General Help
---

### Post by Mark76 on 2008-11-04
Adesklets leaping to the front


Here's my openbox-session autostart file

> #!/bin/sh

eval `cat $HOME/.fehbg` &
lxpanel &
adesklets &
(sleep 10 && cairo-dock &) &
(sleep 12 && skippy &) &
(sleep 13 && xscreensaver &) &
(sleep 15 && yarssr &) &
(sleep 18 && osmo &) &
(sleep 19 && pidgin &) &
(sleep 20 && parcellite &) &
(sleep 21 && transmission &) &
(sleep 25 && seamonkey &) &
(sleep 30 && xcompmgr -n &) &


---

### Post by tonybaqain on 2008-11-04
have you tried to change the appearance visual effects to none ? if you use the normal or extra effects, since this might cause a problem to Adesklets display. if no luck, try install GDesklets instead, it is better and more customizing desklet manager.

have fun :)

---

### Post by Mark76 on 2008-11-04
Appearance visual effects? :| :?

---

### Post by tonybaqain on 2008-11-04
yes system -> preferences -> appearance

---

### Post by Mark76 on 2008-11-04
Oh that.

No. I don't use Gnome.

---

### Post by tonybaqain on 2008-11-04
I'm sorry, anyway try this command **metacity --replace** and see its effects .. but that will disable the AWM you have, which leads me to advice you to remove adesklets and install gdesklets, gdesklets works fine with any window compose like compiz and metacity.

have fun :)

---

### Post by Mark76 on 2008-11-04
Don't use Metacity either.

Openbox.

---

