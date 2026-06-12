---
title: "Icon theme troubles"
date: 2008-07-17
forum: General Help
---

### Post by namelessone on 2008-07-17
I just switched over to hardy, and for some reason whenever a select an icon theme that I installed from gnome-look, ubuntu continues to use the default theme for all the folders and a few other miscellaneous icons.

These are all icon themes that I have had no problem with before...is there some new format of making icon themes that would render older ones obsolete?

---

### Post by crossedout on 2008-07-19
Check the names of the items for which the icons are not changing.  I noticed some of the icon names have changed.  For example, the main window folder icons in nautilus are simply folder.*, whereas in feisty it was gnome-fs-directory.* (or something similar, can't remember atm).

To test the theory before hunting down all the names, just copy a strange icon, rename it to folder.* and paste it into your .icons/places folder.  Check nautilus and you should see a change.

It may take some time to hunt everything down.
Good Luck!

-Xout

---

### Post by namelessone on 2008-07-19
Thanks for the reply, crossedout. I think I see the problem now.

It appears that some of the slightly older icon themes aren't following the full GNOME standard when it comes to icon naming. I'll just have to do a bunch of linking and modifying the theme file.

---

