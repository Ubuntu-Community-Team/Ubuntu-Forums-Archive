---
title: "No root file system is defined"
date: 2008-12-19
forum: Installation &amp; Upgrades
---

### Post by ckcmohq on 2008-12-19
I'm trying to install the system. It comes up as a third partition andonce I click on it it starts downloading fine until this pops up.. "No root file system is defined. Please correct this from the partitioning menu." How do I fix this?

---

### Post by taurus on 2008-12-19
Have you specified a partition as /, mounting that partition as root filesystem?

---

### Post by ckcmohq on 2008-12-19
I don't think so. How would I do that?

---

### Post by pastalavista on 2008-12-19
When you first set up the partitions, (manual install) there's a field called "mount point" which you should type / to designate the 'root' file system (ext3). You should also designate a small partition (about 1 gig) as 'swap' and it is a good idea for future transitions to designate a partition as /home for your saved personal data.

---

### Post by ckcmohq on 2008-12-19
mmkay thanks

---

