---
title: "How Do I Upgrade Gparted ?"
date: 2009-10-19
forum: Installation &amp; Upgrades
---

### Post by gareththomasnz on 2009-10-19
I just installed it - have used it previously but must have uninstalled.

Now my version is way out of date - how do I get the latest version installed using the command line ?

Thanks

---

### Post by stlsaint on 2009-10-19
in terminal run:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

or if your worried about upgrading your system you can download it from synaptic package manager/repos or you can do a manual install from the gparted site.

---

### Post by drs305 on 2009-10-19
Or specifically for gparted, if you mean the latest version in the repositories (main):
```

sudo apt-get update
sudo apt-get install gparted

```

---

