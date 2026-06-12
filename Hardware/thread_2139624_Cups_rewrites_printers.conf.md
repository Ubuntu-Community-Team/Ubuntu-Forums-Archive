---
title: "Cups rewrites printers.conf"
date: 2013-04-27
forum: Hardware
---

### Post by julien2233 on 2013-04-27
Hi to everybody,

[ubuntu/kubuntu 12.10 - 13.04]
Already spent two days trying to figure out what is the problem with cups.
I have a Toshiba e-Studio printer that works well in a network and Kubuntu 11.04 Oneiric. The est6550_Authentication is a filter installed in /usr/lib/cups/filter.
The ppd file is also provided by Toshiba and works fine. The printers.conf file in /etc/cups shows the reference to that filter. (i included the section related to the printer and the filters). 

However when I tried to install the printer with ubuntu/kubuntu 12.10-13.04, I don't manager to get the lines "filter" in the printers.conf file. Even worst, when I manually edit the printers.conf file, cups rewrite the file and erase the 2 lines starting with
```

Filter application/vnd.cups-raw 0 -
Filter application/vnd.cups-postscript 0 /usr/lib/cups/filter/est6550_Authentication

```

Please any help would be greatly appreciated. If anybody knows how to add the two filter lines in the file printers.conf...
Thanks a lot,
Julien


*Printers.conf that works perfectly on kubuntu 11.04*
```

DefaultPrinter e-STUDIO2040C>
Info e-STUDIO2040C
Location xxxxxxxxxx
MakeModel TOSHIBA ColorMFP
DeviceURI socket://192.168.1.11:9100
State Idle
StateTime 1365611665
Reason media-low-report
Type 8401116
Product (TOSHIBA e-STUDIO2040C)
Filter application/vnd.cups-raw 0 -
Filter application/vnd.cups-postscript 0 /usr/lib/cups/filter/est6550_Authentication
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
Option page-bottom 46
Option saturation 94
Attribute marker-colors \#000000,#00FFFF,#FF00FF,#FFFF00,none
Attribute marker-levels 75,100,100,100,-3
Attribute marker-names Black Toner,Cyan Toner,Magenta Toner,Yellow Toner,Waste Toner
Attribute marker-types toner,toner,toner,toner,wasteToner
Attribute marker-change-time 1365611664
</Printer>

```

---

