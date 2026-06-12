---
title: "HP Laserjet 1022nw Will Not Print"
date: 2008-08-23
forum: General Help
---

### Post by jkph00 on 2008-08-23
Hi!

I have spent all day trying to get my HP LJ 1022nw to print under Ubuntu 8.04.  It shows as connected, but will not print.  I receive the following message from the troubleshooter:

Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x9459420>,
 'cups_instance': None,
 'cups_queue': 'LaserJet_1022',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'http',
 'cups_printer_dict': {'device-uri': u'http://192.168.1.110',
                       'printer-info': u'HP Laserjet 1022nw',
                       'printer-is-shared': True,
                       'printer-location': u'Office',
                       'printer-make-and-model': u'HP LaserJet 1022 Foomatic/foo2zjs (recommended)',
                       'printer-state': 3,
                       'printer-state-message': u'No %%BoundingBox: comment in header!',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 167956,
                       'printer-uri-supported': u'ipp://localhost:631/printers/LaserJet_1022'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': 'No %%BoundingBox: comment in header!',
 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_attempted': True,
 'test_page_job_id': [24],
 'test_page_job_status': [(24, 'LaserJet_1022', 'Test Page')],
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': "recoverable: Network host '192.168.1.110' is busy; will retry in 30 seconds...",
 'printer-state-reasons': 'none'}


Despite the indication it will retry, it continues to hang.  How might I get it to work?

Warmest thanks in advance for your help.

  --Kurt

---

### Post by bmac on 2008-08-23
Try installing the HPLIP driver.... It supports your printer....

[http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html)


Hope this helps....

---

### Post by jkph00 on 2008-08-24
> **bmac said:**
> Try installing the HPLIP driver.... It supports your printer....

[http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html)


Hope this helps....

You are a wizard!  That worked handsomely.  Thank you!  Tell me, is there perhaps a list I should subscribe to in order to stay abreast of such things?

--Kurt

---

### Post by bmac on 2008-08-24
Not that I know of - to many hardware OEM's to keep track of...

Someone else might know of a web site....

---

