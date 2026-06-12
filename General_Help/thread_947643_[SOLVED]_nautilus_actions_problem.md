---
title: "[SOLVED] nautilus actions problem"
date: 2008-10-14
forum: General Help
---

### Post by giuspen on 2008-10-14
hi, I installed just today nautilus actions and it works great except for the icons that are not shown in the nautilus menu as they should.
I tried before with ".xpm" and then with ".png" icon but no result.
If anybody had the same problem and solved please tell me.
Thanks.

---

### Post by OwnSurname on 2008-11-10
Same problem here.
Icons I tried are located in /usr/share/icons/gnome/scalable/actions/<name>.svg.
Any solution is really welcome!   ^___^

---

### Post by Brucevdk on 2008-11-16
Tum tum tum....

This is GNOME Bug [#525845](http://bugzilla.gnome.org/show_bug.cgi?id=525845) also see Bug [#534622](http://bugzilla.gnome.org/show_bug.cgi?id=534622).

Use shortnames as a workaround instead (gtk-about etc.). 

You can place custom icons in ~/.icons/hicolor/scalable (SVG) or 48x48 (or any other sizes) for non-SVG icons. That'll allow you to use shortnames for those too.

---

### Post by kylea on 2009-01-08
> **Brucevdk said:**
> Tum tum tum....

This is GNOME Bug [#525845](http://bugzilla.gnome.org/show_bug.cgi?id=525845) also see Bug [#534622](http://bugzilla.gnome.org/show_bug.cgi?id=534622).

Use shortnames as a workaround instead (gtk-about etc.). 

You can place custom icons in ~/.icons/hicolor/scalable (SVG) or 48x48 (or any other sizes) for non-SVG icons. That'll allow you to use shortnames for those too.


I have found that if you place icons in this path

/home/<username>/.icons/gnome/22x22/actions

and they are .png then the nautilus right click menu will show the correct icons after restarting nautilus. The trick is that the nautilus action edit menu will **not** show the icons as it expects them to be in the current active themes directory path. You could put them there too but that would be a pain to maintain.

---

