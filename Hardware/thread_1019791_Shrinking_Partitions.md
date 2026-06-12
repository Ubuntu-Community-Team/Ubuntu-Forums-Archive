---
title: "Shrinking Partitions"
date: 2008-12-23
forum: Hardware
---

### Post by charleskw on 2008-12-23
so, I've used man resize2fs, and now I'm trying to find out which extension is which. I have a dual boot with Windows Vista. To try to sort out the extensions, I typed sudo fdisk /dev/hda and It says that It's unable to open dev/hda. Is it possible to find the file extensions another way, other than using the Terminal? I'm trying to shrink my Ubuntu partition so that I can add a third, MAC. Please help!!

---

### Post by taurus on 2008-12-23
```
sudo fdisk -l
```

---

### Post by SlidingHorn on 2008-12-23
just make it easy on yourself and use gparted from your Ubuntu LiveCD

---

