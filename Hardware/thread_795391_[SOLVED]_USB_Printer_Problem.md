---
title: "[SOLVED] USB Printer Problem"
date: 2008-05-15
forum: Hardware
---

### Post by merlinus on 2008-05-15
I am running a centronics-to-usb cable from my HP LaserJet 4 because my new computer does not have a parallel port.  I cannot, however, get the printer to work, not even a test page, although Ubuntu recognizes it.

Here are the pertinent error messages:

Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x8d78100>,
 'cups_instance': None,
 'cups_queue': 'Unknown',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'hal',
 'cups_printer_dict': {'device-uri': u'hal:///org/freedesktop/Hal/devices/usb_device_9948_5584_noserial_if0_printer_noserial',
                       'printer-info': u'LJ4',
                       'printer-is-shared': True,
                       'printer-location': u'',
                       'printer-make-and-model': u'HP LaserJet 4 Foomatic/hpijs, hpijs 2.8.2',
                       'printer-state': 4,
                       'printer-state-message': u'Printer not connected; will retry in 30 seconds...',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 135196,
                       'printer-uri-supported': u'ipp://localhost:631/printers/Unknown'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': 'Printer not connected; will retry in 30 seconds...',
 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_attempted': True,
 'test_page_completions': [(12, u'Job canceled.')],
 'test_page_job_id': [12],
 'test_page_job_status': [(11, 'Unknown', 'RES3'),
                          (12, 'Unknown', 'Test Page')],
 'test_page_jobs_cancelled': True,
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': 'Printer not connected; will retry in 30 seconds...',
 'printer-state-reasons': 'none'}

Help greatly appreciated!

---

### Post by merlinus on 2008-05-15
I solved the problem by deleting the printer entry in System/Administration/Printing, rebooting, and then editing the properties for the new entry that was automatically added.

---

