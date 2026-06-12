---
title: "Dual Monitor Compiz-Fusion Slow Menus and Window Resize"
date: 2008-09-03
forum: General Help
---

### Post by IntuitiveNipple on 2008-09-03
There's an [archived thread with the same subject as this](http://ubuntuforums.org/showthread.php?t=536045&highlight=Dual+Monitor+Compiz-Fusion) but as it is read-only I can't update it.

The cause of this issue has been found by Aaron Plattner and patched upstream: Launchpad [bug # 149764 "slow gtk popup menus with gtk dual head"](https://bugslaunchpad.net/ubuntu/+source/compiz/+bug/149764).

I've cherry-picked the patch from upstream and applied it on top of the current hardy-proposed compiz package. It will be available from my PPA (Personal Package Archive) shortly.

Please test it and report your results to the [bug report](https://bugslaunchpad.net/ubuntu/+source/compiz/+bug/149764).
```

compiz (1:0.7.4-0ubuntu8~ppa1h) hardy; urgency=low

  * debian/patches 44: Handle sync alarm events on screens other than the last.
     from upstream commit 5031a1f9c91d14fbda4969781f86d806a9dd1be1
     (closes LP #149764).

 -- TJ <ubuntu@tjworld.net>  Thu, 4 Sep 2008 03:30:00 +0100

```

I've also applied the patch to the Intrepid package since it *just* missed it by hours in the git snapshot of 2008-08-07. Newer Intrepid packages from git snapshots after that date will have it built-in.
```

compiz (1:0.7.7+git20080807-0ubuntu6~ppa1i) intrepid; urgency=low

  * debian/patches 44: Handle sync alarm events on screens other than the last.
     from upstream commit 5031a1f9c91d14fbda4969781f86d806a9dd1be1
     (closes LP #149764).

 -- TJ <ubuntu@tjworld.net>  Thu, 4 Sep 2008 03:30:00 +0100

```

---

### Post by pjbgravely on 2008-09-04
I will test the patch for you. I always thought this was an nvidia problem so I never hoped for a fix.

Paul

---

