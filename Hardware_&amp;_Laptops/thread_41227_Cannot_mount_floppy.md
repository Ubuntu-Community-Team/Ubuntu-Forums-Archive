---
title: "Cannot mount floppy"
date: 2005-06-12
forum: Hardware &amp; Laptops
---

### Post by prometheus on 2005-06-12
I cannot mount floppy.

mount /dev/fd0 /mnt/floppy

mount /dev/fd1 /mnt/floppy

dont give out any output, if i try the command. im new to (k)ubuntu i've been using sarge as a server before, but im new to using linux as a desktop-os.

---

### Post by alastair on 2005-06-12
No output at all? Odd.

Check you see some mention of "floppy" in the system boot log i.e.

grep -i floppy /var/log/dmesg

Is there a floppy device e.g.

ls -l /dev/fd?

Is the floppy formatted (FAT)? Try :

mount -t vfat /dev/fd0 /mnt/floppy

---

### Post by David Haas on 2005-06-14
Prometheus--To get the feel of mounting, you might want to first do it the long way. First, format the floppy with the terminal command "fdformat /dev/fd0" (without the quotes of course). Then install the linux filesystem on it with the command "mke2fs /dev/fd0". Then mount it as root (sudo -s) with the full mount command "mount -t  ext2 /dev/fd0  /media/floppy0". /media/floppy0 is the empty directory for mounting, but you can mount in any empty directory. I suggested /media/floppy0, because you probably have this by default in your system. If this goes well, then later you should check the file "fstab" in the directory "/etc" with a "less" command. Mine is as follows: /dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0  With the mount point listed here as /media/floppy0 you can then give the briefer mount command (as root) as "mount /dev/fd0 /media/floppy0". Unmount when finished with the floppy with the command "umount /media/floppy0". I hope this addresses your problem.
David

---

### Post by prometheus on 2005-06-29
-t vfat was missing, thx for your help. i didnt know, that linux only mounts ext2-floppies.

---

