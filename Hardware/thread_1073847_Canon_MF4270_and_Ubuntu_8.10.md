---
title: "Canon MF4270 and Ubuntu 8.10"
date: 2009-02-18
forum: Hardware
---

### Post by onthenarrowpath on 2009-02-18
My problem is the following:

I'm running Ubuntu 8.10 and I would like to run the MF4270 properly with it. However, I couldn't manage it for nearly two weeks now. I can print PDF, but only some pages, afterwards, the printer just doesn't react anymore (except for some beeping) and CUPS keeps telling me everything is allright. I can still print test pages, however. 

Anyone any idea? I followed the instructions at the openprinting page carefully, but still: No go... :(

Thanx.

---

### Post by veloce on 2009-02-24
> **onthenarrowpath said:**
> My problem is the following:

I'm running Ubuntu 8.10 and I would like to run the MF4270 properly with it. However, I couldn't manage it for nearly two weeks now. I can print PDF, but only some pages, afterwards, the printer just doesn't react anymore (except for some beeping) and CUPS keeps telling me everything is allright. I can still print test pages, however. 

Anyone any idea? I followed the instructions at the openprinting page carefully, but still: No go... :(

Thanx.

Is there a driver on the Canon site?  If so, use that.  They work pretty well.

---

### Post by onthenarrowpath on 2009-02-26
Thanks for the hint, but my driver comes from Canon, and it refuses to print jobs exceeding 10 pages nonetheless...
I guess it's a problem on cups side, but I'm not sure.

---

### Post by veloce on 2009-02-26
> **onthenarrowpath said:**
> Thanks for the hint, but my driver comes from Canon, and it refuses to print jobs exceeding 10 pages nonetheless...
I guess it's a problem on cups side, but I'm not sure.

Yeah, that is bizarre.  Probably not helpful in the short term but I'd suggest you try to report the bug to Canon.  They are active in upgrading their drivers so may eventually fix your issue.

---

### Post by veloce on 2009-02-26
[Sorry - double posted]

---

### Post by onthenarrowpath on 2009-03-10
I will do that, probably. If only for all those desperate mf 4270 users out there ;-).

Thanks

---

### Post by alexcuervo on 2009-04-24
For 64bit users there is a good guide here
For the printer part
[http://queleimporta.com/installing-canon-imageclass-mf4270-on-ubuntu-64-bit/]("http://queleimporta.com/installing-canon-imageclass-mf4270-on-ubuntu-64-bit/")

For the scanner part:
[http://queleimporta.com/installing-canons-imageclass-mf4270-scanner-on-ubuntu-64-bit/]("http://queleimporta.com/installing-canons-imageclass-mf4270-scanner-on-ubuntu-64-bit/")

---

### Post by Francewhoa on 2009-04-27
Click here for [*HOWTO: Install Canon ImageCLASS MF4270 Multifunction driver.*]("http://ubuntuforums.org/showthread.php?t=1140724")

---

### Post by onthenarrowpath on 2009-06-04
Thanks for your suggestion, alexcuervo, but unfortunately, I've got a 32 bit architekture.

Onopoc, I followed your instructions carefully, but the main problems remain (I have just updated to 9.04):

Some pdfs don't print at all (even if ubuntu tells me everything is ok), it seems like the data gets lost on the way. Could it be the wrong uri?
When I follow your procedure, i get:
tpu://Canon/MF4200_Series

The report I've run using the ubuntu printing manager (sorry for the scrolling):

Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest Canon-MF4200-UFRII-LT (default)>,
 'cups_instance': None,
 'cups_queue': 'Canon-MF4200-UFRII-LT',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'tpu',
 'cups_printer_dict': {'device-uri': u'tpu://Canon/MF4200_Series',
                       'printer-info': u'Canon Image Class ratteri',
                       'printer-is-shared': True,
                       'printer-location': u'Retos-AAO',
                       'printer-make-and-model': u'Canon MF4200 Series UFRII LT ver.1.8',
                       'printer-state': 4,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 136340,
                       'printer-uri-supported': u'ipp://localhost:631/printers/Canon-MF4200-UFRII-LT'},
 'cups_printer_remote': False,
 'is_cups_class': False}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'BindEdge': u'Left',
                                            u'CNHalftone': u'Gradation',
                                            u'CNImageRefinement': u'None',
                                            u'CNSpecialPrintMode': u'Mode1',
                                            u'CNTonerSaving': u'Auto',
                                            u'Collate': u'False',
                                            u'Duplex': u'None',
                                            u'InputSlot': u'Auto',
                                            u'MediaType': u'Auto',
                                            u'OutputBin': u'Auto',
                                            u'PageRegion': u'A4',
                                            u'PageSize': u'A4',
                                            u'Resolution': u'600'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Error log checkpoint):
{'cups_server_settings': {'DefaultAuthType': 'Basic',
                          'MaxLogSize': '2000000',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '0',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '0',
                          '_share_printers': '0',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 86755L,
 'error_log_debug_logging_set': True}
Page 7 (Print test page):
{'test_page_job_status': [(True,
                           494,
                           'Canon-MF4200-UFRII-LT',
                           '17_02_2009_nietzsche_Nihilismus.pdf',
                           'Ausf\xc3\xbchrend',
                           {'BindEdge': u'Left',
                            'CNHalftone': u'Gradation',
                            'CNImageRefinement': u'None',
                            'CNSpecialPrintMode': u'Mode1',
                            'CNTonerSaving': u'Auto',
                            'Duplex': u'DuplexNoTumble',
                            'InputSlot': u'Auto',
                            'MediaType': u'Auto',
                            'OutputBin': u'Auto',
                            'PageSize': u'A4',
                            'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'de-ch',
                            'document-format': u'application/postscript',
                            'job-hold-until': u'no-hold',
                            'job-id': 494,
                            'job-k-octets': 1592,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/494',
                            'job-name': u'17_02_2009_nietzsche_Nihilismus.pdf',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'reto',
                            'job-printer-up-time': 1244131784,
                            'job-printer-uri': u'ipp://Retos-AAO:631/printers/Canon-MF4200-UFRII-LT',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 5,
                            'job-state-reasons': u'job-printing',
                            'job-uri': u'ipp://localhost:631/jobs/494',
                            'job-uuid': u'urn:uuid:82348e88-c4bb-31c7-7620-2fd65dc17968',
                            'number-up': 1,
                            'printer-uri': u'ipp://localhost:631/printers/Canon-MF4200-UFRII-LT',
                            'time-at-completed': None,
                            'time-at-creation': 1244131680,
                            'time-at-processing': 1244131680})],
 'test_page_successful': False}
Page 8 (Error log fetch):
{'error_log': ['D [04/Jun/2009:18:09:22 +0200] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [04/Jun/2009:18:09:22 +0200] cupsdAuthorize: No authentication data provided.',
               'D [04/Jun/2009:18:09:22 +0200] Get-Jobs ipp://localhost/printers/',
               'D [04/Jun/2009:18:09:22 +0200] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [04/Jun/2009:18:09:22 +0200] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [04/Jun/2009:18:09:22 +0200] cupsdAuthorize: No authentication data provided.',
               'D [04/Jun/2009:18:09:22 +0200] Get-Jobs ipp://localhost/printers/',
               'D [04/Jun/2009:18:09:22 +0200] [Job 474] Loading attributes...',
               'D [04/Jun/2009:18:09:22 +0200] [Job 475] Loading attributes...',
               'D [04/Jun/2009:18:09:22 +0200] [Job 476] Loading attributes...',
               'D [04/Jun/2009:18:09:22 +0200] [Job 477] Loading attributes...',
               'D [04/Jun/2009:18:09:22 +0200] [Job 478] Loading attributes...',
               'D [04/Jun/2009:18:09:22 +0200] [Job 479] Loading attributes...',
               'D [04/Jun/2009:18:09:22 +0200] [Job 480] Loading attributes...',
               'D [04/Jun/2009:18:09:22 +0200] [Job 481] Loading attributes...',
               'D [04/Jun/2009:18:09:22 +0200] [Job 482] Loading attributes...',
               'D [04/Jun/2009:18:09:22 +0200] [Job 483] Loading attributes...',
               'D [04/Jun/2009:18:09:22 +0200] [Job 484] Loading attributes...',
               'D [04/Jun/2009:18:09:22 +0200] [Job 485] Loading attributes...',
               'D [04/Jun/2009:18:09:22 +0200] [Job 486] Loading attributes...',
               'D [04/Jun/2009:18:09:22 +0200] [Job 487] Loading attributes...',
               'D [04/Jun/2009:18:09:22 +0200] [Job 488] Loading attributes...',
               'D [04/Jun/2009:18:09:22 +0200] [Job 489] Loading attributes...',
               'D [04/Jun/2009:18:09:22 +0200] [Job 490] Loading attributes...',
               'D [04/Jun/2009:18:09:22 +0200] [Job 491] Loading attributes...',
               'D [04/Jun/2009:18:09:22 +0200] [Job 493] Loading attributes...',
               'D [04/Jun/2009:18:09:22 +0200] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [04/Jun/2009:18:09:22 +0200] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [04/Jun/2009:18:09:22 +0200] cupsdAuthorize: No authentication data provided.',
               'D [04/Jun/2009:18:09:22 +0200] Create-Printer-Subscription /',
               'D [04/Jun/2009:18:09:22 +0200] cupsdCreateSubscription(con=0xb96f7300(8), uri="/")',
               'D [04/Jun/2009:18:09:22 +0200] pullmethod="ippget"',
               'D [04/Jun/2009:18:09:22 +0200] notify-lease-duration=86400',
               'D [04/Jun/2009:18:09:22 +0200] notify-time-interval=0',
               'D [04/Jun/2009:18:09:22 +0200] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [04/Jun/2009:18:09:22 +0200] Added subscription 261 for server',
               'I [04/Jun/2009:18:09:22 +0200] Saving subscriptions.conf...',
               'D [04/Jun/2009:18:09:22 +0200] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [04/Jun/2009:18:09:23 +0200] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [04/Jun/2009:18:09:23 +0200] cupsdAuthorize: No authentication data provided.',
               'D [04/Jun/2009:18:09:23 +0200] Get-Notifications /',
               'D [04/Jun/2009:18:09:23 +0200] cupsdIsAuthorized: requesting-user-name="reto"',
               'D [04/Jun/2009:18:09:23 +0200] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [04/Jun/2009:18:09:44 +0200] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [04/Jun/2009:18:09:44 +0200] cupsdAuthorize: No authentication data provided.',
               'D [04/Jun/2009:18:09:44 +0200] Get-Job-Attributes ipp://localhost/jobs/494',
               'D [04/Jun/2009:18:09:44 +0200] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [04/Jun/2009:18:09:44 +0200] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [04/Jun/2009:18:09:44 +0200] cupsdAuthorize: No authentication data provided.',
               'D [04/Jun/2009:18:09:44 +0200] Cancel-Subscription /',
               'D [04/Jun/2009:18:09:44 +0200] cupsdIsAuthorized: requesting-user-name="reto"',
               'I [04/Jun/2009:18:09:44 +0200] Saving subscriptions.conf...',
               'D [04/Jun/2009:18:09:44 +0200] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [04/Jun/2009:18:09:44 +0200] cupsdAcceptClient: 9 from localhost (Domain)',
               'D [04/Jun/2009:18:09:44 +0200] cupsdReadClient: 9 GET /admin/log/error_log HTTP/1.1',
               'D [04/Jun/2009:18:09:44 +0200] cupsdAuthorize: No authentication data provided.'],
 'error_log_debug_logging_unset': True}
Page 9 (Locale issues):
{'job_page_size': u'A4',
 'printer_page_size': u'A4',
 'system_locale_lang': None,
 'user_locale_ctype': 'de_CH',
 'user_locale_messages': 'de_CH'}

---

