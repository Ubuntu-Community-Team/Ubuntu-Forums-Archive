---
title: "permanency of dual O.S. on single HDD"
date: 2014-12-06
forum: Hardware
---

### Post by newvan on 2014-12-06
I have a HDD with Win.O.S.(500 GB) and Ubuntu O.S.(500GB).When i installed Ubuntu, i was warned that the resizing of the HDD was permanent. Can i now resize the HDD to 1000 GB  Ubuntu O.S. , or does permanent means permanent as in forever? regards, newvan.

---

### Post by Bashing-om on 2014-12-06
newvan; Hi !

It is only permanent until you change it.
That is the purpose of partitioning tools ( GParted, GUI) .
Or fresh install of an operating system ( erase disk and install ubuntu).

[INDENT][INDENT]just depends on
[INDENT][INDENT][INDENT]what you want to do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by weatherman2 on 2014-12-06
Perhaps what was meant by "permanent" was that it will be difficult to change the partition sizes once you install Ubuntu.  That is true.  Ubuntu's installer tends to make an "extended partition" on hard drives, whereas Windows uses a primary partition.  Trying to resize one or the other is probably difficult now.

It is still POSSIBLE to resize all your partitions now without a complete re-install of Ubuntu - it's just a big pain, depending on how exactly your partitions wound up being created.

You can always erase the whole hard disk and start over with whatever partition sizes you wish, but of course that means a lot of work re-installing everything.

---

### Post by oldfred on 2014-12-06
I would backup Windows, and convert that partition to a data partition as ext4. If you reformat all data in it will be lost, so backups are important with any partition change.

You then can mount data partition into fstab and use it for some or most of your data.

---

