---
title: "Developer upgraded gcc, now can't install packages"
date: 2009-09-21
forum: Installation &amp; Upgrades
---

### Post by whtabtbill on 2009-09-21
Someone ran a package that upgraded gcc to 4.3.2 (1ubuntu12) and when I try to install something off the Ubuntu CD (this system has no internet connection and never will) I get an error message that indicates the gcc-version is expected to be 1ubuntu11 and not 1ubuntu12.  Is there any way to work around this?  I appreciate any input.

---

### Post by BraedenNaylor on 2009-09-21
I'm fairly new at Ubuntu but I will try to help. I may be wrong but the choice I would try would be to uninstall the gcc package that was installed and reinstall the old version. I know there is a command to force packages to be installed and ignore errors but this may not apply in this case and I forget it.

Hope this helps.

---

### Post by whtabtbill on 2009-09-21
> **BraedenNaylor said:**
> I'm fairly new at Ubuntu but I will try to help. I may be wrong but the choice I would try would be to uninstall the gcc package that was installed and reinstall the old version. I know there is a command to force packages to be installed and ignore errors but this may not apply in this case and I forget it.

Hope this helps.


Once you remove a package, it no longer shows up under the package list.  It will also remove other dependent packages as well, again deleting them from the list.  You're right about the force option -- it only works if certain conditions exist.  Thanks for trying to help though!

---

### Post by Juan Largo on 2009-09-21
Try changing the CC environment variable to the older gcc version before compiling:

```

sudo export CC=/usr/bin/gcc-X.X

```

, where X.X is the version of gcc that your kernel was compiled under.  After executing that, then try compiling again.

---

