---
title: "Printer paused, with IPP error"
date: 2007-08-03
forum: Hardware &amp; Laptops
---

### Post by bignickel on 2007-08-03
Hi, I'm trying to connect to a printer at work using my Feisty laptop.  The computer has an IP, and CUPS automatically detected it, but when I try to print it always says the printer is paused (even though it's not) and the printer status is "Paused: /usr/lib/cups/backend/ipp failed".  The printer is a Sharp Ar-C170.

Here's my /etc/cups/printers.conf
```
<Printer AR-C170FP>
Info 
Location Office
DeviceURI ipp://192.168.123.216:631/LPT1
State Stopped
StateMessage /usr/lib/cups/backend/ipp failed
StateTime 1186152592
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>

```

Here's the last bit of my /var/log/cups/error_log:
```
 [03/Aug/2007:10:48:42 -0400] cupsdAuthorize: Local authentication certificate 
not found!
E [03/Aug/2007:10:48:42 -0400] cupsdAuthorize: Local authentication certificate 
not found!
E [03/Aug/2007:10:48:42 -0400] cupsdAuthorize: Local authentication certificate 
not found!
E [03/Aug/2007:10:49:50 -0400] Resume-Printer: Unauthorized
E [03/Aug/2007:10:49:50 -0400] [Job 8] No %%BoundingBox: comment in header!
E [03/Aug/2007:10:49:52 -0400] [Job 8] Destination printer does not exist!
E [03/Aug/2007:10:49:52 -0400] PID 12195 (/usr/lib/cups/backend/ipp) stopped wit
h status 4!

```

There are lots and lots of those cupsdAuthorize messages in the log.  Any ideas?

---

