---
title: "Ooops, Nautilus"
date: 2008-07-16
forum: General Help
---

### Post by Dojan5 on 2008-07-16
Ehehehe.
I tried to align my desktop icons to the right.
So I went into gconf-editor and started messing with nautilus. (apps>nautilus>desktop) and now I don't have any desktop icons at all...
Why is that? How do I fix it? And is it possible to align desktop icons to the right by default?

---

### Post by iaculallad on 2008-07-16
> **Dojan5 said:**
> Ehehehe.
I tried to align my desktop icons to the right.
So I went into gconf-editor and started messing with nautilus. (apps>nautilus>desktop) and now I don't have any desktop icons at all...
Why is that? How do I fix it? And is it possible to align desktop icons to the right by default?

Redo you're steps again, only this time, place a check mark instead of unchecking the values.

1. Press Alt+F2, run "gconf-editor"
2. Find "Apps"-->"nautilus"-->"desktop"
3. Select/Check the  box  after the "volume-visible" (To show drives),  trash_icon_visible (To show Trash icon).

If that's what you mean of getting back the icons.

---

### Post by Dojan5 on 2008-07-16
> **iaculallad said:**
> Redo you're steps again, only this time, place a check mark instead of unchecking the values.

1. Press Alt+F2, run "gconf-editor"
2. Find "Apps"-->"nautilus"-->"desktop"
3. Select/Check the  box  after the "volume-visible" (To show drives),  trash_icon_visible (To show Trash icon).

If that's what you mean of getting back the icons.

Actually I have already done that.
I also tried removing .gconf and .gconfd, but my configuration remains.
The icons disappeared when I edited conputer_icon_name and I can't get them back...
Thanks, but it didnt work.

Oh yeah, I cant even right click the desktop, but I have a wallpaper, but it cant be changed...

===EDIT===
I think when I removed the .gconf and the .gconfd file and pressed ctrl + backspace it didnt apply, but when I got my icons back by opening the trash (dont ask me) I thought that to be on the safe side I try log out and in again, but I did so normally. And then gconf was resetted...
So it is all fixed now, sorry for bothering you.

---

