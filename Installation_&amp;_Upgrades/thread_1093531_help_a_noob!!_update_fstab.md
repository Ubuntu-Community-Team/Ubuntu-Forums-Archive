---
title: "help a noob!! update fstab ?"
date: 2009-03-11
forum: Installation &amp; Upgrades
---

### Post by shift_00 on 2009-03-11
well long story short, i wanted to get rid of my xp partition for it was taking too much space for no good reason.

i used GParted, and created two partitions, which had a default mount point of /media/partitionName .. i can't make it to '/' but we'll come to that later.

now i can't seem to mount those partitions, they are there, used to mount, but my fstab file is outdated, so something happenned after one reboot, now, they are just laying there, and with an old fstab file, which still has the windows partitions in it, the mount from terminal won't work either.


please advice.

---

### Post by mhgsys on 2009-03-11
Probaly you get an error now when you try to mount it manually because your old fstab allready mounted it.

You can use nano or vi to edit the fstab.

I recommed nano although I use vi myself.
Anyway:

open a terminal.
typ:
```
 sudo nano /etc/fstab 
```

and you can delete the old mount options, 

typ: ctrl+O to save it, and ctrl+X to exit.

then try to mount again in a terminal.

---

