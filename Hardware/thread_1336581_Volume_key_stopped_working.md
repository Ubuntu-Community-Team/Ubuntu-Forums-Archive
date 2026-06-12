---
title: "Volume key stopped working"
date: 2009-11-24
forum: Hardware
---

### Post by jrop on 2009-11-24
Help! Yesterday I installed and then uninstalled ubuntustudio, and now my volume keys don't work anymore.  I can still see the balloon in the upper-right hand corner of the desktop showing that the volume should be changing but it doesn't seem to be setting the volume right.

---

### Post by jrop on 2009-11-24
Okay, it works now.  I just needed to delete these folders:

.gconf
.gconfd
.gnome
.gnome2
.gnome2_private

I think I finally get it now: everything in Linux is a config file; if programs get messed up, delete the config file.  I know this isn't always true, but if you're a noob like me, maybe it'll help.

---

