---
title: "[problem] Dell Photo Printer 7200"
date: 2008-08-31
forum: Hardware
---

### Post by optimal on 2008-08-31
Hey all!

I've got my "Dell Photo Printer 7200" attached by USB and I can't get it to work!

Right, here's the problem:

[LIST]
[*]System
[*]Administration
[*]Printing
[*]Select the printer "Photo_Printer_7200"
[*]hit "Print test page"
[/LIST]

It says "Submitted - adding as page n" and then nothing. Sometimes the thing makes a whirr like it's about to print, but ultimately nothing! 

I've tried the troubleshooter and after trying a print test it flags it as "completed" but still nothing. It gives me this report:

```
Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x8703e80>,
 'cups_instance': None,
 'cups_queue': 'Photo_Printer_720',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://Dell%20/Photo%20Printer%20720',
                       'printer-info': u'Dell  Photo Printer 720',
                       'printer-is-shared': True,
                       'printer-location': u'',
                       'printer-make-and-model': u'Dell 1100, 1.1.0',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 45124,
                       'printer-uri-supported': u'ipp://localhost:631/printers/Photo_Printer_720'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_attempted': True,
 'test_page_completions': [(14, u'Job completed.')],
 'test_page_job_id': [14],
 'test_page_job_status': [(14, 'Photo_Printer_720', 'Test Page')],
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}
```

I've also followed the instructions for **printingbuginfo** and here's the resultant output (with the usb switch **-u**):

```
ProblemType: printingbuginfo v2.0: printingbug+localusb (https://wiki.ubuntu.com/PrintingBugInfoScript)
CupsConfiguredDevices:
 device for PDF: cups-pdf:/
 device for Photo_Printer_720: usb://Dell%20/Photo%20Printer%20720
CupsConfiguredPPDs:
 PDF: Generic PDF file generator
 Photo_Printer_720: Dell 1100, 1.1.0
Date: Mon Sep  1 02:03:48 2008
DesktopEnvironment: none
DistroRelease: Ubuntu 8.04
EtcPapersize: a4
InstalledPrintingPackages:
 ii  cupsys                   1.3.7-1ubuntu3           Common UNIX Printing System(tm) - server
 ii  cupsys-driver-gutenprint 5.0.2-2ubuntu1           printer drivers for CUPS
 ii  foo2zjs                  20071205-0ubuntu3        Support for printing to ZjStream-based printers
 ii  foomatic-db              20080211-0ubuntu1        OpenPrinting printer support - database
 ii  foomatic-db-engine       3.0.2-20070719-0ubuntu4  OpenPrinting printer support - programs
 ii  foomatic-db-hpijs        20070813-0ubuntu2        OpenPrinting printer support - database for HPIJS driver
 ii  foomatic-filters         3.0.2-20071204-0ubuntu2. OpenPrinting printer support - filters
 ii  ghostscript              8.61.dfsg.1-1ubuntu3     The GPL Ghostscript PostScript/PDF interpreter
 ii  gs-common                8.61.dfsg.1-1ubuntu3     Transitional package
 ii  gs-esp                   8.61.dfsg.1-1ubuntu3     Transitional package
 ii  gs-esp-x                 8.61.dfsg.1-1ubuntu3     Transitional package
 ii  hpijs                    2.8.2+2.8.2-0ubuntu8     HP Linux Printing and Imaging - gs IJS driver (hpijs)
 ii  hplip                    2.8.2-0ubuntu8           HP Linux Printing and Imaging System (HPLIP)
 ii  libgnomeprint2.2-0       2.18.4-1                 The GNOME 2.2 print architecture - runtime files
 ii  min12xxw                 0.0.9-1build1            Printer driver for KonicaMinolta PagePro 1[234]xxW
 ii  openprinting-ppds        20080211-0ubuntu1        OpenPrinting printer support - PostScript PPD files
 ii  pnm2ppa                  1.12-16                  PPM to PPA converter
 ii  pxljr                    1.1-0ubuntu1             Driver for HP's Color LaserJet 35xx/36xx color laser printers
 ii  splix                    1.1.1-0ubuntu1           Driver for Samsung's SPL2 (bw) and SPLc (color) laser printers
Locale: LANG=en_GB.UTF-8, LC_CTYPE=en_GB.UTF-8, LC_PAPER=en_GB.UTF-8
Uname: Linux cogbox 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
UsbPrinterDevices: lrwxrwxrwx 1 root root 7 Sep  1 01:54 /dev/usblp0 -> usb/lp0
UsbPrinterIEEE1284Id:
 /dev/usblp0: GET_DEVICE_ID string:
 MFG:Dell ;CMD:CPDNPA001;MODEL:Photo Printer 720;CLASS:Printer;DES:Dell Photo Printer 720;COMMENT:030305-1;
UsbPrinterKernelModules:
 usblp                  15872  0 
 usbcore               146028  7 usblp,usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd
lsusb:
 Bus 005 Device 004: ID 3538:0042 Power Quotient International Co., Ltd Cool Drive U339 Flash Disk
 Bus 005 Device 001: ID 0000:0000  
 Bus 004 Device 001: ID 0000:0000  
 Bus 003 Device 002: ID 413c:5008 Dell Computer Corp. 
 Bus 003 Device 001: ID 0000:0000  
 Bus 002 Device 001: ID 0000:0000  
 Bus 001 Device 006: ID 0a81:0101 Chesen Electronics Corp. Keyboard
 Bus 001 Device 004: ID 045e:00f0 Microsoft Corp. 
 Bus 001 Device 001: ID 0000:0000
```

---

