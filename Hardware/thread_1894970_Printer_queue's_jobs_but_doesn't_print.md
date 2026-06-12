---
title: "Printer queue's jobs but doesn't print"
date: 2011-12-13
forum: Hardware
---

### Post by coalie1228 on 2011-12-13
Okay I re-installed 9.10 and everything was working great. 
everything installed fabulously. The first time I attempted to print it started then error-ed.
I followed all the prompts and still nothing worked. Then I tried uninstalling & re-installing. I trudged through 100's of articles and websites and forum posts but nothing fixed my problem. I'm feeling kind of hopeless here so please help ^-^
**ERROR LOGS**
```
D [13/Dec/2011:18:04:42 -0500] cupsdSetBusyState: Not busy
D [13/Dec/2011:18:04:42 -0500] cupsdReadClient: 20 POST / HTTP/1.1
D [13/Dec/2011:18:04:42 -0500] cupsdSetBusyState: Active clients
D [13/Dec/2011:18:04:42 -0500] cupsdAuthorize: Authorized as lisa using PeerCred
D [13/Dec/2011:18:04:42 -0500] cupsdReadClient: 20 1.1 Get-Jobs 1
D [13/Dec/2011:18:04:42 -0500] Get-Jobs ipp://localhost/printers/
D [13/Dec/2011:18:04:42 -0500] [Job 28] Loading attributes...
D [13/Dec/2011:18:04:42 -0500] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [13/Dec/2011:18:04:42 -0500] cupsdSetBusyState: Not busy
D [13/Dec/2011:18:04:42 -0500] cupsdReadClient: 20 POST / HTTP/1.1
D [13/Dec/2011:18:04:42 -0500] cupsdSetBusyState: Active clients
D [13/Dec/2011:18:04:42 -0500] cupsdAuthorize: Authorized as lisa using PeerCred
D [13/Dec/2011:18:04:42 -0500] cupsdReadClient: 20 1.1 Get-Jobs 1
D [13/Dec/2011:18:04:42 -0500] Get-Jobs ipp://localhost/printers/
D [13/Dec/2011:18:04:42 -0500] [Job 17] Loading attributes...
D [13/Dec/2011:18:04:42 -0500] [Job 18] Loading attributes...
D [13/Dec/2011:18:04:42 -0500] [Job 19] Loading attributes...
D [13/Dec/2011:18:04:42 -0500] [Job 20] Loading attributes...
D [13/Dec/2011:18:04:42 -0500] [Job 21] Loading attributes...
D [13/Dec/2011:18:04:42 -0500] [Job 22] Loading attributes...
E [13/Dec/2011:18:04:42 -0500] [Job 22] Unable to queue job for destination "Lexmark--3600-4600-Series"!
D [13/Dec/2011:18:04:42 -0500] [Job 23] Loading attributes...
E [13/Dec/2011:18:04:42 -0500] [Job 23] Unable to queue job for destination "Lexmark_3600-4600_Series"!
D [13/Dec/2011:18:04:42 -0500] [Job 26] Loading attributes...
E [13/Dec/2011:18:04:42 -0500] [Job 26] Unable to queue job for destination "Lexmark--3600-4600-Series"!
D [13/Dec/2011:18:04:42 -0500] [Job 27] Loading attributes...
E [13/Dec/2011:18:04:42 -0500] [Job 27] Unable to queue job for destination "Lexmark--3600-4600-Series"!
D [13/Dec/2011:18:04:42 -0500] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [13/Dec/2011:18:04:42 -0500] cupsdSetBusyState: Not busy
D [13/Dec/2011:18:04:42 -0500] cupsdReadClient: 20 POST / HTTP/1.1
D [13/Dec/2011:18:04:42 -0500] cupsdSetBusyState: Active clients
D [13/Dec/2011:18:04:42 -0500] cupsdAuthorize: Authorized as lisa using PeerCred
D [13/Dec/2011:18:04:42 -0500] cupsdReadClient: 20 1.1 Create-Printer-Subscription 1
D [13/Dec/2011:18:04:42 -0500] Create-Printer-Subscription /
D [13/Dec/2011:18:04:42 -0500] cupsdCreateSubscription(con=0x146d5a0(20), uri="/")
D [13/Dec/2011:18:04:42 -0500] pullmethod="ippget"
D [13/Dec/2011:18:04:42 -0500] notify-lease-duration=86400
D [13/Dec/2011:18:04:42 -0500] notify-time-interval=0
D [13/Dec/2011:18:04:42 -0500] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")
D [13/Dec/2011:18:04:42 -0500] Added subscription 38 for server
D [13/Dec/2011:18:04:42 -0500] cupsdMarkDirty(-----S)
D [13/Dec/2011:18:04:42 -0500] cupsdSetBusyState: Active clients and dirty files
D [13/Dec/2011:18:04:42 -0500] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost
D [13/Dec/2011:18:04:42 -0500] cupsdSetBusyState: Dirty files
D [13/Dec/2011:18:04:43 -0500] cupsdReadClient: 20 POST / HTTP/1.1
D [13/Dec/2011:18:04:43 -0500] cupsdSetBusyState: Active clients and dirty files
D [13/Dec/2011:18:04:43 -0500] cupsdAuthorize: Authorized as lisa using PeerCred
D [13/Dec/2011:18:04:43 -0500] cupsdReadClient: 20 1.1 Get-Notifications 1
D [13/Dec/2011:18:04:43 -0500] Get-Notifications /
D [13/Dec/2011:18:04:43 -0500] cupsdIsAuthorized: username="lisa"
D [13/Dec/2011:18:04:43 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [13/Dec/2011:18:04:43 -0500] cupsdSetBusyState: Dirty files
D [13/Dec/2011:18:04:46 -0500] cupsdReadClient: 20 POST /jobs/ HTTP/1.1
D [13/Dec/2011:18:04:46 -0500] cupsdSetBusyState: Active clients and dirty files
D [13/Dec/2011:18:04:46 -0500] cupsdAuthorize: Authorized as lisa using PeerCred
D [13/Dec/2011:18:04:46 -0500] cupsdReadClient: 20 1.1 Cancel-Job 1
D [13/Dec/2011:18:04:46 -0500] Cancel-Job ipp://localhost/jobs/28
D [13/Dec/2011:18:04:46 -0500] cupsdIsAuthorized: username="lisa"
D [13/Dec/2011:18:04:46 -0500] cupsdMarkDirty(-----S)
I [13/Dec/2011:18:04:46 -0500] [Job 28] Job canceled by "lisa"
D [13/Dec/2011:18:04:46 -0500] cupsdMarkDirty(----J-)
I [13/Dec/2011:18:04:46 -0500] [Job 28] Canceled by "lisa".
D [13/Dec/2011:18:04:46 -0500] Returning IPP successful-ok for Cancel-Job (ipp://localhost/jobs/28) from localhost
D [13/Dec/2011:18:04:46 -0500] cupsdSetBusyState: Dirty files
D [13/Dec/2011:18:04:50 -0500] cupsdNetIFUpdate: "lo" = localhost:631
D [13/Dec/2011:18:04:50 -0500] cupsdNetIFUpdate: "eth0" = 192.168.2.3:631
D [13/Dec/2011:18:04:50 -0500] cupsdNetIFUpdate: "lo" = localhost:631
D [13/Dec/2011:18:04:50 -0500] cupsdNetIFUpdate: "eth0" = fe80::213:20ff:fe87:1d0e%eth0:631
D [13/Dec/2011:18:04:50 -0500] Report: clients=7
D [13/Dec/2011:18:04:50 -0500] Report: jobs=10
D [13/Dec/2011:18:04:50 -0500] Report: jobs-active=0
D [13/Dec/2011:18:04:50 -0500] Report: printers=1
D [13/Dec/2011:18:04:50 -0500] Report: printers-implicit=0
D [13/Dec/2011:18:04:50 -0500] Report: stringpool-string-count=6540
D [13/Dec/2011:18:04:50 -0500] Report: stringpool-alloc-bytes=10856
D [13/Dec/2011:18:04:50 -0500] Report: stringpool-total-bytes=154064
D [13/Dec/2011:18:04:52 -0500] cupsdAcceptClient: 21 from localhost (Domain)
D [13/Dec/2011:18:04:52 -0500] cupsdReadClient: 21 POST /jobs/ HTTP/1.1
D [13/Dec/2011:18:04:52 -0500] cupsdSetBusyState: Active clients and dirty files
D [13/Dec/2011:18:04:52 -0500] cupsdAuthorize: No authentication data provided.
D [13/Dec/2011:18:04:52 -0500] cupsdReadClient: 21 1.1 Cancel-Job 1
D [13/Dec/2011:18:04:52 -0500] Cancel-Job ipp://localhost/jobs/28
D [13/Dec/2011:18:04:52 -0500] cupsdIsAuthorized: requesting-user-name="lisa"
D [13/Dec/2011:18:04:52 -0500] Cancel-Job client-error-not-possible: Job #28 is already canceled - can't cancel.
E [13/Dec/2011:18:04:52 -0500] Returning IPP client-error-not-possible for Cancel-Job (ipp://localhost/jobs/28) from localhost
D [13/Dec/2011:18:04:52 -0500] cupsdSetBusyState: Dirty files
D [13/Dec/2011:18:04:52 -0500] cupsdAcceptClient: 22 from localhost (Domain)
D [13/Dec/2011:18:04:52 -0500] cupsdReadClient: 22 POST / HTTP/1.1
D [13/Dec/2011:18:04:52 -0500] cupsdSetBusyState: Active clients and dirty files
D [13/Dec/2011:18:04:52 -0500] cupsdAuthorize: No authentication data provided.
D [13/Dec/2011:18:04:52 -0500] cupsdReadClient: 22 1.1 Get-Notifications 1
D [13/Dec/2011:18:04:52 -0500] Get-Notifications /
D [13/Dec/2011:18:04:52 -0500] cupsdIsAuthorized: requesting-user-name="lisa"
D [13/Dec/2011:18:04:52 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [13/Dec/2011:18:04:52 -0500] cupsdSetBusyState: Dirty files
D [13/Dec/2011:18:04:52 -0500] cupsdReadClient: 22 WAITING Closing on EOF
D [13/Dec/2011:18:04:52 -0500] cupsdCloseClient: 22
D [13/Dec/2011:18:04:55 -0500] cupsdReadClient: 20 POST / HTTP/1.1
D [13/Dec/2011:18:04:55 -0500] cupsdSetBusyState: Active clients and dirty files
D [13/Dec/2011:18:04:55 -0500] cupsdAuthorize: Authorized as lisa using PeerCred
D [13/Dec/2011:18:04:55 -0500] cupsdReadClient: 20 1.1 Get-Job-Attributes 1
D [13/Dec/2011:18:04:55 -0500] Get-Job-Attributes ipp://localhost/jobs/28
D [13/Dec/2011:18:04:55 -0500] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/28) from localhost
D [13/Dec/2011:18:04:55 -0500] cupsdSetBusyState: Dirty files
D [13/Dec/2011:18:04:55 -0500] cupsdReadClient: 20 POST / HTTP/1.1
D [13/Dec/2011:18:04:55 -0500] cupsdSetBusyState: Active clients and dirty files
D [13/Dec/2011:18:04:55 -0500] cupsdAuthorize: Authorized as lisa using PeerCred
D [13/Dec/2011:18:04:55 -0500] cupsdReadClient: 20 1.1 Cancel-Subscription 1
D [13/Dec/2011:18:04:55 -0500] Cancel-Subscription /
D [13/Dec/2011:18:04:55 -0500] cupsdIsAuthorized: username="lisa"
D [13/Dec/2011:18:04:55 -0500] cupsdMarkDirty(-----S)
D [13/Dec/2011:18:04:55 -0500] Returning IPP successful-ok for Cancel-Subscription (/) from localhost
D [13/Dec/2011:18:04:55 -0500] cupsdSetBusyState: Dirty files
D [13/Dec/2011:18:04:55 -0500] cupsdAcceptClient: 22 from localhost (Domain)
D [13/Dec/2011:18:04:55 -0500] cupsdReadClient: 22 GET /admin/log/error_log HTTP/1.1
D [13/Dec/2011:18:04:55 -0500] cupsdSetBusyState: Active clients and dirty files
D [13/Dec/2011:18:04:55 -0500] cupsdAuthorize: No authentication data provided.
```**DIAGNOSTIC BUG REPORT**
```
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest My_Lexmark_3600-4600_Series (default)>,
 'cups_instance': None,
 'cups_queue': 'My_Lexmark_3600-4600_Series',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://Lexmark/3600-4600%20Series',
                       'printer-info': u'',
                       'printer-is-shared': True,
                       'printer-location': u'',
                       'printer-make-and-model': u'Lexmark 3600-4600 Series, 1.0',
                       'printer-state': 3,
                       'printer-state-message': u'Processing page 5...',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 53260,
                       'printer-uri-supported': u'ipp://localhost:631/printers/My_Lexmark_3600-4600_Series'},
 'cups_printer_remote': False,
 'is_cups_class': False,
 'local_cups_queue_attributes': {'auth-info-required': u'none',
                                 'charset-configured': u'utf-8',
                                 'charset-supported': [u'us-ascii', u'utf-8'],
                                 'color-supported': True,
                                 'compression-supported': [u'none', u'gzip'],
                                 'copies-default': 1,
                                 'copies-supported': (1, 9999),
                                 'cups-version': u'1.4.1',
                                 'device-uri': u'usb://Lexmark/3600-4600%20Series',
                                 'document-format-default': u'application/octet-stream',
                                 'document-format-supported': [u'application/octet-stream',
                                                               u'application/openofficeps',
                                                               u'application/pdf',
                                                               u'application/postscript',
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
                                 'generated-natural-language-supported': [u'en_US'],
                                 'ipp-versions-supported': [u'1.0',
                                                            u'1.1',
                                                            u'2.0',
                                                            u'2.1'],
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
                                                                       u'job-priority',
                                                                       u'media',
                                                                       u'multiple-document-handling',
                                                                       u'number-up',
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
                                 'media-col-supported': [u'media-color',
                                                         u'media-key',
                                                         u'media-size',
                                                         u'media-type'],
                                 'media-default': u'na_letter_8.5x11in',
                                 'media-supported': [u'na_letter_8.5x11in',
                                                     u'na_arch-a_9x12in',
                                                     u'adobe_LetterBA_8.5x110in',
                                                     u'na_legal_8.5x14in',
                                                     u'na_invoice_5.5x8.5in',
                                                     u'adobe_HalfLetter_4.25x5.5in',
                                                     u'na_executive_7.25x10.5in',
                                                     u'iso_a4_210x297mm',
                                                     u'na_letter-plus_8.5x12.69in',
                                                     u'adobe_A4BA_209.973x2970.04mm',
                                                     u'iso_a5_148x210mm',
                                                     u'adobe_A5BL_155.434x236.079mm',
                                                     u'jis_b5_182x257mm',
                                                     u'adobe_B5JISBL_189.512x283.069mm',
                                                     u'na_number-10_4.125x9.5in',
                                                     u'adobe_Envelope9_3.97222x8.875in',
                                                     u'na_monarch_3.875x7.5in',
                                                     u'na_personal_3.625x6.5in',
                                                     u'adobe_EnvelopeBaronial_4.375x5.64306in',
                                                     u'na_a2_4.375x5.75in',
                                                     u'iso_b5_176x250mm',
                                                     u'iso_c5_162x229mm',
                                                     u'iso_c6_114x162mm',
                                                     u'iso_dl_110x220mm',
                                                     u'jpn_chou3_120x235mm',
                                                     u'jpn_chou4_90x205mm',
                                                     u'adobe_EnvelopeChokei40_89.9583x225.002mm',
                                                     u'adobe_EnvelopeKakugata3_216.041x277.001mm',
                                                     u'adobe_EnvelopeKakugata4_197.026x266.996mm',
                                                     u'adobe_EnvelopeKakugata5_7.48056x9.45in',
                                                     u'iso_c5_162x229mm',
                                                     u'na_index-3x5_3x5in',
                                                     u'na_index-5x8_5x8in',
                                                     u'iso_a6_105x148mm',
                                                     u'adobe_CardA6BL_112.466x174.061mm',
                                                     u'jpn_hagaki_100x148mm',
                                                     u'adobe_PostcardHagakiBL_107.491x174.061mm',
                                                     u'adobe_Photo312x5_3.49819x5in',
                                                     u'adobe_Photo312x5BL_96.333x153.106mm',
                                                     u'na_index-4x6_4x6in',
                                                     u'adobe_4x6BL_109.079x178.506mm',
                                                     u'adobe_4x8_4x8in',
                                                     u'na_5x7_5x7in',
                                                     u'adobe_Photo5x7BL_134.479x203.906mm',
                                                     u'na_govt-letter_8x10in',
                                                     u'adobe_PhotoL_3.50556x5in',
                                                     u'adobe_PhotoLBL_3.8x6.02778in',
                                                     u'na_5x7_5x7in',
                                                     u'adobe_Photo2LBL_134.479x203.906mm',
                                                     u'na_index-4x6_4x6in',
                                                     u'adobe_10x15cmBL_109.079x178.858mm',
                                                     u'na_5x7_5x7in',
                                                     u'adobe_13x18cmBL_134.479x204.329mm',
                                                     u'adobe_10x20cm_99.9984x200mm',
                                                     u'adobe_10x20cmBL_106.772x225.4mm',
                                                     u'om_large-photo_200x300',
                                                     u'adobe_9x13cm_89.9583x129.963mm',
                                                     u'adobe_15x21cm_150.036x209.973mm',
                                                     u'custom_min_3x5in',
                                                     u'custom_max_8.5x17in'],
                                 'multiple-document-handling-supported': [u'separate-documents-uncollated-copies',
                                                                          u'separate-documents-collated-copies'],
                                 'multiple-document-jobs-supported': True,
                                 'multiple-operation-time-out': 300,
                                 'natural-language-configured': u'en_US',
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
                                 'notify-schemes-supported': [u'mailto',
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
                                 'page-ranges-supported': True,
                                 'pages-per-minute': 15,
                                 'pdl-override-supported': [u'not-attempted'],
                                 'port-monitor': u'none',
                                 'port-monitor-supported': [u'none'],
                                 'printer-commands': u'none',
                                 'printer-current-time': '(IPP_TAG_DATE)',
                                 'printer-error-policy': u'retry-job',
                                 'printer-error-policy-supported': [u'abort-job',
                                                                    u'retry-current-job',
                                                                    u'retry-job',
                                                                    u'stop-printer'],
                                 'printer-info': u'',
                                 'printer-is-accepting-jobs': True,
                                 'printer-is-shared': True,
                                 'printer-location': u'',
                                 'printer-make-and-model': u'Lexmark 3600-4600 Series, 1.0',
                                 'printer-more-info': u'http://localhost:631/printers/My_Lexmark_3600-4600_Series',
                                 'printer-name': u'My_Lexmark_3600-4600_Series',
                                 'printer-op-policy': u'default',
                                 'printer-op-policy-supported': [u'authenticated',
                                                                 u'default'],
                                 'printer-settable-attributes-supported': [u'printer-info',
                                                                           u'printer-location'],
                                 'printer-state': 3,
                                 'printer-state-change-time': 1323817396,
                                 'printer-state-message': u'Processing page 5...',
                                 'printer-state-reasons': [u'none'],
                                 'printer-type': 53260,
                                 'printer-up-time': 1323817417,
                                 'printer-uri-supported': [u'ipp://localhost:631/printers/My_Lexmark_3600-4600_Series'],
                                 'queued-job-count': 1,
                                 'server-is-sharing-printers': True,
                                 'uri-authentication-supported': [u'requesting-user-name'],
                                 'uri-security-supported': [u'none']}}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'ColorModel': u'Color',
                                            u'MediaType': u'Automatic',
                                            u'PageRegion': u'Letter',
                                            u'PageSize': u'Letter',
                                            u'PrintMirror': u'False',
                                            u'PrintQuality': u'Automatic',
                                            u'Sharpening': u'Automatic'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Choose device):
{'cups_device_dict': {'device-class': u'direct',
                      'device-id': u'MFG:Lexmark;CMD:CPDNPA004;MODEL: 3600-4600 Series;CLASS:Printer;DES:Lexmark 3600-4600 Series;',
                      'device-info': u'Lexmark 3600-4600 Series',
                      'device-make-and-model': u'Lexmark 3600-4600 Series'}}
Page 7 (Printer state reasons):
{'printer-state-message': u'Processing page 5...',
 'printer-state-reasons': [u'none']}
Page 8 (Error log checkpoint):
{'cups_server_settings': {'BrowseLocalProtocols': 'CUPS dnssd',
                          'BrowseRemoteProtocols': '',
                          'DefaultAuthType': 'Basic',
                          'MaxLogSize': '0',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '1',
                          '_remote_admin': '0',
                          '_remote_any': '1',
                          '_remote_printers': '0',
                          '_share_printers': '1',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 4191214L}
Page 9 (Print test page):
{'test_page_job_status': [(True,
                           28,
                           'My_Lexmark_3600-4600_Series',
                           'VBA-22-1995-ARE.pdf',
                           'Stopped',
                           {'ColorModel': u'Color',
                            'MediaType': u'Automatic',
                            'PageSize': u'Letter',
                            'PrintMirror': False,
                            'PrintQuality': u'Automatic',
                            'Sharpening': u'Automatic',
                            'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-us',
                            'document-count': 0,
                            'document-format': u'application/pdf',
                            'job-hold-until': u'no-hold',
                            'job-id': 28,
                            'job-k-octets': 259,
                            'job-media-progress': 0,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/28',
                            'job-name': u'VBA-22-1995-ARE.pdf',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'lisa',
                            'job-preserved': False,
                            'job-printer-state-message': u'Color Cartridge Replacement Required.',
                            'job-printer-state-reasons': [u'none'],
                            'job-printer-up-time': 1323817495,
                            'job-printer-uri': u'ipp://lisa-desktop:631/printers/My_Lexmark_3600-4600_Series',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 7,
                            'job-state-reasons': u'job-canceled-by-user',
                            'job-uri': u'ipp://localhost:631/jobs/28',
                            'job-uuid': u'urn:uuid:2a2561a1-8bfe-324a-686b-bc65b4ba8ab9',
                            'number-up': 1,
                            'printer-uri': u'ipp://localhost:631/printers/My_Lexmark_3600-4600_Series',
                            'time-at-completed': 1323817486,
                            'time-at-creation': 1323817387,
                            'time-at-processing': 1323817387})],
 'test_page_jobs_cancelled': True,
 'test_page_successful': False}
Page 10 (Error log fetch):
{'error_log': ['D [13/Dec/2011:18:04:42 -0500] cupsdSetBusyState: Not busy',
               'D [13/Dec/2011:18:04:42 -0500] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [13/Dec/2011:18:04:42 -0500] cupsdSetBusyState: Active clients',
               'D [13/Dec/2011:18:04:42 -0500] cupsdAuthorize: Authorized as lisa using PeerCred',
               'D [13/Dec/2011:18:04:42 -0500] cupsdReadClient: 20 1.1 Get-Jobs 1',
               'D [13/Dec/2011:18:04:42 -0500] Get-Jobs ipp://localhost/printers/',
               'D [13/Dec/2011:18:04:42 -0500] [Job 28] Loading attributes...',
               'D [13/Dec/2011:18:04:42 -0500] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [13/Dec/2011:18:04:42 -0500] cupsdSetBusyState: Not busy',
               'D [13/Dec/2011:18:04:42 -0500] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [13/Dec/2011:18:04:42 -0500] cupsdSetBusyState: Active clients',
               'D [13/Dec/2011:18:04:42 -0500] cupsdAuthorize: Authorized as lisa using PeerCred',
               'D [13/Dec/2011:18:04:42 -0500] cupsdReadClient: 20 1.1 Get-Jobs 1',
               'D [13/Dec/2011:18:04:42 -0500] Get-Jobs ipp://localhost/printers/',
               'D [13/Dec/2011:18:04:42 -0500] [Job 17] Loading attributes...',
               'D [13/Dec/2011:18:04:42 -0500] [Job 18] Loading attributes...',
               'D [13/Dec/2011:18:04:42 -0500] [Job 19] Loading attributes...',
               'D [13/Dec/2011:18:04:42 -0500] [Job 20] Loading attributes...',
               'D [13/Dec/2011:18:04:42 -0500] [Job 21] Loading attributes...',
               'D [13/Dec/2011:18:04:42 -0500] [Job 22] Loading attributes...',
               'E [13/Dec/2011:18:04:42 -0500] [Job 22] Unable to queue job for destination "Lexmark--3600-4600-Series"!',
               'D [13/Dec/2011:18:04:42 -0500] [Job 23] Loading attributes...',
               'E [13/Dec/2011:18:04:42 -0500] [Job 23] Unable to queue job for destination "Lexmark_3600-4600_Series"!',
               'D [13/Dec/2011:18:04:42 -0500] [Job 26] Loading attributes...',
               'E [13/Dec/2011:18:04:42 -0500] [Job 26] Unable to queue job for destination "Lexmark--3600-4600-Series"!',
               'D [13/Dec/2011:18:04:42 -0500] [Job 27] Loading attributes...',
               'E [13/Dec/2011:18:04:42 -0500] [Job 27] Unable to queue job for destination "Lexmark--3600-4600-Series"!',
               'D [13/Dec/2011:18:04:42 -0500] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [13/Dec/2011:18:04:42 -0500] cupsdSetBusyState: Not busy',
               'D [13/Dec/2011:18:04:42 -0500] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [13/Dec/2011:18:04:42 -0500] cupsdSetBusyState: Active clients',
               'D [13/Dec/2011:18:04:42 -0500] cupsdAuthorize: Authorized as lisa using PeerCred',
               'D [13/Dec/2011:18:04:42 -0500] cupsdReadClient: 20 1.1 Create-Printer-Subscription 1',
               'D [13/Dec/2011:18:04:42 -0500] Create-Printer-Subscription /',
               'D [13/Dec/2011:18:04:42 -0500] cupsdCreateSubscription(con=0x146d5a0(20), uri="/")',
               'D [13/Dec/2011:18:04:42 -0500] pullmethod="ippget"',
               'D [13/Dec/2011:18:04:42 -0500] notify-lease-duration=86400',
               'D [13/Dec/2011:18:04:42 -0500] notify-time-interval=0',
               'D [13/Dec/2011:18:04:42 -0500] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [13/Dec/2011:18:04:42 -0500] Added subscription 38 for server',
               'D [13/Dec/2011:18:04:42 -0500] cupsdMarkDirty(-----S)',
               'D [13/Dec/2011:18:04:42 -0500] cupsdSetBusyState: Active clients and dirty files',
               'D [13/Dec/2011:18:04:42 -0500] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost',
               'D [13/Dec/2011:18:04:42 -0500] cupsdSetBusyState: Dirty files',
               'D [13/Dec/2011:18:04:43 -0500] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [13/Dec/2011:18:04:43 -0500] cupsdSetBusyState: Active clients and dirty files',
               'D [13/Dec/2011:18:04:43 -0500] cupsdAuthorize: Authorized as lisa using PeerCred',
               'D [13/Dec/2011:18:04:43 -0500] cupsdReadClient: 20 1.1 Get-Notifications 1',
               'D [13/Dec/2011:18:04:43 -0500] Get-Notifications /',
               'D [13/Dec/2011:18:04:43 -0500] cupsdIsAuthorized: username="lisa"',
               'D [13/Dec/2011:18:04:43 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [13/Dec/2011:18:04:43 -0500] cupsdSetBusyState: Dirty files',
               'D [13/Dec/2011:18:04:46 -0500] cupsdReadClient: 20 POST /jobs/ HTTP/1.1',
               'D [13/Dec/2011:18:04:46 -0500] cupsdSetBusyState: Active clients and dirty files',
               'D [13/Dec/2011:18:04:46 -0500] cupsdAuthorize: Authorized as lisa using PeerCred',
               'D [13/Dec/2011:18:04:46 -0500] cupsdReadClient: 20 1.1 Cancel-Job 1',
               'D [13/Dec/2011:18:04:46 -0500] Cancel-Job ipp://localhost/jobs/28',
               'D [13/Dec/2011:18:04:46 -0500] cupsdIsAuthorized: username="lisa"',
               'D [13/Dec/2011:18:04:46 -0500] cupsdMarkDirty(-----S)',
               'I [13/Dec/2011:18:04:46 -0500] [Job 28] Job canceled by "lisa"',
               'D [13/Dec/2011:18:04:46 -0500] cupsdMarkDirty(----J-)',
               'I [13/Dec/2011:18:04:46 -0500] [Job 28] Canceled by "lisa".',
               'D [13/Dec/2011:18:04:46 -0500] Returning IPP successful-ok for Cancel-Job (ipp://localhost/jobs/28) from localhost',
               'D [13/Dec/2011:18:04:46 -0500] cupsdSetBusyState: Dirty files',
               'D [13/Dec/2011:18:04:50 -0500] cupsdNetIFUpdate: "lo" = localhost:631',
               'D [13/Dec/2011:18:04:50 -0500] cupsdNetIFUpdate: "eth0" = 192.168.2.3:631',
               'D [13/Dec/2011:18:04:50 -0500] cupsdNetIFUpdate: "lo" = localhost:631',
               'D [13/Dec/2011:18:04:50 -0500] cupsdNetIFUpdate: "eth0" = fe80::213:20ff:fe87:1d0e%eth0:631',
               'D [13/Dec/2011:18:04:50 -0500] Report: clients=7',
               'D [13/Dec/2011:18:04:50 -0500] Report: jobs=10',
               'D [13/Dec/2011:18:04:50 -0500] Report: jobs-active=0',
               'D [13/Dec/2011:18:04:50 -0500] Report: printers=1',
               'D [13/Dec/2011:18:04:50 -0500] Report: printers-implicit=0',
               'D [13/Dec/2011:18:04:50 -0500] Report: stringpool-string-count=6540',
               'D [13/Dec/2011:18:04:50 -0500] Report: stringpool-alloc-bytes=10856',
               'D [13/Dec/2011:18:04:50 -0500] Report: stringpool-total-bytes=154064',
               'D [13/Dec/2011:18:04:52 -0500] cupsdAcceptClient: 21 from localhost (Domain)',
               'D [13/Dec/2011:18:04:52 -0500] cupsdReadClient: 21 POST /jobs/ HTTP/1.1',
               'D [13/Dec/2011:18:04:52 -0500] cupsdSetBusyState: Active clients and dirty files',
               'D [13/Dec/2011:18:04:52 -0500] cupsdAuthorize: No authentication data provided.',
               'D [13/Dec/2011:18:04:52 -0500] cupsdReadClient: 21 1.1 Cancel-Job 1',
               'D [13/Dec/2011:18:04:52 -0500] Cancel-Job ipp://localhost/jobs/28',
               'D [13/Dec/2011:18:04:52 -0500] cupsdIsAuthorized: requesting-user-name="lisa"',
               "D [13/Dec/2011:18:04:52 -0500] Cancel-Job client-error-not-possible: Job #28 is already canceled - can't cancel.",
               'E [13/Dec/2011:18:04:52 -0500] Returning IPP client-error-not-possible for Cancel-Job (ipp://localhost/jobs/28) from localhost',
               'D [13/Dec/2011:18:04:52 -0500] cupsdSetBusyState: Dirty files',
               'D [13/Dec/2011:18:04:52 -0500] cupsdAcceptClient: 22 from localhost (Domain)',
               'D [13/Dec/2011:18:04:52 -0500] cupsdReadClient: 22 POST / HTTP/1.1',
               'D [13/Dec/2011:18:04:52 -0500] cupsdSetBusyState: Active clients and dirty files',
               'D [13/Dec/2011:18:04:52 -0500] cupsdAuthorize: No authentication data provided.',
               'D [13/Dec/2011:18:04:52 -0500] cupsdReadClient: 22 1.1 Get-Notifications 1',
               'D [13/Dec/2011:18:04:52 -0500] Get-Notifications /',
               'D [13/Dec/2011:18:04:52 -0500] cupsdIsAuthorized: requesting-user-name="lisa"',
               'D [13/Dec/2011:18:04:52 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [13/Dec/2011:18:04:52 -0500] cupsdSetBusyState: Dirty files',
               'D [13/Dec/2011:18:04:52 -0500] cupsdReadClient: 22 WAITING Closing on EOF',
               'D [13/Dec/2011:18:04:52 -0500] cupsdCloseClient: 22',
               'D [13/Dec/2011:18:04:55 -0500] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [13/Dec/2011:18:04:55 -0500] cupsdSetBusyState: Active clients and dirty files',
               'D [13/Dec/2011:18:04:55 -0500] cupsdAuthorize: Authorized as lisa using PeerCred',
               'D [13/Dec/2011:18:04:55 -0500] cupsdReadClient: 20 1.1 Get-Job-Attributes 1',
               'D [13/Dec/2011:18:04:55 -0500] Get-Job-Attributes ipp://localhost/jobs/28',
               'D [13/Dec/2011:18:04:55 -0500] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/28) from localhost',
               'D [13/Dec/2011:18:04:55 -0500] cupsdSetBusyState: Dirty files',
               'D [13/Dec/2011:18:04:55 -0500] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [13/Dec/2011:18:04:55 -0500] cupsdSetBusyState: Active clients and dirty files',
               'D [13/Dec/2011:18:04:55 -0500] cupsdAuthorize: Authorized as lisa using PeerCred',
               'D [13/Dec/2011:18:04:55 -0500] cupsdReadClient: 20 1.1 Cancel-Subscription 1',
               'D [13/Dec/2011:18:04:55 -0500] Cancel-Subscription /',
               'D [13/Dec/2011:18:04:55 -0500] cupsdIsAuthorized: username="lisa"',
               'D [13/Dec/2011:18:04:55 -0500] cupsdMarkDirty(-----S)',
               'D [13/Dec/2011:18:04:55 -0500] Returning IPP successful-ok for Cancel-Subscription (/) from localhost',
               'D [13/Dec/2011:18:04:55 -0500] cupsdSetBusyState: Dirty files',
               'D [13/Dec/2011:18:04:55 -0500] cupsdAcceptClient: 22 from localhost (Domain)',
               'D [13/Dec/2011:18:04:55 -0500] cupsdReadClient: 22 GET /admin/log/error_log HTTP/1.1',
               'D [13/Dec/2011:18:04:55 -0500] cupsdSetBusyState: Active clients and dirty files',
               'D [13/Dec/2011:18:04:55 -0500] cupsdAuthorize: No authentication data provided.']}
Page 11 (Locale issues):
{'job_page_size': u'Letter',
 'printer_page_size': u'Letter',
 'system_locale_lang': None,
 'user_locale_ctype': 'en_US',
 'user_locale_messages': 'en_US'}
```P.S. I know it's not the printer/computer because I've had them up and running on various occassions.

---

### Post by foresthill on 2011-12-13
What are you trying to print? PDF and image files can sometimes be slow. Can you print text files OK?

---

