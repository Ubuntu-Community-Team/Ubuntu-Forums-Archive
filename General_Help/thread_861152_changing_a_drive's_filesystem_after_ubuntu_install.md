---
title: "changing a drive's filesystem after ubuntu installation"
date: 2008-07-16
forum: General Help
---

### Post by yosubis on 2008-07-16
I installed ubuntu, and I had a partition for storage, and I usually would mount it through the Places menu. But I needed access from XP, so I formatted it from XP to ntfs. But now, in ubuntu everytime I try to mount it from the Places menu, it tries to mount it with the old filesystem. I can mount it manually from terminal with the mount command, but I need a permanent solution. How can I fix this?

---

### Post by yosubis on 2008-07-16
A little bump, seenig how after only one hour, the thread is in page 3.

---

### Post by somedumbme91 on 2008-07-16
The /ect/fstab file is contains your drive's old filesystem information.
Can you list the file here?

---

### Post by yosubis on 2008-07-16
It lists only those it automatically mounts... I have 2 other ntfs partitions from before I installed ubuntu which do not appear in this file, located in the places menu and I have no problem with them.

/etc/fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=9b00aa31-32cc-43d7-a491-8716355b3727 /               reiserfs notail,relatime 0       1
# /dev/sda6
UUID=dc241286-2dd2-4ea1-b01e-429980ef7d95 /home           reiserfs relatime        0       2
# /dev/sda5
UUID=ef6c9834-f251-42c7-9f10-195057c6c76d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by yosubis on 2008-07-16
A small bump again for the same reason stated above.

---

### Post by jonian_g on 2008-07-16
Install "Storage Device Manager" from add/remove and you will be able to mount any partition you want. After installation it is at System>Admin>Storage Device Manager.
Click the "Assistant" button to enable automount on startup, have write permissions etc.

---

### Post by somedumbme91 on 2008-07-17
Eh,
I don't believe it's listed here,
unless it is the /dev/sda6?
```

# /dev/sda6
UUID=dc241286-2dd2-4ea1-b01e-429980ef7d95 /home           reiserfs relatime        0       2

```
In which case,
just change the reiserfs to ntfs-3g.

Otherwise,
try jonian_g suggestion.

---

