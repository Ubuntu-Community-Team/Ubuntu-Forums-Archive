---
title: "Changing individual icons"
date: 2008-07-15
forum: General Help
---

### Post by StooJ on 2008-07-15
I'm a bit baffled here, I can't seem to find a tutorial or faq about how icons actually work in gnome.

I'm using buuf icons and I love the style, but there are several apps that do not have appropriate icons (pidgin, exaile, tomboy etc.)

I've found appropriate icons for some of the programmes and would like to associate them properly. I don't understand how gnome knows which icon to use, but I'm presuming symlinks are used or something.

How can I change the icon of a programme or mimetype globally? I'm looking to recreate whatever gnome does when I apply an icon pack to a theme.

Can anyone help me or point me to some documentation?

Many thanks

---

### Post by crossedout on 2008-07-19
You'll need to know the name of the icon used for each program.

Open your .icons/<theme> folder and paste the icon you want into the appropriate folder.  For example, pidgin.svg, .png would be placed in the apps folder.  As long as the icon theme you are working with is active, you should notice the change after a relog (some may be instant).
Its not an exact science but things are made easier when working with a self-installed theme rather than with one of the default themes.

-Xout

---

### Post by dangermouse28 on 2008-09-11
Check out the How-To here:

[http://ubuntuforums.org/showthread.php?t=916847](http://ubuntuforums.org/showthread.php?t=916847)

---

### Post by sayakb on 2008-09-11
Within the ~/.icons/themename/size (or /usr/share/icons/themename/size) folder, there are 
**Actions** -- Icons like standard buttons-back, delete etc.
**Apps** -- Program Icons
**Categories **-- Menu icons
**Devices -- **Device icons
**Emblems -- **Folder emblems
**Filesystems -- **Remote folder icons
**Mimetypes  **-- Format specific icons
**Status -- **Notification area icons

---

### Post by pherber12 on 2008-09-13
Did you ever figure out how to change the Tomboy Notes icon that appears in the system tray?? I was able to change the menu icon but the tray icon is still that ugly little yellow notepad.

I even changed the icons under /usr/share/icons/hicolor but that didn't do the trick either.

---

