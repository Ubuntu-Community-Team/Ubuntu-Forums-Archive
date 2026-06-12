---
title: "Epson Photo RX610 Printer installation Problems in Ubuntu 8.10"
date: 2009-01-16
forum: Hardware
---

### Post by Carlos Sevcik on 2009-01-16
I just bought an Epson Photo RX610 multifunction printer and scanner and connected it to an Ubuntu 8.10 fully updated box. The scanner works well but I cannot print. I downloaded a driver from Epson to generate a ppd file, to do that I had to use the pipslitestm command which installed with the Epson drive, it produced an error saying that it was missing the libltdl.so.3 library. I fixed this by doing 

ln -s libltdl.so.7.1.2 libltdl.so.3

in /usr/lib. After that pipslitestm created the ppd file in /usr/share/ppd as eksprx610.ppd and I used this as the ppd to install the printer (Administration->printers->new)
If use Epson's command pipslitestm it shows a window with the ink levels of the cartridges in the printer and says the printer is ready to print. But it fails to print a test page, a popup windows indicates there is a an error and I was able to create the following troubleshooting file:

Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest stylusphotorx610 (default)>,
 'cups_instance': None,
 'cups_queue': 'stylusphotorx610',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://EPSON/Stylus%20Photo%20RX610',
                       'printer-info': u'stylusphotorx610',
                       'printer-is-shared': True,
                       'printer-location': u'farmaco.ivic.ve',
                       'printer-make-and-model': u'Epson  Stylus Photo RX610, Photo Image Print System Lite',
                       'printer-state': 3,
                       'printer-state-message': u"Can't write page 1 header",
                       'printer-state-reasons': [u'none'],
                       'printer-type': 4108,
                       'printer-uri-supported': u'ipp://localhost:631/printers/stylusphotorx610'},
 'cups_printer_remote': False,
 'is_cups_class': False}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'Ink': u'COLOR',
                                            u'PageRegion': u'4X6FULL',
                                            u'PageSize': u'4X6FULL',
                                            u'Quality': u'PMPHOTO_NORMAL'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Choose device):
{'cups_device_dict': {'device-class': u'direct',
                      'device-id': u'MFG:EPSON;CMD:ESCPL2,BDC,D4,D4PX,ESCPR1;MDL:Stylus Photo RX610;CLS:PRINTER;DES:EPSON Stylus Photo RX610;',
                      'device-info': u'EPSON Stylus Photo RX610 USB #1',
                      'device-make-and-model': u'EPSON Stylus Photo RX610'}}
Page 7 (Printer state reasons):
{'printer-state-message': u"Can't write page 1 header",
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
 'error_log_checkpoint': 6208710L}
Page 9 (Print test page):
{'test_page_job_status': [(True,
                           426,
                           'stylusphotorx610',
                           'Test Page',
                           'Stopped',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-us',
                            'document-format': u'application/postscript',
                            'job-hold-until': u'no-hold',
                            'job-id': 426,
                            'job-k-octets': 17,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/426',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'csevcik',
                            'job-preserved': True,
                            'job-printer-state-message': u"Can't write page 1 header",
                            'job-printer-state-reasons': [u'none'],
                            'job-printer-up-time': 1232150582,
                            'job-printer-uri': u'ipp://farmaco.ivic.ve:631/printers/stylusphotorx610',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 6,
                            'job-state-reasons': u'job-stopped',
                            'job-uri': u'ipp://localhost:631/jobs/426',
                            'job-uuid': u'urn:uuid:67cc5482-be8e-390a-6161-5c82e0583b1c',
                            'printer-uri': u'ipp://localhost/printers/stylusphotorx610',
                            'time-at-completed': None,
                            'time-at-creation': 1232150541,
                            'time-at-processing': 1232150541})],
 'test_page_successful': False}
Page 10 (Error log fetch):
{'error_log': ['D [16/Jan/2009:19:32:43 -04-30] cupsdCloseClient: 16',
               'D [16/Jan/2009:19:32:43 -04-30] cupsdAcceptClient: 16 from localhost (Domain)',
               'D [16/Jan/2009:19:32:43 -04-30] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [16/Jan/2009:19:32:43 -04-30] cupsdAuthorize: No authentication data provided.',
               'D [16/Jan/2009:19:32:43 -04-30] Get-Jobs ipp://localhost/jobs/',
               'D [16/Jan/2009:19:32:43 -04-30] [Job 426] Loading attributes...',
               'D [16/Jan/2009:19:32:43 -04-30] cupsdProcessIPPRequest: 16 status_code=0 (successful-ok)',
               'D [16/Jan/2009:19:32:43 -04-30] cupsdCloseClient: 16',
               'D [16/Jan/2009:19:32:43 -04-30] cupsdAcceptClient: 16 from localhost (Domain)',
               'D [16/Jan/2009:19:32:43 -04-30] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [16/Jan/2009:19:32:43 -04-30] cupsdAuthorize: No authentication data provided.',
               'D [16/Jan/2009:19:32:43 -04-30] Create-Printer-Subscription /',
               'D [16/Jan/2009:19:32:43 -04-30] cupsdCreateSubscription(con=0xb9570650(16), uri="/")',
               'D [16/Jan/2009:19:32:43 -04-30] pullmethod="ippget"',
               'D [16/Jan/2009:19:32:43 -04-30] notify-lease-duration=86400',
               'D [16/Jan/2009:19:32:43 -04-30] notify-time-interval=0',
               'D [16/Jan/2009:19:32:43 -04-30] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [16/Jan/2009:19:32:43 -04-30] Added subscription 54 for server',
               'I [16/Jan/2009:19:32:43 -04-30] Saving subscriptions.conf...',
               'D [16/Jan/2009:19:32:43 -04-30] cupsdProcessIPPRequest: 16 status_code=0 (successful-ok)',
               'D [16/Jan/2009:19:32:43 -04-30] cupsdCloseClient: 16',
               'D [16/Jan/2009:19:32:44 -04-30] cupsdAcceptClient: 16 from localhost (Domain)',
               'D [16/Jan/2009:19:32:44 -04-30] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [16/Jan/2009:19:32:44 -04-30] cupsdAuthorize: No authentication data provided.',
               'D [16/Jan/2009:19:32:44 -04-30] Get-Notifications /',
               'D [16/Jan/2009:19:32:44 -04-30] cupsdIsAuthorized: requesting-user-name="csevcik"',
               'D [16/Jan/2009:19:32:44 -04-30] cupsdProcessIPPRequest: 16 status_code=0 (successful-ok)',
               'D [16/Jan/2009:19:32:44 -04-30] cupsdCloseClient: 16',
               'D [16/Jan/2009:19:33:02 -04-30] cupsdAcceptClient: 16 from localhost (Domain)',
               'D [16/Jan/2009:19:33:02 -04-30] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [16/Jan/2009:19:33:02 -04-30] cupsdAuthorize: No authentication data provided.',
               'D [16/Jan/2009:19:33:02 -04-30] Get-Job-Attributes ipp://localhost/jobs/426',
               'D [16/Jan/2009:19:33:02 -04-30] cupsdProcessIPPRequest: 16 status_code=0 (successful-ok)',
               'D [16/Jan/2009:19:33:02 -04-30] cupsdCloseClient: 16',
               'D [16/Jan/2009:19:33:02 -04-30] cupsdAcceptClient: 16 from localhost (Domain)',
               'D [16/Jan/2009:19:33:02 -04-30] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [16/Jan/2009:19:33:02 -04-30] cupsdAuthorize: No authentication data provided.',
               'D [16/Jan/2009:19:33:02 -04-30] Cancel-Subscription /',
               'D [16/Jan/2009:19:33:02 -04-30] cupsdIsAuthorized: requesting-user-name="csevcik"',
               'I [16/Jan/2009:19:33:02 -04-30] Saving subscriptions.conf...',
               'D [16/Jan/2009:19:33:02 -04-30] cupsdProcessIPPRequest: 16 status_code=0 (successful-ok)',
               'D [16/Jan/2009:19:33:02 -04-30] cupsdCloseClient: 16',
               'D [16/Jan/2009:19:33:02 -04-30] cupsdAcceptClient: 16 from localhost (Domain)',
               'D [16/Jan/2009:19:33:02 -04-30] cupsdCloseClient: 14',
               'D [16/Jan/2009:19:33:02 -04-30] cupsdReadClient: 16 GET /admin/log/error_log HTTP/1.1',
               'D [16/Jan/2009:19:33:02 -04-30] cupsdAuthorize: No authentication data provided.']}

Can anybody help?

Many thanks

Carlos

---

### Post by charonred on 2009-05-05
I setup my brothers rx610 and it wouldn't print in Intrepid (never tried the scanner).

When I tried the Jaunty live CD it printed, so I installed/upgraded to Jaunty (with printer connected and on).

Once upgrade was complete, I deleted previous rx610 printer, Jaunty then found a 'new printer' and presto it now prints in both Gnome and KDE, as well as XP in VirtualBox.

still having no scanner detection (new post)

---

