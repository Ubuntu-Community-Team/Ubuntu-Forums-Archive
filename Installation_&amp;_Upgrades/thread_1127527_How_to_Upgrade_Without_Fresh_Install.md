---
title: "How to Upgrade Without Fresh Install"
date: 2009-04-16
forum: Installation &amp; Upgrades
---

### Post by rich1939 on 2009-04-16
I'm currently using Intrepid Ibex and am happy with it, except that for my current programming needs I really want to be able to use the new features in Glade that are available in the upcoming Jaunty Jackalope release.

Is there an easy procedure to upgrade to the new OS without losing my current programs and data...or do I have to do a fresh install of the new OS?

---

### Post by Therion on 2009-04-16
Once Jaunty goes final you'll be prompted to upgrade via the Update Manager. 

You can force an upgrade now if you want by using dist-upgrade:
```
sudo apt-get -u dist-upgrade
```

---

### Post by rich1939 on 2009-04-17
> **Therion said:**
> Once Jaunty goes final you'll be prompted to upgrade via the Update Manager. 

You can force an upgrade now if you want by using dist-upgrade:
```
sudo apt-get -u dist-upgrade
```

Thank you very much. I was worried that I would lose my applications and data in order to upgrade.

You guys are the best! :D

---

### Post by Slim Odds on 2009-04-17
Couple of additional comments:

1) You should still backup important files first....
2) You should do the "sudo apt-get dist-upgrade" on a fully up-to-date system.

In other words:```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```

---

