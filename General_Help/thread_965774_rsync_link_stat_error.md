---
title: "rsync: link_stat error"
date: 2008-10-31
forum: General Help
---

### Post by botfish on 2008-10-31
I have a bash backup script that used rsync to backup my home directory.

Occasionally it runs with the following errors:

rsync: link_stat "/no" failed: No such file or directory (2)
rsync: link_stat "/user@machine:/home/user" failed: No such file or directory (2)
rsync error: some files could not be transferred (code 23) at main.c(977) [sender=2.6.9]

I have tried to solve this by using double quoting '""' as discussed here
[http://samba.anu.edu.au/rsync/FAQ.html#9](http://samba.anu.edu.au/rsync/FAQ.html#9)

But this has resulted in the destination files being saved in
$LOCAL_TARGET (with double quoting)
rather than
$LOCAL_TARGRT/home/user (with out any quoting)

I'm not even sure it will fix the problem as $REMOTE_SOURCE does not contain any spaces.

The relevant lines from my script
!#/bin/bash
REMOTE_SOURCE="/home/user"
REMOTE_MACHINE="machine"

/usr/bin/rsync \
$VERBOSE \
$EXCLUDE \
--delete-excluded \
-a \
--delete \
-e "ssh -i $RKEY" \
$REMOTE_USER@$REMOTE_MACHINE:'"$REMOTE_SOURCE"' \
"$LOCAL_TARGET/$BACKUP_TIME"

---

