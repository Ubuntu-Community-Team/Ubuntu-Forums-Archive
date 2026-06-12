---
title: "Canon i560 Cups driver for usb connected printer"
date: 2008-03-17
forum: Hardware &amp; Laptops
---

### Post by LarryJ2 on 2008-03-17
Memo to users of the old but thankfully refillable Canon i560 bubble jet printer:

There is a driver for it in the package gutenprint.  Install it with

```
sudo apt-get install cupsys-driver-gutenprint
```
Then  you should see  the driver listed during the Add Printer dialog using the CUPS Web Admin page which is available in your web browser (firefox)  at:
> [http://localhost:631/](http://localhost:631/)
After adding this printer, you should see something similar to
> 
Description: Canon i560 inkjet color printer
Location: In LJs room attached to Lian3
Printer Driver: Canon i560 - CUPS+Gutenprint v5.0.1 Simplified
Printer State: idle, accepting jobs, published.
Device URI: canon_usb:/dev/usb/lp0

If a test page doesn't print (maybe you see "broken pipe" error messages),  try putting the Canoni560s on the parallel port.  In that case, the last line in the quote above will read
> Device URI: parallel:/dev/lp0

Also there is a driver available from Canon's Japanese website as an .rpm.   I converted it to a .deb using the program "alien".  I could never get the driver working properly when the printer was connected as USB.  Search for **bjfilterpixus560i-2.4-0.i386.rpm**
and **bjfiltercups-2.4-1.i386.rpm**.  Or try  ```
ftp://download.canon.jp/pub/driver/bj/linux/ 
``` Then, for example using the first file,  
```
sudo apt-get install alien
sudo alien /pathToDotRpmFile/bjfilterpixus560i-2.4-0.i386.rpm
```
The output is a  .deb file which can be installed with the standard Ubuntu/Debian package tools.  My information indicates both files have to be installed.  Apparently,  *pixus* is the brand name  when this printer was  sold in Japan.

---

