---
title: "Brother Printer: Idle - Waiting for printer to finish."
date: 2017-03-19
forum: Hardware
---

### Post by Bucky Ball on 2017-03-19
As in the title. Bought a new Brother HL-L2365DW printer yesterday. Spent hours getting it to work on our network. Finally did and now, after it has printed a page, get the message:

> Idle - Waiting for printer to finish.

Sort of contradicts itself, but anyway ...

It refuses to print anything else until it has finished doing what it's doing, whatever that is and I can't find that it's anything. 

Xubuntu-core 16.04.2. The Brother printer is exclusive to Officeworks, a retailer over here, but uses the HL-L2360DW driver so figuring it is virtually the same Brother printer. There is no driver specific to the 2365 

Yes, I used the Brother Driver Install tool from the Brother site to get this going and that is the driver it gives me. The only way I could get it to successfully install was to put in the printer's IP address. The entry it gives in printer is:

> socket://***.***.***.***

... where '***.***.***.***' is the printer's IP.

Any ideas, suggestions, tips much appreciated. :)

PS: Also yes, did hunt for info on this and didn't find much. What I did find did nothing. Very new printer and not much about it around, especially on Linux, althoug the contradictory message 'Idle - Waiting for printer to finish' does crop up. Still no joy, though.

---

### Post by pdc on 2017-03-19
sorry to hear of your problems; so just sort of scratching around the place on Brother's site; they have funny little bits of info here and there: 

they say for 64bit [http://support.brother.com/g/s/id/linux/en/before.html?c=au&lang=en&prod=hll2365dw_eu_as&redirect=on#004](http://support.brother.com/g/s/id/linux/en/before.html?c=au&lang=en&prod=hll2365dw_eu_as&redirect=on#004) you need "    Requirement ia32-libs or lib32stdc++ is required to be installed."

so far, that is the only little extra I can find; 

_______

the ubuntu wiki [https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems) has a section [https://wiki.ubuntu.com/DebuggingPrintingProblems#CUPS_error_log](https://wiki.ubuntu.com/DebuggingPrintingProblems#CUPS_error_log) on seeing if CUPS will spill the beans on why it is unhappy: would that shed some light?

_______

in their FAQ, 32bit drivers for 64bit installs: [http://support.brother.com/g/s/id/linux/en/faq_prn.html?c=us_ot&lang=en&redirect=on#f00081](http://support.brother.com/g/s/id/linux/en/faq_prn.html?c=us_ot&lang=en&redirect=on#f00081) ..... some stuff to check ............

__________

... whilst mentioning little gems hidden on various bits of Brother's sites, for the scanner side of the Brother, folks have discovered ...for a networked scanner ... one needs libusb-0.1-4 ....... [http://askubuntu.com/questions/868063/installing-brscan4-for-my-brother-scanner-doesnt-work-on-a-fresh-ubuntu-16-10-i](http://askubuntu.com/questions/868063/installing-brscan4-for-my-brother-scanner-doesnt-work-on-a-fresh-ubuntu-16-10-i)      ..... so it is tracking all these things down; ideally the installer tool would capture things; if one manually asks for the LPR driver for the HL-L2365DW, their site recommends exactly what the installer selected for you: [COLOR="#0000FF"]hll2360dlpr-3.2.0-1.i386.deb[/COLOR] which was a 2015 issue, so it covers all the printers in the 2360 series;

---

### Post by Bucky Ball on 2017-03-19
The HL-L2365DW has no scanner. Basic mono duplex laser printer with wired/wireless. Thanks for the searching and info. I will now start trawling through the links I haven't checked already. :)

Just to add, restarting CUPS ([as described in this post]("https://forums.opensuse.org/showthread.php/516876-Waiting-for-printer-to-finish-message-when-selecting-printer?p=2772763#post2772763")) clears the 'Waiting to finish' message so, as you suggest and as also suggested in the last post of the linked thread, further exploration of CUPS may reveal more. Think I'll start by looking there. Wish me luck!

* Quick update: I ran the troubleshooting tool in system-config-printers and it sure enough diagnosed the message as 'Waiting for printer' and the error as 'there is no obvious solution to this problem.' It gives me the option to report the problem, the data it spits out is below.

```
Page 1 (<troubleshoot.SchedulerNotRunning.SchedulerNotRunning object at 0x7fa9d3f6f9e8>):
{'cups_connection_failure': False}
Page 2 (<troubleshoot.ChoosePrinter.ChoosePrinter object at 0x7fa9d3f7e2b0>):
{'cups_dest': <cups.Dest HLL2360D (default)>,
 'cups_instance': None,
 'cups_queue': 'HLL2360D',
 'cups_queue_listed': True}
Page 3 (<troubleshoot.CheckPrinterSanity.CheckPrinterSanity object at 0x7fa9d3f7ee80>):
{'cups_device_uri_scheme': 'socket',
 'cups_printer_dict': {'device-uri': 'socket://***.***.***.***',
                       'printer-info': 'HLL2360D',
                       'printer-is-shared': False,
                       'printer-location': '',
                       'printer-make-and-model': 'Brother HL-L2360D for CUPS ',
                       'printer-state': 3,
                       'printer-state-message': '',
                       'printer-state-reasons': ['none'],
                       'printer-type': 10522644,
                       'printer-uri-supported': 'ipp://localhost/printers/HLL2360D'},
 'cups_printer_remote': False,
 'is_cups_class': False,
 'local_cups_queue_attributes': {'charset-configured': 'utf-8',
                                 'charset-supported': ['us-ascii', 'utf-8'],
                                 'color-supported': False,
                                 'compression-supported': ['none', 'gzip'],
                                 'copies-default': 1,
                                 'copies-supported': (1, 9999),
                                 'cups-version': '2.1.3',
                                 'device-uri': 'socket://192.168.0.112',
                                 'document-format-default': 'application/octet-stream',
                                 'document-format-supported': ['application/octet-stream',
                                                               'application/pdf',
                                                               'application/postscript',
                                                               'application/vnd.adobe-reader-postscript',
                                                               'application/vnd.cups-command',
                                                               'application/vnd.cups-pdf',
                                                               'application/vnd.cups-pdf-banner',
                                                               'application/vnd.cups-postscript',
                                                               'application/vnd.cups-raster',
                                                               'application/vnd.cups-raw',
                                                               'application/x-cshell',
                                                               'application/x-csource',
                                                               'application/x-perl',
                                                               'application/x-shell',
                                                               'image/gif',
                                                               'image/jpeg',
                                                               'image/png',
                                                               'image/pwg-raster',
                                                               'image/tiff',
                                                               'image/urf',
                                                               'image/x-bitmap',
                                                               'image/x-photocd',
                                                               'image/x-portable-anymap',
                                                               'image/x-portable-bitmap',
                                                               'image/x-portable-graymap',
                                                               'image/x-portable-pixmap',
                                                               'image/x-sgi-rgb',
                                                               'image/x-sun-raster',
                                                               'image/x-xbitmap',
                                                               'image/x-xpixmap',
                                                               'image/x-xwindowdump',
                                                               'text/css',
                                                               'text/html',
                                                               'text/plain'],
                                 'finishings-default': 3,
                                 'finishings-supported': [3],
                                 'generated-natural-language-supported': ['en-au'],
                                 'ipp-features-supported': ['subscription-object'],
                                 'ipp-versions-supported': ['1.0',
                                                            '1.1',
                                                            '2.0',
                                                            '2.1'],
                                 'ippget-event-life': 15,
                                 'job-cancel-after-default': 10800,
                                 'job-cancel-after-supported': (0, 2147483647),
                                 'job-creation-attributes-supported': ['copies',
                                                                       'finishings',
                                                                       'ipp-attribute-fidelity',
                                                                       'job-hold-until',
                                                                       'job-name',
                                                                       'job-priority',
                                                                       'job-sheets',
                                                                       'media',
                                                                       'media-col',
                                                                       'multiple-document-handling',
                                                                       'number-up',
                                                                       'output-bin',
                                                                       'orientation-requested',
                                                                       'page-ranges',
                                                                       'print-color-mode',
                                                                       'print-quality',
                                                                       'printer-resolution',
                                                                       'sides'],
                                 'job-hold-until-default': 'no-hold',
                                 'job-hold-until-supported': ['no-hold',
                                                              'indefinite',
                                                              'day-time',
                                                              'evening',
                                                              'night',
                                                              'second-shift',
                                                              'third-shift',
                                                              'weekend'],
                                 'job-ids-supported': True,
                                 'job-k-limit': 0,
                                 'job-k-octets-supported': (0, 15737052),
                                 'job-page-limit': 0,
                                 'job-priority-default': 50,
                                 'job-priority-supported': [100],
                                 'job-quota-period': 0,
                                 'job-settable-attributes-supported': ['copies',
                                                                       'finishings',
                                                                       'job-hold-until',
                                                                       'job-name',
                                                                       'job-priority',
                                                                       'media',
                                                                       'media-col',
                                                                       'multiple-document-handling',
                                                                       'number-up',
                                                                       'output-bin',
                                                                       'orientation-requested',
                                                                       'page-ranges',
                                                                       'print-color-mode',
                                                                       'print-quality',
                                                                       'printer-resolution',
                                                                       'sides'],
                                 'job-sheets-default': ('none', 'none'),
                                 'job-sheets-supported': ['none',
                                                          'classified',
                                                          'confidential',
                                                          'form',
                                                          'secret',
                                                          'standard',
                                                          'topsecret',
                                                          'unclassified'],
                                 'jpeg-k-octets-supported': (0, 15737052),
                                 'jpeg-x-dimension-supported': (0, 65535),
                                 'jpeg-y-dimension-supported': (1, 65535),
                                 'marker-change-time': 1489905221,
                                 'marker-colors': ['#000000', 'none'],
                                 'marker-levels': [-1, 99],
                                 'marker-names': ['Black Toner Cartridge',
                                                  'Drum Unit'],
                                 'marker-types': ['toner', 'opc'],
                                 'media-bottom-margin-supported': [423],
                                 'media-col-default': '(unknown IPP value tag '
                                                      '0x34)',
                                 'media-col-supported': ['media-bottom-margin',
                                                         'media-left-margin',
                                                         'media-right-margin',
                                                         'media-size',
                                                         'media-source',
                                                         'media-top-margin',
                                                         'media-type'],
                                 'media-default': 'iso_a4_210x297mm',
                                 'media-left-margin-supported': [423],
                                 'media-right-margin-supported': [423, 388],
                                 'media-size-supported': ['(unknown IPP value '
                                                          'tag 0x34)',
                                                          '(unknown IPP value '
                                                          'tag 0x34)',
                                                          '(unknown IPP value '
                                                          'tag 0x34)',
                                                          '(unknown IPP value '
                                                          'tag 0x34)',
                                                          '(unknown IPP value '
                                                          'tag 0x34)',
                                                          '(unknown IPP value '
                                                          'tag 0x34)',
                                                          '(unknown IPP value '
                                                          'tag 0x34)',
                                                          '(unknown IPP value '
                                                          'tag 0x34)',
                                                          '(unknown IPP value '
                                                          'tag 0x34)',
                                                          '(unknown IPP value '
                                                          'tag 0x34)',
                                                          '(unknown IPP value '
                                                          'tag 0x34)',
                                                          '(unknown IPP value '
                                                          'tag 0x34)',
                                                          '(unknown IPP value '
                                                          'tag 0x34)',
                                                          '(unknown IPP value '
                                                          'tag 0x34)',
                                                          '(unknown IPP value '
                                                          'tag 0x34)',
                                                          '(unknown IPP value '
                                                          'tag 0x34)',
                                                          '(unknown IPP value '
                                                          'tag 0x34)',
                                                          '(unknown IPP value '
                                                          'tag 0x34)',
                                                          '(unknown IPP value '
                                                          'tag 0x34)',
                                                          '(unknown IPP value '
                                                          'tag 0x34)',
                                                          '(unknown IPP value '
                                                          'tag 0x34)',
                                                          '(unknown IPP value '
                                                          'tag 0x34)',
                                                          '(unknown IPP value '
                                                          'tag 0x34)'],
                                 'media-source-supported': ['manual', 'tray-1'],
                                 'media-supported': ['na_letter_8.5x11in',
                                                     'na_legal_8.5x14in',
                                                     'na_executive_7.25x10.5in',
                                                     'na_foolscap_8.5x13in',
                                                     'iso_a4_210x297mm',
                                                     'iso_a5_148x210mm',
                                                     'iso_a6_105x148mm',
                                                     'na_number-10_4.125x9.5in',
                                                     'na_monarch_3.875x7.5in',
                                                     'iso_dl_110x220mm',
                                                     'iso_c5_162x229mm',
                                                     'iso_b5_176x250mm',
                                                     'jis_b5_182x257mm',
                                                     'iso_b6_125x176mm',
                                                     'jis_b6_128x182mm',
                                                     'na_index-4x6_4x6in',
                                                     'jpn_hagaki_100x148mm',
                                                     'jpn_oufuku_148x200mm',
                                                     'jpn_you4_105x235mm',
                                                     'custom_195.09x269.88mm_195.09x269.88mm',
                                                     'custom_184.15x260mm_184.15x260mm',
                                                     'om_197x273mm_197x273mm',
                                                     'custom_min_3x5in',
                                                     'custom_max_8.5x14in'],
                                 'media-top-margin-supported': [423, 388],
                                 'multiple-document-handling-supported': ['separate-documents-uncollated-copies',
                                                                          'separate-documents-collated-copies'],
                                 'multiple-document-jobs-supported': True,
                                 'multiple-operation-time-out': 300,
                                 'multiple-operation-time-out-action': 'process-job',
                                 'natural-language-configured': 'en-au',
                                 'notify-attributes-supported': ['printer-state-change-time',
                                                                 'notify-lease-expiration-time',
                                                                 'notify-subscriber-user-name'],
                                 'notify-events-default': ['job-completed'],
                                 'notify-events-supported': ['job-completed',
                                                             'job-config-changed',
                                                             'job-created',
                                                             'job-progress',
                                                             'job-state-changed',
                                                             'job-stopped',
                                                             'printer-added',
                                                             'printer-changed',
                                                             'printer-config-changed',
                                                             'printer-deleted',
                                                             'printer-finishings-changed',
                                                             'printer-media-changed',
                                                             'printer-modified',
                                                             'printer-restarted',
                                                             'printer-shutdown',
                                                             'printer-state-changed',
                                                             'printer-stopped',
                                                             'server-audit',
                                                             'server-restarted',
                                                             'server-started',
                                                             'server-stopped'],
                                 'notify-lease-duration-default': 86400,
                                 'notify-lease-duration-supported': (0,
                                                                     2147483647),
                                 'notify-max-events-supported': [100],
                                 'notify-pull-method-supported': ['ippget'],
                                 'notify-schemes-supported': ['dbus',
                                                              'mailto',
                                                              'rss'],
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
                                                          56,
                                                          57,
                                                          59,
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
                                                          16423,
                                                          14],
                                 'orientation-requested-default': None,
                                 'orientation-requested-supported': [3,
                                                                     4,
                                                                     5,
                                                                     6],
                                 'output-bin-default': 'face-down',
                                 'output-bin-supported': ['face-down'],
                                 'page-ranges-supported': True,
                                 'pages-per-minute': 18,
                                 'pdf-k-octets-supported': (0, 15737052),
                                 'pdf-versions-supported': ['adobe-1.2',
                                                            'adobe-1.3',
                                                            'adobe-1.4',
                                                            'adobe-1.5',
                                                            'adobe-1.6',
                                                            'adobe-1.7',
                                                            'iso-19005-1_2005',
                                                            'iso-32000-1_2008',
                                                            'pwg-5102.3'],
                                 'pdl-override-supported': ['attempted'],
                                 'port-monitor': 'none',
                                 'port-monitor-supported': ['none'],
                                 'print-color-mode-default': 'monochrome',
                                 'print-color-mode-supported': ['monochrome'],
                                 'print-quality-default': 4,
                                 'print-quality-supported': [4],
                                 'printer-commands': ['AutoConfigure',
                                                      'Clean',
                                                      'PrintSelfTestPage'],
                                 'printer-config-change-date-time': '(IPP_TAG_DATE)',
                                 'printer-config-change-time': 1489934500,
                                 'printer-current-time': '(IPP_TAG_DATE)',
                                 'printer-dns-sd-name': None,
                                 'printer-error-policy': 'retry-job',
                                 'printer-error-policy-supported': ['abort-job',
                                                                    'retry-current-job',
                                                                    'retry-job',
                                                                    'stop-printer'],
                                 'printer-geo-location': '(unknown IPP value '
                                                         'tag 0x12)',
                                 'printer-get-attributes-supported': ['document-format'],
                                 'printer-icons': 'http://localhost/icons/HLL2360D.png',
                                 'printer-info': 'HLL2360D',
                                 'printer-is-accepting-jobs': True,
                                 'printer-is-shared': False,
                                 'printer-location': '',
                                 'printer-make-and-model': 'Brother HL-L2360D '
                                                           'for CUPS ',
                                 'printer-more-info': 'http://localhost/printers/HLL2360D',
                                 'printer-name': 'HLL2360D',
                                 'printer-op-policy': 'default',
                                 'printer-op-policy-supported': ['authenticated',
                                                                 'default'],
                                 'printer-organization': '',
                                 'printer-organizational-unit': '',
                                 'printer-resolution-default': (300, 300, 3),
                                 'printer-resolution-supported': [(300, 300, 3),
                                                                  (600, 600, 3),
                                                                  (2400,
                                                                   600,
                                                                   3)],
                                 'printer-settable-attributes-supported': ['printer-geo-location',
                                                                           'printer-info',
                                                                           'printer-location',
                                                                           'printer-organization',
                                                                           'printer-organizational-unit'],
                                 'printer-state': 3,
                                 'printer-state-change-date-time': '(IPP_TAG_DATE)',
                                 'printer-state-change-time': 1489905221,
                                 'printer-state-message': '',
                                 'printer-state-reasons': ['none'],
                                 'printer-type': 10522644,
                                 'printer-up-time': 1489934530,
                                 'printer-uri-supported': ['ipp://localhost/printers/HLL2360D'],
                                 'printer-uuid': 'urn:uuid:458f8b8b-66d7-39b6-5333-506f46f1b538',
                                 'pwg-raster-document-resolution-supported': [(300,
                                                                               300,
                                                                               3),
                                                                              (600,
                                                                               600,
                                                                               3),
                                                                              (2400,
                                                                               600,
                                                                               3)],
                                 'pwg-raster-document-sheet-back': 'normal',
                                 'pwg-raster-document-type-supported': ['adobergb-8',
                                                                        'adobergb-16',
                                                                        'black-1',
                                                                        'black-8',
                                                                        'black-16',
                                                                        'cmyk-8',
                                                                        'cmyk-16',
                                                                        'rgb-8',
                                                                        'rgb-16',
                                                                        'sgray-1',
                                                                        'sgray-8',
                                                                        'sgray-16',
                                                                        'srgb-8',
                                                                        'srgb-16'],
                                 'queued-job-count': 0,
                                 'server-is-sharing-printers': False,
                                 'sides-default': 'two-sided-long-edge',
                                 'sides-supported': ['one-sided',
                                                     'two-sided-long-edge',
                                                     'two-sided-short-edge'],
                                 'uri-authentication-supported': ['requesting-user-name'],
                                 'uri-security-supported': ['none'],
                                 'which-jobs-supported': ['completed',
                                                          'not-completed',
                                                          'aborted',
                                                          'all',
                                                          'canceled',
                                                          'pending',
                                                          'pending-held',
                                                          'processing',
                                                          'processing-stopped']}}
Page 4 (<troubleshoot.CheckPPDSanity.CheckPPDSanity object at 0x7fa9d3f7eb00>):
{'cups_printer_ppd_defaults': {'General': {'BrMediaType': 'PLAIN',
                                           'Duplex': 'DuplexNoTumble',
                                           'InputSlot': 'TRAY1',
                                           'PageRegion': 'A4',
                                           'PageSize': 'A4',
                                           'Resolution': '300dpi',
                                           'Sleep': 'PrinterDefault',
                                           'TonerSaveMode': 'ON'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (<troubleshoot.LocalOrRemote.LocalOrRemote object at 0x7fa9d3f7e320>):
{'printer_is_remote': False}
Page 6 (<troubleshoot.PrintTestPage.PrintTestPage object at 0x7fa9d3f88a58>):
{'test_page_attempted': '20/Mar/2017:01:13:07 +1030',
 'test_page_completions': [(29, 'Job completed.')],
 'test_page_job_id': [29],
 'test_page_job_status': [(True,
                           29,
                           'HLL2360D',
                           'Test Page',
                           'Completed',
                           {'attributes-charset': 'utf-8',
                            'attributes-natural-language': 'en-au',
                            'date-time-at-completed': '(IPP_TAG_DATE)',
                            'date-time-at-creation': '(IPP_TAG_DATE)',
                            'date-time-at-processing': '(IPP_TAG_DATE)',
                            'document-format': 'application/vnd.cups-pdf-banner',
                            'document-format-detected': 'application/vnd.cups-pdf-banner',
                            'job-hold-until': 'no-hold',
                            'job-id': 29,
                            'job-impressions-completed': 0,
                            'job-k-octets': 1,
                            'job-media-progress': 0,
                            'job-media-sheets-completed': 0,
                            'job-more-info': 'http://localhost/jobs/29',
                            'job-preserved': False,
                            'job-printer-state-message': '',
                            'job-printer-state-reasons': ['none'],
                            'job-printer-up-time': 1489934714,
                            'job-printer-uri': 'ipp://localhost/printers/HLL2360D',
                            'job-priority': 50,
                            'job-sheets': ['none', 'none'],
                            'job-state': 9,
                            'job-state-reasons': 'processing-to-stop-point',
                            'job-uri': 'ipp://localhost/jobs/29',
                            'job-uuid': 'urn:uuid:a37d0270-32b8-3d50-611f-6b25b52603e4',
                            'number-of-documents': 0,
                            'printer-uri': 'ipp://localhost/printers/HLL2360D',
                            'time-at-completed': 1489934597,
                            'time-at-creation': 1489934587,
                            'time-at-processing': 1489934587})],
 'test_page_successful': True}
Page 7 (<troubleshoot.PrinterStateReasons.PrinterStateReasons object at 0x7fa9d37ddc50>):
{'printer-state-message': 'Waiting for printer to finish.',
 'printer-state-reasons': ['none']}
Page 8 (<troubleshoot.Locale.Locale object at 0x7fa9d37dd9b0>):
{'printer_page_size': 'A4',
 'system_locale_lang': None,
 'user_locale_ctype': 'en_AU',
 'user_locale_messages': 'en_AU'}

```

The IP address it gave was correct. I'll have a look at this and see if I spot anything. Yell out if there's anything obvious (cos I won't see it!).

There is a lot of superfluous stuff in the middle to me, but maybe not to someone who knows about these things, so I left it there. The meaty bits appear to be at the beginning and end, particularly the last bit where it says:

```
Page 7 (<troubleshoot.PrinterStateReasons.PrinterStateReasons object at 0x7fa9d37ddc50>):
{'printer-state-message': 'Waiting for printer to finish.',
 '**printer-state-reasons': ['none']**}
```

Not sure the printer config troubleshooter is going to get us far. :-k

---

### Post by Bucky Ball on 2017-03-19
** Further update: I thought, on a whim, that I would try printing a test page from the printer config GUI while that message was still showing: 'Idle - waiting for the printer to finish.' This time, it changed to 'Connecting to printer' immediately and proceeded to print. A message popped up on the desktop telling me the document had been printed and the message in the GUI went directly back to 'Idle - waiting for printer to finish.'! 

In this case, it is not a deal breaker as the device will print whenever required, despite the screwy message, but why the message? That is a strange anomaly and even the troubleshooter agrees. ;)

---

### Post by SeijiSensei on 2017-03-19
I see the same behavior printing to my HL-3170CDW as well.  I'll see the "waiting to finish" message if I open CUPS with a browser ([http://localhost:631/](http://localhost:631/)), but I can still print another document.  I'd guess its a bug in the printer driver, but I've learned to ignore it.

---

### Post by Bucky Ball on 2017-03-19
> **SeijiSensei said:**
> I'd guess its a bug in the printer driver, but I've learned to ignore it.

At this point, I'll go along with that. I can live with it. Maybe I'll check for a bug report about it later, maybe not, but for now, thanks for the input and let's consider it 'resolved' rather than solved. :)

---

### Post by WEKurtz on 2017-07-09
This has also been bothering me for a while, but I just did a little digging and found the following:

I think what's going on here is that there's a difference between the queue and the printer.
The queue is idle, but the printer hasn't yet finished printing or closed the network connection.

```
if (waiteof)
  {
   /*
    * Shutdown the socket and wait for the other end to finish...
    */

    _cupsLangPrintFilter(stderr, "INFO", _("Waiting for printer to finish."));
    shutdown(device_fd, 1);
    while (wait_bc(device_fd, **90**) > 0);
  }
```

and

```
/*
 * 'wait_bc()' - Wait for back-channel data...
 */

static ssize_t				/* O - # bytes read or -1 on error */
wait_bc(int device_fd,			/* I - Socket */
        int secs)			**/* I - Seconds to wait */**

```

That's the only non-localisation code that has the string "Waiting for printer to finish." in it so that has to be where the status is being generated, and the "wait_bc" part is saying to wait 90seconds.
[Here's a link.]("https://github.com/apple/cups/blob/release-2.1.3/backend/socket.c")

---

### Post by kurt18947 on 2017-07-10
I've seen that message since I can remember but have always been able to print in spite of it.

---

