---
title: "Kubuntu backup utility"
date: 2008-07-31
forum: General Help
---

### Post by lodp on 2008-07-31
I'm looking for a backup utility for Kubuntu.

I've tried Keep, and it does a pretty good job. It does incremental backups with rdiff-backu and runs a daemon to do it automatically. But it has a couple of shortcomings:

- It hasn't seen an update in almost 2 years
- There's a bug that runs backups every hour, even though I specified a 3 days interval.
- I can't use it to do automatic backups to my flash drive, since it doesn't prompt for it to be plugged in first.

As a result, I have to run backups manually every couple of days. Is there something better I could use instead?

There's sbackup for gnome, which looks pretty good too -- but I'd rather stick with KDE.

---

### Post by rbmorse on 2008-07-31
Take a look at kdar

[http://sourceforge.net/project/showfiles.php?group_id=96947](http://sourceforge.net/project/showfiles.php?group_id=96947)

---

### Post by Max Roswell on 2008-09-07
Something wacky's going on with Keep.  I set up the directories I want to back up, I set up where I want them to go (external hard drive), and then I click "backup now."

And then nothing happens.

Wha?????

---

### Post by lodp on 2008-09-08
Have you checked the external hard drive whether the backups actually end up there? There's no success message or anything in Keep. When you hit "backup now" it starts rdiff-backup, it doesn't tell you when it's done.

---

### Post by indytim on 2008-09-08
My usual recommendation: **Partimage**.  It' in the repositories.

IndyTim

---

