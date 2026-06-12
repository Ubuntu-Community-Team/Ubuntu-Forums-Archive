---
title: "Printer Issues"
date: 2008-08-11
forum: General Help
---

### Post by Bbman90 on 2008-08-11
I have a Dell Photo Printer 720, which I cannot get to run. Whenever I tried to click on it in the printer configuration, it gave me the error message "There was a problem connecting to the CUPS server". I ran the troubleshooter on it, and got this information. Does anybody know what is wrong?

Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x91317a0>,
 'cups_instance': None,
 'cups_queue': 'Printer',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://Dell%20/Photo%20Printer%20720',
                       'printer-info': u'',
                       'printer-is-shared': True,
                       'printer-location': u'brandon-desktop',
                       'printer-make-and-model': u'Dell 1100, 1.1.0',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 176196,
                       'printer-uri-supported': u'ipp://localhost:631/printers/Printer'},
 'is_cups_class': False}
Page 3 (Printer state reasons):

---

### Post by ricnmar on 2008-08-12
Bbman90,

Try going into the System > Administration > Services menu, and make sure that the Printer Service is there.  Go in and uncheck and recheck it and then see if you have the same trouble.

Good luck!

-ricnmar

---

