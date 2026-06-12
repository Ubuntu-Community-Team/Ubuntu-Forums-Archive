---
title: "Cairo Uninstall"
date: 2009-08-10
forum: Installation &amp; Upgrades
---

### Post by thestigmatic on 2009-08-10
I was trying to remove Cairo Dock from my machine when I encountered a bit of a snag. When using the Synaptic Package Manager, which seems to be my only viable option, I am informed that I will need to remove "ubuntu-desktop" to complete the uninstall. Needless to say, I'm a bit hesitant to comply with this request. Am going about this the right way?

---

### Post by wojox on 2009-08-10
Open a terminal:
```
sudo apt-get remove cairo-dock cairo-dock-plug-ins
```

See what that says. You don't really want to uninstall ubuntu-desktop.

---

### Post by thestigmatic on 2009-08-11
Yep. That seems to have done the trick! Thanks.

---

