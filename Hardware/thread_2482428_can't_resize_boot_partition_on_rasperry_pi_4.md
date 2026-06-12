---
title: "can't resize boot partition on rasperry pi 4"
date: 2022-12-30
forum: Hardware
---

### Post by bjlockie on 2022-12-30
I have a USB flash drive that I dd'ed to it a micro SD card that has ubuntu-server for the raspberry pi 4.
I need to uncrompress the Linux kernel on it but the boot partition was only 256MB.
I tried to resize it with KDE Partition Manager but it would let me resize that partition so I copied it to a bigger partition and deleted it.


```
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdd3       253M  253M  1.0K 100% /media/rjl/system-boot
```

But KDE Partition Manager says the partition is 1GB (small screenshot below):
[ATTACH=CONFIG]291493[/ATTACH]

My theory is that even though the file system says it is fat32, it is really fat12 which has a 256MB limit.

---

### Post by bjlockie on 2022-12-30
I backed it up and reformatted as fat32 and now it is 1GB.
I can't resize it though. :-(
Maybe the partition manager can't resize fat partitions.

---

