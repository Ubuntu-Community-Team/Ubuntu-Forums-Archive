---
title: "change ubuntu logo"
date: 2008-10-27
forum: General Help
---

### Post by Dadsgé on 2008-10-27
hello,

i tried to change the menulogo of ubuntu into a newer, 3D logo (found it here: [http://www.gnome-look.org/content/show.php/Ubuntu-Logo?content=91593](http://www.gnome-look.org/content/show.php/Ubuntu-Logo?content=91593))
i already search the Inet, also asked it on the forum in dutch but no one seems to know how to change it... (the site i first followed: [http://ubuntuforums.org/showthread.php?t=920284](http://ubuntuforums.org/showthread.php?t=920284))

so if anyone can help me, please do so :)

greetz
D.Dadsgé

---

### Post by cdtech on 2008-10-27
**If you want to change the icons on the GNOME panel:**

You'll need to use the configuration editor. To bring up the configuration editor just type:
**gconf-editor**

If you don't have it installed just install using:
**sudo apt-get install gconf-editor**

Once the application is running, go to "apps > panel > objects" and you'll see a list of folders named something like:
menu_bar, object_0, object_2

You have one as your menu object and the rest as panel icons. The trick is to find which of these objects is the icon you want to change.

If you look in the right panel of each folder you'll see a position key. This key tells you where on the panel the icon is located in pixels.

It could be any one of them. Each folder contains a similar collection of information. Since my menu list icon is at the left side of the panel, it is the position key with the lowest number.

Click the checkbox for "use_custom_icon", then right-click on "custom_icon", select "Edit key..." and enter the full path to your chosen icon.

You may have to change the object_type from menu-bar to menu-object for the icon to work correctly.

Just type in a terminal "killall gnome-panel" to restart the panel with the changes.

---

### Post by Dadsgé on 2008-10-27
well you say it should be the one with the lowest numer
but i got 2 "0's"...
so which one of them is it?

---

### Post by Dadsgé on 2008-10-27
w8, i got a 1 and a 0
the number 0 is an action-applet...
the number 1 is a menu-object, so i suppose it should be this one?

---

### Post by cdtech on 2008-10-27
Thats correct. You can always change it back to it's default settings if its not the right one.

---

### Post by Dadsgé on 2008-10-27
owkey, i tried it and it worked  ^^
thanx

---

