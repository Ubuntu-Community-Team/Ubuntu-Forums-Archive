---
title: "Persistent device-path mapping"
date: 2015-08-02
forum: Hardware
---

### Post by dmytro2 on 2015-08-02
Hello everyone) I wonder is there a way to set persistent mapping of storage devices to paths? For an instance I have a storage device like external HD or a USB flash and I want to unplug it and then plug it back so that all absolute paths would be still valid.
Thanks)

---

### Post by weatherman2 on 2015-08-02
You mean you want the file system path like /media/ubuntu/mydrive or whatever always to be the same?

Or you want the device IDs like /dev/sda or /dev/sdb always to be the same?

You can use UUID numbers to reference partitions instead of /dev/sda or /dev/sdb - the UUID number will always be the same.  Or, use Gparted to set a label for each partition and then use /dev/disk/by-label/MYLABEL (where "MYLABEL" is whatever label you have added to a partition).  "MYLABEL" also is used under /media when you mount partitions using the Gui with your mouse.

---

