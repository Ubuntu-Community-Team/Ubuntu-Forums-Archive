---
title: "Why missing numbers in Ubuntu/Linux kernels ?"
date: 2009-02-06
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2009-02-06
Why does the kernel versions that are available on my machine go from .19 directly to .23 ?  Where are 20, 21, & 22 ?

Thanks.

---

### Post by Tim Sharitt on 2009-02-07
If you are talking about the ones which are installed, I would guess that you just missed a few updates.

If you are talking about the ones which are available to be installed, I haven't the slightest idea :P.

---

### Post by ghettofreeryder on 2009-02-07
Because Ubuntu does not upgrade the kernel everyday.  The linux kernel is actively being updated all the time.  For example, the latest linux kernel is 2.6.29, whereas Ibex uses 2.6.27.x, and jaunty will use 2.6.28.x  Its nothing to be worried about

---

### Post by ibutho on 2009-02-07
> **wpshooter said:**
> Why does the kernel versions that are available on my machine go from .19 directly to .23 ?  Where are 20, 21, & 22 ?

Thanks.
The kernels that you do not see, were probably released but only for internal testing by the kernel packagers. What happens is that packagers bump version numbers of a package every time they build or rebuild even if the package itself is not officially released into the repos.

---

### Post by wpshooter on 2009-02-07
> **ibutho said:**
> The kernels that you do not see, were probably released but only for internal testing by the kernel packagers. What happens is that packagers bump version numbers of a package every time they build or rebuild even if the package itself is not officially released into the repos.

That is what I suspected.

Thanks.

---

