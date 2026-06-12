---
title: "Errors while updating packages"
date: 2009-09-24
forum: Installation &amp; Upgrades
---

### Post by dagoth_pie on 2009-09-24
I'm getting the following error:
```
E: /var/cache/apt/archives/evolution-data-server-common_2.24.3-0ubuntu1_all.deb: unable to make backup link of `./usr/share/doc/evolution-data-server-common/changelog.Debian.gz' before installing new version
```
When I try to update the evolution updates, everything else has updated fine, I also have a similar problem with cups, which I have been trying to sort out and have uninstalled, but get the error while trying to reinstall, I'm stuck, does anyone have any ideas, maybe I can override what it's trying to back up?

---

### Post by rreese6 on 2009-09-24
Possibly, One of two things,
You do not have the correct permissions to do the action...or
you are out of drive space....

I need to think about this some more too....maybe I can come up with another possible reason

---

### Post by dagoth_pie on 2009-09-24
I've got another 9GB or so of disk space, and the update manager asks for the password to run as root, plus it was happening during the other updates which worked fine, maybe the file its trying to backup could be corrupt?

EDIT:
I went to the file it mentions tried to open it and go this error:
```

gzip: /usr/share/doc/evolution-data-server-common/changelog.Debian.gz: not in gzip format

```
AND ANOTHER UPDATE:
I don't even have sufficient permissions to change the file permissions using sudo or su, looks like the file's stuck there...

SOLVED:
I found a work around, I renamed the "evolution-data-server-common" folder to "useless folder" then ran the update and it worked fine.

---

### Post by rreese6 on 2009-09-24
Good thinking! I like the work around. I was thinking that the file
may have been corrupted, possibly because of a bad sector on the hard drive....I have had files do that on old drives...seems like they refuse
to let root work even though they belong to root and are in the same group... Glad it worked out for you.

---

