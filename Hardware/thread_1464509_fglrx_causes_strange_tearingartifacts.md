---
title: "fglrx causes strange tearing/artifacts"
date: 2010-04-28
forum: Hardware
---

### Post by skelooth on 2010-04-28
Lucid, ATI HD 3200

Installs fine through the Restricted Drivers manager, but on reboot the system runs VERY slow, and all rendering has "scan line like" artifacts. The only way to fix it is to uninstall fglrx.

I tried the 10.3 drivers off the ATI website but x complains that it can't load the driver.

Any help/ideas? It's not HORRIBLY important, but my virtualbox is extremely unperformant without the hardware acceleration.

---

### Post by Mark Phelps on 2010-04-28
Don't have that card but have read that disabling compiz fixes the tearing effects...

---

### Post by skelooth on 2010-04-28
I disabled compiz but no go. I had even uninstalled it at one point.

Regardless, in all of my fidgeting with drivers I failed to realize that the open source ati drivers are installed by default, so I'm okay to go. Thanks

---

### Post by Chocrates on 2010-05-20
I have the same problem.  Disabling the extra effects makes it usable for me, but the artifacts are still there.
We have any idea why this is happeneing in 10.4?

---

### Post by SpEcIeS on 2010-07-01
Whether using compiz or not, I have had the same issue with my Radeon 3450 HD, but the open source radeon drivers seem to do the trick for me.

---

