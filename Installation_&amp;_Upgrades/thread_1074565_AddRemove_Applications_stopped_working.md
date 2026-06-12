---
title: "Add/Remove Applications stopped working"
date: 2009-02-19
forum: Installation &amp; Upgrades
---

### Post by noahsachs1 on 2009-02-19
In Ubuntu 8.10, the Add/Remove Applications launches but then shows no applications installed or available.  However if I go thorugh System then Administration I find that the Synaptics Package manager works. I've tried sudo apt-get update and it hasn't helped.  How do I restart the Add/Remove Applications program?

---

### Post by kostkon on 2009-02-19
> **noahsachs1 said:**
> In Ubuntu 8.10, the Add/Remove Applications launches but then shows no applications installed or available.  However if I go thorugh System then Administration I find that the Synaptics Package manager works. I've tried sudo apt-get update and it hasn't helped.  How do I restart the Add/Remove Applications program?
Go to *Synaptic*, search for the *gnome-app-install* package and mark it for reinstallation.
Or in a terminal just give
```
sudo apt-get install gnome-app-install --reinstall
```

---

