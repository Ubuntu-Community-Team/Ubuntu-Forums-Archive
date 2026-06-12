---
title: "RAID Question?"
date: 2010-11-20
forum: Hardware
---

### Post by RastaManPower on 2010-11-20
hello guys i have been reading about RAID and wanted to try out this thing because i have 4TB of data on 2 of my hd. my HD's are 2*2000GB WD 64Mb cache cavier green. is it worth setting them up in raid? will i lose all the data i have in them? with a new install of ubuntu i will lose this config?

---

### Post by CharlesA on 2010-11-20
The only way you'd be able to get 4TB of space with just two drives to use use RAID-0, which has no redundancy at all.

RAID-1 (mirror) requires 4 drives and RAID-5 (stripe with parity) requires 3 drives.

---

### Post by RastaManPower on 2010-11-20
this is what i found about raid0. from what i read it is better for me to keep the drives in regular mode.when i will have the money to buy one more drive i will jsut use raid1. right?

RAID-0 doubles the chance of losing data, because if one drive fails, you lose the data on both drives (but you get double the storage space of a single drive). But it's faster. RAID-1 is what you want, which puts the same data on both drives, so if one dies, you still have the other one (but you only get the storage space of a single drive, rather than both of them added together).

---

### Post by RastaManPower on 2010-11-20
well i have to edit my first post. i dont have 4gb of data now. i have 1tb for now but i will have more in a little bit. so i could use raid1 that is way more safer right? it makes a backup of the files from what i read. but in this case i will loose alot of disk space right?

---

### Post by CharlesA on 2010-11-20
> **RastaManPower said:**
> well i have to edit my first post. i dont have 4gb of data now. i have 1tb for now but i will have more in a little bit. so i could use raid1 that is way more safer right? it makes a backup of the files from what i read. but in this case i will loose alot of disk space right?
RAID-1 would work. If you've only got 1TB of data, you'd be fine to mirror it with two drives.

Keep in mind that RAID isn't a replacement for backups. :)

---

### Post by RastaManPower on 2010-11-20
but if i have only 1 tb used. with raid i will have only 2 tb left of free space right? since it doubles the files into the drives

---

### Post by CharlesA on 2010-11-20
If you mirror it, you would have around 1TB of free space give or take.

See here: [http://www.ibeast.com/content/tools/RaidCalc/RaidCalc.asp](http://www.ibeast.com/content/tools/RaidCalc/RaidCalc.asp)

---

