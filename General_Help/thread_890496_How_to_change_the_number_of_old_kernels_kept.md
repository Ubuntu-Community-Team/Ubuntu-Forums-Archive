---
title: "How to change the number of old kernels kept?"
date: 2008-08-15
forum: General Help
---

### Post by Dremora on 2008-08-15
I looked on my boot partition (120 MB) today and noticed I only had like 25 MB left, removing like 5 kernels and a bunch of related stuff got me back up to 86 MB.

Is there a way to force Ubuntu to trash old kernels itself?

---

### Post by iaculallad on 2008-08-15
> **Dremora said:**
> I looked on my boot partition (120 MB) today and noticed I only had like 25 MB left, removing like 5 kernels and a bunch of related stuff got me back up to 86 MB.

Is there a way to force Ubuntu to trash old kernels itself?

I can't think of a way for Ubuntu to automatically trash old kernel versions. But doing it manually could be done using your Synaptics Package Manager. Click on "Search" and input "linux-image" (w/o quote). From there you could right-click on an OLD kernel and mark it for Complete Removal. Do the same process with other older kernels. Once finished, click on Apply and automatically, your menu.lst file will be updated.

NOTE: It's best to leave at least one working OLD kernel just in case.

---

### Post by tuxerman on 2008-08-15
Download this package called Startup manager

```
sudo apt-get install startupmanager 
```

It has many settings you can configure easily instead of editing config files, and also includes an options regarding the number of kernels to be shown.

---

### Post by tuxerman on 2008-08-15
OOps, sorry about my earlier post... I thought you wanted to restrict the number of kernels shown in grub. :D

---

