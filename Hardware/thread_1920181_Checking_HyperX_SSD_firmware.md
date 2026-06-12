---
title: "Checking HyperX SSD firmware"
date: 2012-02-04
forum: Hardware
---

### Post by ubuntukid on 2012-02-04
Is there some way I can check what firmware version is installed on my Kingston HyperX SSD? Their firmware site only has software and instructions for windows. Is there any way to upgrade firmware using Ubuntu?

---

### Post by Chris_82 on 2012-06-21
> **ubuntukid said:**
> Is there some way I can check what firmware version is installed on my Kingston HyperX SSD?

Yes, check here: [https://wiki.ubuntu.com/MagicFab/SSDchecklist](https://wiki.ubuntu.com/MagicFab/SSDchecklist)
The terminal command is:
```
sudo hdparm -I /dev/sda | grep Firmware
```

> **ubuntukid said:**
> Their firmware site only has software and instructions for windows. Is there any way to upgrade firmware using Ubuntu?
Yes, [download the zip file from the Linux section]("http://www.kingston.com/en/support/technical/downloads?product=SH100S3&filename=SH100S3fw501"). It is right below the Windows section.
Extract the zip file and follow the instructions from the included pdf.

---

