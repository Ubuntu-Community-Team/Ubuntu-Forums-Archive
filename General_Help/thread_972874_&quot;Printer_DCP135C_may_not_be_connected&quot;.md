---
title: "&quot;Printer DCP135C may not be connected&quot;"
date: 2008-11-06
forum: General Help
---

### Post by mherrin on 2008-11-06
I may have posted about this before, and I've searched around for a solution but whilst I have found similar questions, there has been no solution that I can find...

[LIST]
[*]I have a Brother DCP-135C printer / scanner connected to my workstation via USB.
[*]It has been detected by CUPS, & I can manage it with utils & [http://127.0.0.1:631/](http://127.0.0.1:631/)
[*]I send print jobs to it, and get the feedback "Printer DCP135C may not be connected"
[/LIST]
What I have tried so far to try & resolve this issue:-
[LIST]
[*]connecting it to other USB ports = no luck
[*]connected it to other machines (Windows) = works fine
[*]completely removing all traces of CUPS via Synaptic (along with all Brother Drivers)
[*]I tried this :"http://ubuntuforums.org/showthread.php?t=590793&highlight=brother+scanner+howto"
[/LIST]

Nothing gives me a printout.
The printer did work when I tried it on Gutsy the very 1st time I tried Ubuntu.

lsusb gives me:
```
Bus 002 Device 004: ID 04f9:01ce Brother Industries, Ltd DCP-135C
Bus 002 Device 003: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 002 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

[http://127.0.0.1:631/](http://127.0.0.1:631/) "Manage Printers"
```
DCP135C "No %%Pages: comment in header!"
Description: DCP135C
Location: Home
Printer Driver: Brother DCP-135C CUPS v1.1
Printer State: idle, accepting jobs, not published.
Device URI: hal:///org/freedesktop/Hal/devices/usb_device_4f9_1ce_BROE7F477453_if0_printer_noserial 
```
I have gone through the troubleshooter in printing:
Printing troubleshooter
Status Messages
There are status messages associated with this queue.
The printers state message is 'No %%Pages: comment in header!"

(I have done a search on this, but cannot find any references...)

[LIST=1]
[*]Enabled debugging:
[*]Printed a test page (which did not materialise)
[*](printer status comes up 'Held', & releasing it elsewhere makes no difference..goes back to 'Held' in a bit)
[*]Diable Debugging:
[/LIST]
**Error log messages**
There are messages in the error log.

Following is the Diagnostic Output (Advanced) [including error log]
```
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest DCP135C>,
 'cups_instance': None,
 'cups_queue': 'DCP135C',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'hal',
 'cups_printer_dict': {'device-uri': u'hal:///org/freedesktop/Hal/devices/usb_device_4f9_1ce_BROE7F477453_if0_printer_noserial',
                       'printer-info': u'DCP135C',
                       'printer-is-shared': False,
                       'printer-location': u'Home',
                       'printer-make-and-model': u'Brother DCP-135C CUPS v1.1',
                       'printer-state': 3,
                       'printer-state-message': u'No %%Pages: comment in header!',
                       'printer-state-reasons': [u'connecting-to-device'],
                       'printer-type': 2101324,
                       'printer-uri-supported': u'ipp://localhost:631/printers/DCP135C'},
 'cups_printer_remote': False,
 'is_cups_class': False}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'Color Enhancement': {u'BRBlue': u'0',
                                                      u'BRBrightness': u'0',
                                                      u'BRColorEnhancement': u'OFF',
                                                      u'BRContrast': u'0',
                                                      u'BRGreen': u'0',
                                                      u'BRRed': u'0'},
                               u'General': {u'BRBiDir': u'ON',
                                            u'BRColorMediaType': u'Plain',
                                            u'BRColorPaperThick': u'Regular',
                                            u'BRMonoColor': u'BrColor',
                                            u'BRSlowDrying': u'OFF',

                                            u'MirrorPrint': u'OFF',
                                            u'PageRegion': u'A4',
                                            u'PageSize': u'A4',
                                            u'Resolution': u'Fast'},
                               u'Image Type': {u'BRColorMatching': u'Natural',
                                               u'BRDocument': u'Photo',
                                               u'BRHalfTonePattern': u'Diffusion'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Choose device):
{'cups_device_dict': {'device-class': u'direct',
                      'device-id': u'MFG:Brother;MDL:DCP-135C;CLS:PRINTER;',
                      'device-info': u'Brother DCP-135C',
                      'device-make-and-model': u'Brother DCP-135C'}}
Page 7 (Printer state reasons):
{'printer-state-message': u'No %%Pages: comment in header!',
 'printer-state-reasons': [u'connecting-to-device']}
Page 8 (Error log checkpoint):
{'cups_server_settings': {'DefaultAuthType': 'Basic',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '0',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '0',
                          '_share_printers': '0',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 7126,
 'error_log_debug_logging_set': True}
Page 9 (Print test page):
{'test_page_attempted': True,
 'test_page_job_id': [9],
 'test_page_job_status': [(True,
                           9,
                           'DCP135C',
                           'Test Page',
                           'Held',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-gb',
                            'document-format': u'application/postscript',
                            'job-hold-until': u'11:10:15',
                            'job-id': 9,
                            'job-k-octets': 17,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/9',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'mikeh',
                            'job-printer-state-message': u'No %%Pages: comment in header!',
                            'job-printer-state-reasons': [u'connecting-to-device'],
                            'job-printer-up-time': 1225969576,
                            'job-printer-uri': u'ipp://workstation:631/printers/DCP135C',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 4,
                            'job-state-reasons': u'job-hold-until-specified',
                            'job-uri': u'ipp://localhost:631/jobs/9',
                            'job-uuid': u'urn:uuid:40b6b368-bb48-388a-5bbb-5c593f8e733e',
                            'printer-uri': u'ipp://localhost/printers/DCP135C',
                            'time-at-completed': None,
                            'time-at-creation': 1225969459,
                            'time-at-processing': 1225969510})],
 'test_page_successful': False}
Page 10 (Error log fetch):
{'error_log': ['D [06/Nov/2008:11:04:15 +0000] cupsdCloseClient: 7',
               'D [06/Nov/2008:11:04:15 +0000] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [06/Nov/2008:11:04:15 +0000] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [06/Nov/2008:11:04:15 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:04:15 +0000] Get-Jobs ipp://localhost/jobs/',
               'D [06/Nov/2008:11:04:15 +0000] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:04:15 +0000] cupsdCloseClient: 7',
               'D [06/Nov/2008:11:04:15 +0000] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [06/Nov/2008:11:04:15 +0000] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [06/Nov/2008:11:04:15 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:04:15 +0000] Create-Printer-Subscription /',
               'D [06/Nov/2008:11:04:15 +0000] cupsdCreateSubscription(con=0x7fc510cceec0(7), uri="/")',
               'D [06/Nov/2008:11:04:15 +0000] pullmethod="ippget"',
               'D [06/Nov/2008:11:04:15 +0000] notify-lease-duration=86400',
               'D [06/Nov/2008:11:04:15 +0000] notify-time-interval=0',
               'D [06/Nov/2008:11:04:15 +0000] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [06/Nov/2008:11:04:15 +0000] Added subscription 18 for server',
               'I [06/Nov/2008:11:04:15 +0000] Saving subscriptions.conf...',
               'D [06/Nov/2008:11:04:15 +0000] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:04:15 +0000] cupsdCloseClient: 7',
               'D [06/Nov/2008:11:04:16 +0000] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [06/Nov/2008:11:04:16 +0000] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [06/Nov/2008:11:04:16 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:04:16 +0000] Get-Notifications /',
               'D [06/Nov/2008:11:04:16 +0000] cupsdIsAuthorized: requesting-user-name="mikeh"',
               'D [06/Nov/2008:11:04:16 +0000] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:04:16 +0000] cupsdCloseClient: 7',
               'D [06/Nov/2008:11:04:19 +0000] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [06/Nov/2008:11:04:19 +0000] cupsdReadClient: 7 POST /printers/DCP135C HTTP/1.1',
               'D [06/Nov/2008:11:04:19 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:04:19 +0000] Print-Job ipp://localhost/printers/DCP135C',
               'D [06/Nov/2008:11:04:19 +0000] add_job: requesting-user-name="mikeh"',
               'D [06/Nov/2008:11:04:19 +0000] Adding default job-sheets values "none,none"...',
               'I [06/Nov/2008:11:04:19 +0000] [Job 9] Adding start banner page "none".',
               'I [06/Nov/2008:11:04:19 +0000] Saving subscriptions.conf...',
               'I [06/Nov/2008:11:04:19 +0000] [Job 9] Adding end banner page "none".',
               'I [06/Nov/2008:11:04:19 +0000] [Job 9] File of type application/postscript queued by "mikeh".',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] hold_until=0',
               'I [06/Nov/2008:11:04:19 +0000] [Job 9] Queued on "DCP135C" by "mikeh".',
               'I [06/Nov/2008:11:04:19 +0000] Saving subscriptions.conf...',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] job-sheets=none,none',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] banner_page = 0',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] argv[0]="DCP135C"',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] argv[1]="9"',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] argv[2]="mikeh"',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] argv[3]="Test Page"',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] argv[4]="1"',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] argv[5]="job-uuid=urn:uuid:40b6b368-bb48-388a-5bbb-5c593f8e733e"',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] argv[6]="/var/spool/cups/d00009-001"',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] envp[9]="SERVER_ADMIN=root@workstation"',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] envp[10]="SOFTWARE=CUPS/1.3.9"',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] envp[11]="TMPDIR=/var/spool/cups/tmp"',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] envp[12]="TZ=Europe/London"',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] envp[13]="USER=root"',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] envp[15]="CUPS_ENCRYPTION=IfRequested"',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] envp[16]="IPP_PORT=631"',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] envp[17]="CHARSET=utf-8"',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] envp[18]="LANG=en_GB.UTF8"',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] envp[19]="PPD=/etc/cups/ppd/DCP135C.ppd"',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] envp[20]="RIP_MAX_CACHE=8m"',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] envp[21]="CONTENT_TYPE=application/postscript"',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] envp[22]="DEVICE_URI=hal:///org/freedesktop/Hal/devices/usb_device_4f9_1ce_BROE7F477453_if0_printer_noserial"',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] envp[23]="PRINTER=DCP135C"',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] envp[24]="FINAL_CONTENT_TYPE=printer/DCP135C"',
               'I [06/Nov/2008:11:04:19 +0000] [Job 9] Started filter /usr/lib/cups/filter/pstopdf (PID 10613)',
               'I [06/Nov/2008:11:04:19 +0000] [Job 9] Started filter /usr/lib/cups/filter/pdftopdf (PID 10614)',
               'I [06/Nov/2008:11:04:19 +0000] [Job 9] Started filter /usr/lib/cups/filter/cpdftocps (PID 10615)',
               'I [06/Nov/2008:11:04:19 +0000] [Job 9] Started filter /usr/lib/cups/filter/brlpdwrapperdcp135c (PID 10616)',
               'I [06/Nov/2008:11:04:19 +0000] [Job 9] Started backend /usr/lib/cups/backend/hal (PID 10617)',
               'I [06/Nov/2008:11:04:19 +0000] Saving subscriptions.conf...',
               'D [06/Nov/2008:11:04:19 +0000] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'I [06/Nov/2008:11:04:19 +0000] Saving subscriptions.conf...',
               'D [06/Nov/2008:11:04:19 +0000] cupsdCloseClient: 7',
               'E [06/Nov/2008:11:04:19 +0000] [Job 9] Unable to open device "hal:///org/freedesktop/Hal/devices/usb_device_4f9_1ce_BROE7F477453_if0_printer_noserial": Permission denied',
               'I [06/Nov/2008:11:04:19 +0000] Saving subscriptions.conf...',
               'E [06/Nov/2008:11:04:19 +0000] PID 10617 (/usr/lib/cups/backend/hal) stopped with status 1!',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] pstopdf argv[6] = 9 mikeh Test Page 1 job-uuid=urn:uuid:40b6b368-bb48-388a-5bbb-5c593f8e733e /var/spool/cups/d00009-001',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] pdftops - copying to temp print file "/tmp/4912cf339e3c6"',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] Injecting PostScript: <</.HWMargins[9 9 9 9] /Margins[0 0]>>setpagedevice',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] Page = 595x842; 9,9 to 586,833',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] slow_collate=0, slow_duplex=0, slow_order=1',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] Before copy_comments - %!PS-Adobe-3.0',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] %!PS-Adobe-3.0',
               'E [06/Nov/2008:11:04:19 +0000] [Job 9] No %%BoundingBox: comment in header!',
               'I [06/Nov/2008:11:04:19 +0000] Saving subscriptions.conf...',
               'E [06/Nov/2008:11:04:19 +0000] [Job 9] No %%Pages: comment in header!',
               'I [06/Nov/2008:11:04:19 +0000] Saving subscriptions.conf...',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] Before copy_prolog - <</.HWMargins[9 9 9 9] /Margins[0 0]>>setpagedevice',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] Before copy_setup - %%Page: 1 1',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] Before page loop - %%Page: 1 1',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] Copying page 1...',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] pagew = 577.0, pagel = 824.0',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] bboxx = 0, bboxy = 0, bboxw = 595, bboxl = 842',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] PageLeft = 9.0, PageRight = 586.0',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] PageTop = 833.0, PageBottom = 9.0',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] PageWidth = 595.0, PageLength = 842.0',
               'D [06/Nov/2008:11:04:19 +0000] [Job 9] Wrote 1 pages...',
               'D [06/Nov/2008:11:04:19 +0000] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [06/Nov/2008:11:04:19 +0000] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [06/Nov/2008:11:04:19 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:04:19 +0000] Get-Jobs ipp://localhost/jobs/',
               'D [06/Nov/2008:11:04:19 +0000] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:04:19 +0000] cupsdCloseClient: 7',
               'D [06/Nov/2008:11:04:19 +0000] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [06/Nov/2008:11:04:19 +0000] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [06/Nov/2008:11:04:19 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:04:19 +0000] Get-Notifications /',
               'D [06/Nov/2008:11:04:19 +0000] cupsdIsAuthorized: requesting-user-name="mikeh"',
               'D [06/Nov/2008:11:04:19 +0000] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:04:19 +0000] cupsdAcceptClient: 10 from localhost (Domain)',
               'D [06/Nov/2008:11:04:19 +0000] cupsdReadClient: 10 POST / HTTP/1.1',
               'D [06/Nov/2008:11:04:19 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:04:19 +0000] Get-Notifications /',
               'D [06/Nov/2008:11:04:19 +0000] cupsdIsAuthorized: requesting-user-name="mikeh"',
               'D [06/Nov/2008:11:04:19 +0000] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:04:19 +0000] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [06/Nov/2008:11:04:19 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:04:19 +0000] Get-Job-Attributes ipp://localhost/jobs/9',
               'D [06/Nov/2008:11:04:19 +0000] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:04:19 +0000] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [06/Nov/2008:11:04:19 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [06/Nov/2008:11:04:19 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:04:19 +0000] CUPS-Get-Printers',
               'D [06/Nov/2008:11:04:19 +0000] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:04:19 +0000] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [06/Nov/2008:11:04:19 +0000] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [06/Nov/2008:11:04:19 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:04:19 +0000] Get-Printer-Attributes ipp://workstation:631/printers/DCP135C',
               'D [06/Nov/2008:11:04:19 +0000] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:04:19 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [06/Nov/2008:11:04:19 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:04:19 +0000] CUPS-Get-Classes',
               'D [06/Nov/2008:11:04:19 +0000] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:04:19 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [06/Nov/2008:11:04:19 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:04:19 +0000] CUPS-Get-Default',
               'D [06/Nov/2008:11:04:19 +0000] CUPS-Get-Default client-error-not-found: No default printer',
               'D [06/Nov/2008:11:04:19 +0000] cupsdProcessIPPRequest: 11 status_code=406 (client-error-not-found)',
               'D [06/Nov/2008:11:04:19 +0000] cupsdCloseClient: 12',
               'D [06/Nov/2008:11:04:19 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [06/Nov/2008:11:04:19 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:04:19 +0000] CUPS-Get-Printers',
               'D [06/Nov/2008:11:04:19 +0000] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:04:19 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [06/Nov/2008:11:04:19 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:04:19 +0000] CUPS-Get-Classes',
               'D [06/Nov/2008:11:04:19 +0000] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:04:19 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [06/Nov/2008:11:04:19 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:04:19 +0000] CUPS-Get-Default',
               'D [06/Nov/2008:11:04:19 +0000] CUPS-Get-Default client-error-not-found: No default printer',
               'D [06/Nov/2008:11:04:19 +0000] cupsdProcessIPPRequest: 11 status_code=406 (client-error-not-found)',
               'D [06/Nov/2008:11:04:20 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [06/Nov/2008:11:04:20 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:04:20 +0000] CUPS-Get-Printers',
               'D [06/Nov/2008:11:04:20 +0000] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:04:20 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [06/Nov/2008:11:04:20 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:04:20 +0000] CUPS-Get-Classes',
               'D [06/Nov/2008:11:04:20 +0000] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:04:20 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [06/Nov/2008:11:04:20 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:04:20 +0000] CUPS-Get-Default',
               'D [06/Nov/2008:11:04:20 +0000] CUPS-Get-Default client-error-not-found: No default printer',
               'D [06/Nov/2008:11:04:20 +0000] cupsdProcessIPPRequest: 11 status_code=406 (client-error-not-found)',
               'D [06/Nov/2008:11:04:20 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [06/Nov/2008:11:04:20 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:04:20 +0000] CUPS-Get-Printers',
               'D [06/Nov/2008:11:04:20 +0000] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:04:20 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [06/Nov/2008:11:04:20 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:04:20 +0000] CUPS-Get-Classes',
               'D [06/Nov/2008:11:04:20 +0000] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:04:20 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [06/Nov/2008:11:04:20 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:04:20 +0000] CUPS-Get-Default',
               'D [06/Nov/2008:11:04:20 +0000] CUPS-Get-Default client-error-not-found: No default printer',
               'D [06/Nov/2008:11:04:20 +0000] cupsdProcessIPPRequest: 11 status_code=406 (client-error-not-found)',
               'D [06/Nov/2008:11:04:20 +0000] cupsdCloseClient: 7',
               'D [06/Nov/2008:11:04:20 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [06/Nov/2008:11:04:20 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:04:20 +0000] CUPS-Get-Printers',
               'D [06/Nov/2008:11:04:20 +0000] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:04:20 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [06/Nov/2008:11:04:20 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:04:20 +0000] CUPS-Get-Classes',
               'D [06/Nov/2008:11:04:20 +0000] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:04:20 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [06/Nov/2008:11:04:20 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:04:20 +0000] CUPS-Get-Default',
               'D [06/Nov/2008:11:04:20 +0000] CUPS-Get-Default client-error-not-found: No default printer',
               'D [06/Nov/2008:11:04:20 +0000] cupsdProcessIPPRequest: 11 status_code=406 (client-error-not-found)',
               'D [06/Nov/2008:11:04:20 +0000] cupsdCloseClient: 10',
               'D [06/Nov/2008:11:04:20 +0000] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [06/Nov/2008:11:04:20 +0000] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [06/Nov/2008:11:04:20 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:04:20 +0000] Get-Notifications /',
               'D [06/Nov/2008:11:04:20 +0000] cupsdIsAuthorized: requesting-user-name="mikeh"',
               'D [06/Nov/2008:11:04:20 +0000] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:04:20 +0000] cupsdCloseClient: 7',
               'D [06/Nov/2008:11:04:20 +0000] PID 10613 (/usr/lib/cups/filter/pstopdf) exited with no errors.',
               'D [06/Nov/2008:11:04:20 +0000] PID 10614 (/usr/lib/cups/filter/pdftopdf) exited with no errors.',
               'D [06/Nov/2008:11:04:20 +0000] [Job 9] Page = 595x842; 9,9 to 586,833',
               'D [06/Nov/2008:11:04:20 +0000] [Job 9] slow_collate=0, slow_duplex=0, slow_order=1',
               'D [06/Nov/2008:11:04:20 +0000] [Job 9] Before copy_comments - %!PS-Adobe-3.0',
               'D [06/Nov/2008:11:04:20 +0000] [Job 9] %!PS-Adobe-3.0',
               'D [06/Nov/2008:11:04:20 +0000] [Job 9] %%LanguageLevel: 3',
               'D [06/Nov/2008:11:04:20 +0000] [Job 9] %%DocumentSuppliedResources: (atend)',
               'D [06/Nov/2008:11:04:20 +0000] [Job 9] %%DocumentMedia: plain 595 842 0 () ()',
               'D [06/Nov/2008:11:04:20 +0000] [Job 9] %%BoundingBox: 0 0 595 842',
               'D [06/Nov/2008:11:04:20 +0000] [Job 9] %%Pages: 1',
               'D [06/Nov/2008:11:04:20 +0000] [Job 9] %%EndComments',
               'D [06/Nov/2008:11:04:20 +0000] [Job 9] Before copy_prolog - %%BeginDefaults',
               'D [06/Nov/2008:11:04:20 +0000] [Job 9] Before copy_setup - %%BeginSetup',
               'D [06/Nov/2008:11:04:20 +0000] [Job 9] Before page loop - %%Page: 1 1',
               'D [06/Nov/2008:11:04:20 +0000] [Job 9] Copying page 1...',
               'D [06/Nov/2008:11:04:20 +0000] [Job 9] pagew = 577.0, pagel = 824.0',
               'D [06/Nov/2008:11:04:20 +0000] [Job 9] bboxx = 0, bboxy = 0, bboxw = 595, bboxl = 842',
               'D [06/Nov/2008:11:04:20 +0000] [Job 9] PageLeft = 9.0, PageRight = 586.0',
               'D [06/Nov/2008:11:04:20 +0000] [Job 9] PageTop = 833.0, PageBottom = 9.0',
               'D [06/Nov/2008:11:04:20 +0000] [Job 9] PageWidth = 595.0, PageLength = 842.0',
               'D [06/Nov/2008:11:04:20 +0000] [Job 9] Wrote 1 pages...',
               'D [06/Nov/2008:11:04:20 +0000] PID 10615 (/usr/lib/cups/filter/cpdftocps) exited with no errors.',
               'D [06/Nov/2008:11:04:24 +0000] PID 10616 (/usr/lib/cups/filter/brlpdwrapperdcp135c) exited with no errors.',
               'D [06/Nov/2008:11:04:24 +0000] [Job 9] File 0 is complete.',
               'I [06/Nov/2008:11:04:24 +0000] [Job 9] Backend returned status 1 (failed)',
               'I [06/Nov/2008:11:04:24 +0000] Saving subscriptions.conf...',
               'D [06/Nov/2008:11:04:24 +0000] set_hold_until: hold_until = 1225969764',
               'I [06/Nov/2008:11:04:24 +0000] Saving subscriptions.conf...',
               'D [06/Nov/2008:11:04:24 +0000] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [06/Nov/2008:11:04:24 +0000] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [06/Nov/2008:11:04:24 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:04:24 +0000] Get-Jobs ipp://localhost/jobs/',
               'D [06/Nov/2008:11:04:24 +0000] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:04:24 +0000] cupsdAcceptClient: 10 from localhost (Domain)',
               'D [06/Nov/2008:11:04:24 +0000] cupsdReadClient: 10 POST / HTTP/1.1',
               'D [06/Nov/2008:11:04:24 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:04:24 +0000] Get-Notifications /',
               'D [06/Nov/2008:11:04:24 +0000] cupsdIsAuthorized: requesting-user-name="mikeh"',
               'D [06/Nov/2008:11:04:24 +0000] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:04:24 +0000] cupsdCloseClient: 7',
               'D [06/Nov/2008:11:04:24 +0000] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [06/Nov/2008:11:04:24 +0000] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [06/Nov/2008:11:04:24 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:04:24 +0000] Get-Notifications /',
               'D [06/Nov/2008:11:04:24 +0000] cupsdIsAuthorized: requesting-user-name="mikeh"',
               'D [06/Nov/2008:11:04:24 +0000] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:04:24 +0000] cupsdCloseClient: 7',
               'D [06/Nov/2008:11:04:24 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [06/Nov/2008:11:04:24 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:04:24 +0000] CUPS-Get-Printers',
               'D [06/Nov/2008:11:04:24 +0000] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:04:24 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [06/Nov/2008:11:04:24 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:04:24 +0000] CUPS-Get-Classes',
               'D [06/Nov/2008:11:04:24 +0000] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:04:24 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [06/Nov/2008:11:04:24 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:04:24 +0000] CUPS-Get-Default',
               'D [06/Nov/2008:11:04:24 +0000] CUPS-Get-Default client-error-not-found: No default printer',
               'D [06/Nov/2008:11:04:24 +0000] cupsdProcessIPPRequest: 11 status_code=406 (client-error-not-found)',
               'D [06/Nov/2008:11:04:24 +0000] cupsdCloseClient: 10',
               'D [06/Nov/2008:11:04:24 +0000] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [06/Nov/2008:11:04:24 +0000] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [06/Nov/2008:11:04:24 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:04:24 +0000] Get-Notifications /',
               'D [06/Nov/2008:11:04:24 +0000] cupsdIsAuthorized: requesting-user-name="mikeh"',
               'D [06/Nov/2008:11:04:24 +0000] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:04:24 +0000] cupsdCloseClient: 7',
               'D [06/Nov/2008:11:04:47 +0000] Report: clients=1',
               'D [06/Nov/2008:11:04:47 +0000] Report: jobs=7',
               'D [06/Nov/2008:11:04:47 +0000] Report: jobs-active=1',
               'D [06/Nov/2008:11:04:47 +0000] Report: printers=2',
               'D [06/Nov/2008:11:04:47 +0000] Report: printers-implicit=0',
               'D [06/Nov/2008:11:04:47 +0000] Report: stringpool-string-count=2289',
               'D [06/Nov/2008:11:04:47 +0000] Report: stringpool-alloc-bytes=12952',
               'D [06/Nov/2008:11:04:47 +0000] Report: stringpool-total-bytes=48168',
               'D [06/Nov/2008:11:05:10 +0000] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [06/Nov/2008:11:05:10 +0000] cupsdReadClient: 7 POST /jobs/ HTTP/1.1',
               'D [06/Nov/2008:11:05:10 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:05:10 +0000] Set-Job-Attributes ipp://localhost/jobs/9',
               'D [06/Nov/2008:11:05:10 +0000] cupsdIsAuthorized: requesting-user-name="mikeh"',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] Setting job-hold-until to no-hold',
               'I [06/Nov/2008:11:05:10 +0000] Saving subscriptions.conf...',
               'D [06/Nov/2008:11:05:10 +0000] Discarding unused job-config-changed event...',
               'I [06/Nov/2008:11:05:10 +0000] Saving subscriptions.conf...',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] job-sheets=none,none',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] banner_page = 0',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] argv[0]="DCP135C"',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] argv[1]="9"',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] argv[2]="mikeh"',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] argv[3]="Test Page"',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] argv[4]="1"',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] argv[5]="job-uuid=urn:uuid:40b6b368-bb48-388a-5bbb-5c593f8e733e"',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] argv[6]="/var/spool/cups/d00009-001"',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] envp[9]="SERVER_ADMIN=root@workstation"',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] envp[10]="SOFTWARE=CUPS/1.3.9"',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] envp[11]="TMPDIR=/var/spool/cups/tmp"',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] envp[12]="TZ=Europe/London"',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] envp[13]="USER=root"',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] envp[15]="CUPS_ENCRYPTION=IfRequested"',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] envp[16]="IPP_PORT=631"',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] envp[17]="CHARSET=utf-8"',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] envp[18]="LANG=en_GB.UTF8"',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] envp[19]="PPD=/etc/cups/ppd/DCP135C.ppd"',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] envp[20]="RIP_MAX_CACHE=8m"',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] envp[21]="CONTENT_TYPE=application/postscript"',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] envp[22]="DEVICE_URI=hal:///org/freedesktop/Hal/devices/usb_device_4f9_1ce_BROE7F477453_if0_printer_noserial"',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] envp[23]="PRINTER=DCP135C"',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] envp[24]="FINAL_CONTENT_TYPE=printer/DCP135C"',
               'I [06/Nov/2008:11:05:10 +0000] [Job 9] Started filter /usr/lib/cups/filter/pstopdf (PID 10756)',
               'I [06/Nov/2008:11:05:10 +0000] [Job 9] Started filter /usr/lib/cups/filter/pdftopdf (PID 10757)',
               'I [06/Nov/2008:11:05:10 +0000] [Job 9] Started filter /usr/lib/cups/filter/cpdftocps (PID 10758)',
               'I [06/Nov/2008:11:05:10 +0000] [Job 9] Started filter /usr/lib/cups/filter/brlpdwrapperdcp135c (PID 10759)',
               'I [06/Nov/2008:11:05:10 +0000] [Job 9] Started backend /usr/lib/cups/backend/hal (PID 10760)',
               'I [06/Nov/2008:11:05:10 +0000] Saving subscriptions.conf...',
               'D [06/Nov/2008:11:05:10 +0000] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:05:10 +0000] cupsdAcceptClient: 10 from localhost (Domain)',
               'D [06/Nov/2008:11:05:10 +0000] cupsdReadClient: 10 POST / HTTP/1.1',
               'D [06/Nov/2008:11:05:10 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:05:10 +0000] Cancel-Subscription /',
               'D [06/Nov/2008:11:05:10 +0000] cupsdIsAuthorized: requesting-user-name="mikeh"',
               'I [06/Nov/2008:11:05:10 +0000] Saving subscriptions.conf...',
               'D [06/Nov/2008:11:05:10 +0000] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:05:10 +0000] cupsdReadClient: 10 POST / HTTP/1.1',
               'D [06/Nov/2008:11:05:10 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:05:10 +0000] Create-Printer-Subscription /',
               'D [06/Nov/2008:11:05:10 +0000] cupsdCreateSubscription(con=0x7fc510cd7a10(10), uri="/")',
               'D [06/Nov/2008:11:05:10 +0000] pullmethod="ippget"',
               'D [06/Nov/2008:11:05:10 +0000] notify-lease-duration=86400',
               'D [06/Nov/2008:11:05:10 +0000] notify-time-interval=0',
               'D [06/Nov/2008:11:05:10 +0000] cupsdAddSubscription(mask=1798f, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [06/Nov/2008:11:05:10 +0000] Added subscription 19 for server',
               'I [06/Nov/2008:11:05:10 +0000] Saving subscriptions.conf...',
               'D [06/Nov/2008:11:05:10 +0000] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:05:10 +0000] cupsdReadClient: 10 POST / HTTP/1.1',
               'D [06/Nov/2008:11:05:10 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:05:10 +0000] Get-Jobs ipp://localhost/jobs/',
               'D [06/Nov/2008:11:05:10 +0000] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:05:10 +0000] cupsdReadClient: 10 POST / HTTP/1.1',
               'D [06/Nov/2008:11:05:10 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:05:10 +0000] CUPS-Get-Printers',
               'D [06/Nov/2008:11:05:10 +0000] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:05:10 +0000] cupsdReadClient: 10 POST / HTTP/1.1',
               'D [06/Nov/2008:11:05:10 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:05:10 +0000] CUPS-Get-Printers',
               'D [06/Nov/2008:11:05:10 +0000] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:05:10 +0000] cupsdReadClient: 10 POST / HTTP/1.1',
               'D [06/Nov/2008:11:05:10 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:05:10 +0000] CUPS-Get-Classes',
               'D [06/Nov/2008:11:05:10 +0000] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:05:10 +0000] cupsdReadClient: 10 POST / HTTP/1.1',
               'D [06/Nov/2008:11:05:10 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:05:10 +0000] CUPS-Get-Default',
               'D [06/Nov/2008:11:05:10 +0000] CUPS-Get-Default client-error-not-found: No default printer',
               'D [06/Nov/2008:11:05:10 +0000] cupsdProcessIPPRequest: 10 status_code=406 (client-error-not-found)',
               'D [06/Nov/2008:11:05:10 +0000] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [06/Nov/2008:11:05:10 +0000] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [06/Nov/2008:11:05:10 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:05:10 +0000] Get-Printer-Attributes ipp://workstation:631/printers/DCP135C',
               'D [06/Nov/2008:11:05:10 +0000] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:05:10 +0000] cupsdCloseClient: 12',
               'D [06/Nov/2008:11:05:10 +0000] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [06/Nov/2008:11:05:10 +0000] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [06/Nov/2008:11:05:10 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:05:10 +0000] Get-Job-Attributes ipp://localhost/jobs/9',
               'D [06/Nov/2008:11:05:10 +0000] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'E [06/Nov/2008:11:05:10 +0000] PID 10760 (/usr/lib/cups/backend/hal) stopped with status 1!',
               'D [06/Nov/2008:11:05:10 +0000] cupsdCloseClient: 12',
               'E [06/Nov/2008:11:05:10 +0000] [Job 9] Unable to open device "hal:///org/freedesktop/Hal/devices/usb_device_4f9_1ce_BROE7F477453_if0_printer_noserial": Permission denied',
               'I [06/Nov/2008:11:05:10 +0000] Saving subscriptions.conf...',
               'D [06/Nov/2008:11:05:10 +0000] cupsdCloseClient: 10',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] pstopdf argv[6] = 9 mikeh Test Page 1 job-uuid=urn:uuid:40b6b368-bb48-388a-5bbb-5c593f8e733e /var/spool/cups/d00009-001',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] pdftops - copying to temp print file "/tmp/4912cf66c74cc"',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] Injecting PostScript: <</.HWMargins[9 9 9 9] /Margins[0 0]>>setpagedevice',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] Page = 595x842; 9,9 to 586,833',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] slow_collate=0, slow_duplex=0, slow_order=1',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] Before copy_comments - %!PS-Adobe-3.0',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] %!PS-Adobe-3.0',
               'E [06/Nov/2008:11:05:10 +0000] [Job 9] No %%BoundingBox: comment in header!',
               'E [06/Nov/2008:11:05:10 +0000] [Job 9] No %%Pages: comment in header!',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] Before copy_prolog - <</.HWMargins[9 9 9 9] /Margins[0 0]>>setpagedevice',
               'I [06/Nov/2008:11:05:10 +0000] Saving subscriptions.conf...',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] Before copy_setup - %%Page: 1 1',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] Before page loop - %%Page: 1 1',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] Copying page 1...',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] pagew = 577.0, pagel = 824.0',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] bboxx = 0, bboxy = 0, bboxw = 595, bboxl = 842',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] PageLeft = 9.0, PageRight = 586.0',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] PageTop = 833.0, PageBottom = 9.0',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] PageWidth = 595.0, PageLength = 842.0',
               'D [06/Nov/2008:11:05:10 +0000] [Job 9] Wrote 1 pages...',
               'D [06/Nov/2008:11:05:11 +0000] cupsdAcceptClient: 10 from localhost (Domain)',
               'D [06/Nov/2008:11:05:11 +0000] cupsdReadClient: 10 POST / HTTP/1.1',
               'D [06/Nov/2008:11:05:11 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:05:11 +0000] Get-Jobs ipp://localhost/jobs/',
               'D [06/Nov/2008:11:05:11 +0000] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:05:11 +0000] cupsdCloseClient: 10',
               'D [06/Nov/2008:11:05:11 +0000] cupsdAcceptClient: 10 from localhost (Domain)',
               'D [06/Nov/2008:11:05:11 +0000] cupsdReadClient: 10 POST / HTTP/1.1',
               'D [06/Nov/2008:11:05:11 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:05:11 +0000] Get-Notifications /',
               'D [06/Nov/2008:11:05:11 +0000] cupsdIsAuthorized: requesting-user-name="mikeh"',
               'D [06/Nov/2008:11:05:11 +0000] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:05:11 +0000] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [06/Nov/2008:11:05:11 +0000] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [06/Nov/2008:11:05:11 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:05:11 +0000] Get-Notifications /',
               'D [06/Nov/2008:11:05:11 +0000] cupsdIsAuthorized: requesting-user-name="mikeh"',
               'D [06/Nov/2008:11:05:11 +0000] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:05:11 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [06/Nov/2008:11:05:11 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:05:11 +0000] CUPS-Get-Printers',
               'D [06/Nov/2008:11:05:11 +0000] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:05:11 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [06/Nov/2008:11:05:11 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:05:11 +0000] CUPS-Get-Classes',
               'D [06/Nov/2008:11:05:11 +0000] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:05:11 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [06/Nov/2008:11:05:11 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:05:11 +0000] CUPS-Get-Default',
               'D [06/Nov/2008:11:05:11 +0000] CUPS-Get-Default client-error-not-found: No default printer',
               'D [06/Nov/2008:11:05:11 +0000] cupsdProcessIPPRequest: 11 status_code=406 (client-error-not-found)',
               'D [06/Nov/2008:11:05:11 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [06/Nov/2008:11:05:11 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:05:11 +0000] CUPS-Get-Printers',
               'D [06/Nov/2008:11:05:11 +0000] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:05:11 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [06/Nov/2008:11:05:11 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:05:11 +0000] CUPS-Get-Classes',
               'D [06/Nov/2008:11:05:11 +0000] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:05:11 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [06/Nov/2008:11:05:11 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:05:11 +0000] CUPS-Get-Default',
               'D [06/Nov/2008:11:05:11 +0000] CUPS-Get-Default client-error-not-found: No default printer',
               'D [06/Nov/2008:11:05:11 +0000] cupsdProcessIPPRequest: 11 status_code=406 (client-error-not-found)',
               'D [06/Nov/2008:11:05:11 +0000] cupsdCloseClient: 10',
               'D [06/Nov/2008:11:05:11 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [06/Nov/2008:11:05:11 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:05:11 +0000] CUPS-Get-Printers',
               'D [06/Nov/2008:11:05:11 +0000] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:05:11 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [06/Nov/2008:11:05:11 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:05:11 +0000] CUPS-Get-Classes',
               'D [06/Nov/2008:11:05:11 +0000] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:05:11 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [06/Nov/2008:11:05:11 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:05:11 +0000] CUPS-Get-Default',
               'D [06/Nov/2008:11:05:11 +0000] CUPS-Get-Default client-error-not-found: No default printer',
               'D [06/Nov/2008:11:05:11 +0000] cupsdProcessIPPRequest: 11 status_code=406 (client-error-not-found)',
               'D [06/Nov/2008:11:05:11 +0000] cupsdCloseClient: 12',
               'D [06/Nov/2008:11:05:11 +0000] cupsdAcceptClient: 10 from localhost (Domain)',
               'D [06/Nov/2008:11:05:11 +0000] cupsdReadClient: 10 POST / HTTP/1.1',
               'D [06/Nov/2008:11:05:11 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:05:11 +0000] Get-Notifications /',
               'D [06/Nov/2008:11:05:11 +0000] cupsdIsAuthorized: requesting-user-name="mikeh"',
               'D [06/Nov/2008:11:05:11 +0000] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:05:11 +0000] cupsdCloseClient: 10',
               'D [06/Nov/2008:11:05:11 +0000] PID 10756 (/usr/lib/cups/filter/pstopdf) exited with no errors.',
               'D [06/Nov/2008:11:05:11 +0000] PID 10757 (/usr/lib/cups/filter/pdftopdf) exited with no errors.',
               'D [06/Nov/2008:11:05:11 +0000] [Job 9] Page = 595x842; 9,9 to 586,833',
               'D [06/Nov/2008:11:05:11 +0000] [Job 9] slow_collate=0, slow_duplex=0, slow_order=1',
               'D [06/Nov/2008:11:05:11 +0000] [Job 9] Before copy_comments - %!PS-Adobe-3.0',
               'D [06/Nov/2008:11:05:11 +0000] [Job 9] %!PS-Adobe-3.0',
               'D [06/Nov/2008:11:05:11 +0000] [Job 9] %%LanguageLevel: 3',
               'D [06/Nov/2008:11:05:11 +0000] [Job 9] %%DocumentSuppliedResources: (atend)',
               'D [06/Nov/2008:11:05:11 +0000] [Job 9] %%DocumentMedia: plain 595 842 0 () ()',
               'D [06/Nov/2008:11:05:11 +0000] [Job 9] %%BoundingBox: 0 0 595 842',
               'D [06/Nov/2008:11:05:11 +0000] [Job 9] %%Pages: 1',
               'D [06/Nov/2008:11:05:11 +0000] [Job 9] %%EndComments',
               'D [06/Nov/2008:11:05:11 +0000] [Job 9] Before copy_prolog - %%BeginDefaults',
               'D [06/Nov/2008:11:05:11 +0000] [Job 9] Before copy_setup - %%BeginSetup',
               'D [06/Nov/2008:11:05:11 +0000] [Job 9] Before page loop - %%Page: 1 1',
               'D [06/Nov/2008:11:05:11 +0000] [Job 9] Copying page 1...',
               'D [06/Nov/2008:11:05:11 +0000] [Job 9] pagew = 577.0, pagel = 824.0',
               'D [06/Nov/2008:11:05:11 +0000] [Job 9] bboxx = 0, bboxy = 0, bboxw = 595, bboxl = 842',
               'D [06/Nov/2008:11:05:11 +0000] [Job 9] PageLeft = 9.0, PageRight = 586.0',
               'D [06/Nov/2008:11:05:11 +0000] [Job 9] PageTop = 833.0, PageBottom = 9.0',
               'D [06/Nov/2008:11:05:11 +0000] [Job 9] PageWidth = 595.0, PageLength = 842.0',
               'D [06/Nov/2008:11:05:11 +0000] [Job 9] Wrote 1 pages...',
               'D [06/Nov/2008:11:05:11 +0000] PID 10758 (/usr/lib/cups/filter/cpdftocps) exited with no errors.',
               'D [06/Nov/2008:11:05:15 +0000] PID 10759 (/usr/lib/cups/filter/brlpdwrapperdcp135c) exited with no errors.',
               'D [06/Nov/2008:11:05:15 +0000] [Job 9] File 0 is complete.',
               'I [06/Nov/2008:11:05:15 +0000] [Job 9] Backend returned status 1 (failed)',
               'I [06/Nov/2008:11:05:15 +0000] Saving subscriptions.conf...',
               'D [06/Nov/2008:11:05:15 +0000] set_hold_until: hold_until = 1225969815',
               'I [06/Nov/2008:11:05:15 +0000] Saving subscriptions.conf...',
               'D [06/Nov/2008:11:05:16 +0000] cupsdAcceptClient: 10 from localhost (Domain)',
               'D [06/Nov/2008:11:05:16 +0000] cupsdReadClient: 10 POST / HTTP/1.1',
               'D [06/Nov/2008:11:05:16 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:05:16 +0000] Get-Jobs ipp://localhost/jobs/',
               'D [06/Nov/2008:11:05:16 +0000] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:05:16 +0000] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [06/Nov/2008:11:05:16 +0000] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [06/Nov/2008:11:05:16 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:05:16 +0000] Get-Notifications /',
               'D [06/Nov/2008:11:05:16 +0000] cupsdIsAuthorized: requesting-user-name="mikeh"',
               'D [06/Nov/2008:11:05:16 +0000] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:05:16 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [06/Nov/2008:11:05:16 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:05:16 +0000] CUPS-Get-Printers',
               'D [06/Nov/2008:11:05:16 +0000] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:05:16 +0000] cupsdCloseClient: 10',
               'D [06/Nov/2008:11:05:16 +0000] cupsdAcceptClient: 10 from localhost (Domain)',
               'D [06/Nov/2008:11:05:16 +0000] cupsdReadClient: 10 POST / HTTP/1.1',
               'D [06/Nov/2008:11:05:16 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:05:16 +0000] Get-Notifications /',
               'D [06/Nov/2008:11:05:16 +0000] cupsdIsAuthorized: requesting-user-name="mikeh"',
               'D [06/Nov/2008:11:05:16 +0000] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:05:16 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [06/Nov/2008:11:05:16 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:05:16 +0000] CUPS-Get-Classes',
               'D [06/Nov/2008:11:05:16 +0000] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:05:16 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [06/Nov/2008:11:05:16 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:05:16 +0000] CUPS-Get-Default',
               'D [06/Nov/2008:11:05:16 +0000] CUPS-Get-Default client-error-not-found: No default printer',
               'D [06/Nov/2008:11:05:16 +0000] cupsdProcessIPPRequest: 11 status_code=406 (client-error-not-found)',
               'D [06/Nov/2008:11:05:16 +0000] cupsdCloseClient: 12',
               'D [06/Nov/2008:11:05:16 +0000] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [06/Nov/2008:11:05:16 +0000] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [06/Nov/2008:11:05:16 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:05:16 +0000] Get-Notifications /',
               'D [06/Nov/2008:11:05:16 +0000] cupsdIsAuthorized: requesting-user-name="mikeh"',
               'D [06/Nov/2008:11:05:16 +0000] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:05:16 +0000] cupsdCloseClient: 10',
               'D [06/Nov/2008:11:05:16 +0000] cupsdCloseClient: 12',
               'D [06/Nov/2008:11:05:50 +0000] Report: clients=2',
               'D [06/Nov/2008:11:05:50 +0000] Report: jobs=7',
               'D [06/Nov/2008:11:05:50 +0000] Report: jobs-active=1',
               'D [06/Nov/2008:11:05:50 +0000] Report: printers=2',
               'D [06/Nov/2008:11:05:50 +0000] Report: printers-implicit=0',
               'D [06/Nov/2008:11:05:50 +0000] Report: stringpool-string-count=2456',
               'D [06/Nov/2008:11:05:50 +0000] Report: stringpool-alloc-bytes=13056',
               'D [06/Nov/2008:11:05:50 +0000] Report: stringpool-total-bytes=51800',
               'D [06/Nov/2008:11:06:16 +0000] cupsdAcceptClient: 10 from localhost (Domain)',
               'D [06/Nov/2008:11:06:16 +0000] cupsdReadClient: 10 POST / HTTP/1.1',
               'D [06/Nov/2008:11:06:16 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:06:16 +0000] Get-Notifications /',
               'D [06/Nov/2008:11:06:16 +0000] cupsdIsAuthorized: requesting-user-name="mikeh"',
               'D [06/Nov/2008:11:06:16 +0000] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:06:16 +0000] cupsdCloseClient: 10',
               'D [06/Nov/2008:11:06:16 +0000] cupsdAcceptClient: 10 from localhost (Domain)',
               'D [06/Nov/2008:11:06:16 +0000] cupsdReadClient: 10 POST / HTTP/1.1',
               'D [06/Nov/2008:11:06:16 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:06:16 +0000] Get-Job-Attributes ipp://localhost/jobs/9',
               'D [06/Nov/2008:11:06:16 +0000] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:06:16 +0000] cupsdCloseClient: 10',
               'D [06/Nov/2008:11:06:16 +0000] cupsdAcceptClient: 10 from localhost (Domain)',
               'D [06/Nov/2008:11:06:16 +0000] cupsdReadClient: 10 POST / HTTP/1.1',
               'D [06/Nov/2008:11:06:16 +0000] cupsdAuthorize: No authentication data provided.',
               'D [06/Nov/2008:11:06:16 +0000] Cancel-Subscription /',
               'D [06/Nov/2008:11:06:16 +0000] cupsdIsAuthorized: requesting-user-name="mikeh"',
               'I [06/Nov/2008:11:06:16 +0000] Saving subscriptions.conf...',
               'D [06/Nov/2008:11:06:16 +0000] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)',
               'D [06/Nov/2008:11:06:16 +0000] cupsdCloseClient: 10',
               'D [06/Nov/2008:11:06:16 +0000] cupsdAcceptClient: 10 from localhost (Domain)',
               'D [06/Nov/2008:11:06:16 +0000] cupsdReadClient: 10 GET /admin/log/error_log HTTP/1.1',
               'D [06/Nov/2008:11:06:16 +0000] cupsdAuthorize: No authentication data provided.'],
 'error_log_debug_logging_unset': True}

```

I'm too much of a noob to make much sense out of this, but I'm hoping some bright spark out there will reveal all..

Many thanks in advance.
Mike.

---

### Post by mherrin on 2008-11-09
The new CUPS updates have installed, but have made no difference...

Anyone?

 I found my old post on this, and **bluturtl** wrote:

[I][COLOR="Blue"]This could be Debian bug #383091.

I had the same problem on Hardy 32-bit. To fix it, I had to add the following line to the file /etc/cups/cupsd.conf:


FileDevice Yes

After this, I went to localhost:631 with my browser and changed the device URI of the printer to

file:/dev/usb/lp0

That did it for me![/COLOR][/I]

I added the line above, but can't seem to change the device URL.
Any hints.

Regards,
Mike.

---

### Post by mherrin on 2008-11-09
Playing with this a bit more...
in:-**[http://127.0.0.1:631/printers/](http://127.0.0.1:631/printers/)**
I get the message:[COLOR="Red"]*DCP135C "Unable to open device "hal:///org/freedesktop/Hal/devices/usb_device_4f9_1ce_BROE7F477453_if0_printer_noserial": Permission denied"*[/COLOR]

This seems to be different.
How & where do I change permissions for this?
Am I making progress?
I cannot find the device in /dev
I do however, have a */dev/usb/lp0* - how can I connect to this / send a file directly to this to check it out?

Cheers,
Mike.

---

### Post by skintythe1andonly on 2008-11-09
I am having this problem not on xubuntu since i changed to intrepid. Used to work fine on ubuntu hardy....did you find a solution??

---

### Post by cmay on 2008-11-09
i have such printer just i have almost just taken out of the box. it did the same to me. i will post here if i find something out. if not i will read this post again and hope the best. 
thanks for starting this the tread.
and good luck.

---

### Post by mherrin on 2008-11-09
I'm still no closer to a solution.

I'm beginning to wonder if I should have posted this in a different are: Desktop, perhaps?

---

### Post by cmay on 2008-11-09
you can report your own post and ask for it to be moved. mods do not like double post that much ;). just click the report button and ask for the post to be moved. the mod that gets the report will find a suitable place  for it if it needs to be moved.

i did not get any close either so i am hoping also for the solution to pop up anytime soon.
thanks for bringing up the matter.

---

### Post by skintythe1andonly on 2008-11-09
ya i still havnt found it either. It was working initially. The probelsms only arose when i tried to setup the printer on my acer aspire one over the network. The printer works on that directly over USB, but trying to setup the network messed up the setting on the desktop which is where i want it tbh

---

### Post by skintythe1andonly on 2008-11-09
im giving up on this for a while.... looks like i may have to chage this back to hardy

---

### Post by bapoumba on 2008-11-09
Regarding the moving of the thread, are you on a 64-bits version of Ubuntu ?

---

### Post by mherrin on 2008-11-10
Yes I am on 64 bit version, but it's also the desktop version...
I don't know if if the others are on 64bit versions??

---

### Post by skintythe1andonly on 2008-11-10
no i am on 32-bit xubuntu

---

### Post by skintythe1andonly on 2008-11-10
bump

---

### Post by mherrin on 2008-11-10
I have asked for the thread to be moved.

---

### Post by bapoumba on 2008-11-10
Moved to General Help. Hardware could be a good option too. Please let me know.

---

### Post by mherrin on 2008-11-10
I just found out how to assign a different device...

System>Administration>Printing

I clicked properties for the printer I use & changed the device URI to /dev/usb/lp0

I then tried printing again.... the error msg I got in the web interface was: [COLOR="Blue"]"Unable to start backend "/dev/usb/lp0" - No such file or directory."[/COLOR]

Checked the permissions and the file lp0 belongs to the [COLOR="Red"]scanner[/COLOR] group...
I wonder if there is a conflict between the scanner and printer - this being a multi function device......

---

### Post by plucky on 2008-11-10
Post output from a terminal window ```
dpkg -l | grep Brother
``` which should show which drivers you have installed.

Also ```
lpq
``` which should show any jobs that are queued to the printer.
I think you need to clear out the jobs in the printer queue. 

If you have installed Hardy or Intrepid,you need to install both the LPR and Cupswrapper drivers,which are packaged in Synaptic.
Open synaptic and search for **DCP-135C** and it should display the "extra" drivers.Tick the boxes and apply to install.These will only install the printer drivers.

If your printer has a scanner,you have to download the drivers from the [Brother Website](http://solutions.brother.com/linux/en_us/index.html) which also has the installation instructions.

See the [Brother Driver packaging Wiki](https://wiki.ubuntu.com/BrotherDriverPackaging)

Also check out the Brother Website for troubleshooting tips.


Good Luck

---

### Post by skintythe1andonly on 2008-11-10
i dont have access to the printer right now as its in my parents house and i wont be there until the weekend but i was playing around with the drivers to use. When i first had my printer working i just downloaded the lpr driver and the cups wrapper and installed the .deb. I did not use synaptic. It was working then for a while. When it stopped working i found the brother drivers in the repos and installed them. That did nothing either and i installed ALL brother drivers that were there. What was interesting though is that when i tried to reinstall the lpr driver then there was a conflict by having the ones in the repos installed. 

so the question is which one to use. i cant be sure but when i did just try the repos drivers the recommended driver was for the DCP1200 or something and no option for the DCP135C. I could be wrong in this. Il be able to give a better update at the weekend

---

### Post by plucky on 2008-11-11
> so the question is which one to use. i cant be sure but when i did just try the repos drivers the recommended driver was for the DCP1200 or something and no option for the DCP135C


Don't accept the default.If you click on "Forward",I think you are presented with a menu to look for drivers.Select "Brother" and if the drivers were installed by synaptic,you should have one for DCP-135C.


Good Luck

---

### Post by mherrin on 2008-11-11
Hi plucky, thanks for the ideas.

Heres some output:
```
[SIZE="1"]dpkg -l | grep Brother
ii  brother-cups-wrapper-common      1.0.0-10-0ubuntu5          Common files for Brother cups wrapper packages
ii  brscan2                          0.2.4                      Brother Scanner Driver
ii  dcp135ccupswrapper               1.0.1-1                    Brother CUPS Inkjet Printer Definitions
ii  dcp135clpr                       1.0.1-1                    Brother lpr Inkjet Printer Definitions[/SIZE]
```
I cannot get lpq to work - sais I have to install? tried ```
sudo apt-get install lpq
``` get
```
Couldn't find package lpq
```

I have installed the 135-c drivers, and have selected these.
Still no joy...

---

### Post by plucky on 2008-11-11
> I cannot get lpq to work - sais I have to install?


**lpq** is a terminal command and should already be available.Also try ```
lpstat -v
```

In a terminal window ```
man lpq
``` should display the command manual page.

What happens when you go to **System > Administration > Printing** and select new printer? Does it search and find your printer? 

Assuming the printer is turned on.

Is it connected directly to a USB port and not via a HUB?
Have you configured the printer options? Particularly paper size.
Open the CUPS interface in your browser with ```
http://localhost:631/
``` and have a look at the logs.


Good Luck

---

### Post by mherrin on 2008-11-14
Thanks,
installed the necessary packages, and I'll have aplay with them to see what results I get.

I can connect the printer to another machine & print to that, but the setting needs adjusting as the pages all come out off centre.

Cheers,
Mike.

---

### Post by skintythe1andonly on 2008-11-14
ok this is driving me mad now. im back on my parents computer. i get the following when checking which drivers are installed

```
skint@daunt-desktop:~$ dpkg -l | grep Brother
rH  brscan2                                   0.2.4                                 Brother Scanner Driver
ii  dcp135ccupswrapper                        1.0.1-1                               Brother CUPS Inkjet Printer Definitions
ii  dcp135clpr                                1.0.1-1                               Brother lpr Inkjet Printer Definitions
skint@daunt-desktop:~$ 

```

so that looks ok to me. What is interesting now is that i ran an update and there were some updates for cups which i installed. I rebooted. No when i try to install the printer it looks like it goes ok. I try and print a test page though and it doesnt print. This time though there is no "No %%pages:Header in Comment" or what ever that was. It is still coming up though as printer may not be connected in the notification area

I have gone into my cups setting too via localhost:631/admin. The setting there look ok. i have included a screenshot.

I think im going to go back to hardy when things worked

---

### Post by mherrin on 2008-11-15
> **skintythe1andonly said:**
> I think im going to go back to hardy when things worked

I had the same problem with Hardy...

---

### Post by skintythe1andonly on 2008-11-16
ok so im downloading xubuntu hardy at the moment on my ubuntu intrepid laptop. The printer is working no problem on this laptop, I just installed the drivers from the repos and that was it. mherrin ...are you using ubuntu or xubuntu??

---

### Post by skintythe1andonly on 2008-11-17
I have everything working now with xubuntu hardy. I used the drivers in the repos and that was that. I have it working as a networked printer so any laptops on the wireless network can print off that printer.

---

### Post by mherrin on 2008-11-22
Glad to hear you got it working.

I'm using Ubuntu Intrpid @ the mo. 

Not had the time to play with this for a bit - will get back on the cas when I have some time.

I'm planning on installing Ubuntu on the laptop soon, so I may have more luck with that.

Cheers,
Mike.

---

### Post by CyberAngel on 2009-01-14
OK! This is very weird :s

I have the same problem with a HP Deskjet 840C!

When I try to print something I get the following messages from the HP Device Manager:

Started a print job...
Print Job has been completed...
Idle...

In the Document print status of KDE I am getting a Document status: Stopped

In the Printer status of KDE I am getting: Printer 'DESKJET_840C' may not be connected

In the CUPS Page I get exactly the same as what I am getting from the document print status of KDE:
DESKJET_840C-108  	tmpxdlVUT  	cyber  	1403k  	Unknown  	stopped 

Now the weirdest thing of all is that I have setup CUPS as a printer server and my sister that she is using a windows XP machine and I am sharing the printer with her, can print without any problem from the same printer when I have my computer opened!!!

---

### Post by westeh on 2009-03-18
I had the same problem found the solution:

Install the packages:

dcp135ccupswrapper            
dcp135clpr      

From the Brother sides, or from the repositories. (they are named "Extra")
 
Your printer will be recognised and innstalled with the right drivers. Then: 

1. Add the line:    

FileDevice Yes

to the file /etc/cups/cupsd.conf:

2. change the URL of the printer to: file:/dev/usb/lp0

Some have mentioned the URL: dev:/usb/lp0  - or "something" - it has to be "file:"  first.

Some asked about how to change the URL: 
Use the menu system:administration: printers
right click om the printer and choose "options" (I guess) Using norwegian ubuntu. 

See reply nr 2 in this thread - he's got it:-)

Good luck.

---

