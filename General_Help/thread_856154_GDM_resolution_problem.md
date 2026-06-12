---
title: "GDM resolution problem"
date: 2008-07-11
forum: General Help
---

### Post by spike1 on 2008-07-11
After upgrading to Hardy last week, GDM has been unable to show the full screen (only the top quarter is visible).

I can't see any of the controls, the login/password box, anything.
(this was fine before the upgrade).

I have a virtual resolution on the desktop of 2048x1536 and it looks like it's using that maximum resolution for the display, but only allowing a 640x480 viewport which can't move around with the mouse, like a normal virtual resolution on the desktop.

:confused:

I experimented with several things, even reducing the virtual resolution in xorg.conf. That brought the gdm back into line but of course, reduced my desktop size.

Is there a way to force gdm to use one screen resolution and allow my desktop to continue using the ones I prefer? Or force GSM to display things properly at the desktop resolution I specify?

Rather irritating this... Even tried editing gdm.conf to see if I could pass a different xorg.conf file to gdm, without affecting the desktop... No such luck.

Hope someone can help.
Thanks.

---

