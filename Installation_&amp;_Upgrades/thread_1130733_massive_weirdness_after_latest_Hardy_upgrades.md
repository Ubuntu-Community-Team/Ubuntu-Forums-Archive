---
title: "massive weirdness after latest Hardy upgrades"
date: 2009-04-20
forum: Installation &amp; Upgrades
---

### Post by Aurora on 2009-04-20
Greetings,

I still run Hardy for stability and because of problems with the rt kernal in Jaunty.  After the last group of upgrades, about a week's worth, many things have broken:

*Booting takes over 10 minutes.
*Clicking the shutdown button makes the menubar disappear, without bringing up the shutdown dialog.  I have to open a terminal to turn the computer off.
*Firefox is missing all bookmarks, cannot download the bookmarks from the Xmarks server, and cannot log on to this forum.  I am using Epiphany to access this forum.
*Rosegarden won't launch--I tried reinstalling it.

Before all this happened it was mostly running well.  I did have trouble with the desktop crashing periodically, always when Firefox was running.

I am really reluctant to reinstall the whole OS.  Is there a way to troublshoot these problems, and solve them with the current installation intact?

--Paul

---

### Post by yeats on 2009-04-20
Is the previous kernel still in the grub list?  If so, can you boot into it and see if the same problems occur?  That will rule out the kernel as being the problem at least.

---

### Post by Aurora on 2009-04-20
Hi,

Well, it no longer takes ten minutes to get to the GRUB screen; that seems to have fixed itself.  Everything else is the same, even with the old kernal(xxx-22).  I notice now that the shutdown button is no longer in the panel when I boot up.  After adding it to the panel, same thing--panel goes away when I click the button. Have to use ctrl-alt-f2 or the desktop terminal icon to reboot or shutdown.

---

