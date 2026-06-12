---
title: "How to uninstall software correctly?"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by okal on 2009-11-02
Hi,
ok, I'm new to ubuntu (9.04). I just want to use it to compile software and I'm using it in a virutal box on a windows system. Therefore I spend 4GB for a virtual disk (accordingly to my intense linux experiences 10 year's ago, this should be luxuary for my needs).

Concerning to this, I don't need things like OpenOffice, Gimp, Sound, Evolution, Firefox, etc..

My first attempt had been to use the package manager and mark packages I think I don't need for removal. Fortunately (I thought ^^) dependencies have been marked too, as they are not going to be needed anymore (a very good feature when consivering hundreds of packages). As you perhaps already guess from the ironic, this doesn't really work - and after uninstalling all these packages, my desktop (if we consider an empty screen with a right-click-menu as a desktop) looks pretty cleaned up.

It ends up with a completly new installation (just to feed another disussion: the costs have been the price for a commercially sold os).


Second try: a new fresh installation and I still want to get rid of OpenOffice, Gimp, Evolution, Soundsupport, Evolution.

How can I do this without blowing off my installation? (I tend not to use the graphical tool's anymore, since they seem to be somehow in unfinished alpha state and not ready to use yet).

Thanks&best regards!

---

### Post by Gorlist on 2009-11-02
Just mark the program packages for complete removal, and the package manager should do the rest. You could also try the janitor program for any unused libraries (or just do it through the manager).

Only suggestion is I wouldn't try removing evolution email as it may screw up gnome?

Perhaps try the Ubuntu minimal install cd, though you will have to install gnome desktop.

---

### Post by Soul-Sing on 2009-11-02
Tricky. 
1) Example you can uninstall evolution (meta-package), but always let evolution-data-server(-common) untouched.

---

### Post by danastasio on 2009-11-02
```
sudo apt-get purge (package name)
```

---

### Post by Soul-Sing on 2009-11-02
> **danastasio said:**
> ```
sudo apt-get purge (package name)
```

Do not recommend this with Evolution...., or you'r left with a buggy system. Again, always let evolution-data-server(-common) untouched.
So you have to take a look in synaptic package manager to uninstall Evolution...

---

### Post by NickJones on 2009-11-02
If you are running 9.10 simply go Applications, Software Centre, Installed Software, click on the software you wish to remove, then click on the arrow that appears to the right of it, then click remove, all done!
Nick

---

