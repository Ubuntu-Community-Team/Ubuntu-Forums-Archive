---
title: "External USB drive not recongnized unless unplugged (NTFS)"
date: 2010-01-10
forum: Hardware
---

### Post by metalsubstance on 2010-01-10
Hi all,

I have an external hard drive formatted with the NTFS filesystem.  However, Ubuntu is unable to mount it the first time when it is already plugged in.  Trying to access the volume from the Places menu results in a hang, unless I unplug the drive and plug it back in again.  Has anyone else encountered this issue before?

This is on Karmic, with all the latest updates applied.

---

### Post by metalsubstance on 2010-01-23
bump - anyone?

---

### Post by efflandt on 2010-01-23
Are you saying that if you boot with the drive already connected it does not mount, but if you unplug and replug it it auto mounts?

Are you letting it totally auto mount, or is there an /etc/fstab entry for it using /dev/whatever instead of UUID?  A UUID should work, but if you use a device path instead, it is possible that it is a different device when booted than when plugged in later.

See if output of **sudo fdisk -l** (small L) shows it as a different device it when it does not work or does work (or contents of file /proc/diskstats).  Or see if **mount** shows it connected, but you just do not have permission to access it.

Do you by any chance have grub in the mbr of the external drive and/or does the external ntfs partition have Wubi?  Although, I don't think that would be a factor if you are certain that your main hard drive is before USB in boot order (or is it esata connection?).

---

