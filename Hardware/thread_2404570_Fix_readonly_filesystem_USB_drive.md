---
title: "Fix readonly filesystem USB drive"
date: 2018-10-25
forum: Hardware
---

### Post by taghreedaa on 2018-10-25
I tried to format the USB using gparted and I get this error:

```
Input/output error during write on /dev/sdc
```

and tried disk management to delete the partition of the USB but now worked also
[ATTACH=CONFIG]281449[/ATTACH]

---

### Post by TheFu on 2018-10-26
Storage devices need to have a partition table, then a partition, then the partition can be formatted with a file system.
gparted will let you create a fresh partition table, then create a partition and finally format that partition with one of the more popular file systems.

If that isn't working, perhaps the flash drive is about to die?  They fail sometimes and usually not at a convenient time. Not all USB drives are compatible with all USB controllers.  I'd try a USB2 port if you were using a USB3 port too.  USB2 ports have much better support.

If you run **sudo fdisk -l** and post the text output inside "code tags", we might be able to provide suggestions.  Text is preferred over images. Some people pay for internet by the byte.

---

