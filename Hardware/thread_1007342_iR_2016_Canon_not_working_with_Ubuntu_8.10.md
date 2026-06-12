---
title: "iR 2016 Canon not working with Ubuntu 8.10"
date: 2008-12-10
forum: Hardware
---

### Post by vetrivelsn on 2008-12-10
This is the message i got when i used Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest iR2016 (default)>,
 'cups_instance': None,
 'cups_queue': 'iR2016',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://Canon/iR2016',
                       'printer-info': u'',
                       'printer-is-shared': False,
                       'printer-location': u'murale-desktop',
                       'printer-make-and-model': u'Canon iR2016-2020 PXL',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 2240532,
                       'printer-uri-supported': u'ipp://localhost:631/printers/iR2016'},
 'cups_printer_remote': False,
 'is_cups_class': False}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'CanonDeviceSpec': {u'UserID': u'None',
                                                    u'UserPassword': u'None'},
                               u'Features': {u'CNCollate': u'False',
                                             u'CNEconomode': u'False',
                                             u'CNImageRefinement': u'True',
                                             u'CNOutput': u'Auto',
                                             u'Duplex': u'None',
                                             u'InputSlot': u'Tray1',
                                             u'MediaType': u'AUTO',
                                             u'Staple': u'None',
                                             u'WideMedia': u'Default'},
                               u'General': {u'PageRegion': u'A4',
                                            u'PageSize': u'A4'},
                               u'InstallableOptions': {u'Option1': u'None',
                                                       u'Option2': u'None'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Choose device):
{'cups_device_dict': {'device-class': u'direct',
                      'device-id': u'MFG:Canon;MDL:iR2016;CMD:LIPSLX,CPCA;CLS:PRINTER;DES:Canon iR2016;',
                      'device-info': u'Canon iR2016 USB #1',
                      'device-make-and-model': u'Canon iR2016'}}
Page 7 (Error log checkpoint):
{'cups_server_settings': {'DefaultAuthType': 'Basic',
                          'MaxLogSize': '0',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '1',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '0',
                          '_share_printers': '0',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 4671775L}
Page 8 (Print test page):
{'test_page_job_status': [], 'test_page_successful': True}
Page 9 (Error log fetch):
{'error_log': ['D [10/Dec/2008:20:57:59 +0530] cupsdCloseClient: 13',
               'D [10/Dec/2008:20:57:59 +0530] cupsdAcceptClient: 13 from localhost (Domain)',
               'D [10/Dec/2008:20:57:59 +0530] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [10/Dec/2008:20:57:59 +0530] cupsdAuthorize: No authentication data provided.',
               'D [10/Dec/2008:20:57:59 +0530] Get-Jobs ipp://localhost/jobs/',
               'D [10/Dec/2008:20:57:59 +0530] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)',
               'D [10/Dec/2008:20:57:59 +0530] cupsdCloseClient: 13',
               'D [10/Dec/2008:20:57:59 +0530] cupsdAcceptClient: 13 from localhost (Domain)',
               'D [10/Dec/2008:20:57:59 +0530] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [10/Dec/2008:20:57:59 +0530] cupsdAuthorize: No authentication data provided.',
               'D [10/Dec/2008:20:57:59 +0530] Create-Printer-Subscription /',
               'D [10/Dec/2008:20:57:59 +0530] cupsdCreateSubscription(con=0xb83f9e80(13), uri="/")',
               'D [10/Dec/2008:20:57:59 +0530] pullmethod="ippget"',
               'D [10/Dec/2008:20:57:59 +0530] notify-lease-duration=86400',
               'D [10/Dec/2008:20:57:59 +0530] notify-time-interval=0',
               'D [10/Dec/2008:20:57:59 +0530] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [10/Dec/2008:20:57:59 +0530] Added subscription 31 for server',
               'I [10/Dec/2008:20:57:59 +0530] Saving subscriptions.conf...',
               'D [10/Dec/2008:20:57:59 +0530] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)',
               'D [10/Dec/2008:20:57:59 +0530] cupsdCloseClient: 13',
               'D [10/Dec/2008:20:57:59 +0530] cupsdAcceptClient: 13 from localhost (Domain)',
               'D [10/Dec/2008:20:57:59 +0530] cupsdCloseClient: 13',
               'D [10/Dec/2008:20:57:59 +0530] cupsdAcceptClient: 13 from localhost (Domain)',
               'D [10/Dec/2008:20:57:59 +0530] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [10/Dec/2008:20:57:59 +0530] cupsdAuthorize: No authentication data provided.',
               'D [10/Dec/2008:20:57:59 +0530] Cancel-Subscription /',
               'D [10/Dec/2008:20:57:59 +0530] cupsdIsAuthorized: requesting-user-name="murale"',
               'I [10/Dec/2008:20:57:59 +0530] Saving subscriptions.conf...',
               'D [10/Dec/2008:20:57:59 +0530] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)',
               'D [10/Dec/2008:20:57:59 +0530] cupsdCloseClient: 13',
               'D [10/Dec/2008:20:57:59 +0530] cupsdAcceptClient: 13 from localhost (Domain)',
               'D [10/Dec/2008:20:57:59 +0530] cupsdCloseClient: 12',
               'D [10/Dec/2008:20:57:59 +0530] cupsdReadClient: 13 GET /admin/log/error_log HTTP/1.1',
               'D [10/Dec/2008:20:57:59 +0530] cupsdAuthorize: No authentication data provided.']}test page option

---

