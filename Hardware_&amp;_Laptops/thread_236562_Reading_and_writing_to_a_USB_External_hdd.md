---
title: "Reading and writing to a USB External hdd"
date: 2006-08-14
forum: Hardware &amp; Laptops
---

### Post by dunomous on 2006-08-14
Hi, my external drive is being read as a read-only device, when obviously it should be able to be written to. Upon first turning it on, I am allowed to read and write. A few seconds/minutes later, I am only able to read from it. I've tried chmod with no luck.

*it's formatted with fat 32*

---

### Post by simonn on 2006-08-15
> **dunomous said:**
> Upon first turning it on, I am allowed to read and write. A few seconds/minutes later, I am only able to read from it. 

I suspect that the drive has not been mounted yet, so you are writting to the directory where it will be mounted to.

If you umount the drive, are there files in the mount point directory (/media/[something])?

> I've tried chmod with no luck.

*it's formatted with fat 32*

Fat does not support permissions. These must be specified at mount time using the uid, gid and umask parameters. See "Mount options for fat" in man mount.

---

