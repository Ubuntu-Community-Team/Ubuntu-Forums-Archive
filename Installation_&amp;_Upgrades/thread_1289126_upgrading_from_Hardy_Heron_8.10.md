---
title: "upgrading from Hardy Heron 8.10"
date: 2009-10-12
forum: Installation &amp; Upgrades
---

### Post by perubu on 2009-10-12
Hello there,

Running on Hardy Heron 8.10 I would like to upgrade to 9.04.

I updated everything with he System / Update Manager, however it does not propose the button to upgrade.

Any suggestion on how to get the Upgrade button?

Thanks,

Père Ubu

---

### Post by taavikko on 2009-10-12
Open software-sources and check that prompt is set for "normal releases"
And then run
```
sudo aptitude update && update-manager -c
```

btw, this thread is in the wrong subforum, and i've asked the mods to move this to more appropriate subforum.

EDIT: 
Hardy = 8.04
Intrepid = 8.10
Jaunty = 9.04
Karmic = 9.10

---

### Post by perubu on 2009-10-12
Hello Taaviko,

Thank you for your quick answer, the button re-appeared, I'll run the upgrade now.

All the best,

Père Ubu

---

### Post by bapoumba on 2009-10-12
Moved to Installation & Upgrades.

---

