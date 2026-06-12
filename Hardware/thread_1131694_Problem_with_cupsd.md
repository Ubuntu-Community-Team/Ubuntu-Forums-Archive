---
title: "Problem with cupsd"
date: 2009-04-21
forum: Hardware
---

### Post by bcschmerker on 2009-04-21
I am currently unable to print under normal conditions from my Everex with [Elitegroup 'board](http://www.ecsusa.com/) ([nVIDIA GeForce6100/nForce405](http://www.nvidia.com/)).  A test from recovery mode verified that the Enhanced Parallel Port /dev/lp0 is fully functional.

Diagnosing the failure to print from a Panasonic KX-P1124i on /dev/lp0, the Printing Troubleshooter returns the following report:
```
Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x86ff780>,
 'cups_instance': None,
 'cups_queue': 'KX-P1124i',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'parallel',
 'cups_printer_dict': {'device-uri': u'parallel:/dev/lp0',
                       'printer-info': u'Panasonic KX-P1124i 24 Pin Multi--Mode Printer',
                       'printer-is-shared': False,
                       'printer-location': u'hotrodgpc-workstation',
                       'printer-make-and-model': u'Panasonic KX-P1124 Foomatic/epson (recommended)',
                       'printer-state': 3,
                       'printer-state-message': u'/usr/lib/cups/backend/parallel failed',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 2273284,
                       'printer-uri-supported': u'ipp://localhost:631/printers/KX-P1124i'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': '/usr/lib/cups/backend/parallel failed',
 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_attempted': True,
 'test_page_completions': [(15,
                            u'Job aborted; please consult the error_log file for details.')],
 'test_page_job_id': [15],
 'test_page_job_status': [(15, 'KX-P1124i', 'Test Page')],
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': '/usr/lib/cups/backend/parallel failed',
 'printer-state-reasons': 'none'}

```
What possible causes exist for the failure of /usr/lib/cups/backend?/parallel; and what is needed to remedy the cause(s)?

---

### Post by bcschmerker on 2009-12-05
Update:  Problem fixed---I had to reinstall Cupsys from single-user mode, using apt-get.  Mutual interference issue with SELinUX, from what I was able to find on other Threads.  See also [my Thread in Instalation and Upgrades]("http://ubuntuforums.org/showthread.php?t=1346322"). ):P

---

