---
title: "Manual Install of Debian Menu to Applicatioon List."
date: 2008-11-09
forum: General Help
---

### Post by EdWh on 2008-11-09
From- EdWh
Hi All, 

Need help- I have installed the Debian Menu to my 8.10 Intrepid system and find it is now a manual install.  I can locate it under Preferences, main menu bar. Opening the main panel shows, Applications with drop down of 
Accessories then debian with corresponding box to check in right pane but checking does not add it to main Apps listing. Back in main menu bar,  Clicking on Debian in drop down listing shows nothing in right pane.  
Appears it needs a launcher in property boxes and I have no idea what to use to launch the program. 
I have used this in Hardy 8.04 and it was always added to main app"s listing when installed.!!!!    Can anyone help me, please.   Thanks.    Ed.

---

### Post by Dilligaf on 2008-11-09
sudo dpkg-reconfigure menu
sudo dpkg-reconfigure menu-xdg

restart x or reboot

Mike

---

### Post by EdWh on 2008-11-09
:( Hi Mike,

From- EdWh

Your commands put a item in App's listing but clicking on, refuses to launch, Notation "could not excute chjild process.  Gnome no such file or directory!!!!!!!!!!!!    Ed.

---

### Post by EdWh on 2008-11-09
****  Hi Mike,  Went back into main menu under preferences and checked the box and put correct debian menu in applications listing o.k and it launches.                   Thanks Very Much.     Ed.****

---

