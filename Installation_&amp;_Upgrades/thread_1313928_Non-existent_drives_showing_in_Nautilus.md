---
title: "Non-existent drives showing in Nautilus"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by madverb on 2009-11-04
After upgrading to 9.10 from 9.04 I suddenly acquired a non-existent Floppy drive.
Showing up in my Places Menu I now have this Floppy Drive and 2 spares for other drives/partitions I have mounted to the media folder.
Does anyone know of a way to remove these pointless entries?

---

### Post by mc4man on 2009-11-04
> ...and 2 spares for other drives/partitions I have mounted to the media folder.

If these are mounted via fstab then maybe ck./adjust how the fstab entries are written

bug report that may be your issue
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/442130](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/442130)

thread with examples of what works in fstab atm (uuid and label on page 2

[http://ubuntuforums.org/showthread.php?p=8050320](http://ubuntuforums.org/showthread.php?p=8050320)

---

### Post by madverb on 2009-11-04
That explains the extra drives, as I am mounting them using the UUIDs. It doesn't explain the Floppy. I don't have a Floppy attached to this PC and I have completely removed the Floppy line from my fstab.

---

### Post by mc4man on 2009-11-04
> It doesn't explain the Floppy

Try booting to your bios setup and disable/remove the floppy (diskette) drive there.

---

### Post by madverb on 2009-11-05
Thanks for all that. Weird that it shows a Floppy when none is installed in the system at all.

---

