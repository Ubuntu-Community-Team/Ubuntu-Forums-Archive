---
title: "MS SQL Backup app?"
date: 2008-08-19
forum: General Help
---

### Post by gewitty on 2008-08-19
Can anyone recommend a good application that I can use to back up an MS SQL database on a remote Windows server? I've never done this before, so it will need to be something relatively straightforward (if such a thing exists).

---

### Post by senor_jt on 2008-09-13
Sorry -- 

No straightforward solution to offer(as yet) but I have the same question and have just begun my "research".  Which among other leads, brought me to your post here.  I'm using a server with Ubuntu Server 8.04.(latest) installed to handle backups for a small business domain.  Standard setup for me, using rsnapshot to write backups to local drives and a remote process to copy snapshots to an offsite network.  I'm just beginning to look into accessing their MS SQL Server(v2000) and adding that to these backups.

If you're not already tied to a particular backup mechanism, I've seen hints that Amanda/Zmanda may have a module for MS SQL Server backup.  Good luck to you -- I'll share my eventual solution with this thread.

---

