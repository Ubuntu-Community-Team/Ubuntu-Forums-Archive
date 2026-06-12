---
title: "When using NVIDIA propriety drivers, what other driver packages can I safely remove?"
date: 2013-05-12
forum: Hardware
---

### Post by ÄlveKatt on 2013-05-12
When using NVIDIA propriety drivers, what other driver packages can I safely remove?

Can I remove libdrm-intel packages?
Are there any MESA drivers I can remove?
Are there any drivers I should remove other than the open source NVIDIA drivers?

Thank you!

---

### Post by CatKiller on 2013-05-12
Is everything working? Are you terribly low on hard drive space? Why do you want to remove anything?

---

### Post by Yellow Pasque on 2013-05-12
You can remove all of the xserver-xorg-video packages except vesa,fbdev, and modesetting (those may be needed for fallback in case something goes wrong with nvidia blob).

> Can I remove libdrm-intel packages?
When I try that, it wants to remove some other critical packages (gstreamer-bad, xorg, etc.)

---

### Post by Yellow Pasque on 2013-05-12
> **CatKiller said:**
> Why do you want to remove anything?
When I do a default Xubuntu install, I remove a ton of packages I don't need. This makes package management faster (smaller database, less updates to download), cuts down on RAM usage, and decreases startup time.

---

### Post by grahammechanical on 2013-05-12
Beans = 22 compare beans = 8,990. Know what you are doing. Yes?

---

