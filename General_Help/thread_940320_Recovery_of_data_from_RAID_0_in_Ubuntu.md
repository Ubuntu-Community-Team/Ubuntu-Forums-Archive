---
title: "Recovery of data from RAID 0 in Ubuntu"
date: 2008-10-06
forum: General Help
---

### Post by bacat on 2008-10-06
Hi,

I have a Windows XP computer with a RAID 0 array (two striped hard drives). Windows no longer boots and I want to use Ubuntu Live to salvage some data from the hard drives.

However, when Ubuntu Live loads, it cannot mount the drives. I presume this is because they are RAID.

Is there a special trick to mounting RAID arrays with Ubuntu?

---

### Post by fjgaude on 2008-10-07
Install **dmraid** from the repository, read the man pages. Mount the array in Ubuntu using the form:

```
sudo mount -t ext3 /dev/mapper/sil_ahahbhbjaddg /raid
```

The mountpoint can be other than /raid, as you like, say, /home/raid.

---

### Post by bacat on 2008-10-08
Ok, I'll try that. Thanks for the info!

---

