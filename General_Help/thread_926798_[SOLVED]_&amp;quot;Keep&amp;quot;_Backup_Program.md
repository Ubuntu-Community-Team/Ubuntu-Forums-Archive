---
title: "[SOLVED] &amp;quot;Keep&amp;quot; Backup Program"
date: 2008-09-22
forum: General Help
---

### Post by CrusaderAD on 2008-09-22
Does anyone out there know if, when doing a scheduled backup with Keep, it replaces the original files and folders from your previous backup?

---

### Post by CrusaderAD on 2008-09-22
bump

---

### Post by CrusaderAD on 2008-09-24
bump

---

### Post by candtalan on 2008-09-24
I tried to use keep some time ago  because it looks like exactly what I want. At the time, it seemed to do backups on an hourly basis, and I did not know why it was not doing the 24 hour timing I had apparently configured. Maybe I needed to do something with cron or whatever, not sure. 

Anyway I poked around and saw that it was based upon rdiff-backup which is something you can search for independantly for information of course.

If I am correct in my beliefs, it is rdiff-backup with bells on and so should create a mirror of the original and in addition it logs and notes the differences each time. This means that in principle, you could restore to a particular previous date.

The mirror set has an additional directory which contained rdiff-backup-data stuff.

If you find it is all ok in ubuntu now please shout? It will be useful to know.

I currently use rsync for most things now......
hth

---

### Post by CrusaderAD on 2008-09-26
I used Keep and scheduled a backup, but I'm not sure yet whether or not it's replacing the data. I think it is because there isn't any duplicates. I need to update some files and run a backup to see if these files are updated. Still need to test some more, will post again when I conclude this issue. For now I'm using a combination of Keep and Simple Backup.

---

### Post by CrusaderAD on 2008-09-29
I ran some schduled backups last week... it replaces the old data and doesn't seem to make duplicates.

---

