---
title: "[SOLVED] permissions problem"
date: 2008-08-01
forum: General Help
---

### Post by wolfen69 on 2008-08-01
this is a weird one. i have a drive with 2 partitions. sda1 and sda2. it is formatted fat32. everything was fine as far as adding files to them and deleting things. i then had a bunch of mp3's on cd that i copied over to sda1 (music). it put a lock emblem on everything i added to the drive. why is this? here is my fstab: (originally, there were no entries in fstab for sda1 and sda2. i added them after i had this problem)
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=80d16226-b423-4188-9d99-99973280ebd8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=7866b39a-9241-49b3-b4c4-22a1e646556f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#
**/dev/sda1      /media/music    vfat  auto,users,uid=1000,gid=100,utf8,dmask=000,fmask=111**
#
**/dev/sda2     /media/permanent  vfat  auto,users,uid=1000,gid=100,utf8,dmask=000,fmask=111**
```
thanks for any help.

---

### Post by drs305 on 2008-08-01
Did you run the "mount" command to see if they are still recognized as sda1 and sda2 ? If they have changed designations they would mount belonging to root.

If that happened you can prevent it in the future by changing the fstab entries to uuid's or labels (labeling probably harder for fat unless you are willing to reformat the partition).

---

### Post by wolfen69 on 2008-08-01
i just did fdisk -l and yes, they are still recognised as sda1 and sda2. i can access them and play music, but i can't do anything else like create folder, delete, etc. the drives were fine before i added mp3's to them. the added files have a lock emblem on them.

---

### Post by drs305 on 2008-08-01
I just reread your original post. Since the entries weren't in fstab to begin with, root normally owns fat partitions (but wouldn't necessarily lock you out of the files).

Run these to unmount and then remount the partitions with your new fstab settings. Disregard the 'busy' messages:

```
sudo umount -a
sudo mount -a
```

If you still have the locks, then:
```
sudo chown -R username /media/music
```

---

### Post by wolfen69 on 2008-08-01
here's an update. the only problem i have now is with the mp3's i added. they still have a lock emblem on them. i can go in as root and delete them, but that is not acceptable. why would they have a lock emblem after i copied them to the drive?

---

### Post by RuleMaker on 2008-08-01
This is what you need to do:
```
sudo chown <your username> /path/to/music/*
```
Dont forget to change everything as it is, and leave the star at the ent, it stands for "all files".

---

### Post by wolfen69 on 2008-08-01
i did ```
sudo chown -R username /media/music/*
``` and the files still have locks on them.

---

### Post by drs305 on 2008-08-01
```
sudo chmod -R 750 /media/music
```

If the rwx bits are messed up, this should fix them. Other than that ... ?

---

### Post by RuleMaker on 2008-08-01
> **wolfen69 said:**
> i did ```
sudo chown -R username /media/music/*
``` and the files still have locks on them.

I wrote:
```
sudo chown <your username> /path/to/music/*
```
i haven't wrote "-R" nowhere.

---

### Post by wolfen69 on 2008-08-01
thanks for all the help. ive decided to reformat my drive to ext3, and actually learn how to do it. ive always had ntfs and fat partitions in the past. never had to worry about permissions. in my opinion, that is something that linux could do better. an easier way to access an ext3 partition. and change permissions.

---

