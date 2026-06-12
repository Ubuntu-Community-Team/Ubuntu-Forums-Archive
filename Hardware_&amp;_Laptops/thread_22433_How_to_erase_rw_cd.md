---
title: "How to erase rw cd?"
date: 2005-03-27
forum: Hardware &amp; Laptops
---

### Post by drasko on 2005-03-27
Neither Graveman or K3B would erase my rw cd? How to do this?
Maybe I should use cdrecord from the commandline, but how to do this - cdrecord -scanbus is giving me: 
cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI driver.

And  cdrecord -scanbus dev=ATAPI is giving me:
scsidev: 'ATAPI'
devname: 'ATAPI'
scsibus: -2 target: -2 lun: -2
Warning: Using ATA Packet interface.
Warning: The related libscg interface code is in pre alpha.
Warning: There may be fatal problems.
Error trying to open /dev/hda exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hda exclusively (Device or resource busy)... retrying in 1 second.
and so on...

What is supposed to be wrong?

Drasko

---

### Post by drasko on 2005-03-27
Whoops -- just found it: my cd was mounted, so it was bussy. For the erasing to be conducted,  cd should be umounted! I suppose the same goes for writeing, right?

Drasko

---

