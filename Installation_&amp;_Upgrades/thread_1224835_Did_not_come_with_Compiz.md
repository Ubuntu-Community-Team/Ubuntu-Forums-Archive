---
title: "Did not come with Compiz"
date: 2009-07-27
forum: Installation &amp; Upgrades
---

### Post by jaxsmrknrevenge on 2009-07-27
The help manual refers me to the Compiz tab under System for Advanced Desktop effects, but it's not there. Where can I download it?

---

### Post by starcraft.man on 2009-07-27
> **jaxsmrknrevenge said:**
> The help manual refers me to the Compiz tab under System for Advanced Desktop effects, but it's not there. Where can I download it?

Compiz is installed by default. You can find it under System > Preferences > appearances > Visual effects tab > Normal or Extra.

For more fine control, see compizconfig-settings-manager package in the repo. For help installing see my sig pls.

Ensure your graphics driver is installed before turning it on. System > Admin > Hardware Drivers. Enable via there.

---

### Post by philcamlin on 2009-07-27
sudo apt-get install compizconfig-settings-manager

thats what you want

---

### Post by Sef on 2009-07-27
> The help manual refers me to the Compiz tab under System for Advanced Desktop effects, but it's not there. Where can I download it?
Easy way to install CCSM:

Applications > Add/Remove > Show: All Available Applications > Search: CCSM > tic the box next to Advanced Desktop Effects > apply changes > apply > close


> sudo apt-get install compizconfig-settings-manager

That is incomplete.   First you should upgrade the repositories, so one gets the latest versions.

The correct code is ```
sudo apt-get update && sudo apt-get install compizconfig-settings-manager
```

---

