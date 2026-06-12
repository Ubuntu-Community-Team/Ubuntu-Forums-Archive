---
title: "Mask a package from upgrading"
date: 2009-08-06
forum: Installation &amp; Upgrades
---

### Post by buzzin on 2009-08-06
Hey all,

Simple question really... There is a package (wine) which apt wants to upgrade, but i dont want to run the latest version as it has some issues with what i use it for.

So normally i just ignore it.. But is there a way to mask this newer version so apt doesnt keep asking for it to be updated?

In Gentoo i could just add =>package-version into the package.mask file, but im unable to find the ubuntu way of doing this.

Thx.

---

### Post by Partyboi2 on 2009-08-06
Hi, have a look at [[COLOR=Blue]apt-pinning[/COLOR]]("https://help.ubuntu.com/community/PinningHowto").

---

### Post by buzzin on 2009-08-06
Perfect, thx u.

---

