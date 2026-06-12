---
title: "wine help"
date: 2008-09-23
forum: General Help
---

### Post by guest_user on 2008-09-23
I installed quicktime 7.5.5 with wine and when I try to uninstall it, it crashes so I uninstalled wine altogether and removed ~/.wine folder manually but there's still this apple-update menu item which I can't delete by editing the menu, how do I solve this? I want my system with everything restored with wine but without the apple software and quicktime.

---

### Post by guest_user on 2008-09-23
ok so I reinstalled wine and it turns out that quicktime and apple update isn't in the list of installed software, the problem is that in the menu when I go wine>Programs, I get an option for quicktime and apple update, how do I remove it? Deleting them by editing the menu does not work. I want to revert the settings to when wine was first installed.

---

### Post by kokkus on 2008-09-23
Try this in terminal:
nautilus ~/.local/share/applications/wine

and

nautilus ~/.local/share/desktop-directories

---

### Post by guest_user on 2008-09-23
ok I deleted the quicktime files in those places as well as similar places in the .local directory, and it worked so I guess that reverts everything back to normal huh?

btw, what do the files in those directories represent, the options in the menu?

---

