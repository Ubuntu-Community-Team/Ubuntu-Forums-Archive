---
title: "How to intall a printer?"
date: 2008-07-14
forum: Hardware
---

### Post by Momof9Blessings on 2008-07-14
I have been searching, but how do you install a printer on Hardy?

I have a Compaq laptop, Hardy, epson 1400 printer.

I plugged it in - actually looks like it recognizes my printer... but it won't print....  I tried a trouble shoot and here is the result....

Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x8e38d60>,
 'cups_instance': None,
 'cups_queue': 'Stylus_Photo_1400',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://EPSON/Stylus%20Photo%201400',
                       'printer-info': u'EPSON Stylus Photo 1400',
                       'printer-is-shared': True,
                       'printer-location': u'',
                       'printer-make-and-model': u'Epson Stylus Photo 1400 - CUPS+Gutenprint v5.0.2 Simplified',
                       'printer-state': 3,
                       'printer-state-message': u'No %%BoundingBox: comment in header!',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 8564748,
                       'printer-uri-supported': u'ipp://localhost:631/printers/Stylus_Photo_1400'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': 'No %%BoundingBox: comment in header!',
 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_attempted': True,
 'test_page_completions': [(2,
                            u'Job stopped due to filter errors; please consult the error_log file for details.')],
 'test_page_job_id': [2],
 'test_page_job_status': [(1, 'Stylus_Photo_1400', 'Test Page'),
                          (2, 'Stylus_Photo_1400', 'Test Page')],
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': '/usr/lib/cups/filter/pstoraster failed',
 'printer-state-reasons': 'none'}


Thank you,
Mom

---

### Post by Dark_Stang on 2008-07-14
Epson does not have the best drivers and support for Linux. However my epson printer ( a stylus cx7400) would only work if I turned the print quality to High. So give that a shot and see what happens. In the future you may want to stick with HP printers, HP is very Linux friendly.

---

### Post by stchman on 2008-07-14
What kind of Epson 1400 printer?  A more exact model number please.

---

### Post by prshah on 2008-07-14
> **Momof9Blessings said:**
> I have been searching, but how do you install a printer on Hardy?

Open a browser, then enter the below address in the addressbar```
htp://localhost:631
``` This will open the CUPS (Common Unix Printing System) admin page, from which you can add, change and/or setup printers and printing capabilities.

---

### Post by Momof9Blessings on 2008-07-14
it is a epson photo 1400 - professional printer....  I am probably going to have to use a thumb drive to take the items to be printed to my desktop... unless I can setup a home network - with windows computers.....

---

### Post by stchman on 2008-07-14
> **Momof9Blessings said:**
> it is a epson photo 1400 - professional printer....  I am probably going to have to use a thumb drive to take the items to be printed to my desktop... unless I can setup a home network - with windows computers.....

Here is the openprinting entry on the Epson Stylus Photo 1400.

[http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_Photo_1400](http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_Photo_1400)

It is spotty, but you can try the gnutenprint or gnutenprint52 driver.

---

