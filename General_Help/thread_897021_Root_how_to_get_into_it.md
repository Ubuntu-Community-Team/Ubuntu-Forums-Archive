---
title: "Root? how to get into it?"
date: 2008-08-21
forum: General Help
---

### Post by Rickyk on 2008-08-21
umm now i changed to one of the new fonts in gimp and used it in a picture and saved it now all the text is that font. firefox. pidgin chats.
> **Cheesehead said:**
> As a user you don't have permission to tinker with the /usr/share/fonts folder.

You can do it as an admin, but there's an even better way - the right way.

THE RIGHT WAY FOR A USER (easiest):
1) Create a new folder called '.fonts' in your home directory. No sudo or root or special commands needed
2) Put the fonts in.
3) Quit and restart GIMP, and fonts from BOTH folders (/usr/share/fonts and /home/USER/.fonts) should be automatically loaded.
One big advantage of this method is that your normal /home backups will backup the fonts, too. You won't lose the fonts if you ever lose your system.

THE RIGHT WAY FOR AN ADMIN:
This method really only makes sense for a multi-user system. The admin (you) puts the fonts in the /usr/share/fonts folder.
1) Open a file manager with admin permissions. If you use Nautilus, the command is 'gksudo nautilus'
2) Move the fonts.
3) Close the window when finished - it has admin permissions.

---

### Post by Cheesehead on 2008-08-21
As a user you don't have permission to tinker with the /usr/share/fonts folder.

You can do it as an admin, but there's an even better way - the right way.

THE RIGHT WAY FOR A USER (easiest):
1) Create a new folder called '.fonts' in your home directory. No sudo or root or special commands needed
2) Put the fonts in.
3) Quit and restart GIMP, and fonts from BOTH folders (/usr/share/fonts and /home/USER/.fonts) should be automatically loaded.
One big advantage of this method is that your normal /home backups will backup the fonts, too. You won't lose the fonts if you ever lose your system.

THE RIGHT WAY FOR AN ADMIN:
This method really only makes sense for a multi-user system. The admin (you) puts the fonts in the /usr/share/fonts folder.
1) Open a file manager with admin permissions. If you use Nautilus, the command is 'gksudo nautilus'
2) Move the fonts.
3) Close the window when finished - it has admin permissions.

---

### Post by Sycron on 2008-08-21
try with ***sudo*** or ***gksudo***

---

### Post by Catalyst2Death on 2008-08-21
You should post a link to the tutorial your using so that we can see what exactly your trying to do.  You're description of whats going on is confusing.

You should *not* need to switch to the root account.  If you do, be *extremely* careful.  If you mess something up on the root account, you could end up needing to reformat your hard drive to fix it.  (worst case scenario)  BE CAREFUL!

---

### Post by Rickyk on 2008-08-21
i am trying to add new fonts i downloaded to the program GIMP on ubuntu 8.04

---

### Post by Rickyk on 2008-08-21
> **Cheesehead said:**
> As a user you don't have permission to tinker with the /usr/share/fonts folder.

You can do it as an admin, but there's an even better way - the right way.

THE RIGHT WAY FOR A USER (easiest):
1) Create a new folder called '.fonts' in your home directory. No sudo or root or special commands needed
2) Put the fonts in.
3) Quit and restart GIMP, and fonts from BOTH folders (/usr/share/fonts and /home/USER/.fonts) should be automatically loaded.
One big advantage of this method is that your normal /home backups will backup the fonts, too. You won't lose the fonts if you ever lose your system.

THE RIGHT WAY FOR AN ADMIN:
This method really only makes sense for a multi-user system. The admin (you) puts the fonts in the /usr/share/fonts folder.
1) Open a file manager with admin permissions. If you use Nautilus, the command is 'gksudo nautilus'
2) Move the fonts.
3) Close the window when finished - it has admin permissions.



This worked PERFECTLY Thanks:guitar::guitar:

---

