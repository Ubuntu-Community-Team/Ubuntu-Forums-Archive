---
title: "Can't seem to reinstall config file with apt-get"
date: 2009-02-09
forum: Installation &amp; Upgrades
---

### Post by gene02 on 2009-02-09
I've been trying to re-install the gdm package to get everything back to its original configuration before I messed with it.  Unfortunately, apt doesn't seem to want to do this.  I tried **sudo apt-get --reinstall install gdm**, and it looks like it runs, but the config files are not refreshed.  I even tried removing gdm.conf, but it still wasn't replaced.  I also tried **wajig reconfigure gdm** and **wajig fix-configure gdm** all with no luck.

Does anyone know how to force apt-get to replace/reinstall the original configure files for a package?

Thanks

---

### Post by Partyboi2 on 2009-02-09
You could try removing  gdm and its config files then reinstalling the package.
```
sudo apt-get --purge remove gdm
```
then install gdm and the other packages that were also uninstalled when gdm was purged.
```
sudo apt-get install ubuntu-desktop
```

---

### Post by gene02 on 2009-02-11
Thanks for the reply, but is there something wrong that I'm doing with apt-get?  gdm is just an example here, what if this was a package with loads of dependents that I would be unable to remove without trashing half of my install?

---

