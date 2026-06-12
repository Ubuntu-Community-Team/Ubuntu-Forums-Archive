---
title: "Reinstalling But Keeping a Previously Encrypted LVM -- How?"
date: 2009-10-15
forum: Installation &amp; Upgrades
---

### Post by rookcifer on 2009-10-15
I have an encrypted LVM that consists of one large data storage partition and one encrypted swap partition.  Whenever I fire up the alternate CD and attempt to reinstall, the LVM is not detected automatically.  Rather, I have to open a shell and use cryptsetup to open it.  After that, the installer recognizes it.  My problem is, once I get the LVM to be recognized, there is no option to give the partitions their own mount points without formatting them.  I don't want to format them, I want the data to remain intact.

My question:  How can I maintain an encrypted LVM across Ubuntu installs whilst still having Ubuntu automatically mount them at boot with LVM?

---

