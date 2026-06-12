---
title: "hide Linux partition on Windows"
date: 2008-11-30
forum: General Help
---

### Post by rozbarwinek on 2008-11-30
Is there a way to hide Linux partition or forbid access to some folder from Windows that have ext2ifs installed?

---

### Post by The Cog on 2008-11-30
Format the partition with JFS instead of ext3? I don't believe there is a JFS driver for windows. Or encrypt the partition. That won't stop them overwriting or reformatting the partition though.

---

### Post by PocketDog on 2008-11-30
Get Paragon Partition Manager (for Windows). With that you can hide entire partitions, even from BIOS. Handy for non-destructive installs, when you absolutely need to make sure a partition is safe.

---

### Post by rozbarwinek on 2008-11-30
> **The Cog said:**
> Format the partition with JFS instead of ext3? I don't believe there is a JFS driver for windows. Or encrypt the partition. That won't stop them overwriting or reformatting the partition though.

Thanks :) that helped ^^

---

