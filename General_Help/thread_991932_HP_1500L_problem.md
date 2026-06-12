---
title: "HP 1500L problem"
date: 2008-11-24
forum: General Help
---

### Post by art_s on 2008-11-24
Hi all,

I've set up drivers for HP 1500L as described here ([http://foo2oak.rkkda.com/INSTALL](http://foo2oak.rkkda.com/INSTALL)), but I still cannot print anything but test page. 

That's the error I'm getting.

> Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest LaserJet (default)>,
 'cups_instance': None,
 'cups_queue': 'LaserJet',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://HP/color%20LaserJet%201500',
                       'printer-info': u'',
                       'printer-is-shared': True,
                       'printer-location': u'here',
                       'printer-make-and-model': u'HP Color LaserJet 1500 Foomatic/foo2oak (recommended)',
                       'printer-state': 3,
                       'printer-state-message': u'/usr/lib/cups/filter/foomatic-rip failed',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 167948,
                       'printer-uri-supported': u'ipp://localhost:631/printers/LaserJet'},
 'cups_printer_remote': False,
 'is_cups_class': False}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'Adjustment': {u'ICM': u'default'},
                               u'General': {u'BitsPerPlane': u'1-BPP',
                                            u'ColorMode': u'Color',
                                            u'Copies': u'1',
                                            u'InputSlot': u'Auto',
                                            u'MediaType': u'Auto',
                                            u'PageRegion': u'A4',
                                            u'PageSize': u'A4'},
                               u'Miscellaneous': {u'Nup': u'1up',
                                                  u'NupOrient': u'port'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Choose device):
{'cups_device_dict': {'device-class': u'direct',
                      'device-id': u'MFG:Hewlett-Packard;CMD:OAKRAS,DW-PCL;MDL:hp color LaserJet 1500;CLS:PRINTER;DES:Hewlett-Packard color LaserJet 1500;MEM:16MB;1284.4DL:4d,4e,1;MSZ:10000000;FDT:0;CAL:0405040F20384E8D05061522304D6FA2060A12202A465D9303030D111B304F94;',
                      'device-info': u'hp color LaserJet 1500 USB #1',
                      'device-make-and-model': u'hp color LaserJet 1500'}}
Page 7 (Printer state reasons):
{'printer-state-message': u'/usr/lib/cups/filter/foomatic-rip failed',
 'printer-state-reasons': [u'none']}
Page 8 (Error log checkpoint):
{'cups_server_settings': {'DefaultAuthType': 'Basic',
                          'MaxLogSize': '0',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '1',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '0',
                          '_share_printers': '0',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 3140427}
Page 9 (Print test page):
{'test_page_job_status': [(False,
                           7,
                           'LaserJet',
                           'Untitled.jpg',
                           'Stopped',
                           None)],
 'test_page_successful': False}
Page 10 (Error log fetch):
{'error_log': ['D [25/Nov/2008:01:13:40 +1100] cupsdCloseClient: 14',
               'D [25/Nov/2008:01:13:40 +1100] cupsdAcceptClient: 14 from localhost (Domain)',
               'D [25/Nov/2008:01:13:40 +1100] cupsdReadClient: 14 POST / HTTP/1.1',
               'D [25/Nov/2008:01:13:40 +1100] cupsdAuthorize: No authentication data provided.',
               'D [25/Nov/2008:01:13:40 +1100] Get-Jobs ipp://localhost/jobs/',
               'D [25/Nov/2008:01:13:40 +1100] [Job 7] Loading attributes...',
               'D [25/Nov/2008:01:13:40 +1100] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)',
               'D [25/Nov/2008:01:13:40 +1100] cupsdCloseClient: 14',
               'D [25/Nov/2008:01:13:40 +1100] cupsdAcceptClient: 14 from localhost (Domain)',
               'D [25/Nov/2008:01:13:40 +1100] cupsdReadClient: 14 POST / HTTP/1.1',
               'D [25/Nov/2008:01:13:40 +1100] cupsdAuthorize: No authentication data provided.',
               'D [25/Nov/2008:01:13:40 +1100] Create-Printer-Subscription /',
               'D [25/Nov/2008:01:13:40 +1100] cupsdCreateSubscription(con=0x2b3b4b320540(14), uri="/")',
               'D [25/Nov/2008:01:13:40 +1100] pullmethod="ippget"',
               'D [25/Nov/2008:01:13:40 +1100] notify-lease-duration=86400',
               'D [25/Nov/2008:01:13:40 +1100] notify-time-interval=0',
               'D [25/Nov/2008:01:13:40 +1100] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [25/Nov/2008:01:13:40 +1100] Added subscription 20 for server',
               'I [25/Nov/2008:01:13:40 +1100] Saving subscriptions.conf...',
               'D [25/Nov/2008:01:13:40 +1100] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)',
               'D [25/Nov/2008:01:13:40 +1100] cupsdCloseClient: 14',
               'D [25/Nov/2008:01:13:41 +1100] cupsdAcceptClient: 14 from localhost (Domain)',
               'D [25/Nov/2008:01:13:41 +1100] cupsdReadClient: 14 POST / HTTP/1.1',
               'D [25/Nov/2008:01:13:41 +1100] cupsdAuthorize: No authentication data provided.',
               'D [25/Nov/2008:01:13:41 +1100] Get-Notifications /',
               'D [25/Nov/2008:01:13:41 +1100] cupsdIsAuthorized: requesting-user-name="user"',
               'D [25/Nov/2008:01:13:41 +1100] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)',
               'D [25/Nov/2008:01:13:41 +1100] cupsdCloseClient: 14',
               'D [25/Nov/2008:01:13:46 +1100] cupsdAcceptClient: 14 from localhost (Domain)',
               'D [25/Nov/2008:01:13:46 +1100] cupsdCloseClient: 14',
               'D [25/Nov/2008:01:13:46 +1100] cupsdAcceptClient: 14 from localhost (Domain)',
               'D [25/Nov/2008:01:13:46 +1100] cupsdReadClient: 14 POST / HTTP/1.1',
               'D [25/Nov/2008:01:13:46 +1100] cupsdAuthorize: No authentication data provided.',
               'D [25/Nov/2008:01:13:46 +1100] Cancel-Subscription /',
               'D [25/Nov/2008:01:13:46 +1100] cupsdIsAuthorized: requesting-user-name="user"',
               'I [25/Nov/2008:01:13:46 +1100] Saving subscriptions.conf...',
               'D [25/Nov/2008:01:13:46 +1100] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)',
               'D [25/Nov/2008:01:13:46 +1100] cupsdCloseClient: 14',
               'D [25/Nov/2008:01:13:46 +1100] cupsdAcceptClient: 14 from localhost (Domain)',
               'D [25/Nov/2008:01:13:46 +1100] cupsdCloseClient: 13',
               'D [25/Nov/2008:01:13:46 +1100] cupsdReadClient: 14 GET /admin/log/error_log HTTP/1.1',
               'D [25/Nov/2008:01:13:46 +1100] cupsdAuthorize: No authentication data provided.']}


Is it possible to fix that somehow?

Thanks

---

### Post by art_s on 2008-12-05
bump

---

