---
title: "HP Officejet 6700 Premium"
date: 2013-09-14
forum: Hardware
---

### Post by Mdh3MHY on 2013-09-14
Hi all,

I have managed to get my home printer working and am able to print documents, however I now wish to scan documents directly onto my laptop - I don't want to keep turning on the desktop PC, scanning in, then transferring via USB stick. I read some instructions on the ubuntu website and opened up the hp-setup which was already installed. I tried the second option (wireless) since this is the setup I wish to use and nothing could be found; following this I also tried the other functions to no avail - I cannot work out what is causing the problem since I read that this printer is compatible for such uses.

Here is the code from terminal:
```
:~$ sudo hp-setup[sudo] password for [user]: 


HP Linux Imaging and Printing System (ver. 3.12.2)
Printer/Fax Setup Utility ver. 9.0


Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


Searching on USB bus...
error: No devices found on bus: usb
Searching... (bus=net, timeout=5, ttl=4, search=(None) desc=0, method=mdns)
error: No devices found on bus: net
Searching... (bus=usb, search=(None), desc=0)
error: No devices found on bus: usb



```

Any advice on how to get this working? I am using ubuntu 12.04.

Thanks.

---

### Post by qamelian on 2013-10-09
I have the 6600 and was unable to get Ubuntu to recognize the scanner until I installed and ran xsane from the Ubuntu repos. After running xsane once and letting it detect the 6600, the scanner now works fine with the default Simple Scan.

---

### Post by Mdh3MHY on 2013-10-10
I installed xsane from the software centre and let it run, however it failed and came up with this message:
[IMG]http://screencloud.net/img/screenshots/74b7eb8589debc9efe0e2da2ba0cd750.png[/IMG]

---

### Post by Yellow Pasque on 2013-10-10
"You have selected Ubuntu 12.04 using the HP Officejet 6700 Premium E-all-in-one printer-h711n. Ubuntu 12.04 supplies HPLIP 3.12.2 and it does not support your printer. ... Minimum HPLIP version	3.12.4" -- [http://hplipopensource.com/hplip-web/models/officejet/officejet_6700.html](http://hplipopensource.com/hplip-web/models/officejet/officejet_6700.html)

[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

---

### Post by Mdh3MHY on 2013-10-12
> **Temüjin said:**
> "You have selected Ubuntu 12.04 using the HP Officejet 6700 Premium E-all-in-one printer-h711n. Ubuntu 12.04 supplies HPLIP 3.12.2 and it does not support your printer. ... Minimum HPLIP version    3.12.4" -- [http://hplipopensource.com/hplip-web/models/officejet/officejet_6700.html](http://hplipopensource.com/hplip-web/models/officejet/officejet_6700.html)

[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)
I wasn't aware I had an old edition of the hplip software. I have now installed the new version and it detected the printer with ease. I tested the scan function out with the print test page and it worked perfectly. Thanks very much.

---

### Post by Yellow Pasque on 2013-10-12
You're welcome. Please mark thread [SOLVED].

---

### Post by Mdh3MHY on 2013-10-12
I did look for the [solved] tag earlier when posting, but I now realise I was looking in the wrong place. I've marked it now.

---

