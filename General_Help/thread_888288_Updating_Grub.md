---
title: "Updating Grub"
date: 2008-08-13
forum: General Help
---

### Post by Unanimated on 2008-08-13
I'm wondering how I can get an entry removed from the Grub menu. I already put # signs by the entry I don't want, but I'm wondering how I can make it official with Ubuntu, as in to get the whole "Press Escape for Menu" thing to show up.

EDIT: When I installed Ubuntu, I also had Windows XP on my computer, so it added that entry. I recently formatted the drive that XP was on, thanks to Virtualbox, and now I want Grub to look and act like XP was never there at all.

---

### Post by mb_webguy on 2008-08-13
Try typing "sudo update-grub" in the terminal.

If that doesn't work, type "gksu gedit /boot/grub/menu.lst" in the terminal and delete the XP entry.

---

### Post by Unanimated on 2008-08-13
That removed the entry from the menu, but it didn't ask me to press Escape to show the menu.

---

### Post by caljohnsmith on 2008-08-13
Just uncomment the line that says "hiddenmenu" near the top of the menu.lst file, and you will get the "press escape for menu" on startup.

---

### Post by Unanimated on 2008-08-13
I did that, and I'll try rebooting in a bit.

---

### Post by Unanimated on 2008-08-14
It booted up, but it never asked me to press Escape. It never showed Grub.

---

