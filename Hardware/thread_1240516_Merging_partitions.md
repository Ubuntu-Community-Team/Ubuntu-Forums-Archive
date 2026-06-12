---
title: "Merging partitions"
date: 2009-08-14
forum: Hardware
---

### Post by jeb800e on 2009-08-14
Is it possible for me to merge partitions back together using GParted? Please help me out here! I really need to know!

Thanks,
Jeb800e

---

### Post by sailthesea on 2009-08-14
> **jeb800e said:**
> Is it possible for me to merge partitions back together using GParted? Please help me out here! I really need to know!

Thanks,
Jeb800e

Deleting the unwanted partition and expanding the other to the full size of the HDD would amount to the same thing surely?
If you wanted to keep the data and join the two together thats a different matter and depends very much on whats on them and in what filesystem Any specifics?

---

### Post by jeb800e on 2009-08-14
I formatted the rest to the same file format as Ubuntu, ext2.

---

### Post by john stiles on 2009-08-14
You should be able to simply now merge them.
Stating the obvious but back up any personal data before proceeding.
I also seem to remember you may need to use a live CD (usb stick) to boot from in order to make changes to the primary partition i.e. to unlock it.

---

### Post by Mosaab on 2009-08-14
I did the same thing just yesterday and I waited for the process to complete for more than 6 hours !!! and I cancelled it (Turned off the laptop) before the progess bar reached to 1 % !!!!..

it takes very very very very very long time to extend a partition (Merge)

---

### Post by jeb800e on 2009-08-14
n/m. I think I got this problem solved! I will just use the entire disk setting within the installation options. Will this really delete EVERYTHING, or leave something behind?

---

### Post by sailthesea on 2009-08-14
NO all gone Fresh Install of Ubuntu 
Best way to do it Will be doing the same soon just a bit of backing up and note taking to finish!

---

### Post by jeb800e on 2009-08-14
Will the Lost+Found folders be formatted, too, or will they stay the same? I really want them to be formatted, as of I will not need the files within.

Thanks for your help!

---

### Post by running_rabbit07 on 2009-08-14
Every time I have used GParted it has been fast and effective.

---

### Post by sailthesea on 2009-08-14
> **jeb800e said:**
> Will the Lost+Found folders be formatted, too, or will they stay the same? I really want them to be formatted, as of I will not need the files within.

Thanks for your help!

 running dd or dban? from a LiveCD then reinstalling will take care of things But will take ages
 Unless your Dad is in the FBI there is not much need :lolflag:

---

### Post by jeb800e on 2009-08-14
GParted.

---

### Post by jeb800e on 2009-08-14
Wait, so does formatting the hard disk also format the Lost+Found?

---

### Post by lswb on 2009-08-14
The contents of /lost+found will be destroyed when you make a new filesystem or format the partition, as will every other file or directory on the partition. A new, empty /lost+found directory will be created.

---

