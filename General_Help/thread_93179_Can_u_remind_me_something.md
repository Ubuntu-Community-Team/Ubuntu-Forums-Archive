---
title: "Can u remind me something?"
date: 2005-11-21
forum: General Help
---

### Post by SkillZero on 2005-11-21
1-command to see my partitions.
2-command to mount the partition i want to.


tnx

---

### Post by fog on 2005-11-21
1. sudo fdisk -l
2. mount -t filesystem device mountdir 
 (something like this: mount -t ext3 /dev/hda5 /media/data)

---

### Post by earobinson on 2005-11-21
1. I googled (command to see my partitions) first link was [http://www.linuxgazette.com/node/10037](http://www.linuxgazette.com/node/10037) I learned that the command is fdisk, type man fdisk for more info

2. I googled (command to mount the partition) and about 3 links down I found this [http://iew3.technion.ac.il/CC/Comp_news/Mandrake_CMD_line/fs-and-mntpoints-mount.html](http://iew3.technion.ac.il/CC/Comp_news/Mandrake_CMD_line/fs-and-mntpoints-mount.html)
man mount for more info.

---

### Post by astronerd on 2005-11-21
1)
'df -h' will show you your filesystem and sizes or use
'cat /proc/partitions'

2)
'mount' will show you what is mounted, so to mount something just do 
'mount -t /what/youare/mounting  /mount/point/you/want/to/mount/to'

man mount will help if you need more...

---

### Post by landotter on 2005-11-21
I'll cheat and give you the gui way to do this:

System-Administration-Disks

---

### Post by earobinson on 2005-11-21
[QUOTE=landotter]I'll cheat and give you the gui way to do this:

System-Administration-Disks[/QUOTE]
Good Idea I sometimes forget the gui ways

---

