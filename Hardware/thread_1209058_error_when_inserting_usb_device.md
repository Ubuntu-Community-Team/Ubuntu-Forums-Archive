---
title: "error when inserting usb device"
date: 2009-07-09
forum: Hardware
---

### Post by pythonscript on 2009-07-09
When I insert my ntfs-formatted flash drive, this error pops up, and the device will not mount automatically. I get two errors that continually pop up, and I'm forced to mount the drive manually from the command line using
```

sudo mountpy /dev/sdb1

```Also, I cannot write to the device. Error messages comes up saying it's read only. This device contains all the ISO images of my Unix/BSD/Windows systems, so I'm hoping to not have to reformat the whole thing... Any ideas? I attached the error messages for more details. 

First error message:

```

Cannot mount volume.

Error [I]org.freedesktop.Hal.Device.UnknownError.

[/I]libhal.c 1399 : wrong reply from hald. Expecting an array.
org.freedesktop.Hal.Device.Volume.InvalidMountOption

```Second error message:
```

Unable to mount TRANSCEND

DBus error org.freedesktop.DBus.Error.NoReply: Message
did not recieve a reply (timeout by message bus)

```Thanks for the help!

---

