---
title: "reiserfsck has its own life"
date: 2008-07-12
forum: General Help
---

### Post by ziofil on 2008-07-12
hi there!
I have little issue with reiserfsck during bootup: although I edited the /etc/fstab file and wrote 0    1 at the end of the lines of the / and /home partitions, reiserfsck starts during *every* boot and lasts for ~30 secs, as I can see from the bootchart graph.
This is quite annoying, how can I avoid it to check the filesystems at every boot?
thank you in advance!

---

### Post by dcstar on 2008-07-12
> **ziofil said:**
> hi there!
I have little issue with reiserfsck during bootup: although I edited the /etc/fstab file and wrote 0    1 at the end of the lines of the / and /home partitions, reiserfsck starts during *every* boot and lasts for ~30 secs, as I can see from the bootchart graph.
This is quite annoying, how can I avoid it to check the filesystems at every boot?
thank you in advance!

Well, having "1" will cause a fsck at boot (and should **only** be on the root fs), so what do you expect?

---

### Post by ziofil on 2008-07-12
I thought that 1 would cause fsck to run every 30 boots, and that 2 would cause it to run at every boot..! am I wrong?

---

### Post by dcstar on 2008-07-12
> **ziofil said:**
> I thought that 1 would cause fsck to run every 30 boots, and that 2 would cause it to run at every boot..! am I wrong?

They are EXT2/3 filesystem settings and have absolutely nothing to do with Reiserfs.

[http://ubuntuforums.org/showthread.php?t=223858](http://ubuntuforums.org/showthread.php?t=223858)

---

### Post by ziofil on 2008-07-12
allright, thank you, i'll have a look at the link!

---

