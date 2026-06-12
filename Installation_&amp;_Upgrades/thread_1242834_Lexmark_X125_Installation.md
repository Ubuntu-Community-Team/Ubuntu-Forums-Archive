---
title: "Lexmark X125 Installation"
date: 2009-08-17
forum: Installation &amp; Upgrades
---

### Post by hroos on 2009-08-17
I Used the installation for Lexmark X125 on Ubuntu Dapper written by tagra123.
Everything works well but at the moment I want to print a testpage I got the following message:
Whats to do to run X125 correctly? Thanks for any help in advance.
Regards hroos


Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest X125>,
 'cups_instance': None,
 'cups_queue': 'X125',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://Lexmark/X125',
                       'printer-info': u'Lexmark X125',
                       'printer-is-shared': True,
                       'printer-location': u'hubert-laptop',
                       'printer-make-and-model': u'Lexmark X125 Foomatic/drv_x125 (recommended)',
                       'printer-state': 3,
                       'printer-state-message': u'/usr/lib/cups/filter/foomatic-rip failed',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 4108,
                       'printer-uri-supported': u'ipp://localhost:631/printers/X125'},
 'cups_printer_remote': False,
 'is_cups_class': False}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'Bidirectional': u'Yes',
                                            u'ColorMode': u'CMYK',
                                            u'Device': u'usb_lp0',
                                            u'Mode': u'CMYK',
                                            u'PageRegion': u'A4',
                                            u'PageSize': u'A4',
                                            u'Resolution': u'600x600'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Choose device):
{'cups_device_dict': {'device-class': u'direct',
                      'device-id': 'MFG:Lexmark;CMD:LNPAP;MODEL:X125;CLASS:Printer;DES:Lexmark X125;7',
                      'device-info': u'Lexmark X125 USB #1',
                      'device-make-and-model': u'Lexmark X125'}}
Page 7 (Printer state reasons):
{'printer-state-message': u'/usr/lib/cups/filter/foomatic-rip failed',
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
 'error_log_checkpoint': 7668L,
 'error_log_debug_logging_set': True}
Page 9 (Print test page):
{'test_page_job_status': [(True,
                           8,
                           'X125',
                           'Test Page',
                           'Angehalten',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'de-de',
                            'document-format': u'application/postscript',
                            'job-hold-until': u'no-hold',
                            'job-id': 8,
                            'job-k-octets': 150,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/8',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'hubert',
                            'job-preserved': True,
                            'job-printer-state-message': u'/usr/lib/cups/filter/foomatic-rip failed',
                            'job-printer-state-reasons': [u'none'],
                            'job-printer-up-time': 1250532283,
                            'job-printer-uri': u'ipp://hubert-laptop:631/printers/X125',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 6,
                            'job-state-reasons': u'job-stopped',
                            'job-uri': u'ipp://localhost:631/jobs/8',
                            'job-uuid': u'urn:uuid:81219838-ec1a-377a-55a3-261f739acaa3',
                            'printer-uri': u'ipp://localhost/printers/X125',
                            'time-at-completed': None,
                            'time-at-creation': 1250452646,
                            'time-at-processing': 1250452646}),
                          (False,
                           10,
                           'X125',
                           'Test Page',
                           'Angehalten',
                           None)],
 'test_page_successful': True}
Page 10 (Error log fetch):
{'error_log': ['D [17/Aug/2009:20:04:24 +0200] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [17/Aug/2009:20:04:24 +0200] cupsdAuthorize: No authentication data provided.',
               'D [17/Aug/2009:20:04:24 +0200] Get-Jobs ipp://localhost/printers/',
               'D [17/Aug/2009:20:04:24 +0200] [Job 8] Loading attributes...',
               'D [17/Aug/2009:20:04:24 +0200] [Job 10] Loading attributes...',
               'D [17/Aug/2009:20:04:24 +0200] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [17/Aug/2009:20:04:24 +0200] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [17/Aug/2009:20:04:24 +0200] cupsdAuthorize: No authentication data provided.',
               'D [17/Aug/2009:20:04:24 +0200] Get-Jobs ipp://localhost/printers/',
               'D [17/Aug/2009:20:04:24 +0200] [Job 1] Loading attributes...',
               'D [17/Aug/2009:20:04:24 +0200] [Job 2] Loading attributes...',
               'D [17/Aug/2009:20:04:24 +0200] [Job 3] Loading attributes...',
               'D [17/Aug/2009:20:04:24 +0200] [Job 4] Loading attributes...',
               'D [17/Aug/2009:20:04:24 +0200] [Job 5] Loading attributes...',
               'D [17/Aug/2009:20:04:24 +0200] [Job 6] Loading attributes...',
               'D [17/Aug/2009:20:04:24 +0200] [Job 7] Loading attributes...',
               'D [17/Aug/2009:20:04:24 +0200] [Job 9] Loading attributes...',
               'D [17/Aug/2009:20:04:24 +0200] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [17/Aug/2009:20:04:24 +0200] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [17/Aug/2009:20:04:24 +0200] cupsdAuthorize: No authentication data provided.',
               'D [17/Aug/2009:20:04:24 +0200] Create-Printer-Subscription /',
               'D [17/Aug/2009:20:04:24 +0200] cupsdCreateSubscription(con=0xb8267f20(8), uri="/")',
               'D [17/Aug/2009:20:04:24 +0200] pullmethod="ippget"',
               'D [17/Aug/2009:20:04:24 +0200] notify-lease-duration=86400',
               'D [17/Aug/2009:20:04:24 +0200] notify-time-interval=0',
               'D [17/Aug/2009:20:04:24 +0200] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [17/Aug/2009:20:04:24 +0200] Added subscription 16 for server',
               'I [17/Aug/2009:20:04:24 +0200] Saving subscriptions.conf...',
               'D [17/Aug/2009:20:04:24 +0200] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [17/Aug/2009:20:04:25 +0200] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [17/Aug/2009:20:04:25 +0200] cupsdAuthorize: No authentication data provided.',
               'D [17/Aug/2009:20:04:25 +0200] Get-Notifications /',
               'D [17/Aug/2009:20:04:25 +0200] cupsdIsAuthorized: requesting-user-name="hubert"',
               'D [17/Aug/2009:20:04:25 +0200] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [17/Aug/2009:20:04:43 +0200] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [17/Aug/2009:20:04:43 +0200] cupsdAuthorize: No authentication data provided.',
               'D [17/Aug/2009:20:04:43 +0200] Get-Job-Attributes ipp://localhost/jobs/8',
               'D [17/Aug/2009:20:04:43 +0200] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [17/Aug/2009:20:04:43 +0200] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [17/Aug/2009:20:04:43 +0200] cupsdAuthorize: No authentication data provided.',
               'D [17/Aug/2009:20:04:43 +0200] Cancel-Subscription /',
               'D [17/Aug/2009:20:04:43 +0200] cupsdIsAuthorized: requesting-user-name="hubert"',
               'I [17/Aug/2009:20:04:43 +0200] Saving subscriptions.conf...',
               'D [17/Aug/2009:20:04:43 +0200] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [17/Aug/2009:20:04:43 +0200] cupsdAcceptClient: 9 from localhost (Domain)',
               'D [17/Aug/2009:20:04:43 +0200] cupsdReadClient: 9 GET /admin/log/error_log HTTP/1.1',
               'D [17/Aug/2009:20:04:43 +0200] cupsdAuthorize: No authentication data provided.'],
 'error_log_debug_logging_unset': True}
Page 11 (Locale issues):
{'printer_page_size': u'A4',
 'system_locale_lang': None,
 'user_locale_ctype': 'de_DE',
 'user_locale_messages': 'de_DE'}

---

### Post by hroos on 2009-08-30
I solved the problem with cups since Ubuntu 9.04 instead of cupsys.
But the printer doesn't print at all.
The new printer's state message is: '/usr/lib/cups/filter/foomatic-rip failed'.
Does someone know, how to eliminate this error?
Regards hroos



:(> **hroos said:**
> I Used the installation for Lexmark X125 on Ubuntu Dapper written by tagra123.
Everything works well but at the moment I want to print a testpage I got the following message:
Whats to do to run X125 correctly? Thanks for any help in advance.
Regards hroos


Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest X125>,
 'cups_instance': None,
 'cups_queue': 'X125',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://Lexmark/X125',
                       'printer-info': u'Lexmark X125',
                       'printer-is-shared': True,
                       'printer-location': u'hubert-laptop',
                       'printer-make-and-model': u'Lexmark X125 Foomatic/drv_x125 (recommended)',
                       'printer-state': 3,
                       'printer-state-message': u'/usr/lib/cups/filter/foomatic-rip failed',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 4108,
                       'printer-uri-supported': u'ipp://localhost:631/printers/X125'},
 'cups_printer_remote': False,
 'is_cups_class': False}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'Bidirectional': u'Yes',
                                            u'ColorMode': u'CMYK',
                                            u'Device': u'usb_lp0',
                                            u'Mode': u'CMYK',
                                            u'PageRegion': u'A4',
                                            u'PageSize': u'A4',
                                            u'Resolution': u'600x600'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Choose device):
{'cups_device_dict': {'device-class': u'direct',
                      'device-id': 'MFG:Lexmark;CMD:LNPAP;MODEL:X125;CLASS:Printer;DES:Lexmark X125;7',
                      'device-info': u'Lexmark X125 USB #1',
                      'device-make-and-model': u'Lexmark X125'}}
Page 7 (Printer state reasons):
{'printer-state-message': u'/usr/lib/cups/filter/foomatic-rip failed',
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
 'error_log_checkpoint': 7668L,
 'error_log_debug_logging_set': True}
Page 9 (Print test page):
{'test_page_job_status': [(True,
                           8,
                           'X125',
                           'Test Page',
                           'Angehalten',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'de-de',
                            'document-format': u'application/postscript',
                            'job-hold-until': u'no-hold',
                            'job-id': 8,
                            'job-k-octets': 150,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/8',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'hubert',
                            'job-preserved': True,
                            'job-printer-state-message': u'/usr/lib/cups/filter/foomatic-rip failed',
                            'job-printer-state-reasons': [u'none'],
                            'job-printer-up-time': 1250532283,
                            'job-printer-uri': u'ipp://hubert-laptop:631/printers/X125',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 6,
                            'job-state-reasons': u'job-stopped',
                            'job-uri': u'ipp://localhost:631/jobs/8',
                            'job-uuid': u'urn:uuid:81219838-ec1a-377a-55a3-261f739acaa3',
                            'printer-uri': u'ipp://localhost/printers/X125',
                            'time-at-completed': None,
                            'time-at-creation': 1250452646,
                            'time-at-processing': 1250452646}),
                          (False,
                           10,
                           'X125',
                           'Test Page',
                           'Angehalten',
                           None)],
 'test_page_successful': True}
Page 10 (Error log fetch):
{'error_log': ['D [17/Aug/2009:20:04:24 +0200] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [17/Aug/2009:20:04:24 +0200] cupsdAuthorize: No authentication data provided.',
               'D [17/Aug/2009:20:04:24 +0200] Get-Jobs ipp://localhost/printers/',
               'D [17/Aug/2009:20:04:24 +0200] [Job 8] Loading attributes...',
               'D [17/Aug/2009:20:04:24 +0200] [Job 10] Loading attributes...',
               'D [17/Aug/2009:20:04:24 +0200] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [17/Aug/2009:20:04:24 +0200] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [17/Aug/2009:20:04:24 +0200] cupsdAuthorize: No authentication data provided.',
               'D [17/Aug/2009:20:04:24 +0200] Get-Jobs ipp://localhost/printers/',
               'D [17/Aug/2009:20:04:24 +0200] [Job 1] Loading attributes...',
               'D [17/Aug/2009:20:04:24 +0200] [Job 2] Loading attributes...',
               'D [17/Aug/2009:20:04:24 +0200] [Job 3] Loading attributes...',
               'D [17/Aug/2009:20:04:24 +0200] [Job 4] Loading attributes...',
               'D [17/Aug/2009:20:04:24 +0200] [Job 5] Loading attributes...',
               'D [17/Aug/2009:20:04:24 +0200] [Job 6] Loading attributes...',
               'D [17/Aug/2009:20:04:24 +0200] [Job 7] Loading attributes...',
               'D [17/Aug/2009:20:04:24 +0200] [Job 9] Loading attributes...',
               'D [17/Aug/2009:20:04:24 +0200] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [17/Aug/2009:20:04:24 +0200] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [17/Aug/2009:20:04:24 +0200] cupsdAuthorize: No authentication data provided.',
               'D [17/Aug/2009:20:04:24 +0200] Create-Printer-Subscription /',
               'D [17/Aug/2009:20:04:24 +0200] cupsdCreateSubscription(con=0xb8267f20(8), uri="/")',
               'D [17/Aug/2009:20:04:24 +0200] pullmethod="ippget"',
               'D [17/Aug/2009:20:04:24 +0200] notify-lease-duration=86400',
               'D [17/Aug/2009:20:04:24 +0200] notify-time-interval=0',
               'D [17/Aug/2009:20:04:24 +0200] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [17/Aug/2009:20:04:24 +0200] Added subscription 16 for server',
               'I [17/Aug/2009:20:04:24 +0200] Saving subscriptions.conf...',
               'D [17/Aug/2009:20:04:24 +0200] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [17/Aug/2009:20:04:25 +0200] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [17/Aug/2009:20:04:25 +0200] cupsdAuthorize: No authentication data provided.',
               'D [17/Aug/2009:20:04:25 +0200] Get-Notifications /',
               'D [17/Aug/2009:20:04:25 +0200] cupsdIsAuthorized: requesting-user-name="hubert"',
               'D [17/Aug/2009:20:04:25 +0200] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [17/Aug/2009:20:04:43 +0200] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [17/Aug/2009:20:04:43 +0200] cupsdAuthorize: No authentication data provided.',
               'D [17/Aug/2009:20:04:43 +0200] Get-Job-Attributes ipp://localhost/jobs/8',
               'D [17/Aug/2009:20:04:43 +0200] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [17/Aug/2009:20:04:43 +0200] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [17/Aug/2009:20:04:43 +0200] cupsdAuthorize: No authentication data provided.',
               'D [17/Aug/2009:20:04:43 +0200] Cancel-Subscription /',
               'D [17/Aug/2009:20:04:43 +0200] cupsdIsAuthorized: requesting-user-name="hubert"',
               'I [17/Aug/2009:20:04:43 +0200] Saving subscriptions.conf...',
               'D [17/Aug/2009:20:04:43 +0200] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [17/Aug/2009:20:04:43 +0200] cupsdAcceptClient: 9 from localhost (Domain)',
               'D [17/Aug/2009:20:04:43 +0200] cupsdReadClient: 9 GET /admin/log/error_log HTTP/1.1',
               'D [17/Aug/2009:20:04:43 +0200] cupsdAuthorize: No authentication data provided.'],
 'error_log_debug_logging_unset': True}
Page 11 (Locale issues):
{'printer_page_size': u'A4',
 'system_locale_lang': None,
 'user_locale_ctype': 'de_DE',
 'user_locale_messages': 'de_DE'}

---

