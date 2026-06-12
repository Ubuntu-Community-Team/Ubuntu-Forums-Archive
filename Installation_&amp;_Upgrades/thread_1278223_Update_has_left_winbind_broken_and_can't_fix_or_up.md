---
title: "Update has left winbind broken and can't fix or update"
date: 2009-09-29
forum: Installation &amp; Upgrades
---

### Post by andrew_d_mackenzie on 2009-09-29
I recently accepted a regular update of packages to 9.04.

Among them it (tried to) update winbind, but the installation broke (unfullfilled dependancy) and has left winbind package broken.

I can't find any way to fix it (tried apt-get, dpkg etc) and so I now cannot remove it, reinstall it, update or or do any other package updates using synaptic or update manager...

When I try to re-install winbind, or when installing another package it tries to install windind again the problem seems to start with

"/usr sbin/invoke-rc.d: 446 /etc/init.d/winbind: not found"

(BTW: I can't find a way to copy the output of the "Details" window of synaptic, it doesn't like Cntr-C or Shift-COntrolC, and no copy menu).

/etc/init.d/winbind does indeed exist.

Anyone else got this problem?

Any ideas/

---

