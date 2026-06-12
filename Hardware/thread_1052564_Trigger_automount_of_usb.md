---
title: "Trigger automount of usb"
date: 2009-01-27
forum: Hardware
---

### Post by Innova on 2009-01-27
For whatever reason my external usb drive seems to unmount itself occasionally.  If I unplug it and replug it in it will remount.  However, my computer is in a different room, and accessing the the usb drive is a pain.

Is there a way to automatically trigger the computer to search for usb drives w/o unplugging/replugging?

On a side note, the drive has two partitions on it...ubuntu seems to randomly mount them at disk/disk-1.  Is there anyway to force a partition to be mounted in a particular point?  I rsync to the drive, and my backup is now on both partitions.

---

### Post by cpp_sk on 2010-09-10
I'd like to echo the question above: Is there a way to re-trigger the automounting process?

Also, is there a way to read the volume label before mounting?
The automounter is obviously somehow able to do it as it mounts removable devices to /media/*volumename*.

Thanks in advance.

---

### Post by cpp_sk on 2010-09-13
I didn't find a way to re-trigger the automount process by nautilus, but I found how to read the label of non-mounted volumes: Using blkid. Using that, one can write a script that does the same (mkdir when a volume has no mount point + mount, umount + rmdir when a mount point has no underlying volume).

---

