---
title: "backup troubles"
date: 2008-11-21
forum: General Help
---

### Post by notsomeone on 2008-11-21
I want to use rsync to backup my web server, but I have root logins disabled, so I can't do something like:
sudo rsync -avF /somefolders remotepc:/media/server_backup
(or vice versa: sudo rsync -avF server:/somefolders /media/server_backup)
I assume that is the problem, because I can backup any folders that I own (no sudo), but I want to backup the whole system. Can I do that?

---

