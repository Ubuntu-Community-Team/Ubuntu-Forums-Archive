---
title: "Daylight savings and backups/folder merge"
date: 2008-11-07
forum: General Help
---

### Post by darinwc on 2008-11-07
Came across an interesting issue today.

I was trying to merge files from my test website to production.
Problem is that all the files are an hour off, so filezilla thinks one side is allways newer than the other, even immediately after transfer.

How do I adjust time & daylight savings settings in linux?

OS: Ubuntu Server 8.10
file transfer app: Filezilla

---

### Post by fredbird67 on 2009-03-07
It's very simple.  In Ubuntu (using GNOME), go to System --> Administration --> Time and Date.  In the dialog box that pops up, click "Unlock", enter your password, click on the "Time Zone" drop-down list, which is at the very top of this selfsame dialog box, and choose your time zone.  I just tried this, and since I didn't see anything about DST adjustments, I think Ubuntu automatically keeps track of which locations in the list observe DST and which ones don't (I could be wrong, though).

---

### Post by dcstar on 2009-03-07
> **fredbird67 said:**
> It's very simple.  In Ubuntu (using GNOME), go to System --> Administration --> Time and Date.  In the dialog box that pops up, click "Unlock", enter your password, click on the "Time Zone" drop-down list, which is at the very top of this selfsame dialog box, and choose your time zone.  I just tried this, and since I didn't see anything about DST adjustments, I think Ubuntu automatically keeps track of which locations in the list observe DST and which ones don't (I could be wrong, though).

```
sudo tzselect
```

---

