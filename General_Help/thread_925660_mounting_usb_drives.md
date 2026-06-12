---
title: "mounting usb drives"
date: 2008-09-20
forum: General Help
---

### Post by cyclobs on 2008-09-20
hey guys, 

got a usb device here but it's not coming up on the system.

did a lsusb and got this
```

Bus 002 Device 010: ID 0471:084e Philips

```

can i mount that drive?

---

### Post by mb_webguy on 2008-09-20
Does it show up with "sudo fdisk -l"?

---

### Post by cyclobs on 2008-09-20
> **mb_webguy said:**
> Does it show up with "sudo fdisk -l"?

nope, doesn't show any of my other usb drives. just my partitions

---

### Post by mb_webguy on 2008-09-20
It should show all disks on your system and the partitions on those disks, whether mounted or not.  If you have a USB drive plugged in and it is recognized by the OS (which the entry in lsusb seems to indicate it is), then it should be shown by fdisk.

---

