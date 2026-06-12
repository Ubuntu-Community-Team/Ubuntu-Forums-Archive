---
title: "Print jobs keep getting cancelled"
date: 2013-12-16
forum: Hardware
---

### Post by SuperFreak on 2013-12-16
My printer is connected via USB and powered up. 
lsUSB identifies the Brother Printer I believe:
```
$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 002 Device 003: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 002 Device 005: ID 04f9:01f5 Brother Industries, Ltd 
Bus 001 Device 004: ID 046d:c01b Logitech, Inc. MX310 Optical Mouse

```

Scanning with XSane works but the preview window is nonfunctional.
I know I did something that has caused a hiccup with the printer but I do not know how to get it working again. Originally I was trying to set up my functional printer to work with another Ubuntu computer through SAMBA.When I found the printer no longer worked I tried these steps:I tried disconnecting the USB cable from the printer, turning printer on and off and rebooting. I also tried deleting the printer from Printer settings and readding it. It is recognized but when I try to print I get a notification "printing canceled 'Untitled1' on MFC 5490CN" or if I try to print a web page or test page nothing happens
The Printer is a Brother MFC 5490CN


More info:
```
$ dpkg  -l  |  grep  Brother
ii  brscan-skey                                  0.2.4-0                                          Brother Linux scanner S-KEY tool
ii  brscan3                                      0.2.11-5                                         Brother Scanner Driver
ii  mfc5490cncupswrapper:i386                    1.1.2-2                                          Brother CUPS Inkjet Printer Definitions
ii  mfc5490cnlpr:i386                            1.1.2-2                                          Brother lpr Inkjet Printer Definitions
ii  printer-driver-ptouch                        1.3-3ubuntu0.1                                   printer driver Brother P-touch label printers
```

I had a look in Var/spool/lpr and it just has one empty folder "mfc5490cn"

---

### Post by SuperFreak on 2013-12-16
Marking as solved. I had to reinstall lpr and cups drivers

---

