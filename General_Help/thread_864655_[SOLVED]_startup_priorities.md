---
title: "[SOLVED] startup priorities"
date: 2008-07-19
forum: General Help
---

### Post by Zopiac on 2008-07-19
how do i change the order in which programs open on startup? for instance, i want gnome-do to open up first, or as soon as possible, at least.

---

### Post by Spaceman9 on 2008-07-19
Ok, I see what you're saying. There's a hard way and an easy. Easy way is run gnome-do. Click on System>Preferences>Sessions. Under Session Options click Remember Currently Running Applications. Then Log Out or Restart your computer. I don't know the hard way to do it.

---

### Post by drs305 on 2008-07-19
If gnome-do is listed in System, Preferences, Sessions, Current Sessions:

There is an Order column. From the Help page:

The Order
property specifies the order in which the session manager starts session-managed startup applications. The session manager starts applications with lower order values first. The default value is 50.

So setting an app with a low order number would start it earlier. You might then have to use the Remember Current Apps and/or make sure it is listed in the StartUp Programs window for this to stick but perhaps not.

For system commands run at boot, you would find the links in the /etc/rcX.d folders (X being a number) and set the associated S file to a lower number (such as S01samba).

Added:
How to get the order number to stick via System, Preferences, Sessions. 

The Help section seems to indicate there should be an Order box when adding apps to the Startup Programs section. At least on my 64-bit version of Hardy the only Order selection box viewable is in the Current Session tab. As a workaround, place the app in the Startup Programs window. Reboot or log out and back in, and then set the order number for the app in the Current Session tab. Make sure the tick box for 'Automatically remember running apps' is checked in Session Options or manually select the 'Remember Currently Running Applications'. The next time you boot the order number should be retained in the Current Sessions window. A lower order number starts before higher numbers.

---

