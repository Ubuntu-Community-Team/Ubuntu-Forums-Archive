---
title: "[SOLVED] can't access PHP files on localhost"
date: 2008-09-07
forum: General Help
---

### Post by scragar on 2008-09-07
I've been running a local host for a while, and recently overnight it stopped serving PHP pages, and instead offers them for download. any ideas?

The machine is my desktop, and it's configured to install updates automatically.```
sudo a2enmod php5
```tells me the module is already enabled, so I can't find what the problem is, any ideas would be helpful.


EDIT: no idea why it says KDE, I selected all from the menu, go figure.

---

### Post by Rocket2DMn on 2008-09-07
Executable permissions set for World on the php files?

---

### Post by scragar on 2008-09-07
yes and no, on the files I want to edit as my normal user they are on, on phpMyAdmin they are off, but neither loads, so it can't be that(I don't think so anyway)

---

### Post by scragar on 2008-09-07
bah, problem fixed, I did a few things, one of which would have fixed it:
I stopped it, reinstall everything to do with PHP
stopped it again, since it automatcily restarted
removed then enabled the php mod
then restarted apache, and when I restarted it was working again.

---

