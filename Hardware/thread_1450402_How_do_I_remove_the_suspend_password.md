---
title: "How do I remove the suspend password?"
date: 2010-04-09
forum: Hardware
---

### Post by donpdonp on 2010-04-09
After suspending, ubuntu 9.10 asks me to login with my password.

I have unchecked all the boxes in gconf-editor for 
/apps/gnome-power-manager-lock

Yet I am still prompted for a password when coming out of suspend. 
Any ideas? Its a thinkpad R61.

---

### Post by MoarningSun on 2010-05-05
When all the settings are as they should be, try hitting ctrl+alt+delete and suspend from there. Does the lock screen still come up this way? Not all methods of suspending use the settings you mentioned.. Have you launched gconf-editor as user or as root (ie did you type sudo or gksu to launch it) ?

---

