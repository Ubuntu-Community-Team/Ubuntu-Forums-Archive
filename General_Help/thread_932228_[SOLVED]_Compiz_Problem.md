---
title: "[SOLVED] Compiz Problem"
date: 2008-09-28
forum: General Help
---

### Post by smirnoff76 on 2008-09-28
Hi All wonder if someone can help?

I have just done a clean install of my laptop and as part of that install I have installed compiz. 
I actually only want compiz for the one setting (transparent gnome menu) but the problem is that Compiz doesn't appear to load on startup.

I have also installed the Fusion Icon and have set Compiz as the window manager and then do the reload window manager setting at which point it takes me back to the GDM login screen and when I log in Compiz still aint working. 

Does anyone have any idea's as to what is causing this and what I need to do to get it going again? 

Thanks

---

### Post by ft23002 on 2008-09-28
Open: System/Preferences/Sessoins

In the Sessoins Preferences under the defualt loading tab- Startup Programs...
Click "Add"
Name: Fusion Icon
Command: fusion-icon
Comment: Load Fusion Upon Login

Click "OK"


Restart... It should now load fusion along with the icon automaticaly at login.

---

### Post by smirnoff76 on 2008-09-29
Worked a treat thanks!

---

