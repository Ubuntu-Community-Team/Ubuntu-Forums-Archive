---
title: "Dekstop right click menu - openbox"
date: 2008-11-14
forum: General Help
---

### Post by mpcengineering on 2008-11-14
I have a question which hopefully wont be too hard to solve...  The final goal is to remove all right click desktop menu items under nautilus except ones which I define, losing the desktop icons is not a problem here.  Adding items is easy, nautilus-actions, but removing the items that are there by default is seemingly very far from a straight forward process.  I have no doubt there is a gconf or similar somewhere that can be edited (as far as I understand nautilus is all xml based?), but for the life of me I cannot find it and no end of searching reveals the answer.  If anyone knows something I don't on this front I would be grateful.

Otherwise the other option is to use an alternative windows manager, and to this end I have installed openbox.  Also I have added

```
<entry name="show_desktop" type="bool" value="false"></entry>
```

into ~/.gconf/apps/nautilus/preferences/%gconf.xml to disable nautilus' management of the desktop right click and icons, which works fine (with this set, nothing happens on desktop right click and there are no icons).  The problem now lies in enabling the openbox right click desktop menu with nautilus continuing to do the rest of the window management.

It looks like to do this I need to run a gnome/openbox combined session, or can I run this under a pure gnome session?  Logging in with a pure openbox session is fine, but a gnome/openbox combined session immediately fails even before the desktop is reached and kicks me back to the login screen.

So, the questions are I guess, either

- Does anyone know how to remove the default right click desktop items from the gnome desktop when managed by nautilus, or
- How do I use openbox (or an alternative for that matter) to manage only the desktop right click.

Any thoughts on this one?

---

### Post by mpcengineering on 2008-11-14
The login error which occurs when attempting to login to a combined gnome/openbox sessions is due to a reference to a file that doesnt exist...

```
/use/share/apps/kxkb/ubuntu.xmodmap
```

*locate* finds nothing when searching for the above file name

---

