---
title: "External USB not mounting.."
date: 2008-04-06
forum: Hardware &amp; Laptops
---

### Post by rootlinuxusr on 2008-04-06
i'm having problems reading my USB-device. It won't load into fstab, and if I leave it plugged in when booting, it hangs the system(regardless of OS choice...XP/Kubuntu) if I unplug it however, it begins loading normally again...It's worked before, but now even qtparted won't load it.

Mount doesn't produce it in it's list of loaded currently, dmesg produces: 
```
usb 1-3: new high speed USB device using ehci_hcd and address 5
[38655.611128] usb 1-3: configuration #1 chosen from 1 choice
[38655.611460] scsi8 : SCSI emulation for USB Mass Storage devices
[38655.638405] usb-storage: device found at 5
[38655.638410] usb-storage: waiting for device to settle before scanning
[38657.716794] usb-storage: device scan complete
[38658.291884] scsi 8:0:0:0: Direct-Access        & h       3w   ? 8     &    PQ: 0 ANSI: 2
[38658.308683] sd 8:0:0:0: [sdb] 583170332 512-byte hardware sectors (298583 MB)
[38658.310370] sd 8:0:0:0: [sdb] Write Protect is off
[38658.310379] sd 8:0:0:0: [sdb] Mode Sense: 00 00 00 00
[38658.310381] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[38658.313736] sd 8:0:0:0: [sdb] 583170332 512-byte hardware sectors (298583 MB)
[38658.315411] sd 8:0:0:0: [sdb] Write Protect is off
[38658.315417] sd 8:0:0:0: [sdb] Mode Sense: 00 00 00 00
[38658.315421] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[38658.315428]  sdb:
[38658.315428]  sdb:<6>usb 1-3: reset high speed USB device using ehci_hcd and address 5

```


Any ideas? I wouldn't really care normally, but this is a 500gb drive. =/

---

### Post by odin1965 on 2008-04-08
If you can get it loaded, try reformatting it. I've had a couple that did that and when I reformatted them, they were fine. I assumed it developed a new unmarked bad sector that the new format would tag an not use.

If you can't mount it, format it in digital camera.

---

