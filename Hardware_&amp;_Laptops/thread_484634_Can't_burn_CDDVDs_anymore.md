---
title: "Can't burn CD/DVDs anymore"
date: 2007-06-26
forum: Hardware &amp; Laptops
---

### Post by gaten on 2007-06-26
I tried to burn a CD (ISO specifcally) tonight and for some unknown reason it won't work. I've been burning CDs in Nautalis via the "Write to Disk" option for months; in fact I just burned one 2 days ago without problems.

The error I get is: 
> Please replace the disc in the drive with a supported disc with at least 57.1 MiB free.  The following disc types are supported:
DVD+R DL, DVD-R, DVD-RW, DVD+R, DVD+RW, CD-R, CD-RWThe disk is a 700MB CD-R Magnavox, so there isn't a space issue. And I've tried about 15 different disks (no, really), with the same error. DVDs are no exception. Dmesg gives me this:
```
[540774.496000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[540774.496000] ide: failed opcode was: unknown
[540774.496000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[540774.496000] end_request: I/O error, dev hdc, sector 0
[540774.496000] FAT: unable to read boot sector

```

Does anyone have any ideas?

---

### Post by princeza on 2007-10-26
> **gaten said:**
> I tried to burn a CD (ISO specifcally) tonight and for some unknown reason it won't work. I've been burning CDs in Nautalis via the "Write to Disk" option for months; in fact I just burned one 2 days ago without problems.

The error I get is: 
The disk is a 700MB CD-R Magnavox, so there isn't a space issue. And I've tried about 15 different disks (no, really), with the same error. DVDs are no exception. Dmesg gives me this:
```
[540774.496000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[540774.496000] ide: failed opcode was: unknown
[540774.496000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[540774.496000] end_request: I/O error, dev hdc, sector 0
[540774.496000] FAT: unable to read boot sector

```

Does anyone have any ideas?

Completely the same issue here.
:confused:

---

