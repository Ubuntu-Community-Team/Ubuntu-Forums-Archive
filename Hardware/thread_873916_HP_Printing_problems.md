---
title: "HP Printing problems"
date: 2008-07-29
forum: Hardware
---

### Post by polymath on 2008-07-29
I have a HP Deskjet F380 Printer connected locally on a windows machine, and am currently trying to connect to that printer via my wired LAN network.

My problem:

I go through the find printer wizard on ubuntu through the system->printing button.  I create my printer, and download a printer driver from linuxprinting.org and set it to use that ppd.  The ppd is for the f300 series, and the manual says that it should be compatible.  Test page, though, doesn't work.  Try connecting via sudo hp-setup, which doesn't work either (hp-setup can't find the printer over my network, says "found no devices"), and i KNOW that HPLIP supports the f380 (It says so, at least, on their supported devices page).  Try troubleshoot button in printer wiz, doesn't work either.  it says it can't find the problem, printing out for bug report:

Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x87072a0>,
 'cups_instance': None,
 'cups_queue': 'Downstairs_Printer',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'smb',
 'cups_printer_dict': {'device-uri': u'smb://USRHOME/FRDELLE310/HPdeskjet',
                       'printer-info': u'HP DeskJet F380',
                       'printer-is-shared': True,
                       'printer-location': u'Family Room Dell',
                       'printer-make-and-model': u'HP DeskJet F300 Foomatic/hpijs (recommended)',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 167948,
                       'printer-uri-supported': u'ipp://localhost:631/printers/Downstairs_Printer'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_attempted': True,
 'test_page_completions': [(7, u'Job completed.')],
 'test_page_job_id': [7],
 'test_page_job_status': [(7, 'Downstairs_Printer', 'Test Page')],
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}

WHAT SHALL I DO?

---

### Post by stchman on 2008-07-29
> **polymath said:**
> I have a HP Deskjet F380 Printer connected locally on a windows machine, and am currently trying to connect to that printer via my wired LAN network.

My problem:

I go through the find printer wizard on ubuntu through the system->printing button.  I create my printer, and download a printer driver from linuxprinting.org and set it to use that ppd.  The ppd is for the f300 series, and the manual says that it should be compatible.  Test page, though, doesn't work.  Try connecting via sudo hp-setup, which doesn't work either (hp-setup can't find the printer over my network, says "found no devices"), and i KNOW that HPLIP supports the f380 (It says so, at least, on their supported devices page).  Try troubleshoot button in printer wiz, doesn't work either.  it says it can't find the problem, printing out for bug report:

Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x87072a0>,
 'cups_instance': None,
 'cups_queue': 'Downstairs_Printer',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'smb',
 'cups_printer_dict': {'device-uri': u'smb://USRHOME/FRDELLE310/HPdeskjet',
                       'printer-info': u'HP DeskJet F380',
                       'printer-is-shared': True,
                       'printer-location': u'Family Room Dell',
                       'printer-make-and-model': u'HP DeskJet F300 Foomatic/hpijs (recommended)',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 167948,
                       'printer-uri-supported': u'ipp://localhost:631/printers/Downstairs_Printer'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_attempted': True,
 'test_page_completions': [(7, u'Job completed.')],
 'test_page_job_id': [7],
 'test_page_job_status': [(7, 'Downstairs_Printer', 'Test Page')],
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}

WHAT SHALL I DO?

No need to download a driver Linux has it.

[http://openprinting.org/show_printer.cgi?recnum=HP-Multifuncional_HP_Deskjet_F380](http://openprinting.org/show_printer.cgi?recnum=HP-Multifuncional_HP_Deskjet_F380)

My advice is to connect the printer to the Ubuntu machine and share it.  Ubuntu shares printers with other OS much better than Windows.

---

### Post by phidia on 2008-07-29
Or take a look at the Sharing printers section from the Ubuntu page [here]("https://help.ubuntu.com/community/Printers").

---

