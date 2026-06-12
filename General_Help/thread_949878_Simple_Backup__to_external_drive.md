---
title: "Simple Backup  to external drive"
date: 2008-10-16
forum: General Help
---

### Post by eadwacer on 2008-10-16
I just got a "No space left on device" for root. Using the excellent advice in the thread of the same name, plus the standard tools, I found this (sorry about not doing a cut/paste, I'm working on a different machine):
1. After deleting the trash, my internal drive shows as being 98% full. DU says the biggest directory is /media/disk-1
2. My (identical) external USB backup drive /sdb1 shows 80% full. It shows up on the desktop as an external USB drive, mounted as directory /media/disk-1.

The external drive is intended as the backup drive, using Simple Backup.

So, my n00b question is, does this mean I have been writing to the local drive rather than the external drive, and how do I keep that from happening?
-- Answer: No, when I deleted an old backup directory, it showed on the external drive, but didn't expand the space on the internal drive. Simple Backup is working as advertised.

The internal drive turns out to be truely full, with audio files, and audio editing files.

---

