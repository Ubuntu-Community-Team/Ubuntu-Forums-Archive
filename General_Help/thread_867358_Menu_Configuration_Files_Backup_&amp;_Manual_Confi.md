---
title: "Menu Configuration Files: Backup &amp; Manual Config"
date: 2008-07-22
forum: General Help
---

### Post by CarlosNYB on 2008-07-22
1) I want to be able to locate the files which store the customizations I made to the menus and panel launchers on the top bar of the Gnome desktop.

2) I want to be able to look at the categories which are associated with menu items, and the customization file used for menus, so I can edit them manually.

I've been confused by my research so far.

On the one hand there is the /usr/share/applications directory which apparently is supposed to hold the .desktop files which are launched in menus, but I can't see the categories they are associated with, I can only see what seem to be simply the launchers, I right click and see the launcher information, the command line, etc.

Then there's usr/share/desktop-directories, which seems to simply store the launchers for various menus.  usr/share//gnome-menus shows me glade. 

[http://library.gnome.org/admin/system-admin-guide/stable/menustructure-13.html.en](http://library.gnome.org/admin/system-admin-guide/stable/menustructure-13.html.en) informs me of a $XDG_CONFIG_HOME environment variable, so I'm checking that out.

The issue is, I used the main menu applet to re-arrange things nicely, and I put things on panels with separators, and I want to back it up or look at the configuration file myself.  Maybe I want to just write the XML and change some categories around.  It's not obvious where to go.  Obviously I haven't found the right place yet.

---

### Post by CarlosNYB on 2008-07-22
I answered my own question.  By showing hidden files in my home directory, I saw the .config folder, which had a menus folder in it, and there is all the stuff.

---

