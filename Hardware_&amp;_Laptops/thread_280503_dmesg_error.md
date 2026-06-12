---
title: "dmesg error"
date: 2006-10-19
forum: Hardware &amp; Laptops
---

### Post by dmsn on 2006-10-19
Hey i just saw some errors on dmesg:

dmesg:
17180497.316000] hda: tray open
[17180497.316000] end_request: I/O error, dev hda, sector 0
[17180497.316000] Buffer I/O error on device hda, logical block 0
[17180497.316000] hda: tray open
[17180497.316000] end_request: I/O error, dev hda, sector 4
[17180497.316000] Buffer I/O error on device hda, logical block 1
[17180497.316000] hda: tray open
[17180497.316000] end_request: I/O error, dev hda, sector 8
[17180497.316000] Buffer I/O error on device hda, logical block 2
[17180497.316000] hda: tray open
[17180497.316000] end_request: I/O error, dev hda, sector 12
[17180497.316000] Buffer I/O error on device hda, logical block 3
[17180497.316000] hda: tray open
[17180497.316000] end_request: I/O error, dev hda, sector 16
[17180497.316000] Buffer I/O error on device hda, logical block 4
[17180497.320000] hda: tray open
[17180497.320000] end_request: I/O error, dev hda, sector 20
[17180497.320000] Buffer I/O error on device hda, logical block 5
[17180497.320000] hda: tray open
[17180497.320000] end_request: I/O error, dev hda, sector 24
[17180497.320000] Buffer I/O error on device hda, logical block 6
[17180497.320000] hda: tray open
[17180497.320000] end_request: I/O error, dev hda, sector 28
[17180497.320000] Buffer I/O error on device hda, logical block 7
[17180497.320000] hda: tray open
[17180497.320000] end_request: I/O error, dev hda, sector 32
[17180497.320000] Buffer I/O error on device hda, logical block 8
[17180497.324000] hda: tray open
[17180497.324000] end_request: I/O error, dev hda, sector 36
[17180497.324000] Buffer I/O error on device hda, logical block 9
[17180497.324000] hda: tray open
[17180497.324000] end_request: I/O error, dev hda, sector 40
[17180497.324000] hda: tray open
[17180497.324000] end_request: I/O error, dev hda, sector 44
[17180497.324000] hda: tray open
[17180497.324000] end_request: I/O error, dev hda, sector 48
[17180497.328000] hda: tray open
[17180497.328000] end_request: I/O error, dev hda, sector 52
[17180497.328000] hda: tray open
[17180497.328000] end_request: I/O error, dev hda, sector 56
[17180497.328000] hda: tray open
[17180497.328000] end_request: I/O error, dev hda, sector 60
[17180497.328000] hda: tray open
[17180497.328000] end_request: I/O error, dev hda, sector 0
[17180497.332000] hda: tray open
[17180497.332000] end_request: I/O error, dev hda, sector 4
[17180497.332000] hda: tray open
...................

What about this i dont even use hda on my laptop cuz i think i 
only have sata (sda1 and sda2)?

dmsn@lappen:/proc$ cat partitions
major minor  #blocks  name

   8     0   78150744 sda
   8     1    2931831 sda1
   8     2   75216330 sda2
 253     0    2931831 dm-0
 253     1   75216330 dm-1
dmsn@lappen:/proc$




thanks

---

