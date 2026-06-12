---
title: "Boot hangs on &quot;USB Mass storage device registered&quot;"
date: 2008-10-20
forum: Hardware
---

### Post by fizban9 on 2008-10-20
Just some quick backgroud.  I have an Asus Eee PC 701.  It's running Hardy Heron and its running great.

Ok, so the problem I have is intermittent, about 9 out of 10 boots.  It gets to the point where it says "USB Mass Storage device registered" and then sits there for anything from 10 seconds to 3 minutes.  Whats even weirder is that the logs doesn't even show the pause.  Heres an excerpt from /var/log/dmesg

```

[   20.765405] Initializing USB Mass Storage driver...
[   20.773371] scsi2 : SCSI emulation for USB Mass Storage devices
[   20.775084] usbcore: registered new interface driver usb-storage
[   20.775189] USB Mass Storage support registered.
[   20.775486] usb-storage: device found at 2
[   20.775492] usb-storage: waiting for device to settle before scanning

```

Where is hangs is at 20.775189.  The log shows no pause, but I swear it hung at that point for several minutes.

Any ideas?

---

