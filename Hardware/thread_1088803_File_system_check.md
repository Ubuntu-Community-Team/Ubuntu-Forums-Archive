---
title: "File system check"
date: 2009-03-06
forum: Hardware
---

### Post by PippoSniffo on 2009-03-06
When the system is booting het file system check ends with:
```

/dev/sda9 contains a file system with errors, check forces
...
...
..
Give root password for maintenance and resume system boot.ion is writable. 9.png (inode #1561012, mod Time Fri Mar 6 12:00:43)

```
If I type ctrl-D the system then boot normally.
But I cannon execute fsck manually and when I reboot the system I get the same error.

---

### Post by taurus on 2009-03-06
You can only fsck a partition if you either mount it as read-only or not mount it.  Therefore, try to run the fsck for that partition from the LiveCD.

Before you reboot, post the outputs of these commands from a terminal.

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by PippoSniffo on 2009-03-09
I've got fsck by a root console (Instead typing ctrl-d I've entered in the root console) and from there the system seems to have repaired the problem.

I've some "problems" again.
I don't know why, with the new kernel, both wireless card and sound card are not available while with the old kernel was all ok.

---

### Post by jack daniels esq on 2009-03-09
I used to have weekly probs with ext2/3 - drove me nuts - now use Reiserv3 exclusively
Now more fsck
BR>Jack

---

### Post by PippoSniffo on 2009-03-09
Have You changed file system type ?

---

