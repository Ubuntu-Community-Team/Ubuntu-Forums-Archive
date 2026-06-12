---
title: "help installing lexmark 5300 printer"
date: 2009-02-05
forum: Hardware
---

### Post by slavix on 2009-02-05
Hello,
I tried installing Lexmark 5300 usb printer on ubuntu 8.10 and can't print a test page.
here are results from diagnostics utility. thank you for help.

```
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest -5300-Series (default)>,
 'cups_instance': None,
 'cups_queue': '-5300-Series',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://Lexmark/5300%20Series',
                       'printer-info': u'Lexmark 5300',
                       'printer-is-shared': True,
                       'printer-location': u'ilya-desktop',
                       'printer-make-and-model': u'Lexmark 5000 Foomatic/lx5000 (recommended)',
                       'printer-state': 3,
                       'printer-state-message': u'/usr/lib/cups/filter/foomatic-rip failed',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 135180,
                       'printer-uri-supported': u'ipp://localhost:631/printers/-5300-Series'},
 'cups_printer_remote': False,
 'is_cups_class': False}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'Adjustment': {u'AlignA': u'16',
                                               u'AlignB': u'8',
                                               u'DryingTime': u'30s',
                                               u'HeadSeparation': u'16'},
                               u'General': {u'ColorMode': u'Colour',
                                            u'PageRegion': u'A4',
                                            u'PageSize': u'A4',
                                            u'Resolution': u'600x600dpi'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Choose device):
{'cups_device_dict': {'device-class': u'direct',
                      'device-id': u'MFG:Lexmark;CMD:CPDNPA004;MODEL: 5300 Series;CLASS:Printer;DES:Lexmark 5300 Series;\x7f',
                      'device-info': u'Lexmark 5300 Series USB #1',
                      'device-make-and-model': u'Lexmark 5300 Series'}}
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
 'error_log_checkpoint': 99704}
Page 9 (Print test page):
{'test_page_job_status': [(True,
                           13,
                           '-5300-Series',
                           'Test Page',
                           '\xd0\x9e\xd1\x81\xd1\x82\xd0\xb0\xd0\xbd\xd0\xbe\xd0\xb2\xd0\xbb\xd0\xb5\xd0\xbd\xd0\xbe',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'ru-ru',
                            'document-format': u'application/postscript',
                            'job-hold-until': u'no-hold',
                            'job-id': 13,
                            'job-k-octets': 150,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/13',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'ilya',
                            'job-preserved': True,
                            'job-printer-state-message': u'/usr/lib/cups/filter/foomatic-rip failed',
                            'job-printer-state-reasons': [u'none'],
                            'job-printer-up-time': 1233876518,
                            'job-printer-uri': u'ipp://ilya-desktop:631/printers/-5300-Series',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 6,
                            'job-state-reasons': u'job-stopped',
                            'job-uri': u'ipp://localhost:631/jobs/13',
                            'job-uuid': u'urn:uuid:f8d54afe-ce53-3895-64f7-33b88b62b028',
                            'printer-uri': u'ipp://localhost/printers/-5300-Series',
                            'time-at-completed': None,
                            'time-at-creation': 1233876410,
                            'time-at-processing': 1233876410})],
 'test_page_successful': False}
Page 10 (Error log fetch):
{'error_log': ['D [06/Feb/2009:02:28:25 +0300] cupsdCloseClient: 13',
               'D [06/Feb/2009:02:28:25 +0300] cupsdAcceptClient: 13 from localhost (Domain)',
               'D [06/Feb/2009:02:28:25 +0300] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [06/Feb/2009:02:28:25 +0300] cupsdAuthorize: No authentication data provided.',
               'D [06/Feb/2009:02:28:25 +0300] Get-Jobs ipp://localhost/jobs/',
               'D [06/Feb/2009:02:28:25 +0300] [Job 13] Loading attributes...',
               'D [06/Feb/2009:02:28:25 +0300] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)',
               'D [06/Feb/2009:02:28:25 +0300] cupsdCloseClient: 13',
               'D [06/Feb/2009:02:28:25 +0300] cupsdAcceptClient: 13 from localhost (Domain)',
               'D [06/Feb/2009:02:28:25 +0300] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [06/Feb/2009:02:28:25 +0300] cupsdAuthorize: No authentication data provided.',
               'D [06/Feb/2009:02:28:25 +0300] Create-Printer-Subscription /',
               'D [06/Feb/2009:02:28:25 +0300] cupsdCreateSubscription(con=0x7f5a2093f9c0(13), uri="/")',
               'D [06/Feb/2009:02:28:25 +0300] pullmethod="ippget"',
               'D [06/Feb/2009:02:28:25 +0300] notify-lease-duration=86400',
               'D [06/Feb/2009:02:28:25 +0300] notify-time-interval=0',
               'D [06/Feb/2009:02:28:25 +0300] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [06/Feb/2009:02:28:25 +0300] Added subscription 35 for server',
               'I [06/Feb/2009:02:28:25 +0300] Saving subscriptions.conf...',
               'D [06/Feb/2009:02:28:25 +0300] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)',
               'D [06/Feb/2009:02:28:25 +0300] cupsdCloseClient: 13',
               'D [06/Feb/2009:02:28:26 +0300] cupsdAcceptClient: 13 from localhost (Domain)',
               'D [06/Feb/2009:02:28:26 +0300] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [06/Feb/2009:02:28:26 +0300] cupsdAuthorize: No authentication data provided.',
               'D [06/Feb/2009:02:28:26 +0300] Get-Notifications /',
               'D [06/Feb/2009:02:28:26 +0300] cupsdIsAuthorized: requesting-user-name="ilya"',
               'D [06/Feb/2009:02:28:26 +0300] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)',
               'D [06/Feb/2009:02:28:26 +0300] cupsdCloseClient: 13',
               'D [06/Feb/2009:02:28:38 +0300] cupsdAcceptClient: 13 from localhost (Domain)',
               'D [06/Feb/2009:02:28:38 +0300] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [06/Feb/2009:02:28:38 +0300] cupsdAuthorize: No authentication data provided.',
               'D [06/Feb/2009:02:28:38 +0300] Get-Job-Attributes ipp://localhost/jobs/13',
               'D [06/Feb/2009:02:28:38 +0300] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)',
               'D [06/Feb/2009:02:28:38 +0300] cupsdCloseClient: 13',
               'D [06/Feb/2009:02:28:38 +0300] cupsdAcceptClient: 13 from localhost (Domain)',
               'D [06/Feb/2009:02:28:38 +0300] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [06/Feb/2009:02:28:38 +0300] cupsdAuthorize: No authentication data provided.',
               'D [06/Feb/2009:02:28:38 +0300] Cancel-Subscription /',
               'D [06/Feb/2009:02:28:38 +0300] cupsdIsAuthorized: requesting-user-name="ilya"',
               'I [06/Feb/2009:02:28:38 +0300] Saving subscriptions.conf...',
               'D [06/Feb/2009:02:28:38 +0300] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)',
               'D [06/Feb/2009:02:28:38 +0300] cupsdCloseClient: 13',
               'D [06/Feb/2009:02:28:38 +0300] cupsdAcceptClient: 13 from localhost (Domain)',
               'D [06/Feb/2009:02:28:38 +0300] cupsdCloseClient: 7',
               'D [06/Feb/2009:02:28:38 +0300] cupsdReadClient: 13 GET /admin/log/error_log HTTP/1.1',
               'D [06/Feb/2009:02:28:38 +0300] cupsdAuthorize: No authentication data provided.']}
```

---

### Post by Bablefish on 2009-02-05
I have been through this with the exact same printer. What I found is you are going to have to buy a HP printer, as I could never find a working Lexmark driver....period.

---

### Post by slavix on 2009-02-05
Thanks, 
What is a good cheap printer that would be good for Ubuntu?

---

