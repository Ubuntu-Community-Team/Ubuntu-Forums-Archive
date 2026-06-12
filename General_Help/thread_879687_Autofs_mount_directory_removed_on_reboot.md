---
title: "Autofs mount directory removed on reboot"
date: 2008-08-04
forum: General Help
---

### Post by wjlroe on 2008-08-04
Hi,
Very sorry if this has been dealt with before in any Ubuntu-mediums. I looked but I did not find. 

The problem is that I use /mounts for my autofs daemon. This works very nicely until the next day, when that directory has mysteriously vanished. 

Does anyone have any clues as to why it might delete this directory? Is it no longer possible to create top-level directories without something messing with it?

The /etc/autofs.master file only has one active line:
/mounts /etc/auto.mounts --timeout=60

And the /etc/autofs.mounts has a few network shares (SMB, SSHFS) and a couple like this:
iriver   -fstype=vfat,uid=1000,gid=100 :/dev/disk/by-label/H300

Nothing very controversial. 

There's nothing enlightening in the logs (syslog and friends), expect autofs complaining that it can't mount anything - not surprising given the /mounts directory has run away.

Many thanks,

Will

---

### Post by wjlroe on 2008-08-12
Hi,
Does anyone have any idea about this?
Thanks,
Will

---

