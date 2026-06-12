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

### Post by cariboo on 2009-02-09
IF you want to completely remove gdm you have to exit the desktop and stop the service, then you can completely remove it, including configuration files.

Press Ctrl-ALt-F1 to get to a prompt, enter your username and password.  At the prompt type:

```
sudo /etc/init.d/gdm stop
```

This will stop the Gnome Desktop Manager, next type:

```
sudo apt-get purge gdm
```

This will completely remove gdm and it's configuration files. Next reinstall gdm:

```
sudo apt-get install gdm
```

if gdm doesn't start on its own type:

```
sudo /etc/init.d/gdm start
```

Running the above command should put you back to the desktop.

Jim

---

