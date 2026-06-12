---
title: "HP laserjet 1000 not printing"
date: 2009-02-21
forum: Hardware
---

### Post by Iesos on 2009-02-21
Hi.

I'm installing (x)ubuntu on this computer connected to a HP-laserjet 1000 and it is detected perfectly and everything seems to work in the software, but it doesn't print.

I have done all the "use these drivers", "change the Device URI" how to's and I have foo2zjs which seems to be the right driver according to almost every howto and I have changed to every Device URI mentioned in any howto I could find and some more, since the printer seems for me to be /dev/lp0 and not /dev/usb/lp0. But still nothing!

Now I have reversed to the original settings and troubleshot this problem, and what I get is:

```
Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x86fbe20>,
 'cups_instance': None,
 'cups_queue': 'hp_LaserJet_1000',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'hp',
 'cups_printer_dict': {'device-uri': u'hp:/usb/hp_LaserJet_1000?serial=0',
                       'printer-info': u'Hewlett-Packard hp LaserJet 1000',
                       'printer-is-shared': True,
                       'printer-location': u'',
                       'printer-make-and-model': u'HP LaserJet 1000 Foomatic/foo2zjs (recommended)',
                       'printer-state': 4,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 167940,
                       'printer-uri-supported': u'ipp://localhost:631/printers/hp_LaserJet_1000'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_job_status': [(12, 'hp_LaserJet_1000', 'Test Page')],
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}
```

but I can't make heads or tails out of it. If I instead use the lp0 device (file:///dev/lp0) I get a status message "busy" when troubleshooting even though the status is "idle" in the printer configuration (as it also is in reality). Then I get the following debug message:

```
Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x86fbe20>,
 'cups_instance': None,
 'cups_queue': 'hp_LaserJet_1000',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'file',
 'cups_printer_dict': {'device-uri': u'file:///dev/lp0',
                       'printer-info': u'Hewlett-Packard hp LaserJet 1000',
                       'printer-is-shared': True,
                       'printer-location': u'',
                       'printer-make-and-model': u'HP LaserJet 1000 Foomatic/foo2zjs (recommended)',
                       'printer-state': 3,
                       'printer-state-message': u'Unable to open output file "file:///dev/lp0" - Device or resource busy.',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 167940,
                       'printer-uri-supported': u'ipp://localhost:631/printers/hp_LaserJet_1000'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': 'Unable to open output file "file:///dev/lp0" - Device or resource busy.',
 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_job_status': [(13, 'hp_LaserJet_1000', 'Test Page')],
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': 'Unable to open output file "file:///dev/lp0" - Device or resource busy.',
 'printer-state-reasons': 'none'}
```

In the first case the pages are 'printed' according to the software, but in the latter case, when using the usb the pages just shift from "pending" to "stopped".

So any ideas?

---

