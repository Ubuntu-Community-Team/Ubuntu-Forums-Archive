---
title: "HP LaserJet Professional p1606dn will not work."
date: 2011-08-29
forum: Hardware
---

### Post by Number3124 on 2011-08-29
I purchases an HP LaserJet Professional p1606dn yesterday. I've connected it via USB B-A cable as opposed to the networking option. I've always had good luck with HP printers in the past, and I had hoped that I would again. It works fine with windows, however I receive an error when I attempt to use it with Ubuntu 11.04. Two actually. When I go into the "printing" window, its status is marked as, "Idle-/usr/lib/cups/hpcups failed." When I attempt to print a file I receive this error in the Document Print Status window, "Printer 'HP-LaserJet-Professional-p1606dn':'printer requires a binary plugin, run hp-setup'." When I run a diagnostic on the print job a receive the output in quotes at the bottom of the post. Quite frankly, it means nothing to me. I don't understand it, however, I am sure that others do, and I want to provide any useful information.

What is troubling to me is that I have run the hp-setup utility in the  terminal in interactive mode, and I have used it, in sudo, to install  the missing binary. I have restarted since I installed it, and the  utility no longer seems to think that the binary is missing. However, the printer still requests it. Can anyone  give me a hand here? I'm afraid I'm in over my head.

> Page 1 (Scheduler not running?):
 

 {'cups_connection_failure': False}
 

 Page 2 (Choose printer):
 

 {'cups_dest': <cups.Dest HP-LaserJet-Professional-p1606dn (default)>,
 

  'cups_instance': None,
 

  'cups_queue': 'HP-LaserJet-Professional-p1606dn',
 

  'cups_queue_listed': True}
 

 Page 3 (Check printer sanity):
 

 {'cups_device_uri_scheme': u'usb',
 

  'cups_printer_dict': {'device-uri': u'usb://HP/LaserJet%20Professional%20P1606dn?serial=000000000QQ0HDSEPR1a',
 

                        'printer-info': u'HP LaserJet Professional p1606dn',
 

                        'printer-is-shared': False,
 

                        'printer-location': u'',
 

                        'printer-make-and-model': u'HP LaserJet Professional p1606dn, hpcups 3.11.1, requires proprietary plugin',
 

                        'printer-state': 3,
 

                        'printer-state-message': u'/usr/lib/cups/filter/hpcups failed',
 

                        'printer-state-reasons': [u'hplip.plugin-error'],
 

                        'printer-type': 2265116,
 

                        'printer-uri-supported': u'ipp://localhost/printers/HP-LaserJet-Professional-p1606dn'},
 

  'cups_printer_remote': False,
 

  'is_cups_class': False,
 

  'local_cups_queue_attributes': {'auth-info-required': u'none',
 

                                  'charset-configured': u'utf-8',
 

                                  'charset-supported': [u'us-ascii', u'utf-8'],
 

                                  'color-supported': True,
 

                                  'compression-supported': [u'none', u'gzip'],
 

                                  'copies-default': 1,
 

                                  'copies-supported': (1, 9999),
 

                                  'cups-version': u'1.4.6',
 

                                  'device-uri': u'usb://HP/LaserJet%20Professional%20P1606dn?serial=000000000QQ0HDSEPR1a',
 

                                  'document-format-default': u'application/octet-stream',
 

                                  'document-format-supported': [u'application/octet-stream',
 

                                                                u'application/openofficeps',
 

                                                                u'application/pdf',
 

                                                                u'application/postscript',
 

                                                                u'application/vnd.adobe-reader-postscript',
 

                                                                u'application/vnd.cups-banner',
 

                                                                u'application/vnd.cups-pdf',
 

                                                                u'application/vnd.cups-postscript',
 

                                                                u'application/vnd.cups-raster',
 

                                                                u'application/vnd.cups-raw',
 

                                                                u'application/vnd.hp-hpgl',
 

                                                                u'application/x-cshell',
 

                                                                u'application/x-csource',
 

                                                                u'application/x-perl',
 

                                                                u'application/x-shell',
 

                                                                u'image/gif',
 

                                                                u'image/jpeg',
 

                                                                u'image/png',
 

                                                                u'image/tiff',
 

                                                                u'image/x-bitmap',
 

                                                                u'image/x-photocd',
 

                                                                u'image/x-portable-anymap',
 

                                                                u'image/x-portable-bitmap',
 

                                                                u'image/x-portable-graymap',
 

                                                                u'image/x-portable-pixmap',
 

                                                                u'image/x-sgi-rgb',
 

                                                                u'image/x-sun-raster',
 

                                                                u'image/x-xbitmap',
 

                                                                u'image/x-xpixmap',
 

                                                                u'image/x-xwindowdump',
 

                                                                u'text/css',
 

                                                                u'text/html',
 

                                                                u'text/plain'],
 

                                  'finishings-default': 3,
 

                                  'finishings-supported': [3],
 

                                  'generated-natural-language-supported': [u'en-us'],
 

                                  'ipp-versions-supported': [u'1.0',
 

                                                             u'1.1',
 

                                                             u'2.0',
 

                                                             u'2.1'],
 

                                  'ippget-event-life': 15,
 

                                  'job-creation-attributes-supported': [u'copies',
 

                                                                        u'finishings',
 

                                                                        u'ipp-attribute-fidelity',
 

                                                                        u'job-hold-until',
 

                                                                        u'job-name',
 

                                                                        u'job-priority',
 

                                                                        u'job-sheets',
 

                                                                        u'media',
 

                                                                        u'media-col',
 

                                                                        u'multiple-document-handling',
 

                                                                        u'number-up',
 

                                                                        u'output-bin',
 

                                                                        u'output-mode',
 

                                                                        u'orientation-requested',
 

                                                                        u'page-ranges',
 

                                                                        u'print-quality',
 

                                                                        u'printer-resolution',
 

                                                                        u'sides'],
 

                                  'job-hold-until-default': u'no-hold',
 

                                  'job-hold-until-supported': [u'no-hold',
 

                                                               u'indefinite',
 

                                                               u'day-time',
 

                                                               u'evening',
 

                                                               u'night',
 

                                                               u'second-shift',
 

                                                               u'third-shift',
 

                                                               u'weekend'],
 

                                  'job-k-limit': 0,
 

                                  'job-page-limit': 0,
 

                                  'job-priority-default': 50,
 

                                  'job-priority-supported': [100],
 

                                  'job-quota-period': 0,
 

                                  'job-settable-attributes-supported': [u'copies',
 

                                                                        u'finishings',
 

                                                                        u'job-hold-until',
 

                                                                        u'job-name',
 

                                                                        u'job-priority',
 

                                                                        u'media',
 

                                                                        u'media-col',
 

                                                                        u'multiple-document-handling',
 

                                                                        u'number-up',
 

                                                                        u'output-bin',
 

                                                                        u'output-mode',
 

                                                                        u'orientation-requested',
 

                                                                        u'page-ranges',
 

                                                                        u'print-quality',
 

                                                                        u'printer-resolution',
 

                                                                        u'sides'],
 

                                  'job-sheets-default': (u'none', u'none'),
 

                                  'job-sheets-supported': [u'none',
 

                                                           u'classified',
 

                                                           u'confidential',
 

                                                           u'secret',
 

                                                           u'standard',
 

                                                           u'topsecret',
 

                                                           u'unclassified'],
 

                                  'marker-change-time': 0,
 

                                  'media-bottom-margin-supported': [423, 546],
 

                                  'media-col-supported': [u'media-bottom-margin',
 

                                                          u'media-left-margin',
 

                                                          u'media-right-margin',
 

                                                          u'media-size',
 

                                                          u'media-source',
 

                                                          u'media-top-margin',
 

                                                          u'media-type'],
 

                                  'media-default': u'na_letter_8.5x11in',
 

                                  'media-left-margin-supported': [423, 635],
 

                                  'media-right-margin-supported': [423, 635],
 

                                  'media-source-supported': [u'auto',
 

                                                             u'manual'],
 

                                  'media-supported': [u'iso_a6_105x148mm',
 

                                                      u'iso_a5_148x210mm',
 

                                                      u'jpn_hagaki_100x148mm',
 

                                                      u'om_double-postcard_148.16x200.02mm',
 

                                                      u'om_jb5_182.11x257.04mm',
 

                                                      u'na_executive_7.25x10.5in',
 

                                                      u'om_16k195x270_195.08x269.87mm',
 

                                                      u'om_16k184x260_184.15x259.99mm',
 

                                                      u'oe_16k197x273_7.75x10.75in',
 

                                                      u'oe_letter-sm_8.5x11in',
 

                                                      u'na_letter_8.5x11in',
 

                                                      u'om_a4-sm_210.05x296.92mm',
 

                                                      u'iso_a4_210x297mm',
 

                                                      u'oe_flsa-sm_8.5x13in',
 

                                                      u'om_flsa_215.9x325.96mm',
 

                                                      u'oe_legal-sm_8.5x14in',
 

                                                      u'na_legal_8.5x14in',
 

                                                      u'na_monarch_3.875x7.5in',
 

                                                      u'iso_dl_110x220mm',
 

                                                      u'na_number-10_4.125x9.5in',
 

                                                      u'iso_c5_162x229mm',
 

                                                      u'om_env-b5_176.03x250.11mm',
 

                                                      u'custom_min_3x5in',
 

                                                      u'custom_max_17x36in'],
 

                                  'media-top-margin-supported': [423, 546],
 

                                  'media-type-supported': [u'stationery'],
 

                                  'multiple-document-handling-supported': [u'separate-documents-uncollated-copies',
 

                                                                           u'separate-documents-collated-copies'],
 

                                  'multiple-document-jobs-supported': True,
 

                                  'multiple-operation-time-out': 300,
 

                                  'natural-language-configured': u'en-us',
 

                                  'notify-attributes-supported': [u'printer-state-change-time',
 

                                                                  u'notify-lease-expiration-time',
 

                                                                  u'notify-subscriber-user-name'],
 

                                  'notify-events-default': [u'job-completed'],
 

                                  'notify-events-supported': [u'job-completed',
 

                                                              u'job-config-changed',
 

                                                              u'job-created',
 

                                                              u'job-progress',
 

                                                              u'job-state-changed',
 

                                                              u'job-stopped',
 

                                                              u'printer-added',
 

                                                              u'printer-changed',
 

                                                              u'printer-config-changed',
 

                                                              u'printer-deleted',
 

                                                              u'printer-finishings-changed',
 

                                                              u'printer-media-changed',
 

                                                              u'printer-modified',
 

                                                              u'printer-restarted',
 

                                                              u'printer-shutdown',
 

                                                              u'printer-state-changed',
 

                                                              u'printer-stopped',
 

                                                              u'server-audit',
 

                                                              u'server-restarted',
 

                                                              u'server-started',
 

                                                              u'server-stopped'],
 

                                  'notify-lease-duration-default': 86400,
 

                                  'notify-lease-duration-supported': (0,
 

                                                                      2147483647),
 

                                  'notify-max-events-supported': [100],
 

                                  'notify-pull-method-supported': [u'ippget'],
 

                                  'notify-schemes-supported': [u'dbus',
 

                                                               u'mailto',
 

                                                               u'rss'],
 

                                  'number-up-default': 1,
 

                                  'number-up-supported': [1, 2, 4, 6, 9, 16],
 

                                  'operations-supported': [2,
 

                                                           4,
 

                                                           5,
 

                                                           6,
 

                                                           8,
 

                                                           9,
 

                                                           10,
 

                                                           11,
 

                                                           12,
 

                                                           13,
 

                                                           16,
 

                                                           17,
 

                                                           18,
 

                                                           19,
 

                                                           20,
 

                                                           21,
 

                                                           22,
 

                                                           23,
 

                                                           24,
 

                                                           25,
 

                                                           26,
 

                                                           27,
 

                                                           28,
 

                                                           34,
 

                                                           35,
 

                                                           37,
 

                                                           38,
 

                                                           16385,
 

                                                           16386,
 

                                                           16387,
 

                                                           16388,
 

                                                           16389,
 

                                                           16390,
 

                                                           16391,
 

                                                           16392,
 

                                                           16393,
 

                                                           16394,
 

                                                           16395,
 

                                                           16396,
 

                                                           16397,
 

                                                           16398,
 

                                                           16399,
 

                                                           16423],
 

                                  'orientation-requested-default': None,
 

                                  'orientation-requested-supported': [3,
 

                                                                      4,
 

                                                                      5,
 

                                                                      6],
 

                                  'output-bin-default': u'face-down',
 

                                  'output-bin-supported': [u'face-down'],
 

                                  'output-mode-default': u'color',
 

                                  'output-mode-supported': [u'monochrome',
 

                                                            u'color'],
 

                                  'page-ranges-supported': True,
 

                                  'pages-per-minute': 1,
 

                                  'pages-per-minute-color': 1,
 

                                  'pdl-override-supported': [u'attempted'],
 

                                  'port-monitor': u'none',
 

                                  'port-monitor-supported': [u'none'],
 

                                  'print-quality-default': 4,
 

                                  'print-quality-supported': [3, 4],
 

                                  'printer-commands': u'none',
 

                                  'printer-current-time': '(IPP_TAG_DATE)',
 

                                  'printer-dns-sd-name': None,
 

                                  'printer-error-policy': u'retry-job',
 

                                  'printer-error-policy-supported': [u'abort-job',
 

                                                                     u'retry-current-job',
 

                                                                     u'retry-job',
 

                                                                     u'stop-printer'],
 

                                  'printer-icons': u'http://localhost/icons/HP-LaserJet-Professional-p1606dn.png',
 

                                  'printer-info': u'HP LaserJet Professional p1606dn',
 

                                  'printer-is-accepting-jobs': True,
 

                                  'printer-is-shared': False,
 

                                  'printer-location': u'',
 

                                  'printer-make-and-model': u'HP LaserJet Professional p1606dn, hpcups 3.11.1, requires proprietary plugin',
 

                                  'printer-more-info': u'http://localhost/printers/HP-LaserJet-Professional-p1606dn',
 

                                  'printer-name': u'HP-LaserJet-Professional-p1606dn',
 

                                  'printer-op-policy': u'default',
 

                                  'printer-op-policy-supported': [u'authenticated',
 

                                                                  u'default'],
 

                                  'printer-resolution-default': '(unknown IPP tag)',
 

                                  'printer-resolution-supported': '(unknown IPP tag)',
 

                                  'printer-settable-attributes-supported': [u'printer-info',
 

                                                                            u'printer-location'],
 

                                  'printer-state': 3,
 

                                  'printer-state-change-time': 1314643599,
 

                                  'printer-state-message': u'/usr/lib/cups/filter/hpcups failed',
 

                                  'printer-state-reasons': [u'hplip.plugin-error'],
 

                                  'printer-type': 2265116,
 

                                  'printer-up-time': 1314643614,
 

                                  'printer-uri-supported': [u'ipp://localhost/printers/HP-LaserJet-Professional-p1606dn'],
 

                                  'queued-job-count': 1,
 

                                  'server-is-sharing-printers': False,
 

                                  'sides-default': u'one-sided',
 

                                  'sides-supported': [u'one-sided',
 

                                                      u'two-sided-long-edge',
 

                                                      u'two-sided-short-edge'],
 

                                  'uri-authentication-supported': [u'requesting-user-name'],
 

                                  'uri-security-supported': [u'none']}}
 

 Page 4 (Check PPD sanity):
 

 {'cups_printer_ppd_defaults': {u'General': {u'ColorModel': u'Gray',
 

                                             u'Duplex': u'None',
 

                                             u'InputSlot': u'Auto',
 

                                             u'MediaType': u'Plain',
 

                                             u'OutputMode': u'Normal',
 

                                             u'PageRegion': u'Letter',
 

                                             u'PageSize': u'Letter'},
 

                                u'InstallableOptions': {u'OptionDuplex': u'True'}},
 

  'cups_printer_ppd_valid': True,
 

  'missing_pkgs_and_exes': ([], [])}
 

 Page 5 (Local or remote?):
 

 {'printer_is_remote': False}
 

 Page 6 (Error log checkpoint):
 

 {'cups_server_settings': {'BrowseLocalProtocols': 'CUPS dnssd',
 

                           'DefaultAuthType': 'Basic',
 

                           'MaxLogSize': '0',
 

                           'SystemGroup': 'lpadmin',
 

                           '_debug_logging': '0',
 

                           '_remote_admin': '0',
 

                           '_remote_any': '0',
 

                           '_remote_printers': '0',
 

                           '_share_printers': '0',
 

                           '_user_cancel_any': '0'},
 

  'error_log_checkpoint': 246378,
 

  'error_log_debug_logging_set': True}
 

 Page 7 (Print test page):
 

 {'test_page_job_status': [(True,
 

                            8,
 

                            'HP-LaserJet-Professional-p1606dn',
 

                            'Test Page',
 

                            'Stopped',
 

                            {'PageSize': u'Letter',
 

                             'attributes-charset': u'utf-8',
 

                             'attributes-natural-language': u'en-us',
 

                             'document-count': 1,
 

                             'document-format': u'application/postscript',
 

                             'job-hold-until': u'no-hold',
 

                             'job-id': 8,
 

                             'job-k-octets': 201,
 

                             'job-media-progress': 0,
 

                             'job-media-sheets-completed': 0,
 

                             'job-more-info': u'ipp://localhost/jobs/8',
 

                             'job-name': u'Test Page',
 

                             'job-originating-host-name': u'localhost',
 

                             'job-originating-user-name': u'conor',
 

                             'job-preserved': True,
 

                             'job-printer-state-message': u'/usr/lib/cups/filter/hpcups failed',
 

                             'job-printer-state-reasons': [u'hplip.plugin-error'],
 

                             'job-printer-up-time': 1314643660,
 

                             'job-printer-uri': u'ipp://conor-RC512/printers/HP-LaserJet-Professional-p1606dn',
 

                             'job-priority': 50,
 

                             'job-sheets': [u'none', u'none'],
 

                             'job-state': 6,
 

                             'job-state-reasons': u'job-stopped',
 

                             'job-uri': u'ipp://localhost/jobs/8',
 

                             'job-uuid': u'urn:uuid:134370eb-4bfc-375b-79ff-bdc976ff2558',
 

                             'printer-uri': u'ipp://localhost/printers/HP-LaserJet-Professional-p1606dn',
 

                             'time-at-completed': None,
 

                             'time-at-creation': 1314643598,
 

                             'time-at-processing': 1314643598})],
 

  'test_page_successful': True}
 

 Page 8 (Error log fetch):
 

 {'error_log': ['D [29/Aug/2011:14:47:27 -0400] cupsdSetBusyState: Dirty files',
 

                'D [29/Aug/2011:14:47:27 -0400] cupsdReadClient: 11 POST / HTTP/1.1',
 

                'D [29/Aug/2011:14:47:27 -0400] cupsdSetBusyState: Active clients and dirty files',
 

                'D [29/Aug/2011:14:47:27 -0400] cupsdAuthorize: No authentication data provided.',
 

                'D [29/Aug/2011:14:47:27 -0400] cupsdReadClient: 11 1.1 Get-Jobs 1',
 

                'D [29/Aug/2011:14:47:27 -0400] Get-Jobs ipp://localhost/printers/',
 

                'D [29/Aug/2011:14:47:27 -0400] [Job 8] Loading attributes...',
 

                'D [29/Aug/2011:14:47:27 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
 

                'D [29/Aug/2011:14:47:27 -0400] cupsdSetBusyState: Dirty files',
 

                'D [29/Aug/2011:14:47:27 -0400] cupsdReadClient: 11 POST / HTTP/1.1',
 

                'D [29/Aug/2011:14:47:27 -0400] cupsdSetBusyState: Active clients and dirty files',
 

                'D [29/Aug/2011:14:47:27 -0400] cupsdAuthorize: No authentication data provided.',
 

                'D [29/Aug/2011:14:47:27 -0400] cupsdReadClient: 11 1.1 Get-Jobs 1',
 

                'D [29/Aug/2011:14:47:27 -0400] Get-Jobs ipp://localhost/printers/',
 

                'D [29/Aug/2011:14:47:27 -0400] [Job 1] Loading attributes...',
 

                'D [29/Aug/2011:14:47:27 -0400] [Job 2] Loading attributes...',
 

                'D [29/Aug/2011:14:47:27 -0400] [Job 3] Loading attributes...',
 

                'D [29/Aug/2011:14:47:27 -0400] [Job 4] Loading attributes...',
 

                'D [29/Aug/2011:14:47:27 -0400] [Job 5] Loading attributes...',
 

                'D [29/Aug/2011:14:47:27 -0400] [Job 6] Loading attributes...',
 

                'D [29/Aug/2011:14:47:27 -0400] [Job 7] Loading attributes...',
 

                'D [29/Aug/2011:14:47:27 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
 

                'D [29/Aug/2011:14:47:27 -0400] cupsdSetBusyState: Dirty files',
 

                'D [29/Aug/2011:14:47:27 -0400] cupsdReadClient: 11 POST / HTTP/1.1',
 

                'D [29/Aug/2011:14:47:27 -0400] cupsdSetBusyState: Active clients and dirty files',
 

                'D [29/Aug/2011:14:47:27 -0400] cupsdAuthorize: No authentication data provided.',
 

                'D [29/Aug/2011:14:47:27 -0400] cupsdReadClient: 11 1.1 Create-Printer-Subscription 1',
 

                'D [29/Aug/2011:14:47:27 -0400] Create-Printer-Subscription /',
 

                'D [29/Aug/2011:14:47:27 -0400] cupsdCreateSubscription(con=0x7f367c3a2490(11), uri="/")',
 

                'D [29/Aug/2011:14:47:27 -0400] pullmethod="ippget"',
 

                'D [29/Aug/2011:14:47:27 -0400] notify-lease-duration=86400',
 

                'D [29/Aug/2011:14:47:27 -0400] notify-time-interval=0',
 

                'D [29/Aug/2011:14:47:27 -0400] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
 

                'D [29/Aug/2011:14:47:27 -0400] Added subscription 10 for server',
 

                'D [29/Aug/2011:14:47:27 -0400] cupsdMarkDirty(-----S)',
 

                'D [29/Aug/2011:14:47:27 -0400] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost',
 

                'D [29/Aug/2011:14:47:27 -0400] cupsdSetBusyState: Dirty files',
 

                'D [29/Aug/2011:14:47:28 -0400] cupsdReadClient: 11 POST / HTTP/1.1',
 

                'D [29/Aug/2011:14:47:28 -0400] cupsdSetBusyState: Active clients and dirty files',
 

                'D [29/Aug/2011:14:47:28 -0400] cupsdAuthorize: No authentication data provided.',
 

                'D [29/Aug/2011:14:47:28 -0400] cupsdReadClient: 11 1.1 Get-Notifications 1',
 

                'D [29/Aug/2011:14:47:28 -0400] Get-Notifications /',
 

                'D [29/Aug/2011:14:47:28 -0400] cupsdIsAuthorized: requesting-user-name="conor"',
 

                'D [29/Aug/2011:14:47:28 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
 

                'D [29/Aug/2011:14:47:28 -0400] cupsdSetBusyState: Dirty files',
 

                'D [29/Aug/2011:14:47:40 -0400] cupsdReadClient: 11 POST / HTTP/1.1',
 

                'D [29/Aug/2011:14:47:40 -0400] cupsdSetBusyState: Active clients and dirty files',
 

                'D [29/Aug/2011:14:47:40 -0400] cupsdAuthorize: No authentication data provided.',
 

                'D [29/Aug/2011:14:47:40 -0400] cupsdReadClient: 11 1.1 Get-Job-Attributes 1',
 

                'D [29/Aug/2011:14:47:40 -0400] Get-Job-Attributes ipp://localhost/jobs/8',
 

                'D [29/Aug/2011:14:47:40 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/8) from localhost',
 

                'D [29/Aug/2011:14:47:40 -0400] cupsdSetBusyState: Dirty files',
 

                'D [29/Aug/2011:14:47:40 -0400] cupsdReadClient: 11 POST / HTTP/1.1',
 

                'D [29/Aug/2011:14:47:40 -0400] cupsdSetBusyState: Active clients and dirty files',
 

                'D [29/Aug/2011:14:47:40 -0400] cupsdAuthorize: No authentication data provided.',
 

                'D [29/Aug/2011:14:47:40 -0400] cupsdReadClient: 11 1.1 Cancel-Subscription 1',
 

                'D [29/Aug/2011:14:47:40 -0400] Cancel-Subscription /',
 

                'D [29/Aug/2011:14:47:40 -0400] cupsdIsAuthorized: requesting-user-name="conor"',
 

                'D [29/Aug/2011:14:47:40 -0400] cupsdMarkDirty(-----S)',
 

                'D [29/Aug/2011:14:47:40 -0400] Returning IPP successful-ok for Cancel-Subscription (/) from localhost',
 

                'D [29/Aug/2011:14:47:40 -0400] cupsdSetBusyState: Dirty files',
 

                'D [29/Aug/2011:14:47:40 -0400] cupsdReadClient: 11 PUT /admin/conf/cupsd.conf HTTP/1.1',
 

                'D [29/Aug/2011:14:47:40 -0400] cupsdSetBusyState: Active clients and dirty files',
 

                'D [29/Aug/2011:14:47:40 -0400] cupsdAuthorize: No authentication data provided.',
 

                'D [29/Aug/2011:14:47:40 -0400] cupsdIsAuthorized: username=""',
 

                'D [29/Aug/2011:14:47:40 -0400] cupsdSendHeader: 11 WWW-Authenticate: Basic realm="CUPS", trc="y"',
 

                'D [29/Aug/2011:14:47:40 -0400] cupsdCloseClient: 11',
 

                'D [29/Aug/2011:14:47:40 -0400] cupsdSetBusyState: Dirty files',
 

                'D [29/Aug/2011:14:47:40 -0400] cupsdAcceptClient: 11 from localhost (Domain)',
 

                'D [29/Aug/2011:14:47:40 -0400] cupsdReadClient: 11 PUT /admin/conf/cupsd.conf HTTP/1.1',
 

                'D [29/Aug/2011:14:47:40 -0400] cupsdSetBusyState: Active clients and dirty files',
 

                'D [29/Aug/2011:14:47:40 -0400] cupsdAuthorize: Authorized as conor using PeerCred',
 

                'D [29/Aug/2011:14:47:40 -0400] cupsdIsAuthorized: username="conor"',
 

                'I [29/Aug/2011:14:47:40 -0400] Installing config file "/etc/cups/cupsd.conf"...',
 

                'D [29/Aug/2011:14:47:40 -0400] cupsdSetBusyState: Dirty files',
 

                'D [29/Aug/2011:14:47:40 -0400] cupsdCloseClient: 11',
 

                'I [29/Aug/2011:14:47:40 -0400] Generating printcap /var/run/cups/printcap...',
 

                'I [29/Aug/2011:14:47:40 -0400] Saving subscriptions.conf...',
 

                'D [29/Aug/2011:14:47:40 -0400] cupsdSetBusyState: Not busy',
 

                'W [29/Aug/2011:14:47:40 -0400] Duplicate listen address "/var/run/cups/cups.sock" ignored!'],
 

  'error_log_debug_logging_unset': True}
 

 Page 9 (Locale issues):
 

 {'job_page_size': u'Letter',
 

  'printer_page_size': u'Letter',
 

  'system_locale_lang': None,
 

  'user_locale_ctype': 'en_US',
 

  'user_locale_messages': 'en_US'}
 

---

### Post by Number3124 on 2011-08-29
I solved the problem on my own. I uninstalled the printer and the HP drivers. Then I downloaded the newest ones from HP's site, and installed them, then reinstalled the plugin. The printer works great now.

---

