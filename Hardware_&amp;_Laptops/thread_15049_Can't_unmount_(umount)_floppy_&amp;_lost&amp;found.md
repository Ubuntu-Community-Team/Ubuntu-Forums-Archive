---
title: "Can't unmount (umount) floppy &amp; lost&amp;found"
date: 2005-02-11
forum: Hardware &amp; Laptops
---

### Post by David Haas on 2005-02-11
I mounted floppy with "mount -t ext2 /dev/fd0 /media/floppy."  The floppy icon appears on the desktop. /media/floppy was empty when I mounted it. But I can't unmount the floppy (as root). The error message is: "umount: /media/floppy0: device is busy." I read that one can't unmount a disk if the current working directory is somewhere in that disk's directory tree. If it is, then the errror message states that the /floppy filesystem is in use--the error I receive. I've tried many other directories to no avail. However, when the computer shuts down and later runs, the files in the floppy are okay. Any suggestions about this problem?

Another query: what is the lost+found directory that appears in the foppy directory when the disk is mounted?

---

### Post by David Haas on 2005-02-11
The problem is solved thanks to a prior post by ming0. He said in re;lation to an unmounting problem with another device: Is auto-mount on? This is in Computer>Desktop Prefs.>Removable Storage. It should be on by default. So, I entered "Computer>Desktop preferences>Removable storage," and unchecked "Mount removable drives when hot-plugged, Mount removable media when inserted, and browse removable media when inserted." When I did this, I unmounted with the command (in root) "umount /media/floppy" (the directory in which I had mounted the floppy.

Thanks to ming0 and the forum.

---

