---
title: "Kingston USB Stick stopped working"
date: 2007-03-01
forum: Hardware &amp; Laptops
---

### Post by Stuggi on 2007-03-01
I just transferred some files with my Kingston USB Flashdisk from a windtendo box to my laptop running edgy. Suddenly neither of them seem to be able to mount the flashdisk. Both of them recognizes it, but I can't open it or format it. 
After plugging the stick in on my laptop it appears under the computer view, but when I open it it gives me a mount error. When I run "dmesg | tail" I get the following:
```
sstorholm@Phoenix:~$ dmesg | tail
[17179676.120000] sd 0:0:0:0: SCSI error: return code = 0x8000002
[17179676.120000] sda: Current: sense key: Medium Error
[17179676.120000]     Additional sense: No additional sense information
[17179676.120000] Info fld=0x0
[17179676.120000] end_request: I/O error, dev sda, sector 184
[17179676.284000] sd 0:0:0:0: SCSI error: return code = 0x8000002
[17179676.284000] sda: Current: sense key: Medium Error
[17179676.284000]     Additional sense: No additional sense information
[17179676.284000] Info fld=0x0
[17179676.284000] end_request: I/O error, dev sda, sector 192

```

---

### Post by Stuggi on 2007-03-02
Bump...

---

