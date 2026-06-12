---
title: "Is there a list of applications installed by default on the LiveCD?"
date: 2008-11-09
forum: General Help
---

### Post by sstecken on 2008-11-09
I'm creating a lighter distro with Reconstructor and want to get rid of the unnecessary.

Is there a list somewhere of applications installed by default on the Live CD?

---

### Post by red_team316 on 2008-11-09
**The packages that appear on the LiveCD:**
~reconstructor/remaster/casper/filesystem.manifest

**The packages that should be included in the install:**
~reconstructor/remaster/casper/filesystem.manifest-desktop


Doing a 
```

dpkg -l

```
in the chroot terminal will also give you a list of packages.

---

