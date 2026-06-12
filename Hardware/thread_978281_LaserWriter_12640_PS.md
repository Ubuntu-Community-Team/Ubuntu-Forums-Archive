---
title: "LaserWriter 12/640 PS"
date: 2008-11-11
forum: Hardware
---

### Post by matthudson on 2008-11-11
I've already followed the instructions @ [https://help.ubuntu.com/community/AppleTalk](https://help.ubuntu.com/community/AppleTalk)

The printer appears, but it won't print a test page or anything else

Ubuntu 8.10

nbplkup:
LaserWriter 12/640 PS:LaserWriter                        65280.129:129

printers.conf
```
# Printer configuration file for CUPS v1.3.9
# Written by cupsd on 2008-11-11 15:39
<Printer LW>
Info LW
Location Local zone
DeviceURI pap://LaserWriter%2012%2F640%20PS
State Idle
StateTime 1226378340
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

Any and all help appreciated

---

