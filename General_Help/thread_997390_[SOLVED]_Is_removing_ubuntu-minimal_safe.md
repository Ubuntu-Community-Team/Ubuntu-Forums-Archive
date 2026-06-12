---
title: "[SOLVED] Is removing ubuntu-minimal safe?"
date: 2008-11-29
forum: General Help
---

### Post by x1a4 on 2008-11-29
Hi,
I'm almost certain that removing the meta package ubuntu-minimal is quite safe, but could use confirmation.  Is it safe to remove ubuntu-minimal?

Thank you.

EDIT: It is safe to remove ubuntu-minimal.  After removing it, all the packages it installs remain as they were.

---

### Post by sdennie on 2008-11-29
It's safe.  It's a meta-package that just installs a bunch of other things.  If you upgrade your machine to a new version of Ubuntu, you may want to re-install it just before the upgrade because it might understand how to move your system to the new version of Ubuntu.

---

