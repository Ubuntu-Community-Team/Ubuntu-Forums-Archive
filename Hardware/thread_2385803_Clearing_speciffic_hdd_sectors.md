---
title: "Clearing speciffic hdd sectors"
date: 2018-02-25
forum: Hardware
---

### Post by a09fc4b1 on 2018-02-25
How wold i go about clearing certain sectors of my hdd (specifficaly the first). This is linked to my previous issue of my fat32 hdd turning into a linux swap disk(note: rewriting the partition table did absoluteley nothing and it even showed it as fat32 but when mounting it says: unrecognized file system)

Sincereley a09fc4b1

---

### Post by oldfred on 2018-02-25
This is probably the safest:
[https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive](https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive)

You can use dd, but dd's nickname is DataDestroyer as any typo totally erases data. Some systems change drive order on reboot and a user does not pay attention and erases main drive or just does a typo. And there is no undo or recovery.

---

