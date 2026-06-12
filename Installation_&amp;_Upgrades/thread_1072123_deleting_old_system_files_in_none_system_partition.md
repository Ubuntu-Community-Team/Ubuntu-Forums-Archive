---
title: "deleting old system files in none system partition"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by skydiving85 on 2009-02-17
I just re-installed 8.10 and thought the partition for media files was a great idea, except it kept all the old system files; i am assuming they are not part of the systems operations. but would like to selectively remove them; whilst keeping a select few ie music, docs, pictures etc. any ideas?!

---

### Post by cdtech on 2009-02-17
Which partition are you talking about cleaning out? List:
```
sudo fdisk -l
```
What do you mean by system files?

---

### Post by skydiving85 on 2009-02-17
the disk is partitioned 3 ways, the old back up windows files that have never been touched, a 95 GB media system that also has all the OLD system files from the last linux system, and a new 15GB drive with the NEW file system on it. is there a way i can do this with out formating that 95 GB drive?

---

### Post by cdtech on 2009-02-17
If you could list your partitions:
```
sudo fdisk -l
```
and also your /etc/fstab file, we could see your layout. Is the old partition being mounted on boot? Also the "df -H" command will show the partition layout with system.

I would hate to tell you it's ok to delete the files without knowing what partition your talking about.......

---

