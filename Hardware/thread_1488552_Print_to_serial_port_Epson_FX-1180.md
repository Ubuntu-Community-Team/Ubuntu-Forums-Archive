---
title: "Print to serial port Epson FX-1180"
date: 2010-05-20
forum: Hardware
---

### Post by resolv_25 on 2010-05-20
I didn't see this topic or other proper advice and spent some hours figuring how to print a dot matrix printer on a serial port.
In my case it was an Epson FX-1180.
(this is on Ubuntu 8.04. I guess it is working on another versions as well)

1. System-Administration-Printing
2. New Printer-Serial port1 (or other ports if you have more ports)
**Set Baud Rate to Default**
First option was 115200, and it didn't work properly.
The other options are also default.
3. Choose Epson  (or another printer) - 9 pin
4. Name of printer - Apply
Device URI shall be like this: 
**serial:/dev/ttyS0**

I have 3-4 ports with the PCI card Kouwell KW222N-2 and it works properly with such a setup.
:guitar:

So, maybe will someone need this information.

---

