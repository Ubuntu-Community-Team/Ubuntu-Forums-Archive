---
title: "Unable to unmount the main partition"
date: 2008-10-11
forum: General Help
---

### Post by Dragoola on 2008-10-11
I want to create a separate partition and install xp on it. However, when I run GParted there is a key icon besides the main partition and when I try to unmount it, it gives me an error. Is there anything I should do before that? This is the error that I get:

The partition could not be unmounted from the following mountpoints:

/

Most likely other partitions are also mounted on these mountpoints. You are advised to unmount them manually.

---

### Post by ubunny on 2008-10-11
try running Gparted from the disc in rescue mode, as it needs that vantage point to perform a root partition change.  Before that of course make all necessary data backups in case of failure or loss.

cheers

---

### Post by bodhi.zazen on 2008-10-11
LOL

You need to manage your partitions from a live CD. The Ubuntu desktop CD will do.

The ubuntu Cd will automatically mount your swap partition, but you can unmount it from gparted (or the command line).

---

