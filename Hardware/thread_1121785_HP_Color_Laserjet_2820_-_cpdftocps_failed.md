---
title: "HP Color Laserjet 2820 - cpdftocps failed"
date: 2009-04-10
forum: Hardware
---

### Post by newonlinux on 2009-04-10
I've installed the HP Color Laserjet 2820 as a network printer.
It's plugged into a computer with Windows XP.
I'm using a Dell Inspiron Mini 9 laptop with Ubuntu.

When i try to print i get this error:
[[IMG]http://img87.imageshack.us/img87/1071/noprint1.png[/IMG]](http://img87.imageshack.us/my.php?image=noprint1.png)

with printer status:
[[IMG]http://img511.imageshack.us/img511/7384/noprint2.png[/IMG]](http://img511.imageshack.us/my.php?image=noprint2.png)

Here is the diagnostic file:
```
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest HP>,
 'cups_instance': None,
 'cups_queue': 'HP',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'smb',
 'cups_printer_dict': {'device-uri': u'smb://ROBERTHOME/HALL/HP%20Bigass%202820',
                       'printer-info': u'HP Color Laserjet 2820',
                       'printer-is-shared': True,
                       'printer-location': u'Hall',
                       'printer-make-and-model': u'HP Color LaserJet 2800 Series Postscript (recommended)',
                       'printer-state': 3,
                       'printer-state-message': u'/usr/lib/cups/filter/cpdftocps failed',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 36940,
                       'printer-uri-supported': u'ipp://localhost:631/printers/HP'},
 'cups_printer_remote': False,
 'is_cups_class': False,
 'nmblookup_output': ('querying HALL on 192.168.0.255\n192.168.0.2 HALL<00>\n',
                      ''),
 'remote_server_name': '192.168.0.2'}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'InputSlot': u'Auto',
                                            u'ManualFeed': u'False',
                                            u'MediaType': u'Unspecified',
                                            u'PageRegion': u'A4',
                                            u'PageSize': u'A4'},
                               u'HPCMYKInksPanel': {u'HPCMYKInks': u'Default'},
                               u'HPColorOptionsPanel': {u'ColorModel': u'CMYK',
                                                        u'HPColorSmart': u'Automatic',
                                                        u'HPEdgeControl': u'Normal',
                                                        u'HPGraphicsHalftone': u'Detail',
                                                        u'HPGraphicsNeutralGrays': u'Black',
                                                        u'HPPhotoHalftone': u'Detail',
                                                        u'HPPhotoNeutralGrays': u'ProcessBlack',
                                                        u'HPRGBEmulation': u'sRGB',
                                                        u'HPTextHalftone': u'Detail',
                                                        u'HPTextNeutralGrays': u'Black'},
                               u'HPFinishingPanel': {u'HPManualDuplex': u'False'},
                               u'HPWaterOverlayPanel': {u'HPwmBrightness': u'Medium',
                                                        u'HPwmFontName': u'HelveticaB',
                                                        u'HPwmFontSize': u'pt48',
                                                        u'HPwmPages': u'AllPages',
                                                        u'HPwmSwitch': u'Off',
                                                        u'HPwmTextAngle': u'Deg45',
                                                        u'HPwmTextColor': u'Black',
                                                        u'HPwmTextMessage': u'Draft',
                                                        u'HPwmTextStyle': u'Medium'},
                               u'InstallableOptions': {u'HPOption_250_Sheet_Feeder_Tray2': u'True',
                                                       u'HPOption_PaperPolicy': u'Prompt',
                                                       u'InstalledMemory': u'96-127MB'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Check network server sanity):
{'remote_server_name_resolves': ['192.168.0.2', '192.168.0.2', '192.168.0.2'],
 'remote_server_try_connect': '192.168.0.2'}
Page 7 (Printer state reasons):
{'printer-state-message': u'/usr/lib/cups/filter/cpdftocps failed',
 'printer-state-reasons': [u'none']}
Page 8 (Error log checkpoint):
{'cups_server_settings': {'DefaultAuthType': 'Basic',
                          'MaxLogSize': '0',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '1',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '1',
                          '_share_printers': '0',
                          '_user_cancel_any': '1'},
 'error_log_checkpoint': 75128L}
Page 9 (Print test page):
{'test_page_attempted': True,
 'test_page_completions': [(37,
                            u'Job stopped due to filter errors; please consult the error_log file for details.')],
 'test_page_job_id': [37],
 'test_page_job_status': [(False, 36, 'HP', 'Untitled1', 'Stopped', None),
                          (True,
                           37,
                           'HP',
                           'Test Page',
                           'Stopped',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-gb',
                            'document-format': u'application/postscript',
                            'job-hold-until': u'no-hold',
                            'job-id': 37,
                            'job-k-octets': 17,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/37',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'robert',
                            'job-preserved': True,
                            'job-printer-state-message': u'/usr/lib/cups/filter/cpdftocps failed',
                            'job-printer-state-reasons': [u'none'],
                            'job-printer-up-time': 1239370599,
                            'job-printer-uri': u'ipp://robert-laptop:631/printers/HP',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 6,
                            'job-state-reasons': u'job-stopped',
                            'job-uri': u'ipp://localhost:631/jobs/37',
                            'job-uuid': u'urn:uuid:33c1cb67-9176-3d40-787d-6e54a4c380cd',
                            'printer-uri': u'ipp://localhost/printers/HP',
                            'time-at-completed': None,
                            'time-at-creation': 1239370590,
                            'time-at-processing': 1239370590})],
 'test_page_successful': False}
Page 10 (Error log fetch):
{'error_log': ['D [10/Apr/2009:14:36:23 +0100] cupsdCloseClient: 12',
               'D [10/Apr/2009:14:36:23 +0100] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [10/Apr/2009:14:36:23 +0100] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [10/Apr/2009:14:36:23 +0100] cupsdAuthorize: No authentication data provided.',
               'D [10/Apr/2009:14:36:23 +0100] Get-Jobs ipp://localhost/jobs/',
               'D [10/Apr/2009:14:36:23 +0100] [Job 36] Loading attributes...',
               'D [10/Apr/2009:14:36:23 +0100] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [10/Apr/2009:14:36:23 +0100] cupsdCloseClient: 12',
               'D [10/Apr/2009:14:36:23 +0100] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [10/Apr/2009:14:36:23 +0100] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [10/Apr/2009:14:36:23 +0100] cupsdAuthorize: No authentication data provided.',
               'D [10/Apr/2009:14:36:23 +0100] Create-Printer-Subscription /',
               'D [10/Apr/2009:14:36:23 +0100] cupsdCreateSubscription(con=0xb90d5d78(12), uri="/")',
               'D [10/Apr/2009:14:36:23 +0100] pullmethod="ippget"',
               'D [10/Apr/2009:14:36:23 +0100] notify-lease-duration=86400',
               'D [10/Apr/2009:14:36:23 +0100] notify-time-interval=0',
               'D [10/Apr/2009:14:36:23 +0100] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [10/Apr/2009:14:36:23 +0100] Added subscription 41 for server',
               'I [10/Apr/2009:14:36:23 +0100] Saving subscriptions.conf...',
               'D [10/Apr/2009:14:36:23 +0100] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [10/Apr/2009:14:36:23 +0100] cupsdCloseClient: 12',
               'D [10/Apr/2009:14:36:24 +0100] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [10/Apr/2009:14:36:24 +0100] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [10/Apr/2009:14:36:24 +0100] cupsdAuthorize: No authentication data provided.',
               'D [10/Apr/2009:14:36:24 +0100] Get-Notifications /',
               'D [10/Apr/2009:14:36:24 +0100] cupsdIsAuthorized: requesting-user-name="robert"',
               'D [10/Apr/2009:14:36:24 +0100] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [10/Apr/2009:14:36:24 +0100] cupsdCloseClient: 12',
               'D [10/Apr/2009:14:36:30 +0100] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [10/Apr/2009:14:36:30 +0100] cupsdReadClient: 12 POST /printers/HP HTTP/1.1',
               'D [10/Apr/2009:14:36:30 +0100] cupsdAuthorize: No authentication data provided.',
               'D [10/Apr/2009:14:36:30 +0100] Print-Job ipp://localhost/printers/HP',
               'D [10/Apr/2009:14:36:30 +0100] add_job: requesting-user-name="robert"',
               'D [10/Apr/2009:14:36:30 +0100] Adding default job-sheets values "none,none"...',
               'I [10/Apr/2009:14:36:30 +0100] [Job 37] Adding start banner page "none".',
               'I [10/Apr/2009:14:36:30 +0100] Saving subscriptions.conf...',
               'I [10/Apr/2009:14:36:30 +0100] [Job 37] Adding end banner page "none".',
               'I [10/Apr/2009:14:36:30 +0100] [Job 37] File of type application/postscript queued by "robert".',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] hold_until=0',
               'I [10/Apr/2009:14:36:30 +0100] [Job 37] Queued on "HP" by "robert".',
               'I [10/Apr/2009:14:36:30 +0100] Saving subscriptions.conf...',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] job-sheets=none,none',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] banner_page = 0',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] argv[0]="HP"',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] argv[1]="37"',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] argv[2]="robert"',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] argv[3]="Test Page"',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] argv[4]="1"',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] argv[5]="job-uuid=urn:uuid:33c1cb67-9176-3d40-787d-6e54a4c380cd"',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] argv[6]="/var/spool/cups/d00037-001"',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] envp[9]="SERVER_ADMIN=root@robert-laptop"',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] envp[10]="SOFTWARE=CUPS/1.3.9"',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] envp[11]="TMPDIR=/var/spool/cups/tmp"',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] envp[12]="TZ=Europe/London"',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] envp[13]="USER=root"',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] envp[15]="CUPS_ENCRYPTION=IfRequested"',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] envp[16]="IPP_PORT=631"',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] envp[17]="CHARSET=utf-8"',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] envp[18]="LANG=en_GB.UTF8"',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] envp[19]="PPD=/etc/cups/ppd/HP.ppd"',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] envp[20]="RIP_MAX_CACHE=8m"',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] envp[21]="CONTENT_TYPE=application/postscript"',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] envp[22]="DEVICE_URI=smb://ROBERTHOME/HALL/HP%20Bigass%202820"',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] envp[23]="PRINTER=HP"',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] envp[24]="FINAL_CONTENT_TYPE=application/vnd.cups-postscript"',
               'I [10/Apr/2009:14:36:30 +0100] [Job 37] Started filter /usr/lib/cups/filter/pstopdf (PID 8103)',
               'I [10/Apr/2009:14:36:30 +0100] [Job 37] Started filter /usr/lib/cups/filter/pdftopdf (PID 8104)',
               'I [10/Apr/2009:14:36:30 +0100] [Job 37] Started filter /usr/lib/cups/filter/cpdftocps (PID 8105)',
               'I [10/Apr/2009:14:36:30 +0100] [Job 37] Started backend /usr/lib/cups/backend/smb (PID 8106)',
               'I [10/Apr/2009:14:36:30 +0100] Saving subscriptions.conf...',
               'D [10/Apr/2009:14:36:30 +0100] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [10/Apr/2009:14:36:30 +0100] cupsdCloseClient: 12',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] pstopdf argv[6] = 37 robert Test Page 1 job-uuid=urn:uuid:33c1cb67-9176-3d40-787d-6e54a4c380cd /var/spool/cups/d00037-001',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] PPD: /etc/cups/ppd/HP.ppd',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] Resolution: 600',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] Page size: A4',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] Width: 595, height: 842, absolute margins: , , ,',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] Relative margins: 12.00, 12.12, 11.92, 12.32',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] PPD options: -r600 -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] PostScript to be injected:',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] Running cat | /usr/bin/ps2pdf13 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                -dPDFSETTINGS=/printer -r600 -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842 - -',
               'D [10/Apr/2009:14:36:30 +0100] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [10/Apr/2009:14:36:30 +0100] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [10/Apr/2009:14:36:30 +0100] cupsdAuthorize: No authentication data provided.',
               'D [10/Apr/2009:14:36:30 +0100] Get-Jobs ipp://localhost/jobs/',
               'D [10/Apr/2009:14:36:30 +0100] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [10/Apr/2009:14:36:30 +0100] cupsdCloseClient: 12',
               'D [10/Apr/2009:14:36:30 +0100] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [10/Apr/2009:14:36:30 +0100] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [10/Apr/2009:14:36:30 +0100] cupsdAuthorize: No authentication data provided.',
               'D [10/Apr/2009:14:36:30 +0100] Get-Notifications /',
               'D [10/Apr/2009:14:36:30 +0100] cupsdIsAuthorized: requesting-user-name="robert"',
               'D [10/Apr/2009:14:36:30 +0100] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [10/Apr/2009:14:36:30 +0100] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [10/Apr/2009:14:36:30 +0100] cupsdAuthorize: No authentication data provided.',
               'D [10/Apr/2009:14:36:30 +0100] Get-Job-Attributes ipp://localhost/jobs/37',
               'D [10/Apr/2009:14:36:30 +0100] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [10/Apr/2009:14:36:30 +0100] cupsdCloseClient: 12',
               'D [10/Apr/2009:14:36:30 +0100] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [10/Apr/2009:14:36:30 +0100] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [10/Apr/2009:14:36:30 +0100] cupsdAuthorize: No authentication data provided.',
               'D [10/Apr/2009:14:36:30 +0100] Get-Notifications /',
               'D [10/Apr/2009:14:36:30 +0100] cupsdIsAuthorized: requesting-user-name="robert"',
               'D [10/Apr/2009:14:36:30 +0100] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [10/Apr/2009:14:36:30 +0100] cupsdCloseClient: 12',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] Connected using Kerberos...',
               'D [10/Apr/2009:14:36:30 +0100] [Job 37] GPL Ghostscript 8.63: Set UseCIEColor for UseDeviceIndependentColor to work properly.',
               'D [10/Apr/2009:14:36:31 +0100] PID 8103 (/usr/lib/cups/filter/pstopdf) exited with no errors.',
               'D [10/Apr/2009:14:36:31 +0100] PID 8104 (/usr/lib/cups/filter/pdftopdf) exited with no errors.',
               "D [10/Apr/2009:14:36:31 +0100] [Job 37] Can't open /dev/null: Permission denied",
               'D [10/Apr/2009:14:36:31 +0100] [Job 37] grep: write error: Broken pipe',
               'E [10/Apr/2009:14:36:31 +0100] PID 8105 (/usr/lib/cups/filter/cpdftocps) stopped with status 13!',
               'D [10/Apr/2009:14:36:31 +0100] PID 8106 (/usr/lib/cups/backend/smb) exited with no errors.',
               'D [10/Apr/2009:14:36:31 +0100] [Job 37] File 0 is complete.',
               'E [10/Apr/2009:14:36:31 +0100] [Job 37] Job stopped due to filter errors.',
               'I [10/Apr/2009:14:36:31 +0100] Saving subscriptions.conf...',
               'I [10/Apr/2009:14:36:31 +0100] Saving subscriptions.conf...',
               'D [10/Apr/2009:14:36:31 +0100] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [10/Apr/2009:14:36:31 +0100] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [10/Apr/2009:14:36:31 +0100] cupsdAuthorize: No authentication data provided.',
               'D [10/Apr/2009:14:36:31 +0100] Get-Jobs ipp://localhost/jobs/',
               'D [10/Apr/2009:14:36:31 +0100] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [10/Apr/2009:14:36:31 +0100] cupsdCloseClient: 12',
               'D [10/Apr/2009:14:36:31 +0100] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [10/Apr/2009:14:36:31 +0100] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [10/Apr/2009:14:36:31 +0100] cupsdAuthorize: No authentication data provided.',
               'D [10/Apr/2009:14:36:31 +0100] Get-Notifications /',
               'D [10/Apr/2009:14:36:31 +0100] cupsdIsAuthorized: requesting-user-name="robert"',
               'D [10/Apr/2009:14:36:31 +0100] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [10/Apr/2009:14:36:31 +0100] cupsdCloseClient: 12',
               'D [10/Apr/2009:14:36:31 +0100] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [10/Apr/2009:14:36:31 +0100] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [10/Apr/2009:14:36:31 +0100] cupsdAuthorize: No authentication data provided.',
               'D [10/Apr/2009:14:36:31 +0100] Get-Notifications /',
               'D [10/Apr/2009:14:36:31 +0100] cupsdIsAuthorized: requesting-user-name="robert"',
               'D [10/Apr/2009:14:36:31 +0100] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [10/Apr/2009:14:36:31 +0100] cupsdCloseClient: 12',
               'D [10/Apr/2009:14:36:32 +0100] [Job 37] Unloading...',
               'D [10/Apr/2009:14:36:39 +0100] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [10/Apr/2009:14:36:39 +0100] Report: clients=3',
               'D [10/Apr/2009:14:36:39 +0100] Report: jobs=31',
               'D [10/Apr/2009:14:36:39 +0100] Report: jobs-active=2',
               'D [10/Apr/2009:14:36:39 +0100] Report: printers=2',
               'D [10/Apr/2009:14:36:39 +0100] Report: printers-implicit=0',
               'D [10/Apr/2009:14:36:39 +0100] Report: stringpool-string-count=854',
               'D [10/Apr/2009:14:36:39 +0100] Report: stringpool-alloc-bytes=9720',
               'D [10/Apr/2009:14:36:39 +0100] Report: stringpool-total-bytes=16936',
               'D [10/Apr/2009:14:36:39 +0100] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [10/Apr/2009:14:36:39 +0100] cupsdAuthorize: No authentication data provided.',
               'D [10/Apr/2009:14:36:39 +0100] Get-Job-Attributes ipp://localhost/jobs/37',
               'D [10/Apr/2009:14:36:39 +0100] [Job 37] Loading attributes...',
               'D [10/Apr/2009:14:36:39 +0100] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [10/Apr/2009:14:36:39 +0100] cupsdCloseClient: 12',
               'D [10/Apr/2009:14:36:39 +0100] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [10/Apr/2009:14:36:39 +0100] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [10/Apr/2009:14:36:39 +0100] cupsdAuthorize: No authentication data provided.',
               'D [10/Apr/2009:14:36:39 +0100] Cancel-Subscription /',
               'D [10/Apr/2009:14:36:39 +0100] cupsdIsAuthorized: requesting-user-name="robert"',
               'I [10/Apr/2009:14:36:39 +0100] Saving subscriptions.conf...',
               'D [10/Apr/2009:14:36:39 +0100] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [10/Apr/2009:14:36:39 +0100] cupsdCloseClient: 12',
               'D [10/Apr/2009:14:36:39 +0100] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [10/Apr/2009:14:36:39 +0100] cupsdCloseClient: 11',
               'D [10/Apr/2009:14:36:39 +0100] cupsdReadClient: 12 GET /admin/log/error_log HTTP/1.1',
               'D [10/Apr/2009:14:36:39 +0100] cupsdAuthorize: No authentication data provided.']}
```

Thanks in advance for any help getting my printer working.

P.S. Weird thing is that I have Ubuntu running on a Dell computer as well in the house, and the printer works fine as a network printer on that one. I'll provide any files for that one if needed.

---

### Post by PaDV on 2009-05-23
Please post the output of the following command on a terminal:
ls -l /dev/null

---

### Post by newonlinux on 2009-05-23
Hi, thanks for the reply but this was resolved when i installed 9.04 Netbook Remix.
Sorry for not updating this

---

### Post by Kounterfeit on 2009-06-01
I am actually experiencing this exact same issue with a HP 2840 over network on Ubuntu 9.04 (ASUS M51Va).  It always worked fine and then all of a sudden just nothing!

The output of ls -l /dev/null;
crw-rw---- 1 root dialout 1, 3 2009-05-05 08:56 /dev/null

My cups error log also has similar log entries;
E [02/Jun/2009:10:57:39 +1000] PID 14072 (/usr/lib/cups/filter/cpdftocps) stopped with status 13!
E [02/Jun/2009:10:57:44 +1000] [Job 8] Job stopped due to filter errors.

I have tried removing and re-installing cups many times without success.

Any help much appreciated.

---

### Post by Kounterfeit on 2009-06-10
I guess nobody is able to help at all then?

---

### Post by pferreira on 2009-07-03
I also ran into this problem.
The solution is pretty simple, I think you will notice in the logs (just before the fail message from cpdftocps) the error on /dev/null.

"Can't open /dev/null: Permission denied"

All I did was make /dev/null world readable (chmod o+r /dev/null), and everything worked (It seems that this little problem will stop you printing to any type of printer, I couldn't print to a cups-pdf or an HP 2500N I had installed a long time ago).

While you are at it, you might also do this to /dev/random and /dev/urandom, or else the web manager for CUPS will probably fail on you as well ([http://localhost:631/](http://localhost:631/))

---

