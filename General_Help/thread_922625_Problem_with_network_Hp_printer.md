---
title: "Problem with network Hp printer"
date: 2008-09-17
forum: General Help
---

### Post by checcouniud on 2008-09-17
Hi all,
I am trying to install a network printer.
I have used the printer configuration tool but i still have some problems.
I AM ABLE TO PRINT corretly from firefox, but the printer is not printing anything from "OpenOffice" or from "Document viewer", which is unfortunate since usually i print only pdf files ...
Moreover if i hit the " Print test Page" under the printer configuration it is not printng, but if i go to help>>troubleshoot i am able to print the test page  and i have this report :
------------------------------------------------------------------------
Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x8708e80>,
 'cups_instance': None,
 'cups_queue': 'Se-lab',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'socket',
 'cups_printer_dict': {'device-uri': u'socket://***.***.**.**:9100',
                       'printer-info': u'Se-lab',
                       'printer-is-shared': False,
                       'printer-location': u'EG3112',
                       'printer-make-and-model': u'HP LaserJet 4000 Series Postscript (recommended)',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 2265300,
                       'printer-uri-supported': u'ipp://localhost:631/printers/Se-lab'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_attempted': True,
 'test_page_completions': [(40, u'Job completed.')],
 'test_page_job_id': [40],
 'test_page_job_status': [(40, 'Se-lab', 'Test Page')],
 'test_page_successful': True}
Page 5 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}
--------------------------------------------------------------------------
In all the cases i can see the printing job in the "document printing status" window and the status is always "Completed".

Does anybody has an idea on what is going on? 
I am not an expert and i do not know what to try now!

THANK YOU A LOT FOR ANY HELP!
PLEASE....

---

