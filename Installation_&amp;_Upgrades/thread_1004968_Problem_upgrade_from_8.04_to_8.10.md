---
title: "Problem upgrade from 8.04 to 8.10"
date: 2008-12-07
forum: Installation &amp; Upgrades
---

### Post by GnomeMax on 2008-12-07
Upgraded from 8.04 to 8.10.  Everything appeared to happen properly, BUT - 
window title bars now lose their color and the graphics get goofed up.  You can still grab the title bar, and the min-max-close buttons are still there and active, but the icons for those buttons are mostly not there.  If I fuss with the title bar I can make it all come back, but it won't stay.  Also, the About Ubuntu Version and Release Numbers page shows "This version () was released in so its version number is ."

This looks to me like a slightly incomplete upgrade.  Any ideas on an easy fix?  Possibly a new Gnome problem?  Anybody know of a rollback function to 8.04? (ha-ha... ;-( 

And, what's with the removal of shutdown from the logout?  What's the improvement with taking something easy and adding more mouse clicks?

---

### Post by mikewhatever on 2008-12-07
This is a graphical bug related to the new compiz. There is an easy fix (or even two), don't use compiz, or change the window borders to sometthing other then default by following the steps below.

System->Preferences->Appearence, click on Customize, and switch to the Window Boarders tab, choose a different border, then save the new theme.

---

### Post by GnomeMax on 2008-12-08
Yep - changing to a custom preference appears to have fixed the window title bar problem - thanks!

---

