---
title: "mount cdrom: no medium found on /dev/sr0"
date: 2010-06-07
forum: Hardware
---

### Post by 80aless on 2010-06-07
Hi people, 
Tedious problem: how to mount my cd/dvd rom? I get mount: no medium found on /dev/sr0 :

```
mount -t iso9660 /dev/cdrom /media/cdrom/
mount: no medium found on /dev/sr0

```
same with /dev/cdrw, /dev/scd0, /dev/dvd, or without -t iso9660

```
mount /dev/scd0 /media/cdrom
mount: /dev/sr0: unknown device
```

fstab does not contain anything useful, and could you suggest a proper line to add to fstab?
Thanks,
Alex

---

