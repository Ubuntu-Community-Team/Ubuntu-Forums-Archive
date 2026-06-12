---
title: "Printer prints every page twice"
date: 2007-06-08
forum: Hardware &amp; Laptops
---

### Post by TheodoreWard on 2007-06-08
We have a networked Canon Image Runner 3300i that works except ir prints every page twice. There wasn't a default printer driver for it, so I downloaded one from the manufacturer (some SQUE something or other package) and the exact driver was there. When I got to add the printer I choose it as a "detected printer" and select the driver. I have tried deleting it and readding it with no change.
My other printers don't share this problem, just the Canon.

Any idea what would make a printer print everything twice?

printers.conf:

<Printer iR2200i-3300i>
Info iR2200i-3300i
Location IT Lounge
DeviceURI ipp://someyipaddress/ipp
State Idle
StateTime 1181162770
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>

---

### Post by Dedoimedo on 2007-06-08
Hello,
I have a Lexmark E232 printer that does not have any Linux drivers. So I am using HP PCL-6 ones. If I chose PCL-5, I would have multiple pages printed, test pages running wild etc. I suggest you try several other drivers that most closely resemble your family of printer. And try to test-print to see how it goes.
Dedoimedo

---

### Post by TheodoreWard on 2007-06-08
> **Dedoimedo said:**
> Hello,
I have a Lexmark E232 printer that does not have any Linux drivers. So I am using HP PCL-6 ones. If I chose PCL-5, I would have multiple pages printed, test pages running wild etc. I suggest you try several other drivers that most closely resemble your family of printer. And try to test-print to see how it goes.
Dedoimedo

Ok. I know that there is a driver that will work with this printer, but it has its own problems (always prints two ID sheets before every job) Plus the manufacturers driver gives me access to the "finishing" features like stapling. But I guess you have to go with whatever works best....

Thanks

Ted

---

