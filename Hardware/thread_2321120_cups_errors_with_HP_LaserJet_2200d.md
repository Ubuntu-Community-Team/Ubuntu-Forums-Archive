---
title: "cups errors with HP LaserJet 2200d"
date: 2016-04-20
forum: Hardware
---

### Post by ioctlz on 2016-04-20
I have an HP LaserJet 2200d that has worked fine for over 10 years. Its only connection is via parallel port.

Since getting a new computer (with no parallel port) and installing Kubuntu 14.04 on it this printer has not worked well at all.

The current problem is that when I try to print a 20 or so page PDF document from Acrobat Reader it does so very slowly (having like a 10 minute gap between printing pages with the printer light flashing the whole time). I see a steady stream of this /var/log/cups/error_log while this slow printing is happening:
D [20/Apr/2016:13:10:20 -0500] cupsd is not idle any more, canceling shutdown.
D [20/Apr/2016:13:10:20 -0500] [Job 53] Wrote 8192 bytes of print data...
D [20/Apr/2016:13:10:20 -0500] [Job 53] Read 8192 bytes of print data.
D [20/Apr/2016:13:10:20 -0500] cupsd is not idle any more, canceling shutdown.
D [20/Apr/2016:13:10:21 -0500] cupsd is not idle any more, canceling shutdown.
D [20/Apr/2016:13:10:26 -0500] [Job 53] Wrote 8192 bytes of print data...
D [20/Apr/2016:13:10:26 -0500] [Job 53] Read 8192 bytes of print data.
D [20/Apr/2016:13:10:26 -0500] cupsd is not idle any more, canceling shutdown.
D [20/Apr/2016:13:10:27 -0500] cupsd is not idle any more, canceling shutdown.

I intentionally edited my CUPS config to access this printer over parallel port after hearing that using USB to access a printer over a parallel-port-to-USB cable was more likely to be problematic:

From /etc/cups/printers.conf:
DeviceURI parallel:/dev/usb/lp0

Any help is appreciated.

Thanks,
Ivan

---

