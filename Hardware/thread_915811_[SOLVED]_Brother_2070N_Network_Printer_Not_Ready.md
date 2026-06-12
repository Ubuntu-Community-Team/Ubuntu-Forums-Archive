---
title: "[SOLVED] Brother 2070N Network Printer Not Ready"
date: 2008-09-10
forum: Hardware
---

### Post by smyrna5 on 2008-09-10
Hi. I recently installed Xubuntu and am happy with it, but I am having trouble printing. I installed a Brother 2070N network printer (connected to my router). It prints when I first install it, but if I turn off the computer for awhile it always says it is not connected and I have to reinstall it to get it to work. Here is the message the printing troubleshooter gave me:

Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x86f09a0>,
 'cups_instance': None,
 'cups_queue': 'Brother',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'socket',
 'cups_printer_dict': {'device-uri': u'socket://192.168.1.101:9100',
                       'printer-info': u'Brother',
                       'printer-is-shared': True,
                       'printer-location': u'larry-desktop',
                       'printer-make-and-model': u'Brother HL-2060 Foomatic/hl1250 (recommended)',
                       'printer-state': 4,
                       'printer-state-message': u'No %%BoundingBox: comment in header!',
                       'printer-state-reasons': [u'connecting-to-device'],
                       'printer-type': 143364,
                       'printer-uri-supported': u'ipp://localhost:631/printers/Brother'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': 'No %%BoundingBox: comment in header!',
 'printer-state-reasons': 'connecting-to-device'}
Page 4 (Print test page):
{'test_page_attempted': True,
 'test_page_job_id': [14],
 'test_page_job_status': [(13, 'Brother', 'Test Page'),
                          (14, 'Brother', 'Test Page')],
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': 'No %%BoundingBox: comment in header!',
 'printer-state-reasons': 'connecting-to-device'}



What do I need to do to get this printer to work? Thanks

---

### Post by smyrna5 on 2008-09-12
To answer my own question, Brother has created updated linux drivers for this printer. I downloaed the Debian version and installed it. It seems to have cured the problem. 

[http://solutions.brother.com/linux/en_us/download_prn.html]("http://solutions.brother.com/linux/en_us/download_prn.html")

I am marking this one solved.

---

