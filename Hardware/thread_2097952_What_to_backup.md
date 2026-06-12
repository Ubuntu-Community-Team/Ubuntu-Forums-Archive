---
title: "What to backup"
date: 2012-12-25
forum: Hardware
---

### Post by Wim Sturkenboom on 2012-12-25
[I]Note to moderators:
Not sure where to post this; was not quite an Ubuntu question but also not really an 'other os' question.
[/I]
My wife had dual a boot WinXP / Ubuntu 10.04 laptop. Somebody borrowed the laptop and decided to install Win7 (with or without agreement is debatable).

All partitions still seem to be there and I made a backup (dd) of his Win7 (/dev/sda1; on his request). If I also make a backup of the MBR, will I be able to restore Win7 if needed. Or is there something else I need to backup as well to get the system back to the current state?

Note
I'm going to re-install WinXP and probably upgrade Ubuntu (possibly to 12.04 flavor).

---

### Post by ahallubuntu on 2012-12-25
You can always copy the MBR directly with dd:

```
sudo dd if=/dev/sda of=./out.mbr bs=446 count=1
```

This copies only the MBR and not the partition table.  If you want the partition table too then do:

```
sudo dd if=/dev/sda of=./out.mbr bs=512 count=1
```

Restoring just the MBR without partition table is a bit safer.  I guess there are cases where you might want both.  (If you restore the partition table, the old partition structure is blown away.)

Using dd to copy partitions is crude but should work if you are careful - but you have to be careful when you restore it.  Clonezilla would probably be a lot more efficient.

---

### Post by Wim Sturkenboom on 2012-12-25
Thanks; I can always chop the last few bytes of the 512 byte backup. I like to keep the partition table though as that defines the size of sda1.

Marked as solved.

---

