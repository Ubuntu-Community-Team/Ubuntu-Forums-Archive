---
title: "phpmyadmin update results in blank page"
date: 2009-10-27
forum: Installation &amp; Upgrades
---

### Post by Bruce H on 2009-10-27
This morning's update to phpmyadmin breaks the configuration.

The problem is that /etc/phpmyadmin/config-db.php has the wrong permissions. To fix this, do:

sudo chmod 644 /etc/phpmyadmin/config-db.php

I don't have time to track down who is responsible for maintaining this package, so I thought to leave a quick note here.

HTH

---

### Post by twowheeler on 2009-11-19
Excellent, thank you!  This solved the problem for me.

---

