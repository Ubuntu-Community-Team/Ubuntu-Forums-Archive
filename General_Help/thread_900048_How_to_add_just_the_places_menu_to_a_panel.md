---
title: "How to add just the places menu to a panel"
date: 2008-08-24
forum: General Help
---

### Post by jmjohn on 2008-08-24
Hey all,

Does anybody know how to add just the "places" menu to the panel without all the other menus?  All the menus with their text took up too much space, so I replaced them with custom menu applets.

Preferably without the word "Places", just an icon, if anybody knows how.

Thanks much!
glass.dimly

---

### Post by pauper on 2008-08-25
Not a direct approach you're looking for, but still an option.

Add "Main Menu" applet, which is ubuntu-logo icon with a drop-down list of
"Apps..Places...System". You can clean up "Apps" and "System" with Right-click
and select "Edit Menus".

Other feasible workaround is to add "Drawer" applet, and populate it with
whatever you feel worthy: simply Right-click, select "Add to Drawer". Click on
"Custom Application..." button and type in, for example,

Name: Music
Command: nautilus /home/.../Music

(to recreate Music Bookmark folder). Then add "Show Desktop" from available 
applets, etc.

---

### Post by jmjohn on 2008-08-25
Thanks!

This would work but...

I still would like a menu with all my file bookmarks.  For instance, how would I add a new menu and then remove the "Applications" and "System" menu, leaving behind just the "Places" menu, and maybe turn it into an icon rather than a word?

thanks,
glass.dimly

---

### Post by pauper on 2008-08-25
Add "Main Menu" applet (it is just an icon with drop-down menu), Right-click
and select "Edit Menus". Now, uncheck all Applications entries, then apply the
same action for Preferences and Administration tabs from System tab (it is
sufficient to untick just the tabs and leave the entries as they are).

You will end up with Places menu, System (Help and Support, About GNOME, About
Ubuntu) and Quit.

It's likely the closest thing you can get short of touching the source code.
There is no config file for that.

---

