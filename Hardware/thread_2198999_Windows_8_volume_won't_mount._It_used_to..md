---
title: "Windows 8 volume won't mount. It used to."
date: 2014-01-11
forum: Hardware
---

### Post by goodpunk6 on 2014-01-11
this is the error I get.  that long drawn out number is the volume ubuntu assigned it.  I wonder if there is a way to change that as well.  How do I get this thing to mount again?

Error mounting /dev/sda2 at /media/manny/3CCC9E8BCC9E3ED8: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sda2" "/media/manny/3CCC9E8BCC9E3ED8"' exited with non-zero exit status 14: Windows is hibernated, refused to mount.
Failed to mount '/dev/sda2': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

---

### Post by oldfred on 2014-01-11
> Windows is hibernated, refused to mount.
You have to turn off hibernation. And if Windows 8, hibernation is always on, but is called Fast Boot.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

I assign labels to my partitions that I do not mount with fstab. Then the default mount is by label.
You can use Disks or Disk Utility to assign labels. Partition will have to be unmounted but also to edit it will need the hibernation turned off.

---

