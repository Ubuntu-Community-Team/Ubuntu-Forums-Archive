---
title: "Lost Mount Points"
date: 2020-03-30
forum: Hardware
---

### Post by jweese74 on 2020-03-30
Well, I've been using Ubuntu on and off for a number of years now and most recently for about a year with a couple different installations - one being for a home theater setup, so with that out of the way; my question and issue.

I have a number of external hard drives connected to my HTPC box, all of which had very specific mapping that docker relies on. I've made no changes in a number of months but after installing some updates and doing a reboot two of my drives and mount points have disappeared.

sdb and sdc -- sure, I could just remount them however, it's been set up for so long I don't remember where they were mounted specifically and I don't want to cause further issues and have to reconfigure multiple docker containers. I don't know what happened but - is there any way via console (I run my HTPC headless) to remount them to their previous mount points? To add to that, any way to find out what happened to cause them not to automatically mount on boot?

Thanks for the help, it really is much appreciated and avoids me much wife-agro.

---

### Post by TheFu on 2020-03-30
Sure.  Just restore from the backup made prior to the updates.  That would let you see the mounts, the mount points and restore the system to what you had before as reference.

Or you could just look at the backed up files to see that information.

Depending on how you did the mounts, then just look at the fstab or auto.* or the systemd-automount files.  if you did any mounts using a GUi, i don't have any clue where that data may be stored.

Hope you didn't mount the entire disk, without partitions. Best to always, always, have partitions.  That would be sdb1, sdc1, sdc3, sdc99 ...

/etc/ is tiny.  Best to always have a backup of that.  Daily, automatic, versioned.  Probably less than 2 seconds to create on any Unix system. Be certain to retain all the permissions, owner, group, and ACLs too wth the backups.  The data alone is about 50% of the backup.

if you shared what software the "htpc" was running, perhaps someone familiar would know where to look for media data?

---

