---
title: "DVD drive failure when using K3B"
date: 2008-09-15
forum: Hardware
---

### Post by El Rogueo on 2008-09-15
Hi all,

Recently got possession of a new old computer, and in trying to put kubuntu on it I'm having the following problem:

When I boot up kubuntu, the dvd drive can open and close, and works just fine (it is a TS-H653A, but I don't know what that means since the drive cover is missing, maybe toshiba, idk). But when I open K3B, the drive immediately stops working. If there's a DVD in the tray (previously openable in VLC, etc) it immediately stops recognizing the DVD, and the drive won't open or close.

I tried to enable it in Disk & File Systems (google advice recommended) and got this error:

```
An error occurred while enabling /media/cdrom1.
The system reported: mount: block device /dev/scd1 is write-protected, mounting read-only
mount: you must specify the filesystem type
```

Following other google advice, I tried doing hdparm on it and got the following output:

```
/dev/scd1:
IO_support = 0 (default)
16-bit)
HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
HDIO_GET_DMA failed: Inappropriate ioctl for device
HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
readonly = 0 (off)
readahead = 256 (on)
HDIO_GETGEO failed: Inappropriate ioctl for device

```

tl;dr I'm not sure why I'm having this problem, and it's not hardware related since the drive has worked fine in previous installations.

Any ideas?

---

