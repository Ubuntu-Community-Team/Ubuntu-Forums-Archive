---
title: "downgrade from studio to normal ubuntu..."
date: 2008-07-27
forum: General Help
---

### Post by ubockto on 2008-07-27
is that possible? if so, how? downgrade from studio variant of ubuntu

---

### Post by dexter.deepak on 2008-07-27
ubuntu studio is not a kernel upgrade...so this is not a question of downgrading.
simply remove the ubuntustudio-desktop from synaptic/apt-get.
```
sudo apt-get remove --purge ubuntustudio-desktop
```

---

### Post by CatKiller on 2008-07-27
Actually, Ubuntu Studio does use a different kernel - it uses the experimental realtime kernel.

You can install the ubuntu-desktop package to get all of the packages that are in the straight install, and install the -generic kernel. Also, removing the ubuntustudio-desktop package won't remove all the audio applications (Ardour and so on) so if there are any of those that you don't want any more you can remove those packages too.

All of the components from all of the variants are pretty much interchangeable, so you can install whatever you want, and remove all the things that you don't want.

---

