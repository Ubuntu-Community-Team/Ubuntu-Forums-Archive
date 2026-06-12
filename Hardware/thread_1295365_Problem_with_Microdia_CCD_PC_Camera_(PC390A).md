---
title: "Problem with Microdia CCD PC Camera (PC390A)"
date: 2009-10-19
forum: Hardware
---

### Post by jhahoneyk on 2009-10-19
lsusb shows me the following

```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 005: ID 0c45:607c Microdia CCD PC Camera (PC390A)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

I googled for the webcam and found out its listed in [http://cateee.net/lkddb/web-lkddb/USB_GSPCA_SONIXJ.html](http://cateee.net/lkddb/web-lkddb/USB_GSPCA_SONIXJ.html) so it should be supported in the Linux kernel.

I tried to do "modprobe gspca_sonixj" but it isn't working. It might be because I installed some other version of the driver by following instructions at [http://ubuntuforums.org/showpost.php?p=7456689&postcount=4](http://ubuntuforums.org/showpost.php?p=7456689&postcount=4)

Any idea what should I do? Is modprobe enough or I've to do some insmod thingy also?

Edit:there is a file /dev/video0 . Confirmed after deleting, modprobe, and then reboot, its still there ...

---

### Post by ManfredKlinglmair on 2010-06-10
Same problem here! Please help!

---

