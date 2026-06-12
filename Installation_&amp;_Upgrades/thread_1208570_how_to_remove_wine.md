---
title: "how to remove wine"
date: 2009-07-09
forum: Installation &amp; Upgrades
---

### Post by raymondvillain on 2009-07-09
Installed wine but it didn't work.  Wanted to use a wireless network adapter.

To get rid of wine, I did:

sudo aptitude remove wine

Now when I open synaptic and search wine, all the boxes are un-checked.

But if I go to (on the taskbar) applications>wine>  etc. there are still some choices.  Is there a way to remove all of that, too?

---

### Post by ptn107 on 2009-07-09
Try:
```
sudo aptitude purge wine
```

If the entries still remain you can right-click the menu above and click 'Edit menus' and delete those entries manually.

---

### Post by raymondvillain on 2009-07-09
Thanks, ptn107.  I am going to mark this solved.

---

