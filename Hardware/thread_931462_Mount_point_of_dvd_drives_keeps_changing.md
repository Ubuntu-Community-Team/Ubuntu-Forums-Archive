---
title: "Mount point of dvd drives keeps changing"
date: 2008-09-27
forum: Hardware
---

### Post by wild_oscar on 2008-09-27
I have two dvd drives:
- SATA dvd rom 
- IDE dvd-rw

My /etc/fstab is like this:
```

/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/scd0 /media/dvdrw udf,iso9660 user,noauto 0 0

```

However, when I have a cd/dvd in the drive, the mount point of the same drive keeps changing.

Example:
1) I put a movie dvd in the DVD drive, and it is mounted on /media/cdrom0

2) On what to seems to be a random behaviour, on consecutive reboots (and without taking the dvd out), the dvd appears mounted either on /media/cdrom0 or /media/dvdrw.

This is very inconvenient as, for example, xine, needs to have the name of the dvd drive defined. So if I define it as /media/cdrom0, sometimes the dvd will play and other times it won't (and I'll have to either phisically change my movie to the other drive or change the preferences).

Any idea for this behaviour?

---

### Post by wild_oscar on 2008-10-14
Does anyone have the answer for this?

---

