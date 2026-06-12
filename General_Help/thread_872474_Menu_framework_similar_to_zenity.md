---
title: "Menu framework similar to zenity"
date: 2008-07-28
forum: General Help
---

### Post by kriukov on 2008-07-28
I'd like to create a simple menu (specifically, a GNOME panel applet). Is there any framework already made for it, like zenity? AS far as I know, zenity can do only dialog windows and messages, not menus.

---

### Post by dexter.deepak on 2008-07-28
i never used zenity, but you can try gtk-dialog (its in the repos) or even Xdialog, to make menus.

---

### Post by kriukov on 2008-07-29
I didn't find the option to create cascading menus in zenity. Actually, what I was trying to make is an alternative Start menu. The freedesktop shortcut structure is very complicated and as I am the only user on my computer I needed something much simpler and minimalistic, yet easily manageable. After a while, I found file-browser-applet:

[http://code.google.com/p/gnome-menu-file-browser-applet/](http://code.google.com/p/gnome-menu-file-browser-applet/)

It was meant for file browsing, but I could use it as a start menu. I created a root directory for it with subdirectories and files, where files were just shell scripts for running programs -- that was what I meant to make. I just wondered if there was more standard software for this purpose.

---

