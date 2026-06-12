---
title: "Failed installation"
date: 2009-07-28
forum: Installation &amp; Upgrades
---

### Post by Greasy_Larry on 2009-07-28
I tried installing Ubuntu beside Windows, and the installation failed, apparently due to a bad disk. Once I get to the partition manager on the second installation it has a portion of the disk already associated with Ubuntu and it wants to create a 2nd Ubuntu partition, how do I delete the first one and the file swap and do a second clean installation.

---

### Post by merlinus on 2009-07-28
You should be able to select the ubuntu partition, choose use as ext3, format, and mountpoint /.  This will overwrite whatever is already on it.

---

### Post by vinutux on 2009-07-28
all you need is getting from installation menu when selct to **manual partition** instead of proposed ubuntu installer

---

