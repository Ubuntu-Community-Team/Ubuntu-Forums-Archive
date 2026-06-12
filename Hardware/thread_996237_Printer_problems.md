---
title: "Printer problems"
date: 2008-11-28
forum: Hardware
---

### Post by Rodhill on 2008-11-28
I have an HP Deskjet 845 printer used in Ubuntu 8.10. When I tried to print an EMail it just kept running through all the paper printing gobbledygook on the top of each page. I can't stop the thing unless I take out the paper and disconnect it.As soon as I put some paper back in it, it starts again doing the same thing.can anyone advise?
I have just done a diagnostics on it and this is the report

Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest DESKJET-845C (default)>,
 'cups_instance': None,
 'cups_queue': 'DESKJET-845C',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'hp',
 'cups_printer_dict': {'device-uri': u'hp:/usb/DeskJet_845C?serial=CN23C1P12KSX',
                       'printer-info': u'HEWLETT-PACKARD DESKJET 845C',
                       'printer-is-shared': True,
                       'printer-location': u'rod-desktop',
                       'printer-make-and-model': u'HP DeskJet 845C Foomatic/cdj670',
                       'printer-state': 4,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'media-empty-error'],
                       'printer-type': 143372,
                       'printer-uri-supported': u'ipp://localhost:631/printers/DESKJET-845C'},
 'cups_printer_remote': False,
 'hplip_output': (['',
                   '\x1b[01mHP Linux Imaging and Printing System (ver. 2.8.7)\x1b[0m',
                   '\x1b[01mSystem Tray Status Service ver. 0.1\x1b[0m',
                   '',
                   'Copyright (c) 2001-8 Hewlett-Packard Development Company, LP',
                   'This software comes with ABSOLUTELY NO WARRANTY.',
                   'This is free software, and you are welcome to distribute it',
                   'under certain conditions. See COPYING file for more details.',
                   '',
                   '',
                   '\x1b[01mHP Linux Imaging and Printing System (ver. 2.8.7)\x1b[0m',
                   '\x1b[01mDevice Information Utility ver. 4.1\x1b[0m',
                   '',
                   'Copyright (c) 2001-8 Hewlett-Packard Development Company, LP',
                   'This software comes with ABSOLUTELY NO WARRANTY.',
                   'This is free software, and you are welcome to distribute it',
                   'under certain conditions. See COPYING file for more details.',
                   '',
                   '',
                   '\x1b[01mhp:/usb/DeskJet_845C?serial=CN23C1P12KSX\x1b[0m',
                   '',
                   '\x1b[01mDevice Parameters (dynamic data):\x1b[0m',
                   '\x1b[01m  Parameter                     Value(s)                                                  \x1b[0m',
                   '  ----------------------------  ----------------------------------------------------------',
                   '  back-end                      hp                                                        ',
                   '  cups-printer                  DESKJET-845C                                              ',
                   '  cups-uri                      hp:/usb/DeskJet_845C?serial=CN23C1P12KSX                  ',
                   '  dev-file                                                                                ',
                   '  device-state                  -1                                                        ',
                   '  device-uri                    hp:/usb/DeskJet_845C?serial=CN23C1P12KSX                  ',
                   '  deviceid                                                                                ',
                   '  error-state                   101                                                       ',
                   '  host                                                                                    ',
                   '  is-hp                         True                                                      ',
                   '  panel                         0                                                         ',
                   '  panel-line1                                                                             ',
                   '  panel-line2                                                                             ',
                   '  port                          1                                                         ',
                   '  serial                        CN23C1P12KSX                                              ',
                   '  status-code                   5002                                                      ',
                   '  status-desc                                                                             ',
                   '\x1b[01m',
                   'Model Parameters (static data):\x1b[0m',
                   '\x1b[01m  Parameter                     Value(s)                                                  \x1b[0m',
                   '  ----------------------------  ----------------------------------------------------------',
                   '  align-type                    2                                                         ',
                   '  clean-type                    1                                                         ',
                   '  color-cal-type                0                                                         ',
                   '  copy-type                     0                                                         ',
                   '  embedded-server-type          0                                                         ',
                   '  fax-type                      0                                                         ',
                   '  fw-download                   0                                                         ',
                   '  icon                          DESKJET_840C.png                                          ',
                   '  io-mfp-mode                   6                                                         ',
                   '  io-mode                       1                                                         ',
                   '  io-support                    2                                                         ',
                   '  job-storage                   0                                                         ',
                   '  linefeed-cal-type             0                                                         ',
                   '  model                         DeskJet_845C                                              ',
                   '  model-ui                      HP Deskjet 845c                                           ',
                   '  model1                        Deskjet 845c                                              ',
                   '  model2                        Deskjet 845cvr                                            ',
                   '  panel-check-type              0                                                         ',
                   '  pcard-type                    0                                                         ',
                   '  plugin                        0                                                         ',
                   '  power-settings                0                                                         ',
                   '  pq-diag-type                  0                                                         ',
                   '  r-type                        0                                                         ',
                   '  r0-agent1-kind                3                                                         ',
                   '  r0-agent1-sku                 15 (C6615DN)                                              ',
                   '  r0-agent1-type                1                                                         ',
                   '  r0-agent2-kind                3                                                         ',
                   '  r0-agent2-sku                 17 (C6625AN)                                              ',
                   '  r0-agent2-type                2                                                         ',
                   '  scan-style                    0                                                         ',
                   '  scan-type                     0                                                         ',
                   '  status-battery-check          0                                                         ',
                   '  status-dynamic-counters       0                                                         ',
                   '  status-type                   1                                                         ',
                   '  support-released              1                                                         ',
                   '  support-type                  2                                                         ',
                   '  support-ver                   0.9.5                                                     ',
                   "  tech-class                    ['DJ8x5']                                                 ",
                   "  tech-subclass                 ['Normal']                                                ",
                   '  tech-type                     2                                                         ',
                   '  usb-pid                       0904                                                      ',
                   '  usb-vid                       03f0                                                      ',
                   '',
                   'Done.',
                   ''],
                  ['\x1b[31;01merror: Device busy: hp:/usb/DeskJet_845C?serial=CN23C1P12KSX\x1b[0m',
                   '\x1b[31;01merror: Error opening device (Device not found).\x1b[0m',
                   '']),
 'is_cups_class': False}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'Adjustment': {u'GammaBlack': u'0.0',
                                               u'GammaCyan': u'0.0',
                                               u'GammaGeneral': u'1.0',
                                               u'GammaMagenta': u'0.0',
                                               u'GammaYellow': u'0.0'},
                               u'General': {u'MediaType': u'plain',
                                            u'PageRegion': u'A4',
                                            u'PageSize': u'A4',
                                            u'Quality': u'normal',
                                            u'RET': u'on'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Choose device):
{'cups_device_dict': {'device-class': u'direct',
                      'device-id': u'MFG:HP;MDL:DeskJet 845C;CLS:PRINTER;DES:DeskJet 845C;SN:CN23C1P12KSX;',
                      'device-info': u'HP DeskJet 845C USB CN23C1P12KSX HPLIP',
                      'device-make-and-model': u'HP DeskJet 845C'}}
Page 7 (Printer state reasons):
{'printer-state-message': u'', 'printer-state-reasons': [u'media-empty-error']}
Page 8 (Error log checkpoint):
{'cups_server_settings': {'DefaultAuthType': 'Basic',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '0',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '0',
                          '_share_printers': '0',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 603L}
Page 9 (Print test page):
{'test_page_attempted': True,
 'test_page_job_id': [8],
 'test_page_job_status': [(False,
                           5,
                           'DESKJET-845C',
                           'evolution job #1',
                           'Cancelled',
                           None),
                          (False,
                           6,
                           'DESKJET-845C',
                           'Test Page',
                           'Cancelled',
                           None),
                          (False,
                           7,
                           'DESKJET-845C',
                           'Test Page',
                           'Cancelled',
                           None),
                          (True,
                           8,
                           'DESKJET-845C',
                           'Test Page',
                           'Processing',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-gb',
                            'document-format': u'application/postscript',
                            'job-hold-until': u'no-hold',
                            'job-id': 8,
                            'job-k-octets': 17,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/8',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'rod',
                            'job-printer-state-message': u'',
                            'job-printer-state-reasons': [u'none'],
                            'job-printer-up-time': 1227910085,
                            'job-printer-uri': u'ipp://rod-desktop:631/printers/DESKJET-845C',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 5,
                            'job-state-reasons': u'job-printing',
                            'job-uri': u'ipp://localhost:631/jobs/8',
                            'job-uuid': u'urn:uuid:2a8c761d-55bb-3cc9-72d2-54dc9f29933d',
                            'printer-uri': u'ipp://localhost/printers/DESKJET-845C',
                            'time-at-completed': None,
                            'time-at-creation': 1227910078,
                            'time-at-processing': 1227910078})],
 'test_page_jobs_cancelled': True,
 'test_page_successful': False}
Page 10 (Error log fetch):
{'error_log': ['E [28/Nov/2008:22:07:51 +0000] PID 7023 (/usr/lib/cups/filter/pstopdf) stopped with status 1!',
               'E [28/Nov/2008:22:07:51 +0000] PID 7031 (/usr/lib/cups/filter/pstopdf) stopped with status 1!']}

Anyone can help?

---

### Post by Rodhill on 2008-11-30
Problem is sorted!:) I changed the driver from foo to cups and it worked.

---

### Post by sjv123 on 2008-11-30
I have a similar problem, but I dont know how to change from "foo to cups". Or what that is exactly.

---

### Post by sjv123 on 2008-12-01
Problem solved, I just used synaptic to remove "foo" printing references and installed "cups".

I then deleted the previously installed printer, un-plugged the usb cable then restarted the computer, plugged in the printer cable and it worked. :)

Thanks to Rodhill for the post.

---

