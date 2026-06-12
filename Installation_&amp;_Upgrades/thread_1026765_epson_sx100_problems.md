---
title: "epson sx100 problems"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by chrismarsh1987 on 2008-12-31
running ubuntu 8.10 on a ibm thinkpad t23 with enhanced internet connectivity and ram modules.

brought a epson stylus sx100 all in one printer, followed various options on geting the blasted thing to work. its apparently installed and when i send a document to print it fails reading cannot write page 1 image and running through the trouble shooting it cannot diagnose but kicks out the following information. if anyone has any ideas i am open, but still relatively new so please, any instructions be precise and step by step, thanks, this is the information it gives from the bugging modes

Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest snx100 (default)>,
'cups_instance': None,
'cups_queue': 'snx100',
'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'ekplp',
'cups_printer_dict': {'device-uri': u'ekplp:/var/ekpd/ekplp0',
'printer-info': u'snx100',
'printer-is-shared': True,
'printer-location': u'',
'printer-make-and-model': u'Epson Stylus NX100, Photo Image Print System',
'printer-state': 3,
'printer-state-message': u"Can't write page 1 image",
'printer-state-reasons': [u'none'],
'printer-type': 135180,
'printer-uri-supported': u'ipp://localhost:631/printers/snx100'},
'cups_printer_remote': False,
'is_cups_class': False}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'Ink': u'COLOR',
u'PageRegion': u'A4_AUTO',
u'PageSize': u'A4_AUTO',
u'Quality': u'PLAIN_S'}},
'cups_printer_ppd_valid': True,
'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Choose device):
{'cups_device_dict': {'device-class': u'direct',
'device-id': u'',
'device-info': u'Epson Inkjet Printer #1',
'device-make-and-model': u'Photo Image Print System'}}
Page 7 (Printer state reasons):
{'printer-state-message': u"Can't write page 1 image",
'printer-state-reasons': [u'none']}
Page 8 (Error log checkpoint):
{'cups_server_settings': {'DefaultAuthType': 'Basic',
'MaxLogSize': '2000000',
'SystemGroup': 'lpadmin',
'_debug_logging': '0',
'_remote_admin': '0',
'_remote_any': '0',
'_remote_printers': '0',
'_share_printers': '0',
'_user_cancel_any': '0'},
'error_log_checkpoint': 30652L,
'error_log_debug_logging_set': True}
Page 9 (Print test page):
{'test_page_job_status': [(True,
9,
'snx100',
'life kist open air logo.jpg',
'Stopped',
{'Ink': u'COLOR',
'PageSize': u'A4',
'Quality': u'PLAIN_S',
'attributes-charset': u'utf-8',
'attributes-natural-language': u'en-gb',
'document-format': u'application/pdf',
'job-hold-until': u'no-hold',
'job-id': 9,
'job-k-octets': 89,
'job-media-sheets-completed': 0,
'job-more-info': u'ipp://localhost:631/jobs/9',
'job-name': u'life kist open air logo.jpg',
'job-originating-host-name': u'localhost',
'job-originating-user-name': u'chris',
'job-preserved': True,
'job-printer-state-message': u"Can't write page 1 image",
'job-printer-state-reasons': [u'none'],
'job-printer-up-time': 1230751640,
'job-printer-uri': u'ipp://nautilus:631/printers/snx100',
'job-priority': 100,
'job-sheets': [u'none', u'none'],
'job-state': 6,
'job-state-reasons': u'job-stopped',
'job-uri': u'ipp://localhost:631/jobs/9',
'job-uuid': u'urn:uuid:2d244fbf-35d5-3982-4e6a-aa6fcb8c29f6',
'number-up': 1,
'printer-uri': u'ipp://localhost:631/printers/snx100',
'time-at-completed': None,
'time-at-creation': 1230751097,
'time-at-processing': 1230751097})],
'test_page_successful': False}
Page 10 (Error log fetch):
{'error_log': ['D [31/Dec/2008:19:26:11 +0000] cupsdCloseClient: 7',
'D [31/Dec/2008:19:26:11 +0000] cupsdAcceptClient: 7 from localhost (Domain)',
'D [31/Dec/2008:19:26:11 +0000] cupsdReadClient: 7 POST / HTTP/1.1',
'D [31/Dec/2008:19:26:11 +0000] cupsdAuthorize: No authentication data provided.',
'D [31/Dec/2008:19:26:11 +0000] Get-Jobs ipp://localhost/jobs/',
'D [31/Dec/2008:19:26:11 +0000] [Job 9] Loading attributes...',
'D [31/Dec/2008:19:26:11 +0000] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
'D [31/Dec/2008:19:26:11 +0000] cupsdCloseClient: 7',
'D [31/Dec/2008:19:26:11 +0000] cupsdAcceptClient: 7 from localhost (Domain)',
'D [31/Dec/2008:19:26:11 +0000] cupsdReadClient: 7 POST / HTTP/1.1',
'D [31/Dec/2008:19:26:11 +0000] cupsdAuthorize: No authentication data provided.',
'D [31/Dec/2008:19:26:11 +0000] Create-Printer-Subscription /',
'D [31/Dec/2008:19:26:11 +0000] cupsdCreateSubscription(con=0xb84e6088(7), uri="/")',
'D [31/Dec/2008:19:26:11 +0000] pullmethod="ippget"',
'D [31/Dec/2008:19:26:11 +0000] notify-lease-duration=86400',
'D [31/Dec/2008:19:26:11 +0000] notify-time-interval=0',
'D [31/Dec/2008:19:26:11 +0000] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
'D [31/Dec/2008:19:26:11 +0000] Added subscription 16 for server',
'I [31/Dec/2008:19:26:11 +0000] Saving subscriptions.conf...',
'D [31/Dec/2008:19:26:11 +0000] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
'D [31/Dec/2008:19:26:11 +0000] cupsdCloseClient: 7',
'D [31/Dec/2008:19:26:12 +0000] cupsdAcceptClient: 7 from localhost (Domain)',
'D [31/Dec/2008:19:26:12 +0000] cupsdReadClient: 7 POST / HTTP/1.1',
'D [31/Dec/2008:19:26:12 +0000] cupsdAuthorize: No authentication data provided.',
'D [31/Dec/2008:19:26:12 +0000] Get-Notifications /',
'D [31/Dec/2008:19:26:12 +0000] cupsdIsAuthorized: requesting-user-name="chris"',
'D [31/Dec/2008:19:26:12 +0000] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
'D [31/Dec/2008:19:26:12 +0000] cupsdCloseClient: 7',
'D [31/Dec/2008:19:27:12 +0000] cupsdAcceptClient: 7 from localhost (Domain)',
'D [31/Dec/2008:19:27:12 +0000] [Job 9] Unloading...',
'D [31/Dec/2008:19:27:12 +0000] Report: clients=1',
'D [31/Dec/2008:19:27:12 +0000] Report: jobs=6',
'D [31/Dec/2008:19:27:12 +0000] Report: jobs-active=1',
'D [31/Dec/2008:19:27:12 +0000] Report: printers=2',
'D [31/Dec/2008:19:27:12 +0000] Report: printers-implicit=0',
'D [31/Dec/2008:19:27:12 +0000] Report: stringpool-string-count=2602',
'D [31/Dec/2008:19:27:12 +0000] Report: stringpool-alloc-bytes=10344',
'D [31/Dec/2008:19:27:12 +0000] Report: stringpool-total-bytes=55928',
'D [31/Dec/2008:19:27:12 +0000] cupsdReadClient: 7 POST / HTTP/1.1',
'D [31/Dec/2008:19:27:12 +0000] cupsdAuthorize: No authentication data provided.',
'D [31/Dec/2008:19:27:12 +0000] Get-Notifications /',
'D [31/Dec/2008:19:27:12 +0000] cupsdIsAuthorized: requesting-user-name="chris"',
'D [31/Dec/2008:19:27:12 +0000] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
'D [31/Dec/2008:19:27:12 +0000] cupsdCloseClient: 7',
'D [31/Dec/2008:19:27:20 +0000] cupsdAcceptClient: 7 from localhost (Domain)',
'D [31/Dec/2008:19:27:20 +0000] cupsdReadClient: 7 POST / HTTP/1.1',
'D [31/Dec/2008:19:27:20 +0000] cupsdAuthorize: No authentication data provided.',
'D [31/Dec/2008:19:27:20 +0000] Get-Job-Attributes ipp://localhost/jobs/9',
'D [31/Dec/2008:19:27:20 +0000] [Job 9] Loading attributes...',
'D [31/Dec/2008:19:27:20 +0000] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
'D [31/Dec/2008:19:27:20 +0000] cupsdCloseClient: 7',
'D [31/Dec/2008:19:27:20 +0000] cupsdAcceptClient: 7 from localhost (Domain)',
'D [31/Dec/2008:19:27:20 +0000] cupsdReadClient: 7 POST / HTTP/1.1',
'D [31/Dec/2008:19:27:20 +0000] cupsdAuthorize: No authentication data provided.',
'D [31/Dec/2008:19:27:20 +0000] Cancel-Subscription /',
'D [31/Dec/2008:19:27:20 +0000] cupsdIsAuthorized: requesting-user-name="chris"',
'I [31/Dec/2008:19:27:20 +0000] Saving subscriptions.conf...',
'D [31/Dec/2008:19:27:20 +0000] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
'D [31/Dec/2008:19:27:20 +0000] cupsdCloseClient: 7',
'D [31/Dec/2008:19:27:20 +0000] cupsdAcceptClient: 7 from localhost (Domain)',
'D [31/Dec/2008:19:27:20 +0000] cupsdReadClient: 7 GET /admin/log/error_log HTTP/1.1',
'D [31/Dec/2008:19:27:20 +0000] cupsdAuthorize: No authentication data provided.'],
'error_log_debug_logging_unset': True}

---

### Post by wirah on 2009-02-08
Try the drivers here:

[http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)

---

### Post by herr doktor on 2009-04-06
I've tried the  drivers at avasys.jp, but I couldn't  make the printer work.

The problem was very similar to chrismarsh1987's situation.

I've resolved the problem updating gutenprint to 5.5.2 (ubuntu repositories are updatet to 5.2.0)

I've found a deb package at: [http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_SX100](http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_SX100)

then I've (uninstalled and) reinstalled the driver and all went well

(please: uninstalling the driver you have to delete manually the icon in the system-->administration-->printers panel

good luck

---

