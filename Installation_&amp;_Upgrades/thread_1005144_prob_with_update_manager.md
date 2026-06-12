---
title: "prob with update manager"
date: 2008-12-07
forum: Installation &amp; Upgrades
---

### Post by gdog355 on 2008-12-07
I was using update manager successfully for months, but I just tried to download a couple security updates and got a connection refused msg.
anyone have any ideas?
Thnx
George

---

### Post by mk1w86 on 2008-12-08
Open a terminal and run

```
sudo apt-get update
```

and see if that updates your package lists.

If it does run 

```
sudo apt-get dist-upgrade
```

to install any updates.

---

