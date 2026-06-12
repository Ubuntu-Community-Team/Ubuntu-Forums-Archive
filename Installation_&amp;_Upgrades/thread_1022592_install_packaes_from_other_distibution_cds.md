---
title: "install packaes from other distibution cds"
date: 2008-12-27
forum: Installation &amp; Upgrades
---

### Post by arunkumar413 on 2008-12-27
is it possible to install packages from other distribution cd.for example i am using ubunu8.04 and i have a suse 11 cd.is it possible to install packages form suse 11 cd to ubuntu8.04 system.

---

### Post by cariboo on 2008-12-27
It is possible, but I wouldn't advise it, as Suse is an rpm based distribution. You would have to use alien to convert them to .debs. Other distrbutions don't place config files in the same place as Ubuntu so you may run into problems running some programs.

Alien is in the repositories and you can use Add/Remove Programs, Synaptic Packale Manger and of course the command line to install it.

Jim

---

