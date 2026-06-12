---
title: "Uninstalling Pidgin"
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by ritckare231 on 2009-02-20
Hey, beginner here. I checked several other "Solved" threads on this site but still can't get it to work. I've got a rather dated Dell Inspiron 3500 running Ubuntu 8.10, and I'm trying to uninstall Pidgin. 

I've tried sudo apt-get remove --purge pidgin and sudo apt-get remove pidgin*, tried "sudo make uninstall" but was told the rule doesn't exist. 

At this point I still have a notification that Pidgin is availible on my panel; the buddy list appears if this is clicked... and disappears before it can resolve into anything more than a white box and Pidgin icon. The pidgin folder (/usr/lib/pidgin) only has nautilis.so in it but can't be moved to trash or deleted.

Any ideas? 

[/infodump]

EDIT: Solved. The reason I couldn't delete the folder was permissions... I was logged in as root but needed to delete with "sudo" from the terminal. D'oi.

---

### Post by Partyboi2 on 2009-02-20
Press Ctrl+Alt+Backspace and log back in.

---

### Post by vginov on 2009-02-20
hi

Give a restart and try. Most of the time restart works for this kind of problems.

---

### Post by ritckare231 on 2009-02-21
> **vginov said:**
> hi

Give a restart and try. Most of the time restart works for this kind of problems.

I'd already restarted it a few times before asking here. I've also "quit" from the panel icon - it's no longer on the panel, in the menu, etc., but I still can't delete or move the pidgin folder to the trash. The entire point was to free up disk space, so I really want to get rid of that.

---

