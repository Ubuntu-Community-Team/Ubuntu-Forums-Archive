---
title: "up to breezy"
date: 2005-12-15
forum: Installation &amp; Upgrades
---

### Post by phil123 on 2005-12-15
ok I recently got my Breezy CD and I would like to know how to upgrade from Hoary Hedghog without erasing all my internet settings printer settings recently installed programs. I really dont want to start from scratch. That would be a real mission. maybe this question has been dealt with before.

---

### Post by mlomker on 2005-12-15
Back your important things up somewhere because upgrades aren't a sure thing, but insert the new CD and:

```

sudo apt-cdrom add
sudo apt-get update
sudo apt-get dist-upgrade

```

The same steps can be done within Synaptic.

---

