---
title: "DVD-R unable to burn after upgrade to Edgy"
date: 2006-11-17
forum: Hardware &amp; Laptops
---

### Post by mbertini on 2006-11-17
After upgrading from 6.06 to 6.10 (edgy) my CD/DVD burner has stopped to burn DVD-R.

I'm using an Acer Aspire 1800 with an LG HL-DT-ST DVDRAM GSA-4080N CD/DVD burner, that worked perfectly before the upgrade.

Now, when I try to burn a DVD-R (or I insert a blank DVD-R) I get the following messages in the syslog:

```
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
Nov 17 15:51:24 matrix kernel: [17185387.784000] hdb: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Nov 17 15:51:24 matrix kernel: [17185387.784000] ide: failed opcode was: unknown
Nov 17 15:51:24 matrix kernel: [17185387.784000] end_request: I/O error, dev hdb, sector 0
```

If I reboot under Windows the DVD-R can be burned. 
If I insert an already written DVD-R, of the same brand of the blank DVD-R, I can read them.

---

