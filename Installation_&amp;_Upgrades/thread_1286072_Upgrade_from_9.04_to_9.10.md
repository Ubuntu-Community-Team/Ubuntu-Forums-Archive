---
title: "Upgrade from 9.04 to 9.10?"
date: 2009-10-08
forum: Installation &amp; Upgrades
---

### Post by Gordonbp531 on 2009-10-08
Will there be an automatic upgrade, or will I have to download 9.10 Remix and create the install media myself?

---

### Post by tom.swartz07 on 2009-10-08
When its released, it will update automatically.

After it is released, check your computer upgrades and it will download like any other update.

---

### Post by QIII on 2009-10-08
Depends on what you mean by "automatically".

If this works like it has in past releases, the Update Manager will inform you that a new version is available and you will be given the option to upgrade to it.  You do not have to.

If you want to upgrade from the terminal, you can use dist-upgrade.

There are any number of opinions on whether the best course of action is to dist-upgrade or install fresh...

---

### Post by slakkie on 2009-10-09
cli upgrades can be done via another tools:

```

sudo aptitude install update-manager-core
sudo do-release-upgrade

```

There is no need for a distupgrade command (although it can be used off course, but is not advised by Ubuntu developers).

---

### Post by fran_lelli on 2009-10-09
hi all! it's my 1st post so excuse me if i'm begging you. but i'm a newbie and i need some reassurance....

i have ubuntu netbook remix 9.04, if i make an alt+f2 and then type upgrade -d, i'm going to have "only" ubuntu 9.10 karmic or the netbook remix edition for karmic ?

In that case, how can i switch to the new netbook launcher of the karmic netbook remix edition?

Tnx All

---

### Post by slakkie on 2009-10-09
fran_nelli, as you are new, do NOT upgrade now to Karmic. It is still in a development phase. It is not advisable for new users to switch to development releases.

---

