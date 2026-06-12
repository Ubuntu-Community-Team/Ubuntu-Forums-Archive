---
title: "How to activate suspend to ram?"
date: 2006-06-05
forum: Hardware &amp; Laptops
---

### Post by DJ_Cyberdance on 2006-06-05
Hi! I am using Dapper Drake on a Samsung R50 notebook. The first time I booted Ubuntu I could choose between Hibernation, Suspend, Reboot and Shutdown in the System => Quit menu.

Unfortunately the Suspend button dissappeared somehow and I wonder how to get it back? The hibernation button shows up and works pretty fine.

---

### Post by .t. on 2006-06-05
Run gconf-editor, and go to apps/gnome-power-manager, and look for can_suspend. Check it.

---

### Post by DJ_Cyberdance on 2006-06-06
Great, that works! Thank you very much!

I am used to work with configuration files, does anybody know in what file this setting must be changed?

---

