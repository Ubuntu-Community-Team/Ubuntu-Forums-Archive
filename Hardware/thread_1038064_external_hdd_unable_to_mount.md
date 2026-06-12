---
title: "external hdd unable to mount"
date: 2009-01-12
forum: Hardware
---

### Post by geltonas on 2009-01-12
Hi, I'm new here, I would read all forums trying to find how to mount external hdd, but the thing is its not my hdd and on this hdd are all my files from win vista. 
I would like to make safe mounting hdd on ubuntu 8.10 and there is what I get when I plug in the hdd to laptop.

---

### Post by taurus on 2009-01-12
Why don't you connect that external drive into a windows machine and either shutdown your windows cleanly or at least use the safely remove hardware to remove that drive.  Don't just unplug it from your machine.

If you do that, Ubuntu shouldn't have any problem mounting it.  Otherwise, you can use ntfsfix to fix it.

```
sudo apt-get update
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdb1
```

---

### Post by geltonas on 2009-01-12
Thanks indeed taurus!

---

### Post by hockey97 on 2009-01-12
hmm? what file system format is it?

---

### Post by taurus on 2009-01-12
> **hockey97 said:**
> hmm? what file system format is it?

It says NTFS from the screenshot.  And besides, I am not sure if vista would even install on a fat32 filesystem (probably would)!

---

