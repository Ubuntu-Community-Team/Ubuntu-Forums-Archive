---
title: "Software RAID (MDADM)"
date: 2009-06-24
forum: Installation &amp; Upgrades
---

### Post by shockuk on 2009-06-24
Hi all,

I've been looking at articles for setting up MDADM but i'm a little bit confused :). No articles seem to answer my following question:

If, for example, I create a device called **/dev/md0** which mirrored the partitions **/dev/hda2** and **/dev/hdc2** - what would happen if I was to access **/dev/hda2** (which is where my /home is located)?

Would simply writing to the **/dev/hda2** partition be automatically copied to **/dev/hdc2**, or would I need to access it through **/dev/md0** for it to work?

Thanks for your help,
Shockuk.

---

### Post by mk1w86 on 2009-06-24
With software RAID you do not access the partitions directly so you would treat /dev/md0 (which is the RAID volume) as your /home partition.  Writing to the partition directly would probably cause problems because the one you write to would no longer be a mirror of the other partition.

---

