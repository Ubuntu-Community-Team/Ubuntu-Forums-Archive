---
title: "Add/Remove programs question"
date: 2008-07-29
forum: General Help
---

### Post by jras20 on 2008-07-29
When my first installed on Ubuntu 8.04 it had a bunch of programs/games etc.  But now after I had to re-install it, it only has maybe half of the programs/games as it did before.  How can I update that list?  Or will it update with in time?

---

### Post by drs305 on 2008-07-29
Were these perhaps in the Medibuntu repository. Have you added it to your sources.list?

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

These wouldn't have been on an initial install but if you had added them afterwards perhaps that is why you don't have them now on reinstalling.

Added: If you think it's your menu that is messed up and want to restore it to the defaults:
```

alacarte

```
Select > Revert

---

### Post by Archimedes0212 on 2008-07-29
are you talking pre-installed games/apps or in general.  If you are asking about the pre-installed ones, you can install a bunch of good stuff via the Add/Remove Programs option in the Applications menu

---

### Post by jras20 on 2008-07-29
> **Archimedes0212 said:**
> are you talking pre-installed games/apps or in general.  If you are asking about the pre-installed ones, you can install a bunch of good stuff via the Add/Remove Programs option in the Applications menu

Yeah in the add/remove section of the applications.  I had a bunch more the first time around than I did this time after my second install.

---

### Post by spiderbatdad on 2008-07-29
Have you checked the "All Available Applications" in the Show dialogue window.

---

### Post by jnw222 on 2008-07-29
make sure extra repos are enabled

---

### Post by jnw222 on 2008-07-29
go to system-administration-software sources
there should be 5 boxes 
check all but source code (very unneeded)

---

### Post by jras20 on 2008-07-30
> **spiderbatdad said:**
> Have you checked the "All Available Applications" in the Show dialogue window.

That was it.
Thanks.

---

