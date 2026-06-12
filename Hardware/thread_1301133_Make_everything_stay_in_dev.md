---
title: "Make everything stay in /dev?"
date: 2009-10-25
forum: Hardware
---

### Post by ownaginatious on 2009-10-25
Is there a way to make my hard drives always get the same device id (e.g. /dev/...)? I'm getting really sick of all the devices suddenly jumping around and screwing up the mounting whenever I unplug or plugin a new piece of hardware and restart.

Any help would be greatly appreciated,

Thanks,

Dillon

---

### Post by earthpigg on 2009-10-25
hi,

here are three links. if the first doesn't work, check out the 2nd. if the 2nd doesn't work, check out the third.

[http://pysdm.sourceforge.net/](http://pysdm.sourceforge.net/)
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[http://www.archlinux.it/wiki/index.php?title=Fstab](http://www.archlinux.it/wiki/index.php?title=Fstab)

---

### Post by sisco311 on 2009-10-25
Use the UUIDs or LABELs to mount the partitions:
[uhelp]community/UsingUUID[/uhelp]

---

### Post by ownaginatious on 2009-10-25
Oh right, UUIDs - I completely forgot about those; at least now I know their purpose :p.

Thanks a lot guys, I really appreciate it. Problem solved :).

---

