---
title: "Cannot Mount Volume"
date: 2008-09-17
forum: Hardware
---

### Post by trebnoj on 2008-09-17
I'm trying to hook up an external hard drive (Calvalry USB) to my hardy desktop.  When I attempt to attach it I get the error attached to this post.  The drive is already formatted and apparently already contains 200 GB of recovered data.  The irony is that I was getting the same error before I got the new hard drive, so now I'm thinking the problem may have been with my computer rather than the hard drive... 

Can anybody offer me some advice?

---

### Post by IntuitiveNipple on 2008-09-17
As the messages says, the volume is marked as in-use. That happens when the device is disconnected or powered down before the operating system has had chance to flush unsaved data to the disk.

Attach it to a Windows PC and then use the command-line to run:
```

chkdsk /f d:

```
Where **d:** is the drive-letter given to the device.

Then use the Safely Remove Hardware icon in the Windows task-bar to flush data before disconnecting the drive.

---

