---
title: "chkdsk error on boot"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by Gauntlet on 2009-01-28
I'm trying to boot ubuntu and everytime it gets to checking the partition it says I need to run a chkdsk /r on the drive in windows and then it should install fine. I ran the disk check and it tells me again to run chkdsk. I also installed ubuntu to a partitioned drive using wubi. Can anyone help me?

---

### Post by cariboo on 2009-01-28
In a lot of cases you have to run chcdsk -r twice after resizing the partition.

Jim

---

### Post by Gauntlet on 2009-01-29
Thankyou. I just re partitioned the drive and re installed ubuntu and it worked perfectly.

---

