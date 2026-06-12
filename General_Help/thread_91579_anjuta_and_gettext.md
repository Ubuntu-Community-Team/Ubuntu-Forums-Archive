---
title: "anjuta and gettext"
date: 2005-11-17
forum: General Help
---

### Post by garba on 2005-11-17
i'm having quite a hard time getting anjuta to work... the problem is the same old dread issue with gettext... first, disabling gettext support does nothing, wonder why... the project template can be built, though it complains about AM_GNU_GETTEXT being in configure.in but the .po and .intl subdirs are missing... the project can be succesfully built, but what i can't do is build a package for redistribution because of this gettext thing... anybody got a clue? luckily i still have my trusty debian lying around somewhere on my hd, i must confess building stuff on this distro is everything but easy... :???:

---

### Post by garba on 2005-11-21
solved: installing automake 1.9 sorted things out

---

