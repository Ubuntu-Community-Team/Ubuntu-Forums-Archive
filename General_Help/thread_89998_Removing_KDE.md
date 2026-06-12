---
title: "Removing KDE"
date: 2005-11-13
forum: General Help
---

### Post by woopud on 2005-11-13
I recently installed KDE on my Ubuntu but for some reason it really slowed down my PC.  What is the command in the terminal to remove KDE and all of it's components ?

Bert

---

### Post by adwait on 2005-11-14
```
sudo apt-get remove kubuntu-desktop
```

---

### Post by asimon on 2005-11-14
[QUOTE=adwait]```
sudo apt-get remove kubuntu-desktop
```[/QUOTE]
This will only remove the meta-package kubuntu-desktop, not all kde components on your system. kubuntu-desktop is just a package which depends on a lot of other packages to make installation of kubuntu easy. Sadly there is no easy single-command way to remove all kde packages which got installed by kubuntu-desktop.

What you can try is to remove libarts (libarts1c2) and all packages which depend on it (the easiest is to use synaptic for this). That should remove nearly all off KDE.

---

### Post by Zerocool10482 on 2005-11-14
If you use synaptic package manager. Go to the KDE section and select all of the KDE stuff. And then click uninstall.

---

### Post by matthewv on 2005-11-14
[QUOTE=Zerocool10482]If you use synaptic package manager. Go to the KDE section and select all of the KDE stuff. And then click uninstall.[/QUOTE]
Wouldn't that also remove things like kdelibs, which are required to run kde progs under gnome, e.g amarok?

---

