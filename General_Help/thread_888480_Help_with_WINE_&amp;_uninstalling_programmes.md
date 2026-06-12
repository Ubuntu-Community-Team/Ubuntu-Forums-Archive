---
title: "Help with WINE &amp; uninstalling programmes"
date: 2008-08-13
forum: General Help
---

### Post by Fabs1980 on 2008-08-13
I recently uploaded WINE so I could use a multi diary programme that is only available for work.

Stupidly I installed iTunes and QuickTime and it has seriously messed up my system. As well as not being able to play anything in all my linux media players (they all crash now!) I cannot uninstall iTunes and Quicktime - each time I try to uninstall it ends up installing!!!!

Please let me know I can permanently delete these programmes and hopefully restore my linux system :(

thanks

---

### Post by /////// on 2008-08-13
Uninstall WINE,
Go to terminal and type: sudo apt-get remove wine
Then delete the .wine directory (Go to /home/username, enable show hidden files (CTRL+H) and delete the .wine directory)
Reinstall wine (sudo apt-get install wine)

---

### Post by conanrealm on 2008-08-13
Also you can remove itunes and quicktime entries from the menu, go to /home/"user"/.local/share/applications/wine/ and delete the folders you don't want to appear on the menu

---

