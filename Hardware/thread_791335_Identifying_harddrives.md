---
title: "Identifying harddrives"
date: 2008-05-12
forum: Hardware
---

### Post by keirlawson on 2008-05-12
I think one of my hard drives is failing (I have one as a home partition and the other as root).  dmesg produces messages like:

```
[ 9192.552837] ata5.01: status: { DRDY }
[ 9192.552850] ata5: soft resetting link
[ 9192.895427] ata5.01: configured for PIO0
[ 9192.895437] ata5: EH complete
[ 9197.052591] ata5.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 9197.052600] ata5.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
[ 9197.052601]          cdb 1e 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 9197.052602]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
```

It isn't really reproducible, it only happens sometimes.

So my question is, how do i work out what harddrive "ata5" or "ata5.01" is?

---

### Post by sdennie on 2008-05-12
I'm not sure how to map that dmesg back to a physical device but, you may want to install:

```

sudo apt-get install smartmontools

```

That will allow you to get at the data that your disk keeps about it's general health with:

```

sudo smartctl --all /dev/sda

```

Replace /dev/sda with your device names.  You'll want to check the man page for smartctl and probably google a bit to understand the data but, that should help in determining if your disks are dieing.

---

