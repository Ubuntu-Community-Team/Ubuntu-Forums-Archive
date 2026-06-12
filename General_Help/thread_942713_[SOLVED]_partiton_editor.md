---
title: "[SOLVED] partiton editor"
date: 2008-10-09
forum: General Help
---

### Post by suhaib1thariq on 2008-10-09
i previously asked a doubt about how to format a pendrive..memorycard or even a hard drive in that..they replied me to install gparted...which is opening as partition editor...
in that how can i format...no opton for that
in that there is a option for change label...it tells me changing label will erase all details in he drive...how can label adrive using that without erase disk

---

### Post by jerome1232 on 2008-10-09
I hope these screenshots will clear it up for you, in order to change labels you must unmount the partition, then click label and you can type one in, then you can remount it. Doing it this way will not cause you to lose data.


In order to change labels you must have certain utilities installed; You can use apt-get, or synaptic to install them.

```
ntfsprogs     - For ntfs
e2fsprogs     - For ext2, ext3
mtools        - For fat12,16,32
jfsutils      - For jfs
xfsprogs      - For xfs
reiserfsprogs - For reiserfs
```

---

### Post by jerome1232 on 2008-10-09
more screenshots

---

### Post by suhaib1thariq on 2008-10-09
thank you..for you reply......i had installed that for format a pen drive and memory card and drive....can i do that using format to option listing in menu when i write click a drive as your screen shot

---

### Post by jerome1232 on 2008-10-09
> **suhaib1thariq said:**
> thank you..for you reply......i had installed that for format a pen drive and memory card and drive....can i do that using format to option listing in menu when i write click a drive as your screen shot

Format to> will erase any data currently on the disk.

---

### Post by WWSmith36 on 2008-10-09
> in that there is a option for change label...it tells me changing label will erase all details in he drive...how can label adrive using that without erase disk

BE CAREFUL
In gparted if you go to menu Device-> Disklabel
This will wipe all data off the drive.  I think it removes all partitions from the drive as well.

---

### Post by suhaib1thariq on 2008-10-09
thank you....

---

### Post by jerome1232 on 2008-10-09
> **WWSmith36 said:**
> BE CAREFUL
In gparted if you go to menu Device-> Disklabel
This will wipe all data off the drive.  I think it removes all partitions from the drive as well.

I forgot about that option, and your right to warn, it can be misleading.

I can confirm that setting the disklabel from Device->Disklabel wipes the partition table too; ( an early attempt at figuring out how to change labels taught me this lesson :) ) 

That actually has nothing to do with setting the (I guess it's a partition label) label the way I was showing in my screen shots.

---

### Post by suhaib1thariq on 2008-10-09
oh...i can't ale to change label using that...

---

