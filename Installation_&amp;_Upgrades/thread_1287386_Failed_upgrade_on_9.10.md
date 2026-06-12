---
title: "Failed upgrade on 9.10"
date: 2009-10-10
forum: Installation &amp; Upgrades
---

### Post by buntolith on 2009-10-10
Hi,

I was running 9.10 on kernel 2.6.31-12 and all was working fine. I did an upgrade of the system which also included an upgrade to 2.6.31-13 but this upgrade did not finish correctly. When I am restarting the system I get this error message:

"The configuration defaults for Gnome Power Manager has not been installed correctly"

I can login but I only end up with the background image. Gnome desktop does not start.

I have tried to do a upgrade in safe mode in the shell but it does not correct the problem.

Does anyone have any suggestions?

---

### Post by aheckler on 2009-10-10
Try going into the shell and typing these lines in terminal:
```
aptitude purge gnome-power-manager
aptitude install gnome-power-manager
```

---

### Post by buntolith on 2009-10-10
Thank's for the advice. Unfortunately it did not help ): I will do a reinstall instead.

---

