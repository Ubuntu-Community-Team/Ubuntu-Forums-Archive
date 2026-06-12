---
title: "DVD-RW drive not being properly recognized"
date: 2009-06-09
forum: Hardware
---

### Post by BinaryMn on 2009-06-09
```
chris@chris-desktop:~$ dmesg | grep -i dvd
[    5.152368] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-H10N, JL10, max UDMA/33
[    5.237056] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-H10N  JL10 PQ: 0 ANSI: 5
[    5.240892] sr0: scsi3-mmc drive: 37x/37x writer dvd-ram cd/rw xa/form2 cdda tray

```

The DVD drive in question is connected via IDE, not SCSI. This is a problem for me because I get crap read/write speeds and can't enable DMA. Other than that, it mounts and detects media okay.

How do I fix this?

---

