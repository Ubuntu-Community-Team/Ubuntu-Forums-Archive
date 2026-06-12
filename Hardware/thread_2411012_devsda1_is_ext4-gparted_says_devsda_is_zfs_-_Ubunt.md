---
title: "/dev/sda1 is ext4-gparted says /dev/sda is zfs???? - Ubuntu 18.04"
date: 2019-01-23
forum: Hardware
---

### Post by LVDave on 2019-01-23
I just discovered that an install of Ubuntu 18.04, which is working fine, with the single hard drive /dev/sda being the installed location, and ext4 being the
installed filesystem, according to what I chose at install and what the "disks" app says now. However, I noticed that gparted claims /dev/sda is zfs and shows
dashes for space used/unused, but shows drive size correctly.. I don't have a current need to use gparted, but with it disagreeing on filesystem, using it, if I did
need it would be a non-starter. Have I discovered a bug somewhere in 18.04?

---

### Post by TheFu on 2019-01-23
Best not to use "disks". It has issues.

Post the output from **sudo fdisk -l** and please use code tags so everything lines up.

---

### Post by gedakc on 2019-01-24
My guess is that there are old **zfs** signatures on the disk drive.

For an example of how to identify and remove old zfs signatures see [zfs partition wrongly shows occupying the whole disk]("https://gitlab.gnome.org/GNOME/gparted/issues/14") and [URL="https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/1808421"]
gparted produces unusual results when ZFS partitions exist[/URL]

---

### Post by LVDave on 2019-01-26
Not sure whats going on.. fdisk -l shows all good partitions and now.. gparted is showing all ext4 filesystems on both drives.. Not sure why I was seeing
zfs before...

---

### Post by TheFu on 2019-01-26
A few options come to mind:
a) "Disks" issue
b) User error
c) Cable not completely connected/loose
d) Flaky power
e) Some other failing hardware interfering on the bus

Regardless, if this is solved, please use the Thread Tools button near to to to mark it so.

---

