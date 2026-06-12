---
title: "deleting contents of /usr/src"
date: 2009-02-08
forum: Installation &amp; Upgrades
---

### Post by rabidityfactor on 2009-02-08
is it safe to remove the contents of /usr/src ?? i installed a new kernel and its taking up around 2.5gb of space.

---

### Post by lemming465 on 2009-02-09
Yes and no.  Yes, in the sense that the system will boot without the contents of /usr/src.  No, in the sense that source code installed from packages but deleted behind the back of synaptic or apt-get or dpkg will leave metadata debris behind and confuse things the next time you try to add something to /usr/src.

A quick way to reclaim space in many source packages is to run "make clean".
If you downloaded the source, you can delete it freely.
If you got the source from a package install, use your package manager, e.g. synaptic, to remove it.

---

