---
title: "HELP! Releasing Panel Lockdown"
date: 2008-11-05
forum: General Help
---

### Post by Hijinx on 2008-11-05
Hey everyone thanks for stopping by.  I appreciate it.

I have the mini9 preloaded with ubuntu, gnome v.2.22.2

So i was moving my panels about and switched between desktop modes a couple times.  Then my panels went put into lockdown.  No problem, i said to myself, ill just right click and uncheck the lock property.  First right click menu: nothing.  In properties i'm greeted with "some of these properties have been locked down."  Ok whatever...  Under panel orientation, i see that it has been greyed out in the standard 'clicking this wont do anything' fashion.  So ill google my problem away.  I find the global option to lock down the panels but its unchecked... hmmm...

How do i release my panels?  Update gnome? How?  Hidden option?  Where?  Help me out collective!  Show me that ubuntu is better than mac!

Im sorry if this is newb, but i post in two other sections without success and search checked three related topics without success.

Thanks for the help guys!
Hijinx

---

### Post by Franko30 on 2008-11-07
Hi,

before I found out, that using "uncheck the lock property" twice did the trick, I used "gconf-editor" to edit these properties.

gconf-editor can be used via the terminal or by making accessible via the main menu options (it is hidden by default).

In gconf-editor search for "panel" and the go to "/apps/panel/toplevel" in the results area.

Uncheck "disable_movement" in the top_panel and bottom_panel trees.

Cheers

Franko30

---

### Post by Poor Wandering One on 2009-02-17
> **Franko30 said:**
> Hi,

before I found out, that using "uncheck the lock property" twice did the trick,.

Cheers

Franko30

sorry for the noob question but where does one find this property to uncheck?

---

### Post by Franko30 on 2009-02-18
> **Poor Wandering One said:**
> sorry for the noob question but where does one find this property to uncheck?

Right mouseclick on an empty part of teh panel, disable or enable movement.

Franko30

---

