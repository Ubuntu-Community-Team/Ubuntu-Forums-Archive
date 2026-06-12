---
title: "[SOLVED] Intrepid printing issues?"
date: 2008-11-14
forum: General Help
---

### Post by Merovius on 2008-11-14
I have notived that I cannot print after a clean Intrepid Ibex install. If I go to Printing it shows no printers. If I click add everything is greyed out. If I go through troubleshoot it says CUPS is not running check under services etc. I check under services and CUPS is not listed there and therefor I cannot tell it to start at boot. 

I checked in Synaptic and all kinds of CUPS stuff is installed. I reinstalled several of them to try and jump start things but it had no effect.

How do I get CUPS to run when it's supposed to? I suspect something to do with Permisions or Authorizations. 

Ideas??

TIA

---

### Post by sancho panza on 2008-11-14
Same problem here. Anyone?

---

### Post by philinux on 2008-11-14
Does this get it going.

sudo /etc/init.d/cupsys restart

---

### Post by Merovius on 2008-11-14
I get this in the terminal

"/etc/init.d/cupsys: command not found"

That doesn't seem good..

---

### Post by Merovius on 2008-11-14
Tried this one too

 sudo /etc/init.d/cups restart
 * Restarting Common Unix Printing System: cupsd                                cupsd: Child exited with status 1!
                                                                         [fail]


I think it's cups in Ibex so I tried that. Something is obviously not right.

---

### Post by Merovius on 2008-11-15
I have found that if I ununstall cups and install an older version from a deb I can then see a printer on USB1 and set it up. It did not succesfully print but I didn't experiment much beyond this point. If I let the update tool update cups as it immediatly wants to I lose all funtionality. Printer disapears and I can't add one.

What is the previous version of cups just before the most recent?

I have 1.3.9-2ubuntu1. It does not work. I would like to try the previous version. The one I tried was quite old.

Anyone?

---

### Post by Merovius on 2008-11-15
I've noticed on the forums that many people have various printing issues with Intrepid.

Doesn't seem to be getting much attention though. Nobody out there has had this and fixed it? I very much doubt that. Somebody must have.

Anybody? Ideas? Suggestions? Pretty Please...;)

TIA

---

### Post by nikgare on 2008-11-15
Without the output from your cups log file, it will be hard for anyone to help you.

---

### Post by TheLions on 2008-11-15
i also have printing problems (especially when printing PDFs) and i found out that has something related with new printing method where is everything converted to PDF before printing:

[http://www.linuxfoundation.org/en/OpenPrinting/PDF_as_Standard_Print_Job_Format](http://www.linuxfoundation.org/en/OpenPrinting/PDF_as_Standard_Print_Job_Format)

so how to disable it or revert to old one CUPS???

---

### Post by Merovius on 2008-11-15
Where do I find the log file? 

Thanks

---

### Post by Merovius on 2008-11-16
In var/log/cups I found,

E [16/Nov/2008:08:49:07 -0500] "/etc/cups/ssl/server.crt" is a bad symlink - No such file or directory

Does this help at all?

---

### Post by Merovius on 2008-11-16
I removed two files from the var/log/cups file. Both said they were bad symlinks. After this I restarted cups and the computer auto detected my printer. It does not seem to have the right driver and does not actually print. 

Error disappeared also. Still working on it..

---

### Post by edilsonka on 2008-11-16
Dear all; 

Got the log from my printer (as I am facing the same problem (no paper out from printer when I ask to do so): 

Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest LaserPrint (default)>,
 'cups_instance': None,
 'cups_queue': 'LaserPrint',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://OKI%20DATA%20CORP/B2200',
                       'printer-info': u'B2200',
                       'printer-is-shared': False,
                       'printer-location': u'',
                       'printer-make-and-model': u'Oki B4100 Foomatic/hpijs (recommended)',
                       'printer-state': 3,
                       'printer-state-message': u'/usr/lib/cups/filter/foomatic-rip failed',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 2265108,
                       'printer-uri-supported': u'ipp://localhost:631/printers/LaserPrint'},
 'cups_printer_remote': False,
 'is_cups_class': False}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'Adjustment': {u'AutoTraySwitch': u'True',
                                               u'Economode': u'Off',
                                               u'TonerDensity': u'Medium',
                                               u'TrCurrent': u'Medium'},
                               u'General': {u'Copies': u'1',
                                            u'Duplex': u'None',
                                            u'InputSlot': u'Default',
                                            u'MediaType': u'',
                                            u'PageRegion': u'A4',
                                            u'PageSize': u'A4',
                                            u'PaperWeight': u'Medium',
                                            u'Resolution': u'600'},
                               u'PrintoutMode': {u'Quality': u'600GrayscaleK'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Choose device):
{'cups_device_dict': {'device-class': u'direct',
                      'device-id': u'MANUFACTURER:OKI DATA CORP;COMMAND SET:PJL,PCL,SDL;MODEL:B2200;CLASS:PRINTER;DESCRIPTION:OKI B2200;',
                      'device-info': u'OKI DATA CORP B2200 USB #1',
                      'device-make-and-model': u'OKI DATA CORP B2200'}}
Page 7 (Printer state reasons):
{'printer-state-message': u'/usr/lib/cups/filter/foomatic-rip failed',
 'printer-state-reasons': [u'none']}
Page 8 (Error log checkpoint):
{'cups_server_settings': {'DefaultAuthType': 'Basic',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '0',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '0',
                          '_share_printers': '0',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 15914L,
 'error_log_debug_logging_set': True}
Page 9 (Print test page):
{'test_page_attempted': True,
 'test_page_completions': [(38, u'Job completed.')],
 'test_page_job_id': [38],
 'test_page_job_status': [(True,
                           37,
                           'LaserPrint',
                           '',
                           'Cancelled',
                           {'AutoTraySwitch': True,
                            'Copies': u'1',
                            'Duplex': u'None',
                            'Economode': u'Off',
                            'InputSlot': u'Default',
                            'MediaType': u'',
                            'PageRegion': u'Custom',
                            'PageSize': u'Custom',
                            'PaperWeight': u'Medium',
                            'Quality': u'600GrayscaleK',
                            'Resolution': u'600',
                            'TonerDensity': u'Medium',
                            'TrCurrent': u'Medium',
                            'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'pt-br',
                            'document-format': u'application/postscript',
                            'job-hold-until': u'no-hold',
                            'job-id': 37,
                            'job-k-octets': 13,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/37',
                            'job-name': u'',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'edilson',
                            'job-preserved': False,
                            'job-printer-state-message': u'/usr/lib/cups/filter/foomatic-rip failed',
                            'job-printer-state-reasons': [u'none'],
                            'job-printer-up-time': 1226846935,
                            'job-printer-uri': u'ipp://edilson-desktop:631/printers/LaserPrint',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 7,
                            'job-state-reasons': u'job-canceled-by-user',
                            'job-uri': u'ipp://localhost:631/jobs/37',
                            'job-uuid': u'urn:uuid:9f88986a-5bc3-3074-4951-58fcd1347b89',
                            'orientation-requested': 3,
                            'printer-uri': u'ipp://localhost/printers/LaserPrint',
                            'sides': u'one-sided',
                            'time-at-completed': 1226846921,
                            'time-at-creation': 1226846784,
                            'time-at-processing': 1226846784}),
                          (False,
                           38,
                           'LaserPrint',
                           'Test Page',
                           'Completo',
                           None)],
 'test_page_jobs_cancelled': True,
 'test_page_successful': False}
Page 10 (Error log fetch):
{'error_log': ['D [16/Nov/2008:12:47:06 -0200] cupsdCloseClient: 9',
               'D [16/Nov/2008:12:47:06 -0200] cupsdAcceptClient: 9 from localhost (Domain)',
               'D [16/Nov/2008:12:47:06 -0200] cupsdReadClient: 9 POST / HTTP/1.1',
               'D [16/Nov/2008:12:47:06 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:47:06 -0200] Get-Jobs ipp://localhost/jobs/',
               'D [16/Nov/2008:12:47:06 -0200] [Job 37] Loading attributes...',
               'D [16/Nov/2008:12:47:06 -0200] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:47:06 -0200] cupsdCloseClient: 9',
               'D [16/Nov/2008:12:47:06 -0200] cupsdAcceptClient: 9 from localhost (Domain)',
               'D [16/Nov/2008:12:47:06 -0200] cupsdReadClient: 9 POST / HTTP/1.1',
               'D [16/Nov/2008:12:47:06 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:47:06 -0200] Create-Printer-Subscription /',
               'D [16/Nov/2008:12:47:06 -0200] cupsdCreateSubscription(con=0xb9ba9218(9), uri="/")',
               'D [16/Nov/2008:12:47:06 -0200] pullmethod="ippget"',
               'D [16/Nov/2008:12:47:06 -0200] notify-lease-duration=86400',
               'D [16/Nov/2008:12:47:06 -0200] notify-time-interval=0',
               'D [16/Nov/2008:12:47:06 -0200] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [16/Nov/2008:12:47:06 -0200] Added subscription 20 for server',
               'I [16/Nov/2008:12:47:06 -0200] Saving subscriptions.conf...',
               'D [16/Nov/2008:12:47:06 -0200] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:47:06 -0200] cupsdCloseClient: 9',
               'D [16/Nov/2008:12:47:07 -0200] cupsdAcceptClient: 9 from localhost (Domain)',
               'D [16/Nov/2008:12:47:07 -0200] cupsdReadClient: 9 POST / HTTP/1.1',
               'D [16/Nov/2008:12:47:07 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:47:07 -0200] Get-Notifications /',
               'D [16/Nov/2008:12:47:07 -0200] cupsdIsAuthorized: requesting-user-name="edilson"',
               'D [16/Nov/2008:12:47:07 -0200] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:47:07 -0200] cupsdCloseClient: 9',
               'D [16/Nov/2008:12:47:10 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:47:10 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:47:10 -0200] CUPS-Get-Default',
               'D [16/Nov/2008:12:47:10 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:47:10 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:47:10 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:47:10 -0200] CUPS-Get-Printers',
               'D [16/Nov/2008:12:47:10 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:47:15 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:47:15 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:47:15 -0200] CUPS-Get-Default',
               'D [16/Nov/2008:12:47:15 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:47:15 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:47:15 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:47:15 -0200] CUPS-Get-Printers',
               'D [16/Nov/2008:12:47:15 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:47:20 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:47:20 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:47:20 -0200] CUPS-Get-Default',
               'D [16/Nov/2008:12:47:20 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:47:20 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:47:20 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:47:20 -0200] CUPS-Get-Printers',
               'D [16/Nov/2008:12:47:20 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:47:25 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:47:25 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:47:25 -0200] CUPS-Get-Default',
               'D [16/Nov/2008:12:47:25 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:47:25 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:47:25 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:47:25 -0200] CUPS-Get-Printers',
               'D [16/Nov/2008:12:47:25 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:47:30 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:47:30 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:47:30 -0200] CUPS-Get-Default',
               'D [16/Nov/2008:12:47:30 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:47:30 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:47:30 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:47:30 -0200] CUPS-Get-Printers',
               'D [16/Nov/2008:12:47:30 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:47:30 -0200] cupsdAcceptClient: 9 from localhost (Domain)',
               'D [16/Nov/2008:12:47:30 -0200] cupsdReadClient: 9 POST / HTTP/1.1',
               'D [16/Nov/2008:12:47:30 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:47:30 -0200] Get-Job-Attributes ipp://localhost/jobs/37',
               'D [16/Nov/2008:12:47:30 -0200] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:47:30 -0200] cupsdCloseClient: 9',
               'D [16/Nov/2008:12:47:30 -0200] cupsdAcceptClient: 9 from localhost (Domain)',
               'D [16/Nov/2008:12:47:30 -0200] cupsdReadClient: 9 POST / HTTP/1.1',
               'D [16/Nov/2008:12:47:30 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:47:30 -0200] Cancel-Subscription /',
               'D [16/Nov/2008:12:47:30 -0200] cupsdIsAuthorized: requesting-user-name="edilson"',
               'I [16/Nov/2008:12:47:30 -0200] Saving subscriptions.conf...',
               'D [16/Nov/2008:12:47:30 -0200] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:47:30 -0200] cupsdCloseClient: 9',
               'D [16/Nov/2008:12:47:30 -0200] cupsdAcceptClient: 9 from localhost (Domain)',
               'D [16/Nov/2008:12:47:30 -0200] cupsdReadClient: 9 GET /admin/log/error_log HTTP/1.1',
               'D [16/Nov/2008:12:47:30 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:47:34 -0200] cupsdAcceptClient: 10 from localhost (Domain)',
               'D [16/Nov/2008:12:47:34 -0200] cupsdReadClient: 10 POST / HTTP/1.1',
               'D [16/Nov/2008:12:47:34 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:47:34 -0200] Get-Jobs ipp://localhost/jobs/',
               'D [16/Nov/2008:12:47:34 -0200] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:47:34 -0200] cupsdCloseClient: 10',
               'D [16/Nov/2008:12:47:34 -0200] cupsdAcceptClient: 10 from localhost (Domain)',
               'D [16/Nov/2008:12:47:34 -0200] cupsdReadClient: 10 POST / HTTP/1.1',
               'D [16/Nov/2008:12:47:34 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:47:34 -0200] Create-Printer-Subscription /',
               'D [16/Nov/2008:12:47:34 -0200] cupsdCreateSubscription(con=0xb9bad130(10), uri="/")',
               'D [16/Nov/2008:12:47:34 -0200] pullmethod="ippget"',
               'D [16/Nov/2008:12:47:34 -0200] notify-lease-duration=86400',
               'D [16/Nov/2008:12:47:34 -0200] notify-time-interval=0',
               'D [16/Nov/2008:12:47:34 -0200] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [16/Nov/2008:12:47:34 -0200] Added subscription 21 for server',
               'I [16/Nov/2008:12:47:34 -0200] Saving subscriptions.conf...',
               'D [16/Nov/2008:12:47:34 -0200] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:47:34 -0200] cupsdCloseClient: 10',
               'D [16/Nov/2008:12:47:35 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:47:35 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:47:35 -0200] CUPS-Get-Default',
               'D [16/Nov/2008:12:47:35 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:47:35 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:47:35 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:47:35 -0200] CUPS-Get-Printers',
               'D [16/Nov/2008:12:47:35 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:47:35 -0200] cupsdAcceptClient: 10 from localhost (Domain)',
               'D [16/Nov/2008:12:47:35 -0200] cupsdReadClient: 10 POST / HTTP/1.1',
               'D [16/Nov/2008:12:47:35 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:47:35 -0200] Get-Notifications /',
               'D [16/Nov/2008:12:47:35 -0200] cupsdIsAuthorized: requesting-user-name="edilson"',
               'D [16/Nov/2008:12:47:35 -0200] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:47:35 -0200] cupsdCloseClient: 10',
               'D [16/Nov/2008:12:47:37 -0200] cupsdAcceptClient: 10 from localhost (Domain)',
               'D [16/Nov/2008:12:47:37 -0200] cupsdReadClient: 10 POST /printers/LaserPrint HTTP/1.1',
               'D [16/Nov/2008:12:47:37 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:47:37 -0200] Print-Job ipp://localhost/printers/LaserPrint',
               'D [16/Nov/2008:12:47:37 -0200] add_job: requesting-user-name="edilson"',
               'D [16/Nov/2008:12:47:37 -0200] Adding default job-sheets values "none,none"...',
               'I [16/Nov/2008:12:47:37 -0200] [Job 38] Adding start banner page "none".',
               'I [16/Nov/2008:12:47:37 -0200] Saving subscriptions.conf...',
               'I [16/Nov/2008:12:47:37 -0200] [Job 38] Adding end banner page "none".',
               'I [16/Nov/2008:12:47:37 -0200] [Job 38] File of type application/postscript queued by "edilson".',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] hold_until=0',
               'I [16/Nov/2008:12:47:37 -0200] [Job 38] Queued on "LaserPrint" by "edilson".',
               'I [16/Nov/2008:12:47:37 -0200] Saving subscriptions.conf...',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] job-sheets=none,none',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] banner_page = 0',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] argv[0]="LaserPrint"',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] argv[1]="38"',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] argv[2]="edilson"',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] argv[3]="Test Page"',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] argv[4]="1"',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] argv[5]="job-uuid=urn:uuid:5a059670-20fe-3036-7fb7-586c912700c4"',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] argv[6]="/var/spool/cups/d00038-001"',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] envp[9]="SERVER_ADMIN=root@edilson-desktop"',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] envp[10]="SOFTWARE=CUPS/1.3.9"',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] envp[11]="TMPDIR=/var/spool/cups/tmp"',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] envp[12]="TZ=America/Sao_Paulo"',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] envp[13]="USER=root"',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] envp[15]="CUPS_ENCRYPTION=IfRequested"',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] envp[16]="IPP_PORT=631"',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] envp[17]="CHARSET=utf-8"',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] envp[18]="LANG=pt_BR.UTF8"',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] envp[19]="PPD=/etc/cups/ppd/LaserPrint.ppd"',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] envp[20]="RIP_MAX_CACHE=8m"',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] envp[21]="CONTENT_TYPE=application/postscript"',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] envp[22]="DEVICE_URI=usb://OKI%20DATA%20CORP/B2200"',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] envp[23]="PRINTER=LaserPrint"',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] envp[24]="FINAL_CONTENT_TYPE=printer/LaserPrint"',
               'I [16/Nov/2008:12:47:37 -0200] [Job 38] Started filter /usr/lib/cups/filter/pstopdf (PID 21001)',
               'I [16/Nov/2008:12:47:37 -0200] [Job 38] Started filter /usr/lib/cups/filter/pdftopdf (PID 21002)',
               'I [16/Nov/2008:12:47:37 -0200] [Job 38] Started filter /usr/lib/cups/filter/cpdftocps (PID 21003)',
               'I [16/Nov/2008:12:47:37 -0200] [Job 38] Started filter /usr/lib/cups/filter/foomatic-rip (PID 21005)',
               'I [16/Nov/2008:12:47:37 -0200] [Job 38] Started backend /usr/lib/cups/backend/usb (PID 21009)',
               'I [16/Nov/2008:12:47:37 -0200] Saving subscriptions.conf...',
               'D [16/Nov/2008:12:47:37 -0200] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] Getting input from file',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] foomatic-rip version 4.0.0.177 running...',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] Parsing PPD file ...',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] Added option Resolution',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] Added option PageSize',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] Added option Model',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] Added option ImageableArea',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] Added option PaperDimension',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] Added option InputSlot',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] Added option ComFeed',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] Added option PJLFeed',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] Added option MediaType',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] Added option Media',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] Added option PJLTray1M',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] Added option PJLTray2M',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] Added option PaperWeight',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] Added option PJLTray1W',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] Added option PJLTray2W',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] Added option Duplex',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] Added option Copies',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] Added option Quality',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] Added option Economode',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] Added option TonerDensity',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] Added option TrCurrent',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] Added option AutoTraySwitch',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] Added option PJLPlacePage',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] Added option',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] Added option Font',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38]',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] Parameter Summary',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] -----------------',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38]',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] Spooler: cups',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] Printer: LaserPrint',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] Shell: /bin/bash',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] PPD file: /etc/cups/ppd/LaserPrint.ppd',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] ATTR file:',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] Printer model: Oki B4100 Foomatic/hpijs (recommended)',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] Job title: Test Page',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] File(s) to be printed:',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] <STDIN>',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38]',
               "D [16/Nov/2008:12:47:37 -0200] [Job 38] GhostScript extra search path ('GS_LIB'): /usr/share/cups/fonts",
               "D [16/Nov/2008:12:47:37 -0200] [Job 38] Pondering option 'job-uuid=urn:uuid:5a059670-20fe-3036-7fb7-586c912700c4'",
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] Unknown option job-uuid=urn:uuid:5a059670-20fe-3036-7fb7-586c912700c4.',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38]',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] ================================================',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38]',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] File: <STDIN>',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38]',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] ================================================',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38]',
               'I [16/Nov/2008:12:47:37 -0200] Saving subscriptions.conf...',
               'D [16/Nov/2008:12:47:37 -0200] cupsdCloseClient: 10',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] Printer using device file "/dev/usblp0"...',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] backendRunLoop(print_fd=0, device_fd=5, use_bc=1, side_cb=0xb800ea80)',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] Received 230 bytes of back-channel data!',
               'I [16/Nov/2008:12:47:37 -0200] Saving subscriptions.conf...',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] pstopdf argv[6] = 38 edilson Test Page 1 job-uuid=urn:uuid:5a059670-20fe-3036-7fb7-586c912700c4 /var/spool/cups/d00038-001',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] PPD: /etc/cups/ppd/LaserPrint.ppd',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] Resolution: 600',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] pdftops - copying to temp print file "/tmp/4920328922d32"',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] Page size: A4',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] Width: 595, height: 842, absolute margins: , , ,',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] Relative margins: 18, 14.40, 18, 14.40',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] PostScript to be injected: <</.HWMargins[18 14.40 18 14.40] /Margins[0 0]>>setpagedevice',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] PPD options: -r600 -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] Injecting PostScript: <</.HWMargins[18 14.40 18 14.40] /Margins[0 0]>>setpagedevice',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] Running cat | /usr/bin/ps2pdf13 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                -dPDFSETTINGS=/printer -r600 -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842 - -',
               'D [16/Nov/2008:12:47:37 -0200] [Job 38] GPL Ghostscript 8.63: Set UseCIEColor for UseDeviceIndependentColor to work properly.',
               'D [16/Nov/2008:12:47:37 -0200] cupsdAcceptClient: 10 from localhost (Domain)',
               'D [16/Nov/2008:12:47:37 -0200] cupsdReadClient: 10 POST / HTTP/1.1',
               'D [16/Nov/2008:12:47:37 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:47:37 -0200] Get-Jobs ipp://localhost/jobs/',
               'D [16/Nov/2008:12:47:37 -0200] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:47:37 -0200] cupsdCloseClient: 10',
               'D [16/Nov/2008:12:47:37 -0200] cupsdAcceptClient: 10 from localhost (Domain)',
               'D [16/Nov/2008:12:47:37 -0200] cupsdReadClient: 10 POST / HTTP/1.1',
               'D [16/Nov/2008:12:47:37 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:47:37 -0200] Get-Notifications /',
               'D [16/Nov/2008:12:47:37 -0200] cupsdIsAuthorized: requesting-user-name="edilson"',
               'D [16/Nov/2008:12:47:37 -0200] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:47:37 -0200] cupsdReadClient: 10 POST / HTTP/1.1',
               'D [16/Nov/2008:12:47:37 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:47:37 -0200] Get-Job-Attributes ipp://localhost/jobs/38',
               'D [16/Nov/2008:12:47:37 -0200] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:47:37 -0200] cupsdCloseClient: 10',
               'D [16/Nov/2008:12:47:37 -0200] cupsdAcceptClient: 10 from localhost (Domain)',
               'D [16/Nov/2008:12:47:37 -0200] cupsdReadClient: 10 POST / HTTP/1.1',
               'D [16/Nov/2008:12:47:37 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:47:37 -0200] Get-Notifications /',
               'D [16/Nov/2008:12:47:37 -0200] cupsdIsAuthorized: requesting-user-name="edilson"',
               'D [16/Nov/2008:12:47:37 -0200] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:47:37 -0200] cupsdCloseClient: 10',
               'D [16/Nov/2008:12:47:37 -0200] PID 21001 (/usr/lib/cups/filter/pstopdf) exited with no errors.',
               'D [16/Nov/2008:12:47:38 -0200] PID 21002 (/usr/lib/cups/filter/pdftopdf) exited with no errors.',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Page = 595x842; 18,14 to 577,828',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] slow_collate=0, slow_duplex=0, slow_order=0',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Before copy_comments - %!PS-Adobe-3.0',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] %!PS-Adobe-3.0',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] %%LanguageLevel: 3',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] %%DocumentSuppliedResources: (atend)',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] %%DocumentMedia: plain 595 842 0 () ()',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] %%BoundingBox: 0 0 595 842',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] %%Pages: 1',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] %%EndComments',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Before copy_prolog - %%BeginDefaults',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Filetype: PostScript',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Reading PostScript input ...',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] --> This document is DSC-conforming!',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Found %RBINumCopies: 1',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Job claims to be DSC-conforming, but "%%BeginProlog" was missing before first line with another"%%BeginProlog" comment (is this a TeX/LaTeX/dvips-generated PostScript file?). Assuming start of "Prolog" here.',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38]',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] -----------',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Found: %%BeginProlog',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Before copy_setup - %%BeginSetup',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Found: %%EndProlog',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38]',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] -----------',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Found: %%BeginSetup',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Found: %%BeginFeature: *Quality 600GrayscaleK',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Option: Quality=600GrayscaleK',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Setting option',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Found: %% FoomaticRIPOptionSetting: Quality=600GrayscaleK',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Option: Quality=600GrayscaleK',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Setting option',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Found: %%BeginFeature: *InputSlot Default',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Option: InputSlot=Default',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Setting option',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Found: %% FoomaticRIPOptionSetting: InputSlot=Default',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Option: InputSlot=Default',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Setting option',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Found: %%BeginFeature: *PaperWeight Medium',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Option: PaperWeight=Medium',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Setting option',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Found: %% FoomaticRIPOptionSetting: PaperWeight=Medium',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Option: PaperWeight=Medium',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Setting option',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Found: %%BeginFeature: *Copies 1',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Option: Copies=1',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Setting option',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Found: %% FoomaticRIPOptionSetting: Copies=1',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Option: Copies=1',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Setting option',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Found: %%BeginFeature: *TonerDensity Medium',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Option: TonerDensity=Medium',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Setting option',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Found: %% FoomaticRIPOptionSetting: TonerDensity=Medium',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Option: TonerDensity=Medium',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Setting option',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Found: %%BeginFeature: *AutoTraySwitch True',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Option: AutoTraySwitch=True',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Setting option',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Found: %% FoomaticRIPOptionSetting: AutoTraySwitch=On',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Option: AutoTraySwitch=On',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Setting option',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Found: %%BeginFeature: *PageRegion A4',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Option: PageRegion=A4',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Setting option',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Found: %% FoomaticRIPOptionSetting: PageSize=A4',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Option: PageSize=A4',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Setting option',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Found: %%BeginFeature: *Duplex None',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Option: Duplex=None',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Setting option',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Found: %% FoomaticRIPOptionSetting: Duplex=None',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Option: Duplex=None',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Setting option',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Found: %%BeginFeature: *TrCurrent Medium',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Option: TrCurrent=Medium',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Setting option',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Found: %% FoomaticRIPOptionSetting: TrCurrent=Medium',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Option: TrCurrent=Medium',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Setting option',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Found: %%BeginFeature: *Economode Off',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Option: Economode=Off',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Setting option',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Found: %% FoomaticRIPOptionSetting: Economode=Off',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Option: Economode=Off',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Setting option',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Found: %%BeginFeature: *Resolution 600',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Option: Resolution=600',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Setting option',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Found: %% FoomaticRIPOptionSetting: Resolution=600',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Option: Resolution=600',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Setting option',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Before page loop - %%Page: 1 1',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Copying page 1...',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] pagew = 559.0, pagel = 813.2',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] bboxx = 0, bboxy = 0, bboxw = 595, bboxl = 842',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] PageLeft = 18.0, PageRight = 577.0',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] PageTop = 827.6, PageBottom = 14.4',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] PageWidth = 595.0, PageLength = 842.0',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Found: %%EndSetup',
               "D [16/Nov/2008:12:47:39 -0200] [Job 38] Inserting PostScript code for CUPS' page accounting",
               'D [16/Nov/2008:12:47:39 -0200] [Job 38]',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] -----------',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] New page: %%Page: 1 1',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Inserting option code into "PageSetup" section.',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38]',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Found: %%BeginPageSetup',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Wrote 1 pages...',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Flushing FIFO.',
               'D [16/Nov/2008:12:47:39 -0200] PID 21003 (/usr/lib/cups/filter/cpdftocps) exited with no errors.',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38]',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Starting renderer with command: "gs -sstdout=%stderr  -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=ijs -sIjsServer=hpijs -sDeviceManufacturer="HEWLETT-PACKARD" -sDeviceModel="HP LaserJet" -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842 -dDuplex=false -r600 -sIjsParams=Quality:Quality=0,Quality:ColorMode=0,Quality:MediaType=0,Quality:PenSet=0,PS:MediaPosition=7 -dIjsUseOutputFD -sOutputFile=%stdout -"',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Starting process "kid3" (generation 1)',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Starting process "kid4" (generation 2)',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] JCL: @PJL SET OKIAUTOTRAYSWITCH=ON',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] @PJL SET DENSITY=0',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] @PJL SET OKIMEDIAINTRAY2=MEDIUM',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] @PJL SET OKIMEDIAINTRAY1=MEDIUM',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] @PJL SET OKIMEDIATYPEINTRAY2=PLAIN',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] @PJL SET OKIMEDIATYPEINTRAY1=PLAIN',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] @PJL SET OKISETTING=0',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] @PJL SET OKIPLACEPAGE=CENTER',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] @PJL SET ECONOMODE=OFF',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] @PJL SET OKIRESOLUTION=600',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] <job data> \x1b%-12345X@PJL RESET',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38]',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38]',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Starting process "renderer" (generation 2)',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38]',
               'D [16/Nov/2008:12:47:39 -0200] [Job 38] Closing renderer',
               'I [16/Nov/2008:12:47:39 -0200] Saving subscriptions.conf...',
               'D [16/Nov/2008:12:47:40 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:47:40 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:47:40 -0200] CUPS-Get-Default',
               'D [16/Nov/2008:12:47:40 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:47:40 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:47:40 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:47:40 -0200] CUPS-Get-Printers',
               'D [16/Nov/2008:12:47:40 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:47:40 -0200] [Job 38] Read 4096 bytes of print data...',
               'D [16/Nov/2008:12:47:40 -0200] [Job 38] Wrote 4096 bytes of print data...',
               'D [16/Nov/2008:12:47:40 -0200] [Job 38] Read 8192 bytes of print data...',
               'I [16/Nov/2008:12:47:40 -0200] Saving subscriptions.conf...',
               'D [16/Nov/2008:12:47:40 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:40 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:40 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:40 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:40 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:40 -0200] [Job 38] Received 151 bytes of back-channel data!',
               'D [16/Nov/2008:12:47:40 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:40 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:40 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:40 -0200] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [16/Nov/2008:12:47:40 -0200] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [16/Nov/2008:12:47:40 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:47:40 -0200] Get-Jobs ipp://localhost/jobs/',
               'D [16/Nov/2008:12:47:40 -0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:47:40 -0200] cupsdCloseClient: 11',
               'D [16/Nov/2008:12:47:40 -0200] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [16/Nov/2008:12:47:40 -0200] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [16/Nov/2008:12:47:40 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:47:40 -0200] Get-Notifications /',
               'D [16/Nov/2008:12:47:40 -0200] cupsdIsAuthorized: requesting-user-name="edilson"',
               'D [16/Nov/2008:12:47:40 -0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:47:40 -0200] cupsdCloseClient: 11',
               'D [16/Nov/2008:12:47:40 -0200] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [16/Nov/2008:12:47:40 -0200] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [16/Nov/2008:12:47:40 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:47:40 -0200] Get-Notifications /',
               'D [16/Nov/2008:12:47:40 -0200] cupsdIsAuthorized: requesting-user-name="edilson"',
               'D [16/Nov/2008:12:47:40 -0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:47:40 -0200] cupsdCloseClient: 11',
               'D [16/Nov/2008:12:47:40 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:40 -0200] [Job 38] Received 92 bytes of back-channel data!',
               'D [16/Nov/2008:12:47:40 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:40 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:40 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:40 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:40 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:40 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:40 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:40 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:40 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:40 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:40 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:40 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:40 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:40 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:40 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:40 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:40 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:40 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:40 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:41 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:41 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:41 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:41 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:41 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:41 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:41 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:41 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:41 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:41 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:41 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:41 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:41 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:41 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:41 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:41 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:41 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:41 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:41 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:41 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:41 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:41 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:41 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:41 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:41 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:41 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:41 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:41 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:41 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:41 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:41 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:41 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:41 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:41 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:41 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:41 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:41 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:41 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:41 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:41 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:41 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:41 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:42 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:42 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:42 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:42 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:42 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:42 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:42 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:42 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:42 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:42 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:42 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:42 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:42 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:42 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:42 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:42 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:42 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:42 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:42 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:42 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:42 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:42 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:42 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:42 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:43 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:43 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:43 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:43 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:43 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:43 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:43 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:43 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:43 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:43 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:43 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:43 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:44 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:44 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:44 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:44 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:44 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:44 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:44 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:44 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:44 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:44 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:44 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:44 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:45 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:45 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:45 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:45 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:45 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:47:45 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:47:45 -0200] CUPS-Get-Default',
               'D [16/Nov/2008:12:47:45 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:47:45 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:47:45 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:47:45 -0200] CUPS-Get-Printers',
               'D [16/Nov/2008:12:47:45 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:47:45 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:45 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:45 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:45 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:45 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:45 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:45 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:45 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:45 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:45 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:45 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:45 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:46 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:46 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:46 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:46 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:46 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:46 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:46 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:46 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:46 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:46 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:46 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:46 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:47 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:47 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:47 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:47 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:47 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:47 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:47 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:47 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:47 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:47 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:47 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:48 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:48 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:48 -0200] [Job 38] renderer exited with status 0',
               'D [16/Nov/2008:12:47:48 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:48 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:48 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:48 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:48 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:48 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:48 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:48 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:48 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:48 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:48 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:48 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:48 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:49 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:49 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:49 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:49 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:49 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:49 -0200] [Job 38] kid4 exited with status 0',
               'D [16/Nov/2008:12:47:49 -0200] [Job 38] kid3 finished',
               'D [16/Nov/2008:12:47:49 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:49 -0200] [Job 38] kid3 exited with status 0',
               'D [16/Nov/2008:12:47:49 -0200] [Job 38]',
               'D [16/Nov/2008:12:47:49 -0200] [Job 38] Closing foomatic-rip.',
               'D [16/Nov/2008:12:47:49 -0200] PID 21005 (/usr/lib/cups/filter/foomatic-rip) exited with no errors.',
               'D [16/Nov/2008:12:47:49 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:49 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:49 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:49 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:49 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:49 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:49 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:49 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:49 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:49 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:49 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:49 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:49 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:49 -0200] [Job 38] Read 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:49 -0200] [Job 38] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:12:47:49 -0200] [Job 38] Read 846 bytes of print data...',
               'D [16/Nov/2008:12:47:49 -0200] [Job 38] Wrote 846 bytes of print data...',
               'D [16/Nov/2008:12:47:49 -0200] PID 21009 (/usr/lib/cups/backend/usb) exited with no errors.',
               'D [16/Nov/2008:12:47:49 -0200] [Job 38] File 0 is complete.',
               'I [16/Nov/2008:12:47:49 -0200] [Job 38] Completed successfully.',
               'I [16/Nov/2008:12:47:49 -0200] Saving subscriptions.conf...',
               'I [16/Nov/2008:12:47:49 -0200] Saving subscriptions.conf...',
               'D [16/Nov/2008:12:47:50 -0200] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [16/Nov/2008:12:47:50 -0200] [Job 38] Unloading...',
               'D [16/Nov/2008:12:47:50 -0200] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [16/Nov/2008:12:47:50 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:47:50 -0200] Get-Jobs ipp://localhost/jobs/',
               'D [16/Nov/2008:12:47:50 -0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:47:50 -0200] cupsdCloseClient: 11',
               'D [16/Nov/2008:12:47:50 -0200] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [16/Nov/2008:12:47:50 -0200] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [16/Nov/2008:12:47:50 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:47:50 -0200] Get-Notifications /',
               'D [16/Nov/2008:12:47:50 -0200] cupsdIsAuthorized: requesting-user-name="edilson"',
               'D [16/Nov/2008:12:47:50 -0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:47:50 -0200] cupsdCloseClient: 11',
               'D [16/Nov/2008:12:47:50 -0200] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [16/Nov/2008:12:47:50 -0200] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [16/Nov/2008:12:47:50 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:47:50 -0200] Get-Notifications /',
               'D [16/Nov/2008:12:47:50 -0200] cupsdIsAuthorized: requesting-user-name="edilson"',
               'D [16/Nov/2008:12:47:50 -0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:47:50 -0200] cupsdCloseClient: 11',
               'D [16/Nov/2008:12:47:50 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:47:50 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:47:50 -0200] CUPS-Get-Default',
               'D [16/Nov/2008:12:47:50 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:47:50 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:47:50 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:47:50 -0200] CUPS-Get-Printers',
               'D [16/Nov/2008:12:47:50 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:47:55 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:47:55 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:47:55 -0200] CUPS-Get-Default',
               'D [16/Nov/2008:12:47:55 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:47:55 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:47:55 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:47:55 -0200] CUPS-Get-Printers',
               'D [16/Nov/2008:12:47:55 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:48:00 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:48:00 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:48:00 -0200] CUPS-Get-Default',
               'D [16/Nov/2008:12:48:00 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:48:00 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:48:00 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:48:00 -0200] CUPS-Get-Printers',
               'D [16/Nov/2008:12:48:00 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:48:05 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:48:05 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:48:05 -0200] CUPS-Get-Default',
               'D [16/Nov/2008:12:48:05 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:48:05 -0200] Report: clients=2',
               'D [16/Nov/2008:12:48:05 -0200] Report: jobs=12',
               'D [16/Nov/2008:12:48:05 -0200] Report: jobs-active=1',
               'D [16/Nov/2008:12:48:05 -0200] Report: printers=2',
               'D [16/Nov/2008:12:48:05 -0200] Report: printers-implicit=0',
               'D [16/Nov/2008:12:48:05 -0200] Report: stringpool-string-count=4503',
               'D [16/Nov/2008:12:48:05 -0200] Report: stringpool-alloc-bytes=10952',
               'D [16/Nov/2008:12:48:05 -0200] Report: stringpool-total-bytes=93968',
               'D [16/Nov/2008:12:48:05 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:48:05 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:48:05 -0200] CUPS-Get-Printers',
               'D [16/Nov/2008:12:48:05 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:48:10 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:48:10 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:48:10 -0200] [Job 37] Unloading...',
               'D [16/Nov/2008:12:48:10 -0200] CUPS-Get-Default',
               'D [16/Nov/2008:12:48:10 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:48:10 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:48:10 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:48:10 -0200] CUPS-Get-Printers',
               'D [16/Nov/2008:12:48:10 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:48:15 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:48:15 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:48:15 -0200] CUPS-Get-Default',
               'D [16/Nov/2008:12:48:15 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:48:15 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:48:15 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:48:15 -0200] CUPS-Get-Printers',
               'D [16/Nov/2008:12:48:15 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:48:20 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:48:20 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:48:20 -0200] CUPS-Get-Default',
               'D [16/Nov/2008:12:48:20 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:48:20 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:48:20 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:48:20 -0200] CUPS-Get-Printers',
               'D [16/Nov/2008:12:48:20 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:48:25 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:48:25 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:48:25 -0200] CUPS-Get-Default',
               'D [16/Nov/2008:12:48:25 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:48:25 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:48:25 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:48:25 -0200] CUPS-Get-Printers',
               'D [16/Nov/2008:12:48:25 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:48:30 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:48:30 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:48:30 -0200] CUPS-Get-Default',
               'D [16/Nov/2008:12:48:30 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:48:30 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:48:30 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:48:30 -0200] CUPS-Get-Printers',
               'D [16/Nov/2008:12:48:30 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:48:35 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:48:35 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:48:35 -0200] CUPS-Get-Default',
               'D [16/Nov/2008:12:48:35 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:48:35 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:48:35 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:48:35 -0200] CUPS-Get-Printers',
               'D [16/Nov/2008:12:48:35 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:48:40 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:48:40 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:48:40 -0200] CUPS-Get-Default',
               'D [16/Nov/2008:12:48:40 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:48:40 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:48:40 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:48:40 -0200] CUPS-Get-Printers',
               'D [16/Nov/2008:12:48:40 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:48:41 -0200] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [16/Nov/2008:12:48:41 -0200] cupsdReadClient: 11 POST /jobs/ HTTP/1.1',
               'D [16/Nov/2008:12:48:41 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:48:41 -0200] Cancel-Job ipp://localhost/jobs/37',
               'D [16/Nov/2008:12:48:41 -0200] cupsdIsAuthorized: requesting-user-name="edilson"',
               'D [16/Nov/2008:12:48:41 -0200] [Job 37] Loading attributes...',
               'I [16/Nov/2008:12:48:41 -0200] Saving subscriptions.conf...',
               'I [16/Nov/2008:12:48:41 -0200] [Job 37] Canceled by "edilson".',
               'D [16/Nov/2008:12:48:41 -0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:48:41 -0200] cupsdReadClient: 11 POST /jobs/ HTTP/1.1',
               'D [16/Nov/2008:12:48:41 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:48:41 -0200] Cancel-Job ipp://localhost/jobs/38',
               'D [16/Nov/2008:12:48:41 -0200] cupsdIsAuthorized: requesting-user-name="edilson"',
               "D [16/Nov/2008:12:48:41 -0200] Cancel-Job client-error-not-possible: Job #38 is already completed - can't cancel.",
               'D [16/Nov/2008:12:48:41 -0200] cupsdProcessIPPRequest: 11 status_code=404 (client-error-not-possible)',
               'D [16/Nov/2008:12:48:41 -0200] cupsdCloseClient: 11',
               'D [16/Nov/2008:12:48:45 -0200] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [16/Nov/2008:12:48:45 -0200] cupsdReadClient: 11 POST /jobs/ HTTP/1.1',
               'D [16/Nov/2008:12:48:45 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:48:45 -0200] Cancel-Job ipp://localhost/jobs/37',
               'D [16/Nov/2008:12:48:45 -0200] cupsdIsAuthorized: requesting-user-name="edilson"',
               "D [16/Nov/2008:12:48:45 -0200] Cancel-Job client-error-not-possible: Job #37 is already canceled - can't cancel.",
               'D [16/Nov/2008:12:48:45 -0200] cupsdProcessIPPRequest: 11 status_code=404 (client-error-not-possible)',
               'D [16/Nov/2008:12:48:45 -0200] cupsdReadClient: 11 POST /jobs/ HTTP/1.1',
               'D [16/Nov/2008:12:48:45 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:48:45 -0200] Cancel-Job ipp://localhost/jobs/38',
               'D [16/Nov/2008:12:48:45 -0200] cupsdIsAuthorized: requesting-user-name="edilson"',
               "D [16/Nov/2008:12:48:45 -0200] Cancel-Job client-error-not-possible: Job #38 is already completed - can't cancel.",
               'D [16/Nov/2008:12:48:45 -0200] cupsdProcessIPPRequest: 11 status_code=404 (client-error-not-possible)',
               'D [16/Nov/2008:12:48:45 -0200] cupsdCloseClient: 11',
               'D [16/Nov/2008:12:48:45 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:48:45 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:48:45 -0200] CUPS-Get-Default',
               'D [16/Nov/2008:12:48:45 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:48:45 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:48:45 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:48:45 -0200] CUPS-Get-Printers',
               'D [16/Nov/2008:12:48:45 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:48:50 -0200] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [16/Nov/2008:12:48:50 -0200] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [16/Nov/2008:12:48:50 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:48:50 -0200] Get-Notifications /',
               'D [16/Nov/2008:12:48:50 -0200] cupsdIsAuthorized: requesting-user-name="edilson"',
               'D [16/Nov/2008:12:48:50 -0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:48:50 -0200] cupsdCloseClient: 11',
               'D [16/Nov/2008:12:48:50 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:48:50 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:48:50 -0200] CUPS-Get-Default',
               'D [16/Nov/2008:12:48:50 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:48:50 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:48:50 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:48:50 -0200] CUPS-Get-Printers',
               'D [16/Nov/2008:12:48:50 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:48:55 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:48:55 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:48:55 -0200] CUPS-Get-Default',
               'D [16/Nov/2008:12:48:55 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:48:55 -0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:12:48:55 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:48:55 -0200] CUPS-Get-Printers',
               'D [16/Nov/2008:12:48:55 -0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:48:55 -0200] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [16/Nov/2008:12:48:55 -0200] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [16/Nov/2008:12:48:55 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:48:55 -0200] Get-Job-Attributes ipp://localhost/jobs/37',
               'D [16/Nov/2008:12:48:55 -0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:48:55 -0200] cupsdCloseClient: 11',
               'D [16/Nov/2008:12:48:55 -0200] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [16/Nov/2008:12:48:55 -0200] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [16/Nov/2008:12:48:55 -0200] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:12:48:55 -0200] Cancel-Subscription /',
               'D [16/Nov/2008:12:48:55 -0200] cupsdIsAuthorized: requesting-user-name="edilson"',
               'I [16/Nov/2008:12:48:55 -0200] Saving subscriptions.conf...',
               'D [16/Nov/2008:12:48:55 -0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [16/Nov/2008:12:48:55 -0200] cupsdCloseClient: 11',
               'D [16/Nov/2008:12:48:55 -0200] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [16/Nov/2008:12:48:55 -0200] cupsdCloseClient: 9',
               'D [16/Nov/2008:12:48:55 -0200] cupsdReadClient: 11 GET /admin/log/error_log HTTP/1.1',
               'D [16/Nov/2008:12:48:55 -0200] cupsdAuthorize: No authentication data provided.']}

Hope this helps to find out what is going on ...

Tkx

Edilson

---

### Post by Merovius on 2008-11-16
I found this error log for cups through web interface I didn't know about until 2 minutes ago..

E [16/Nov/2008:08:49:07 -0500] "/etc/cups/ssl/server.crt" is a bad symlink - No such file or directory
E [16/Nov/2008:09:22:39 -0500] "/etc/cups/ssl/server.crt" is a bad symlink - No such file or directory
E [16/Nov/2008:09:24:49 -0500] "/etc/cups/ssl/server.crt" is a bad symlink - No such file or directory
E [16/Nov/2008:09:26:47 -0500] "/etc/cups/ssl/server.key" is a bad symlink - No such file or directory
E [16/Nov/2008:09:28:44 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [16/Nov/2008:09:32:46 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [16/Nov/2008:09:33:13 -0500] Pause-Printer: Unauthorized
E [16/Nov/2008:09:33:13 -0500] cupsdAuthorize: Local authentication certificate not found!
E [16/Nov/2008:09:33:13 -0500] cupsdAuthorize: Local authentication certificate not found!
E [16/Nov/2008:09:33:13 -0500] cupsdAuthorize: Local authentication certificate not found!
E [16/Nov/2008:09:33:13 -0500] cupsdAuthorize: Local authentication certificate not found!
E [16/Nov/2008:09:33:29 -0500] Resume-Printer: Unauthorized
E [16/Nov/2008:09:33:29 -0500] cupsdAuthorize: Local authentication certificate not found!
E [16/Nov/2008:09:33:29 -0500] cupsdAuthorize: Local authentication certificate not found!
E [16/Nov/2008:09:33:29 -0500] cupsdAuthorize: Local authentication certificate not found!
E [16/Nov/2008:09:33:29 -0500] cupsdAuthorize: Local authentication certificate not found!
E [16/Nov/2008:09:33:29 -0500] cupsdAuthorize: Local authentication certificate not found!
E [16/Nov/2008:09:33:29 -0500] cupsdAuthorize: Local authentication certificate not found!
E [16/Nov/2008:09:33:29 -0500] cupsdAuthorize: Local authentication certificate not found!
E [16/Nov/2008:09:33:29 -0500] cupsdAuthorize: Local authentication certificate not found!
E [16/Nov/2008:09:33:29 -0500] cupsdAuthorize: Local authentication certificate not found!
E [16/Nov/2008:09:33:29 -0500] cupsdAuthorize: Local authentication certificate not found!
E [16/Nov/2008:09:33:29 -0500] cupsdAuthorize: Local authentication certificate not found!
E [16/Nov/2008:09:33:29 -0500] cupsdAuthorize: Local authentication certificate not found!
E [16/Nov/2008:09:33:30 -0500] cupsdAuthorize: Local authentication certificate not found!
E [16/Nov/2008:09:33:30 -0500] cupsdAuthorize: Local authentication certificate not found!
E [16/Nov/2008:09:33:30 -0500] cupsdAuthorize: Local authentication certificate not found!
E [16/Nov/2008:09:33:30 -0500] cupsdAuthorize: Local authentication certificate not found!
E [16/Nov/2008:09:33:31 -0500] cupsdAuthorize: Local authentication certificate not found!
E [16/Nov/2008:09:33:31 -0500] cupsdAuthorize: Local authentication certificate not found!
E [16/Nov/2008:09:33:31 -0500] cupsdAuthorize: Local authentication certificate not found!
E [16/Nov/2008:09:33:31 -0500] cupsdAuthorize: Local authentication certificate not found!
E [16/Nov/2008:09:34:10 -0500] cupsdAuthorize: Local authentication certificate not found!
E [16/Nov/2008:09:34:10 -0500] cupsdAuthorize: Local authentication certificate not found!
E [16/Nov/2008:09:34:14 -0500] cupsdAuthorize: Local authentication certificate not found!
E [16/Nov/2008:09:34:14 -0500] cupsdAuthorize: Local authentication certificate not found!
E [16/Nov/2008:09:34:14 -0500] cupsdAuthorize: Local authentication certificate not found!
E [16/Nov/2008:09:37:48 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [16/Nov/2008:09:39:17 -0500] CUPS-Delete-Printer: Unauthorized
E [16/Nov/2008:09:41:34 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [16/Nov/2008:09:43:09 -0500] CUPS-Delete-Printer: Unauthorized
E [16/Nov/2008:09:44:05 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [16/Nov/2008:09:52:11 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [16/Nov/2008:10:30:40 -0500] Purge-Jobs: Unauthorized
E [16/Nov/2008:10:30:53 -0500] Purge-Jobs: Unauthorized
E [16/Nov/2008:10:31:10 -0500] CUPS-Set-Default: Unauthorized
E [16/Nov/2008:10:31:13 -0500] cupsdAuthorize: Empty Basic password!
E [16/Nov/2008:10:31:13 -0500] CUPS-Set-Default: Unauthorized
E [16/Nov/2008:10:31:15 -0500] cupsdAuthorize: Empty Basic password!
E [16/Nov/2008:10:31:15 -0500] CUPS-Set-Default: Unauthorized
E [16/Nov/2008:10:31:34 -0500] CUPS-Set-Default: Unauthorized
E [16/Nov/2008:10:32:04 -0500] Purge-Jobs: Unauthorized

trashed file server.crt

trashed file server.key

Thats how I got the printer to detect. Now I just need to be authorized..

---

### Post by Merovius on 2008-11-16
Got this from troubleshooting

Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest Stylus-CX4200 (default)>,
 'cups_instance': None,
 'cups_queue': 'Stylus-CX4200',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://EPSON/Stylus%20CX4200',
                       'printer-info': u'EPSON Stylus CX4200',
                       'printer-is-shared': True,
                       'printer-location': u'steve-desktop',
                       'printer-make-and-model': u'Epson Stylus Color PRO Foomatic/stcolor',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 143372,
                       'printer-uri-supported': u'ipp://localhost:631/printers/Stylus-CX4200'},
 'cups_printer_remote': False,
 'is_cups_class': False}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'Dithering': u'ColourFastCMYK',
                                            u'PageRegion': u'Letter',
                                            u'PageSize': u'Letter',
                                            u'Resolution': u'360dpi',
                                            u'Unidirectional': u'False',
                                            u'Weaving': u'Off'},
                               u'Miscellaneous': {u'Encoding': u'RunLength',
                                                  u'Uniform': u'False',
                                                  u'stcolor': u'False'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Choose device):
{'cups_device_dict': {'device-class': u'direct',
                      'device-id': u'MFG:EPSON;CMD:ESCPL2,BDC,D4,ESCPR1;MDL:Stylus CX4200;CLS:PRINTER;DES:EPSON Stylus CX4200;',
                      'device-info': u'EPSON Stylus CX4200 USB #1',
                      'device-make-and-model': u'EPSON Stylus CX4200'}}
Page 7 (Error log checkpoint):
{'cups_server_settings': {'DefaultAuthType': 'Basic',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '0',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '0',
                          '_share_printers': '0',
                          '_user_cancel_any': '1'},
 'error_log_checkpoint': 6683L,
 'error_log_debug_logging_set': True}
Page 8 (Print test page):
{'test_page_attempted': True,
 'test_page_completions': [(14, u'Job completed.')],
 'test_page_job_id': [14],
 'test_page_job_status': [(True,
                           14,
                           'Stylus-CX4200',
                           'Test Page',
                           'Completed',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-us',
                            'document-format': u'application/postscript',
                            'job-hold-until': u'no-hold',
                            'job-id': 14,
                            'job-k-octets': 17,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/14',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'steve',
                            'job-preserved': False,
                            'job-printer-state-message': u'Printer is now on-line.',
                            'job-printer-state-reasons': [u'none'],
                            'job-printer-up-time': 1226850525,
                            'job-printer-uri': u'ipp://steve-desktop:631/printers/Stylus-CX4200',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 9,
                            'job-state-reasons': u'job-completed-successfully',
                            'job-uri': u'ipp://localhost:631/jobs/14',
                            'job-uuid': u'urn:uuid:c9e8e46a-e130-320a-4891-d2f560b75d9f',
                            'printer-uri': u'ipp://localhost/printers/Stylus-CX4200',
                            'time-at-completed': 1226850518,
                            'time-at-creation': 1226850516,
                            'time-at-processing': 1226850516})],
 'test_page_successful': False}
Page 9 (Error log fetch):
{'error_log': ['D [16/Nov/2008:10:48:26 -0500] cupsdCloseClient: 7',
               'D [16/Nov/2008:10:48:26 -0500] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [16/Nov/2008:10:48:26 -0500] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:10:48:26 -0500] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:10:48:26 -0500] Get-Jobs ipp://localhost/jobs/',
               'D [16/Nov/2008:10:48:26 -0500] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:10:48:26 -0500] cupsdCloseClient: 7',
               'D [16/Nov/2008:10:48:26 -0500] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [16/Nov/2008:10:48:26 -0500] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:10:48:26 -0500] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:10:48:26 -0500] Create-Printer-Subscription /',
               'D [16/Nov/2008:10:48:26 -0500] cupsdCreateSubscription(con=0xb8201d98(7), uri="/")',
               'D [16/Nov/2008:10:48:26 -0500] pullmethod="ippget"',
               'D [16/Nov/2008:10:48:26 -0500] notify-lease-duration=86400',
               'D [16/Nov/2008:10:48:26 -0500] notify-time-interval=0',
               'D [16/Nov/2008:10:48:26 -0500] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [16/Nov/2008:10:48:26 -0500] Added subscription 43 for server',
               'I [16/Nov/2008:10:48:26 -0500] Saving subscriptions.conf...',
               'D [16/Nov/2008:10:48:26 -0500] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:10:48:26 -0500] cupsdCloseClient: 7',
               'D [16/Nov/2008:10:48:27 -0500] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [16/Nov/2008:10:48:27 -0500] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:10:48:27 -0500] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:10:48:27 -0500] Get-Notifications /',
               'D [16/Nov/2008:10:48:27 -0500] cupsdIsAuthorized: requesting-user-name="steve"',
               'D [16/Nov/2008:10:48:27 -0500] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:10:48:27 -0500] cupsdCloseClient: 7',
               'D [16/Nov/2008:10:48:36 -0500] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [16/Nov/2008:10:48:36 -0500] cupsdReadClient: 7 POST /printers/Stylus-CX4200 HTTP/1.1',
               'D [16/Nov/2008:10:48:36 -0500] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:10:48:36 -0500] Print-Job ipp://localhost/printers/Stylus-CX4200',
               'D [16/Nov/2008:10:48:36 -0500] add_job: requesting-user-name="steve"',
               'D [16/Nov/2008:10:48:36 -0500] Adding default job-sheets values "none,none"...',
               'I [16/Nov/2008:10:48:36 -0500] [Job 14] Adding start banner page "none".',
               'I [16/Nov/2008:10:48:36 -0500] Saving subscriptions.conf...',
               'I [16/Nov/2008:10:48:36 -0500] [Job 14] Adding end banner page "none".',
               'I [16/Nov/2008:10:48:36 -0500] [Job 14] File of type application/postscript queued by "steve".',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] hold_until=0',
               'I [16/Nov/2008:10:48:36 -0500] [Job 14] Queued on "Stylus-CX4200" by "steve".',
               'I [16/Nov/2008:10:48:36 -0500] Saving subscriptions.conf...',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] job-sheets=none,none',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] banner_page = 0',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] argv[0]="Stylus-CX4200"',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] argv[1]="14"',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] argv[2]="steve"',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] argv[3]="Test Page"',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] argv[4]="1"',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] argv[5]="job-uuid=urn:uuid:c9e8e46a-e130-320a-4891-d2f560b75d9f"',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] argv[6]="/var/spool/cups/d00014-001"',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] envp[9]="SERVER_ADMIN=root@steve-desktop"',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] envp[10]="SOFTWARE=CUPS/1.3.9"',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] envp[11]="TMPDIR=/var/spool/cups/tmp"',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] envp[12]="TZ=America/New_York"',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] envp[13]="USER=root"',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] envp[15]="CUPS_ENCRYPTION=IfRequested"',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] envp[16]="IPP_PORT=631"',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] envp[17]="CHARSET=utf-8"',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] envp[18]="LANG=en_US.UTF8"',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] envp[19]="PPD=/etc/cups/ppd/Stylus-CX4200.ppd"',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] envp[20]="RIP_MAX_CACHE=8m"',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] envp[21]="CONTENT_TYPE=application/postscript"',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] envp[22]="DEVICE_URI=usb://EPSON/Stylus%20CX4200"',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] envp[23]="PRINTER=Stylus-CX4200"',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] envp[24]="FINAL_CONTENT_TYPE=printer/Stylus-CX4200"',
               'I [16/Nov/2008:10:48:36 -0500] [Job 14] Started filter /usr/lib/cups/filter/pstopdf (PID 7560)',
               'I [16/Nov/2008:10:48:36 -0500] [Job 14] Started filter /usr/lib/cups/filter/pdftopdf (PID 7562)',
               'I [16/Nov/2008:10:48:36 -0500] [Job 14] Started filter /usr/lib/cups/filter/foomatic-rip (PID 7564)',
               'I [16/Nov/2008:10:48:36 -0500] [Job 14] Started backend /usr/lib/cups/backend/usb (PID 7567)',
               'I [16/Nov/2008:10:48:36 -0500] Saving subscriptions.conf...',
               'D [16/Nov/2008:10:48:36 -0500] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] pstopdf argv[6] = 14 steve Test Page 1 job-uuid=urn:uuid:c9e8e46a-e130-320a-4891-d2f560b75d9f /var/spool/cups/d00014-001',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] PPD: /etc/cups/ppd/Stylus-CX4200.ppd',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] Getting input from file',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] foomatic-rip version 4.0.0.177 running...',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] Parsing PPD file ...',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] Added option PageSize',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] Added option ImageableArea',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] Added option PaperDimension',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] Added option Unidirectional',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] Added option Weaving',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] Printer using device file "/dev/usblp0"...',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] backendRunLoop(print_fd=0, device_fd=5, use_bc=1, side_cb=0xb8014a80)',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] Added option Dithering',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] Added option Resolution',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] Added option stcolor',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] Added option Uniform',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] Added option Encoding',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] Added option Font',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14]',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] Parameter Summary',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] -----------------',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14]',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] Spooler: cups',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] Printer: Stylus-CX4200',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] Shell: /bin/bash',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] PPD file: /etc/cups/ppd/Stylus-CX4200.ppd',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] ATTR file:',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] Printer model: Epson Stylus Color PRO Foomatic/stcolor',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] Job title: Test Page',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] File(s) to be printed:',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] <STDIN>',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14]',
               "D [16/Nov/2008:10:48:36 -0500] [Job 14] GhostScript extra search path ('GS_LIB'): /usr/share/cups/fonts",
               'I [16/Nov/2008:10:48:36 -0500] Saving subscriptions.conf...',
               "D [16/Nov/2008:10:48:36 -0500] [Job 14] Pondering option 'job-uuid=urn:uuid:c9e8e46a-e130-320a-4891-d2f560b75d9f'",
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] Unknown option job-uuid=urn:uuid:c9e8e46a-e130-320a-4891-d2f560b75d9f.',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14]',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] ================================================',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14]',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] File: <STDIN>',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14]',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] ================================================',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14]',
               'D [16/Nov/2008:10:48:36 -0500] cupsdCloseClient: 7',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] Resolution: 360',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] Page size: Letter',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] Width: 612, height: 792, absolute margins: , , ,',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] Relative margins: 18, 36, 18, 36',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] PostScript to be injected: <</.HWMargins[18 36 18 36] /Margins[0 0]>>setpagedevice',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] PPD options: -r360 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] Injecting PostScript: <</.HWMargins[18 36 18 36] /Margins[0 0]>>setpagedevice',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] Running cat | /usr/bin/ps2pdf13 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode -r360 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 - -',
               'D [16/Nov/2008:10:48:36 -0500] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [16/Nov/2008:10:48:36 -0500] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:10:48:36 -0500] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:10:48:36 -0500] Get-Notifications /',
               'D [16/Nov/2008:10:48:36 -0500] cupsdIsAuthorized: requesting-user-name="steve"',
               'D [16/Nov/2008:10:48:36 -0500] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:10:48:36 -0500] cupsdAcceptClient: 9 from localhost (Domain)',
               'D [16/Nov/2008:10:48:36 -0500] cupsdReadClient: 9 POST / HTTP/1.1',
               'E [16/Nov/2008:10:48:36 -0500] cupsdAuthorize: Local authentication certificate not found!',
               'D [16/Nov/2008:10:48:36 -0500] CUPS-Get-Printers',
               'D [16/Nov/2008:10:48:36 -0500] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [16/Nov/2008:10:48:36 -0500] cupsdReadClient: 9 POST / HTTP/1.1',
               'E [16/Nov/2008:10:48:36 -0500] cupsdAuthorize: Local authentication certificate not found!',
               'D [16/Nov/2008:10:48:36 -0500] CUPS-Get-Classes',
               'D [16/Nov/2008:10:48:36 -0500] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [16/Nov/2008:10:48:36 -0500] cupsdReadClient: 9 POST / HTTP/1.1',
               'E [16/Nov/2008:10:48:36 -0500] cupsdAuthorize: Local authentication certificate not found!',
               'D [16/Nov/2008:10:48:36 -0500] CUPS-Get-Default',
               'D [16/Nov/2008:10:48:36 -0500] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [16/Nov/2008:10:48:36 -0500] cupsdReadClient: 9 POST / HTTP/1.1',
               'E [16/Nov/2008:10:48:36 -0500] cupsdAuthorize: Local authentication certificate not found!',
               'D [16/Nov/2008:10:48:36 -0500] CUPS-Get-Printers',
               'D [16/Nov/2008:10:48:36 -0500] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [16/Nov/2008:10:48:36 -0500] cupsdReadClient: 9 POST / HTTP/1.1',
               'E [16/Nov/2008:10:48:36 -0500] cupsdAuthorize: Local authentication certificate not found!',
               'D [16/Nov/2008:10:48:36 -0500] CUPS-Get-Classes',
               'D [16/Nov/2008:10:48:36 -0500] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [16/Nov/2008:10:48:36 -0500] cupsdReadClient: 9 POST / HTTP/1.1',
               'E [16/Nov/2008:10:48:36 -0500] cupsdAuthorize: Local authentication certificate not found!',
               'D [16/Nov/2008:10:48:36 -0500] CUPS-Get-Default',
               'D [16/Nov/2008:10:48:36 -0500] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [16/Nov/2008:10:48:36 -0500] cupsdAcceptClient: 13 from localhost (Domain)',
               'D [16/Nov/2008:10:48:36 -0500] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [16/Nov/2008:10:48:36 -0500] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:10:48:36 -0500] Get-Jobs ipp://localhost/jobs/',
               'D [16/Nov/2008:10:48:36 -0500] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)',
               'D [16/Nov/2008:10:48:36 -0500] cupsdCloseClient: 13',
               'D [16/Nov/2008:10:48:36 -0500] cupsdAcceptClient: 13 from localhost (Domain)',
               'D [16/Nov/2008:10:48:36 -0500] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [16/Nov/2008:10:48:36 -0500] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:10:48:36 -0500] Get-Notifications /',
               'D [16/Nov/2008:10:48:36 -0500] cupsdIsAuthorized: requesting-user-name="steve"',
               'D [16/Nov/2008:10:48:36 -0500] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)',
               'D [16/Nov/2008:10:48:36 -0500] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [16/Nov/2008:10:48:36 -0500] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:10:48:36 -0500] Get-Job-Attributes ipp://localhost/jobs/14',
               'D [16/Nov/2008:10:48:36 -0500] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)',
               'D [16/Nov/2008:10:48:36 -0500] cupsdCloseClient: 7',
               'D [16/Nov/2008:10:48:36 -0500] cupsdCloseClient: 13',
               'D [16/Nov/2008:10:48:36 -0500] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [16/Nov/2008:10:48:36 -0500] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:10:48:36 -0500] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:10:48:36 -0500] Get-Notifications /',
               'D [16/Nov/2008:10:48:36 -0500] cupsdIsAuthorized: requesting-user-name="steve"',
               'D [16/Nov/2008:10:48:36 -0500] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:10:48:36 -0500] cupsdCloseClient: 7',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] Filetype: PDF',
               'D [16/Nov/2008:10:48:36 -0500] [Job 14] Storing temporary files in /var/spool/cups/tmp',
               'D [16/Nov/2008:10:48:36 -0500] PID 7560 (/usr/lib/cups/filter/pstopdf) exited with no errors.',
               'D [16/Nov/2008:10:48:36 -0500] PID 7562 (/usr/lib/cups/filter/pdftopdf) exited with no errors.',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] File contains 1 pages',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Starting renderer with command: gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=stcolor -r360x360 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -dnoWeave -sDithering=gscmyk -sOutputCode=runlength -sOutputFile=-    /var/spool/cups/tmp/foomatic-daMrvx',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Starting process "kid3" (generation 1)',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Starting process "kid4" (generation 2)',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] JCL: <job data>',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14]',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Starting process "renderer" (generation 2)',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Read 8192 bytes of print data...',
               'I [16/Nov/2008:10:48:37 -0500] Saving subscriptions.conf...',
               'I [16/Nov/2008:10:48:37 -0500] Saving subscriptions.conf...',
               'I [16/Nov/2008:10:48:37 -0500] Saving subscriptions.conf...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [16/Nov/2008:10:48:37 -0500] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:10:48:37 -0500] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:10:48:37 -0500] Get-Jobs ipp://localhost/jobs/',
               'D [16/Nov/2008:10:48:37 -0500] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:10:48:37 -0500] cupsdAcceptClient: 13 from localhost (Domain)',
               'D [16/Nov/2008:10:48:37 -0500] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [16/Nov/2008:10:48:37 -0500] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:10:48:37 -0500] Get-Notifications /',
               'D [16/Nov/2008:10:48:37 -0500] cupsdIsAuthorized: requesting-user-name="steve"',
               'D [16/Nov/2008:10:48:37 -0500] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)',
               'D [16/Nov/2008:10:48:37 -0500] cupsdCloseClient: 7',
               'D [16/Nov/2008:10:48:37 -0500] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [16/Nov/2008:10:48:37 -0500] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:10:48:37 -0500] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:10:48:37 -0500] Get-Notifications /',
               'D [16/Nov/2008:10:48:37 -0500] cupsdIsAuthorized: requesting-user-name="steve"',
               'D [16/Nov/2008:10:48:37 -0500] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:10:48:37 -0500] cupsdReadClient: 9 POST / HTTP/1.1',
               'E [16/Nov/2008:10:48:37 -0500] cupsdAuthorize: Local authentication certificate not found!',
               'D [16/Nov/2008:10:48:37 -0500] CUPS-Get-Printers',
               'D [16/Nov/2008:10:48:37 -0500] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [16/Nov/2008:10:48:37 -0500] cupsdReadClient: 9 POST / HTTP/1.1',
               'E [16/Nov/2008:10:48:37 -0500] cupsdAuthorize: Local authentication certificate not found!',
               'D [16/Nov/2008:10:48:37 -0500] CUPS-Get-Classes',
               'D [16/Nov/2008:10:48:37 -0500] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [16/Nov/2008:10:48:37 -0500] cupsdReadClient: 9 POST / HTTP/1.1',
               'E [16/Nov/2008:10:48:37 -0500] cupsdAuthorize: Local authentication certificate not found!',
               'D [16/Nov/2008:10:48:37 -0500] CUPS-Get-Default',
               'D [16/Nov/2008:10:48:37 -0500] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [16/Nov/2008:10:48:37 -0500] cupsdCloseClient: 7',
               'D [16/Nov/2008:10:48:37 -0500] cupsdReadClient: 9 POST / HTTP/1.1',
               'E [16/Nov/2008:10:48:37 -0500] cupsdAuthorize: Local authentication certificate not found!',
               'D [16/Nov/2008:10:48:37 -0500] CUPS-Get-Printers',
               'D [16/Nov/2008:10:48:37 -0500] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [16/Nov/2008:10:48:37 -0500] cupsdReadClient: 9 POST / HTTP/1.1',
               'E [16/Nov/2008:10:48:37 -0500] cupsdAuthorize: Local authentication certificate not found!',
               'D [16/Nov/2008:10:48:37 -0500] CUPS-Get-Classes',
               'D [16/Nov/2008:10:48:37 -0500] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [16/Nov/2008:10:48:37 -0500] cupsdReadClient: 9 POST / HTTP/1.1',
               'E [16/Nov/2008:10:48:37 -0500] cupsdAuthorize: Local authentication certificate not found!',
               'D [16/Nov/2008:10:48:37 -0500] CUPS-Get-Default',
               'D [16/Nov/2008:10:48:37 -0500] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] cupsdReadClient: 9 POST / HTTP/1.1',
               'E [16/Nov/2008:10:48:37 -0500] cupsdAuthorize: Local authentication certificate not found!',
               'D [16/Nov/2008:10:48:37 -0500] CUPS-Get-Printers',
               'D [16/Nov/2008:10:48:37 -0500] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [16/Nov/2008:10:48:37 -0500] cupsdReadClient: 9 POST / HTTP/1.1',
               'E [16/Nov/2008:10:48:37 -0500] cupsdAuthorize: Local authentication certificate not found!',
               'D [16/Nov/2008:10:48:37 -0500] CUPS-Get-Classes',
               'D [16/Nov/2008:10:48:37 -0500] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [16/Nov/2008:10:48:37 -0500] cupsdReadClient: 9 POST / HTTP/1.1',
               'E [16/Nov/2008:10:48:37 -0500] cupsdAuthorize: Local authentication certificate not found!',
               'D [16/Nov/2008:10:48:37 -0500] CUPS-Get-Default',
               'D [16/Nov/2008:10:48:37 -0500] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] cupsdCloseClient: 13',
               'D [16/Nov/2008:10:48:37 -0500] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [16/Nov/2008:10:48:37 -0500] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:10:48:37 -0500] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:10:48:37 -0500] Get-Notifications /',
               'D [16/Nov/2008:10:48:37 -0500] cupsdIsAuthorized: requesting-user-name="steve"',
               'D [16/Nov/2008:10:48:37 -0500] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:10:48:37 -0500] cupsdCloseClient: 7',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] renderer exited with status 0',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:37 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:38 -0500] [Job 14] kid4 exited with status 0',
               'D [16/Nov/2008:10:48:38 -0500] [Job 14] kid3 finished',
               'D [16/Nov/2008:10:48:38 -0500] [Job 14] Kid3 exit status: 0',
               'D [16/Nov/2008:10:48:38 -0500] [Job 14]',
               'D [16/Nov/2008:10:48:38 -0500] [Job 14] Closing foomatic-rip.',
               'D [16/Nov/2008:10:48:38 -0500] PID 7564 (/usr/lib/cups/filter/foomatic-rip) exited with no errors.',
               'D [16/Nov/2008:10:48:38 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:38 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:38 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:38 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:38 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:38 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:38 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:38 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:38 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:38 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:38 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:38 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:38 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:38 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:38 -0500] [Job 14] Read 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:38 -0500] [Job 14] Wrote 8192 bytes of print data...',
               'D [16/Nov/2008:10:48:38 -0500] [Job 14] Read 5835 bytes of print data...',
               'D [16/Nov/2008:10:48:38 -0500] [Job 14] Wrote 5835 bytes of print data...',
               'D [16/Nov/2008:10:48:38 -0500] PID 7567 (/usr/lib/cups/backend/usb) exited with no errors.',
               'D [16/Nov/2008:10:48:38 -0500] [Job 14] File 0 is complete.',
               'I [16/Nov/2008:10:48:38 -0500] [Job 14] Completed successfully.',
               'I [16/Nov/2008:10:48:38 -0500] Saving subscriptions.conf...',
               'I [16/Nov/2008:10:48:38 -0500] Saving subscriptions.conf...',
               'D [16/Nov/2008:10:48:38 -0500] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [16/Nov/2008:10:48:38 -0500] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:10:48:38 -0500] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:10:48:38 -0500] Get-Jobs ipp://localhost/jobs/',
               'D [16/Nov/2008:10:48:38 -0500] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:10:48:38 -0500] cupsdAcceptClient: 13 from localhost (Domain)',
               'D [16/Nov/2008:10:48:38 -0500] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [16/Nov/2008:10:48:38 -0500] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:10:48:38 -0500] Get-Notifications /',
               'D [16/Nov/2008:10:48:38 -0500] cupsdIsAuthorized: requesting-user-name="steve"',
               'D [16/Nov/2008:10:48:38 -0500] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)',
               'D [16/Nov/2008:10:48:38 -0500] cupsdCloseClient: 7',
               'D [16/Nov/2008:10:48:38 -0500] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [16/Nov/2008:10:48:38 -0500] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:10:48:38 -0500] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:10:48:38 -0500] Get-Notifications /',
               'D [16/Nov/2008:10:48:38 -0500] cupsdIsAuthorized: requesting-user-name="steve"',
               'D [16/Nov/2008:10:48:38 -0500] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:10:48:38 -0500] cupsdCloseClient: 7',
               'D [16/Nov/2008:10:48:38 -0500] cupsdReadClient: 9 POST / HTTP/1.1',
               'E [16/Nov/2008:10:48:38 -0500] cupsdAuthorize: Local authentication certificate not found!',
               'D [16/Nov/2008:10:48:38 -0500] CUPS-Get-Printers',
               'D [16/Nov/2008:10:48:38 -0500] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [16/Nov/2008:10:48:38 -0500] cupsdReadClient: 9 POST / HTTP/1.1',
               'E [16/Nov/2008:10:48:38 -0500] cupsdAuthorize: Local authentication certificate not found!',
               'D [16/Nov/2008:10:48:38 -0500] CUPS-Get-Classes',
               'D [16/Nov/2008:10:48:38 -0500] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [16/Nov/2008:10:48:38 -0500] cupsdReadClient: 9 POST / HTTP/1.1',
               'E [16/Nov/2008:10:48:38 -0500] cupsdAuthorize: Local authentication certificate not found!',
               'D [16/Nov/2008:10:48:38 -0500] CUPS-Get-Default',
               'D [16/Nov/2008:10:48:38 -0500] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [16/Nov/2008:10:48:38 -0500] cupsdCloseClient: 13',
               'D [16/Nov/2008:10:48:38 -0500] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [16/Nov/2008:10:48:38 -0500] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:10:48:38 -0500] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:10:48:38 -0500] Get-Notifications /',
               'D [16/Nov/2008:10:48:38 -0500] cupsdIsAuthorized: requesting-user-name="steve"',
               'D [16/Nov/2008:10:48:38 -0500] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:10:48:38 -0500] cupsdCloseClient: 7',
               'D [16/Nov/2008:10:48:39 -0500] [Job 14] Unloading...',
               'D [16/Nov/2008:10:48:42 -0500] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [16/Nov/2008:10:48:42 -0500] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:10:48:42 -0500] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:10:48:42 -0500] Get-Notifications /',
               'D [16/Nov/2008:10:48:42 -0500] cupsdIsAuthorized: requesting-user-name="steve"',
               'D [16/Nov/2008:10:48:42 -0500] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:10:48:42 -0500] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:10:48:42 -0500] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:10:48:42 -0500] Get-Job-Attributes ipp://localhost/jobs/14',
               'D [16/Nov/2008:10:48:42 -0500] [Job 14] Loading attributes...',
               'D [16/Nov/2008:10:48:42 -0500] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:10:48:42 -0500] cupsdAcceptClient: 13 from localhost (Domain)',
               'D [16/Nov/2008:10:48:42 -0500] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [16/Nov/2008:10:48:42 -0500] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:10:48:42 -0500] Get-Printer-Attributes ipp://steve-desktop:631/printers/Stylus-CX4200',
               'D [16/Nov/2008:10:48:42 -0500] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)',
               'D [16/Nov/2008:10:48:42 -0500] cupsdCloseClient: 13',
               'D [16/Nov/2008:10:48:42 -0500] cupsdCloseClient: 7',
               'D [16/Nov/2008:10:48:45 -0500] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [16/Nov/2008:10:48:45 -0500] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:10:48:45 -0500] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:10:48:45 -0500] Get-Job-Attributes ipp://localhost/jobs/14',
               'D [16/Nov/2008:10:48:45 -0500] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:10:48:45 -0500] cupsdCloseClient: 7',
               'D [16/Nov/2008:10:48:45 -0500] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [16/Nov/2008:10:48:45 -0500] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [16/Nov/2008:10:48:45 -0500] cupsdAuthorize: No authentication data provided.',
               'D [16/Nov/2008:10:48:45 -0500] Cancel-Subscription /',
               'D [16/Nov/2008:10:48:45 -0500] cupsdIsAuthorized: requesting-user-name="steve"',
               'I [16/Nov/2008:10:48:45 -0500] Saving subscriptions.conf...',
               'D [16/Nov/2008:10:48:45 -0500] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [16/Nov/2008:10:48:45 -0500] cupsdCloseClient: 7',
               'D [16/Nov/2008:10:48:45 -0500] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [16/Nov/2008:10:48:45 -0500] cupsdReadClient: 7 GET /admin/log/error_log HTTP/1.1',
               'D [16/Nov/2008:10:48:45 -0500] cupsdAuthorize: No authentication data provided.'],
 'error_log_debug_logging_unset': True}

---

### Post by Merovius on 2008-11-16
Fixed it.

I was reading that someone had a problem printing to .pdf because cups-pdf was not installed by default. I decided to look and see if mine was. (no idea why, just did) While I was there I saw cups-driver-gutenprint. It was not installed so i installed it as well as cups-pdf.

Voila! I can now select the correct driver for my printer and it works as it should.

Man. That was a hassle...:shock:

Thanks again.

---

### Post by VictorR on 2008-11-18
For me the situation is as follows:
the printer worked fine in Ubuntu 8.04 and previous releases down to 7.04 (Brother MFC210C and PDFprinter);
after upgrade to Intrepid there is no Cups in the list of services,
the file /etc/init.d/cups is a broken link to non-existing /etc/init.d/cupsys,
all packages, related to cups, are correctly installed,
all logs in /var/log/cups are empty files.

Any ideas?

---

### Post by aggiemarine07 on 2008-11-20
I am having a similar issue with IPP printing (I posted over here: [http://ubuntuforums.org/showthread.php?t=967203&highlight=cups](http://ubuntuforums.org/showthread.php?t=967203&highlight=cups)) but no one wants to seem to look into it so I thought I would post in hopes that someone might actually see this problem. Thanks!

edit:
I found this in a bug report that at least solved some of the issue:
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/275407](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/275407)

using "chmod 0755 /usr/lib/cups/backend/*" seemed to allow me to see ipp in the gnome printer manager

---

### Post by aggiemarine07 on 2008-11-21
figure out my problem [here]("http://ubuntuforums.org/showthread.php?p=6223093#post6223093")

---

### Post by Zetheroo on 2008-11-21
I cannot even click on the button to add a new printer because its greyed out. :(

Not an issue with driver or anything like it .. just have a greyed out "NEW" button!

---

### Post by aggiemarine07 on 2008-11-22
Go to System->Administration->Printing

and then in the gnome-print-manager go to Server->Connect

try all of the following seperately to see which one works

/var/run/cups/cups.sock
localhost
127.0.0.1

After you enter one of the following select connect. See if that works.

---

### Post by Zetheroo on 2008-11-24
OK well here is what was happening and what I did to fix it ...

I had my printer (HP LaserJet 1010) working perfectly with the Foomatic driver in Hardy Heron. Then I upgraded to Intrepid Ibex (Fresh Install) and found that the printer had been automatically installed and was still using the Foomatic (recommended) driver. 

The odd thing was that I could print test pages from the properties window but I could not print from any program .... all I would get is a message saying "Printer HP LaserJet 1010 may not be connected".

After searching all over online for a solution ... and posting on this thread ... I went onto the Ubuntu IRC chat channel and enquired there. Someone was trying to help me and suggested I remove the installed printer and add a "New" printer. I had already removed the old printer profile and setup and had the greyed out "New" button I mentioned in my previous post. After restarting CUPS it was no longer greyed out.

So I added a new printer several times using the "recommended" Foomatic driver. Then this guy on the IRC chat suggested I try one of the other ones - there were 3 available drivers. So I tried the next one in line .... and voila - It worked fine!

Just thought I would share that with ppl here ... in case it helps. :)

---

### Post by omns on 2008-11-26
> **Merovius said:**
> In var/log/cups I found,

E [16/Nov/2008:08:49:07 -0500] "/etc/cups/ssl/server.crt" is a bad symlink - No such file or directory

This error is cause by the broken symilnks that exist within this directory. I deleted both the broken links in this directory and cups started without error.

Hope this helps someone :)

---

### Post by cccv on 2008-11-26
The following command restarted CUPS on my Intrepid Ibex installation:

sudo /etc/init.d/cupsys restart

---

### Post by cybrsaylr on 2008-11-26
> **Zetheroo said:**
>  Someone was trying to help me and suggested I remove the installed printer and add a "New" printer. I had already removed the old printer profile and setup and had the greyed out "New" button I mentioned in my previous post. After restarting CUPS it was no longer greyed out.
I'm having the same probblem. A HP Deskjet 5400 printer worked fine with Hardy but won't work with Ibex. 
I thought about uninstalling the printer.
How do you uninstall a printer? I looked around and can't find out how?

---

### Post by Zetheroo on 2008-11-27
Go to: System > Administration > Printing

then right-click on your printer and select "Delete".

If you want to add a printer simply click on the big "New" button to get you started.

---

### Post by timoschenko on 2008-11-27
Hi,

after installing Intrepid Ibex, my HP Deskjet 5440 no longer works. It is correctly recognized, but when I try to print a document, the printer spits out blank pages --endlessly. It does print a test page, though.
I tried the lastest driver from HP, to no avail. I deleted and reinstalled the printer, first using the HP utility, then via the browser (CUPS) and then using Systems>Administration>Printing. Finally, I did a complete --and useless-- reinstall.
Quite a few people have posted similar woes, with different printers. There was a cups update yesterday, but still I am not able to print. The problem is *not* solved.

---

### Post by Zetheroo on 2008-11-28
I saw that there is only a Foomatic driver available from within Ubuntu for your Deskjet 54xx printer. I had issues with the Foomatic driver with my HP Laserjet 1010 so I installed the other one ... but for your printer there are no other options ...  :(

---

### Post by amr2205 on 2008-11-28
> **GrantG said:**
> This error is cause by the broken symilnks that exist within this directory. I deleted both the broken links in this directory and cups started without error.

Hope this helps someone :)
Thanks! it worked for me too! ;)

---

### Post by warpasylum on 2009-06-05
Thanks omns. Deleted the 2 broken symlinks n' cups is happy now.

---

### Post by thradius on 2009-06-09
I'm having an odd problem. I'm connected to a HPLaserjet9040 on the network. I can print to it just fine. The problem is no matter what it prints 4 copies of everything. The OpenOffice app has one page in print settings the properties of the printer itself is set to 1 copy. It doesn't matter it prints 4 copies. I could work around it if it wouldn't also print 4 copies of each page at a time so if I print 30 page doc I get 4 pages of page 1 then 4 pages of page 2... and so on.

Thanks
Brent

---

