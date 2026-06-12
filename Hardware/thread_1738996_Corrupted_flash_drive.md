---
title: "Corrupted flash drive"
date: 2011-04-25
forum: Hardware
---

### Post by east.sg89 on 2011-04-25
Hey guys, i'm having trouble creating a partition table for a flash drive, i think it might be corrupted. I used lsusb to check the computer recognized it, then used GParted to try to format it, it showed me the drive is lacking a partition table, but when i tried to create a new one, Gparted throws an error, checked the info and it shows a warning telling me this:
[FONT=Courier New]
/dev/sdb/ unrecognized disk label.[/FONT]

I don't know what to do next ](*,), could you guys help me out please?

---

### Post by wilee-nilee on 2011-04-25
> **east.sg89 said:**
> Hey guys, i'm having trouble creating a partition table for a flash drive, i think it might be corrupted. I used lsusb to check the computer recognized it, then used GParted to try to format it, it showed me the drive is lacking a partition table, but when i tried to create a new one, Gparted throws an error, checked the info and it shows a warning telling me this:
[FONT=Courier New]
/dev/sdb/ unrecognized disk label.[/FONT]

I don't know what to do next ](*,), could you guys help me out please?

Give us a screen shot of gparted looking at the thumb, and make sure you know how to make a partition table it is done from device drop down at the top of gparted. Make the table then the partition.

---

### Post by east.sg89 on 2011-04-25
Hey, thanks for your quick reply. Here are the screenshots.

---

### Post by wilee-nilee on 2011-04-25
> **east.sg89 said:**
> Hey, thanks for your quick reply. Here are the screenshots.

Creating a partition table and then partitions is about my limit. It is a 1 gig thumb, not knowing how old it is or if it may have a virus in the mbr=first 512MB or in any firmware it is hard to say.

Probably not a virus, but we don't know the history of the thumb, is it worn out possibly?

---

### Post by east.sg89 on 2011-04-25
It looks operational, it is from a friend of mine, he has the same problem in Windows, the memory is recognized by the system, but it is unusable, can't format it using the Fast Format or the slow one. Thanks for your help anyway.

---

