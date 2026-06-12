---
title: "Update manager doesn't show the new release"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by MyR on 2009-04-27
Hello!

Update manager does not show the 9.04 release.  I have software settings set to show "normal releases".  I can't pick out any problems with my sources list.  I just can't figure it out and I don't want to do a fresh install.

First I had downloaded & burned the desktop iso and put it in the cd drive.  Once I realized I couldn't upgrade with it I took it out & removed it from the sources list.  Could this have caused a problem somehow?

Any ideas?

---

### Post by cariboo on 2009-04-27
Press Alt-F2 and type:

```
gksu update-manager -d
```

This should allow you to upgrade to Jaunty.

---

### Post by MyR on 2009-04-27
thanks! I went ahead with the command line method
do-release-upgrade -d

now using jaunty!

---

