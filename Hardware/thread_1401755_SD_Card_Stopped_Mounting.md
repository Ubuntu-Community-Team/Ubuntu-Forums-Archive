---
title: "SD Card Stopped Mounting"
date: 2010-02-08
forum: Hardware
---

### Post by Steviebe on 2010-02-08
Last week, I had no problem mounting my SD card in my card reader on my laptop, but this morning it doesn't work anymore.

dmesg shows things like this:
```
[  339.673636] end_request: I/O error, dev mmcblk0, sector 3
[  339.674119] mmcblk0: error -84 transferring data, sector 4, nr 4, card status 0x900
[  339.674126] end_request: I/O error, dev mmcblk0, sector 4
[  339.674555] mmcblk0: error -84 transferring data, sector 5, nr 3, card status 0x900
[  339.674562] end_request: I/O error, dev mmcblk0, sector 5
[  339.674990] mmcblk0: error -84 transferring data, sector 6, nr 2, card status 0x900
[  339.674997] end_request: I/O error, dev mmcblk0, sector 6
[  339.675426] mmcblk0: error -84 transferring data, sector 7, nr 1, card status 0x900
[  339.675433] end_request: I/O error, dev mmcblk0, sector 7
```

Any idea how I can fix this?

Edit:  I just tried another card reader.  The card seems to work fine.

---

### Post by Steviebe on 2010-02-08
Bump...anyone out there?

---

