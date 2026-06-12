---
title: "Broken Epson USB Printer (Cups Upgrade?)"
date: 2008-01-10
forum: Hardware &amp; Laptops
---

### Post by pwaldo on 2008-01-10
Hi all,

I am running Kubuntu Gutsy i386 and my Epson Stylus Photo 1280 USB printer was working fine.  It now no longer works, which I think may be due to a cups upgrade.  IIRC, I added either backports or gutsy-proposed to my sources.list and it all stopped working.

The kernel knows the hardware is there:
```

paul@office:~$ lsusb|grep Epson
Bus 001 Device 002: ID 04b8:0005 Seiko Epson Corp. Stylus Printer
paul@office:~$ /usr/lib/cups/backend/usb
direct usb://EPSON/Stylus%20Photo%201280 "EPSON Stylus Photo 1280" "EPSON Stylus Photo 1280 USB #1" "MFG:EPSON;CMD:ESCPL2,BDC,D4;MDL:Stylus Photo 1280;CLS:PRINTER;DES:EPSON Stylus Photo 1280;&#65533;&#65533;"
paul@office:~$ /usr/lib/cups/backend/epson
direct epson:/dev/usb/lp0 "EPSON USB Printer" "Gutenprint USB Printer #1"

```

After the update, all printing to this printer stopped.  I deleted the printer and tried to re-add it, but the Local Printer type is greyed out.  I even tried to add it with the local CUPS web interface, which worked, but I am back to getting no printed output!  When I use the Epson Printer Utilities from Printer Management, I get an error dialog saying "Unsupported connection type: epson"

Here is the relevent section from /etc/cups/printers.conf
```

<Printer epson>
Info Epson Stylus Photo 1280
Location Paul's Office
DeviceURI epson:/dev/usb/lp0
State Idle
StateTime 1199978573
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
and here are the cups packages I have installed:
```
paul@office:~$ dpkg -l cups\* |grep "ii"
ii  cups-pdf                     2.4.6-3ubuntu10  PDF printer for CUPS
ii  cupsys                       1.3.2-1ubuntu7.4 Common UNIX Printing System(tm) - server
ii  cupsys-bsd                   1.3.2-1ubuntu7.4 Common UNIX Printing System(tm) - BSD comman
ii  cupsys-client                1.3.2-1ubuntu7.4 Common UNIX Printing System(tm) - client pro
ii  cupsys-common                1.3.2-1ubuntu7.4 Common UNIX Printing System(tm) - common fil
ii  cupsys-driver-gutenprint     5.0.1-0ubuntu8   printer drivers for CUPS

```

Thanks in advance!

---

