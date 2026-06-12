---
title: "Installing Epson Driver in Ubuntu 9.10 all variants"
date: 2009-12-12
forum: Hardware
---

### Post by gopherbyrd on 2009-12-12
I was having a problem getting an Epson Sylus NX215 to work. Following the FAQ on the Avasys.jp site got it working. Here is the link:

[http://avasys.jp/eng/linux_driver/faq/id000608.php]("http://avasys.jp/eng/linux_driver/faq/id000608.php")

The link above has you building a .deb custom for your system from source. The FAQ is easy to follow so don't get freaked out using the CLI. You will need to download the driver tarball specific for your Epson device as well as the .ppd file for your Epson. Copy the .ppd file to /usr/share/ppd then install your .deb making sure the printer is not connected yet. 

sudo dpkg -i ./pipslite[version_for_your_printer].deb 

Connect your Epson and configure it pointing to the .ppd file you put in /usr/share/ppd.

---

### Post by LinuxDeal on 2009-12-13
You marked this thread as solved, does that mean you solved the problem yourself?

---

### Post by gopherbyrd on 2009-12-16
I had posted to the avasys site and was pointed to the link in my original post. I put here as solved so folks looking for answers in getting their Epson working could find it.

---

### Post by jolitical on 2010-01-10
i tried installing the driver on Ubuntu 9.04 as per the link above and was not successful.
here is the report i got after it failed.
can anyone help me to get it working?:

Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest NX215 (default)>,
 'cups_instance': None,
 'cups_queue': 'NX215',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://EPSON/Stylus%20NX210',
                       'printer-info': u'Epson NX215',
                       'printer-is-shared': True,
                       'printer-location': u'',
                       'printer-make-and-model': u'Epson Epson Stylus NX215, Photo Image Print System Lite',
                       'printer-state': 3,
                       'printer-state-message': u'/usr/lib/cups/filter/pipslite-wrapper failed',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 135180,
                       'printer-uri-supported': u'ipp://localhost:631/printers/NX215'},
 'cups_printer_remote': False,
 'is_cups_class': False}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'Ink': u'COLOR',
                                            u'PageRegion': u'Letter',
                                            u'PageSize': u'Letter',
                                            u'Quality': u'PLAIN_NORMAL'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Choose device):
{'cups_device_dict': {'device-class': u'direct',
                      'device-id': 'MFG:EPSON;CMD:ESCPL2,BDC,D4,D4PX,ESCPR1;MDL:Epson Stylus NX210;CLS:PRINTER;DES:EPSON Epson Stylus NX210;CID:EpsonRGB7',
                      'device-info': u'Epson Stylus NX210 USB #1',
                      'device-make-and-model': u'Epson Stylus NX210'}}
Page 7 (Printer state reasons):
{'printer-state-message': u'/usr/lib/cups/filter/pipslite-wrapper failed',
 'printer-state-reasons': [u'none']}
Page 8 (Error log checkpoint):
{'cups_server_settings': {'DefaultAuthType': 'Basic',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '0',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '0',
                          '_share_printers': '0',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 1990L,
 'error_log_debug_logging_set': True}
Page 9 (Print test page):
{'test_page_attempted': '10/Jan/2010:11:43:46 +0000',
 'test_page_completions': [(46,
                            u'Job stopped due to filter errors; please consult the error_log file for details.')],
 'test_page_job_id': [46],
 'test_page_job_status': [(True,
                           44,
                           'NX215',
                           'Test Page',
                           'Stopped',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-ca',
                            'document-format': u'application/postscript',
                            'job-hold-until': u'no-hold',
                            'job-id': 44,
                            'job-k-octets': 150,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/44',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'asia',
                            'job-preserved': True,
                            'job-printer-state-message': u'/usr/lib/cups/filter/pipslite-wrapper failed',
                            'job-printer-state-reasons': [u'none'],
                            'job-printer-up-time': 1263141846,
                            'job-printer-uri': u'ipp://milo:631/printers/NX215',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 6,
                            'job-state-reasons': u'job-stopped',
                            'job-uri': u'ipp://localhost:631/jobs/44',
                            'job-uuid': u'urn:uuid:acdd4779-3953-3062-45f7-567888eec74a',
                            'printer-uri': u'ipp://localhost/printers/NX215',
                            'time-at-completed': None,
                            'time-at-creation': 1263141740,
                            'time-at-processing': 1263141740}),
                          (False, 45, 'NX215', 'Test Page', 'Stopped', None),
                          (True,
                           46,
                           'NX215',
                           'Test Page',
                           'Stopped',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-ca',
                            'document-format': u'application/postscript',
                            'job-hold-until': u'no-hold',
                            'job-id': 46,
                            'job-k-octets': 17,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/46',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'asia',
                            'job-preserved': True,
                            'job-printer-state-message': u'/usr/lib/cups/filter/pipslite-wrapper failed',
                            'job-printer-state-reasons': [u'none'],
                            'job-printer-up-time': 1263141846,
                            'job-printer-uri': u'ipp://milo:631/printers/NX215',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 6,
                            'job-state-reasons': u'job-stopped',
                            'job-uri': u'ipp://localhost:631/jobs/46',
                            'job-uuid': u'urn:uuid:f9396015-bf74-35f9-414e-3e72453dfa9c',
                            'printer-uri': u'ipp://localhost/printers/NX215',
                            'time-at-completed': None,
                            'time-at-creation': 1263141826,
                            'time-at-processing': 1263141826})],
 'test_page_successful': False}
Page 10 (Error log fetch):
{'error_log': ['D [10/Jan/2010:11:43:34 -0500] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [10/Jan/2010:11:43:34 -0500] cupsdAuthorize: No authentication data provided.',
               'D [10/Jan/2010:11:43:34 -0500] Get-Jobs ipp://localhost/printers/',
               'D [10/Jan/2010:11:43:34 -0500] [Job 44] Loading attributes...',
               'D [10/Jan/2010:11:43:34 -0500] [Job 45] Loading attributes...',
               'D [10/Jan/2010:11:43:34 -0500] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [10/Jan/2010:11:43:34 -0500] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [10/Jan/2010:11:43:34 -0500] cupsdAuthorize: No authentication data provided.',
               'D [10/Jan/2010:11:43:34 -0500] Get-Jobs ipp://localhost/printers/',
               'D [10/Jan/2010:11:43:34 -0500] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [10/Jan/2010:11:43:35 -0500] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [10/Jan/2010:11:43:35 -0500] cupsdAuthorize: No authentication data provided.',
               'D [10/Jan/2010:11:43:35 -0500] Create-Printer-Subscription /',
               'D [10/Jan/2010:11:43:35 -0500] cupsdCreateSubscription(con=0xb834ee48(8), uri="/")',
               'D [10/Jan/2010:11:43:35 -0500] pullmethod="ippget"',
               'D [10/Jan/2010:11:43:35 -0500] notify-lease-duration=86400',
               'D [10/Jan/2010:11:43:35 -0500] notify-time-interval=0',
               'D [10/Jan/2010:11:43:35 -0500] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [10/Jan/2010:11:43:35 -0500] Added subscription 40 for server',
               'I [10/Jan/2010:11:43:35 -0500] Saving subscriptions.conf...',
               'D [10/Jan/2010:11:43:35 -0500] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [10/Jan/2010:11:43:36 -0500] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [10/Jan/2010:11:43:36 -0500] cupsdAuthorize: No authentication data provided.',
               'D [10/Jan/2010:11:43:36 -0500] Get-Notifications /',
               'D [10/Jan/2010:11:43:36 -0500] cupsdIsAuthorized: requesting-user-name="asia"',
               'D [10/Jan/2010:11:43:36 -0500] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [10/Jan/2010:11:43:46 -0500] cupsdAcceptClient: 9 from localhost (Domain)',
               'D [10/Jan/2010:11:43:46 -0500] cupsdReadClient: 9 POST /printers/NX215 HTTP/1.1',
               'D [10/Jan/2010:11:43:46 -0500] cupsdAuthorize: No authentication data provided.',
               'D [10/Jan/2010:11:43:46 -0500] Print-Job ipp://localhost/printers/NX215',
               'D [10/Jan/2010:11:43:46 -0500] [Job ???] Auto-typing file...',
               'I [10/Jan/2010:11:43:46 -0500] [Job ???] Request file type is application/postscript.',
               'D [10/Jan/2010:11:43:46 -0500] add_job: requesting-user-name="asia"',
               'D [10/Jan/2010:11:43:46 -0500] Adding default job-sheets values "none,none"...',
               'I [10/Jan/2010:11:43:46 -0500] [Job 46] Adding start banner page "none".',
               'I [10/Jan/2010:11:43:46 -0500] Saving subscriptions.conf...',
               'I [10/Jan/2010:11:43:46 -0500] [Job 46] Adding end banner page "none".',
               'I [10/Jan/2010:11:43:46 -0500] [Job 46] File of type application/postscript queued by "asia".',
               'D [10/Jan/2010:11:43:46 -0500] [Job 46] hold_until=0',
               'I [10/Jan/2010:11:43:46 -0500] [Job 46] Queued on "NX215" by "asia".',
               'I [10/Jan/2010:11:43:46 -0500] Saving subscriptions.conf...',
               'D [10/Jan/2010:11:43:46 -0500] [Job 46] job-sheets=none,none',
               'D [10/Jan/2010:11:43:46 -0500] [Job 46] banner_page = 0',
               'D [10/Jan/2010:11:43:46 -0500] [Job 46] argv[0]="NX215"',
               'D [10/Jan/2010:11:43:46 -0500] [Job 46] argv[1]="46"',
               'D [10/Jan/2010:11:43:46 -0500] [Job 46] argv[2]="asia"',
               'D [10/Jan/2010:11:43:46 -0500] [Job 46] argv[3]="Test Page"',
               'D [10/Jan/2010:11:43:46 -0500] [Job 46] argv[4]="1"',
               'D [10/Jan/2010:11:43:46 -0500] [Job 46] argv[5]="job-uuid=urn:uuid:f9396015-bf74-35f9-414e-3e72453dfa9c"',
               'D [10/Jan/2010:11:43:46 -0500] [Job 46] argv[6]="/var/spool/cups/d00046-001"',
               'D [10/Jan/2010:11:43:46 -0500] [Job 46] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [10/Jan/2010:11:43:46 -0500] [Job 46] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [10/Jan/2010:11:43:46 -0500] [Job 46] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [10/Jan/2010:11:43:46 -0500] [Job 46] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [10/Jan/2010:11:43:46 -0500] [Job 46] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [10/Jan/2010:11:43:46 -0500] [Job 46] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [10/Jan/2010:11:43:46 -0500] [Job 46] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [10/Jan/2010:11:43:46 -0500] [Job 46] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [10/Jan/2010:11:43:46 -0500] [Job 46] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [10/Jan/2010:11:43:46 -0500] [Job 46] envp[9]="SERVER_ADMIN=root@milo"',
               'D [10/Jan/2010:11:43:46 -0500] [Job 46] envp[10]="SOFTWARE=CUPS/1.3.9"',
               'D [10/Jan/2010:11:43:46 -0500] [Job 46] envp[11]="TMPDIR=/var/spool/cups/tmp"',
               'D [10/Jan/2010:11:43:46 -0500] [Job 46] envp[12]="TZ=America/Toronto"',
               'D [10/Jan/2010:11:43:46 -0500] [Job 46] envp[13]="USER=root"',
               'D [10/Jan/2010:11:43:46 -0500] [Job 46] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [10/Jan/2010:11:43:46 -0500] [Job 46] envp[15]="CUPS_ENCRYPTION=IfRequested"',
               'D [10/Jan/2010:11:43:46 -0500] [Job 46] envp[16]="IPP_PORT=631"',
               'D [10/Jan/2010:11:43:46 -0500] [Job 46] envp[17]="CHARSET=utf-8"',
               'D [10/Jan/2010:11:43:46 -0500] [Job 46] envp[18]="LANG=en_CA.UTF8"',
               'D [10/Jan/2010:11:43:46 -0500] [Job 46] envp[19]="PPD=/etc/cups/ppd/NX215.ppd"',
               'D [10/Jan/2010:11:43:46 -0500] [Job 46] envp[20]="RIP_MAX_CACHE=8m"',
               'D [10/Jan/2010:11:43:46 -0500] [Job 46] envp[21]="CONTENT_TYPE=application/postscript"',
               'D [10/Jan/2010:11:43:46 -0500] [Job 46] envp[22]="DEVICE_URI=usb://EPSON/Stylus%20NX210"',
               'D [10/Jan/2010:11:43:46 -0500] [Job 46] envp[23]="PRINTER=NX215"',
               'D [10/Jan/2010:11:43:46 -0500] [Job 46] envp[24]="FINAL_CONTENT_TYPE=printer/NX215"',
               'I [10/Jan/2010:11:43:46 -0500] [Job 46] Started filter /usr/lib/cups/filter/pstopdf (PID 4546)',
               'I [10/Jan/2010:11:43:47 -0500] [Job 46] Started filter /usr/lib/cups/filter/pdftopdf (PID 4548)',
               'I [10/Jan/2010:11:43:47 -0500] [Job 46] Started filter /usr/lib/cups/filter/pdftoraster (PID 4552)',
               'I [10/Jan/2010:11:43:47 -0500] [Job 46] Started filter /usr/lib/cups/filter/pipslite-wrapper (PID 4554)',
               'I [10/Jan/2010:11:43:47 -0500] [Job 46] Started backend /usr/lib/cups/backend/usb (PID 4556)',
               'I [10/Jan/2010:11:43:47 -0500] Saving subscriptions.conf...',
               'D [10/Jan/2010:11:43:47 -0500] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [10/Jan/2010:11:43:47 -0500] [Job 46] pstopdf 6 args: 46 asia Test Page 1 job-uuid=urn:uuid:f9396015-bf74-35f9-414e-3e72453dfa9c /var/spool/cups/d00046-001',
               'D [10/Jan/2010:11:43:47 -0500] [Job 46] PPD: /etc/cups/ppd/NX215.ppd',
               'D [10/Jan/2010:11:43:47 -0500] [Job 46] Printer using device file "/dev/usblp0"...',
               'D [10/Jan/2010:11:43:47 -0500] [Job 46] backendRunLoop(print_fd=0, device_fd=5, use_bc=1, side_cb=0xb7f92a80)',
               'I [10/Jan/2010:11:43:47 -0500] Saving subscriptions.conf...',
               'D [10/Jan/2010:11:43:47 -0500] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [10/Jan/2010:11:43:47 -0500] [Job 46] Resolution:',
               'D [10/Jan/2010:11:43:47 -0500] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [10/Jan/2010:11:43:47 -0500] cupsdAuthorize: No authentication data provided.',
               'D [10/Jan/2010:11:43:47 -0500] Get-Printer-Attributes ipp://localhost/printers/NX215',
               'D [10/Jan/2010:11:43:47 -0500] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [10/Jan/2010:11:43:47 -0500] cupsdReadClient: 11 GET /printers/NX215.ppd HTTP/1.1',
               'D [10/Jan/2010:11:43:47 -0500] cupsdAuthorize: No authentication data provided.',
               'D [10/Jan/2010:11:43:47 -0500] [Job 46] Page size: Letter',
               'D [10/Jan/2010:11:43:47 -0500] [Job 46] Width: , height: , absolute margins: , , ,',
               'D [10/Jan/2010:11:43:47 -0500] [Job 46] Relative margins: , , ,',
               'D [10/Jan/2010:11:43:47 -0500] [Job 46] PPD options:',
               'D [10/Jan/2010:11:43:47 -0500] [Job 46] PostScript to be injected:',
               'D [10/Jan/2010:11:43:47 -0500] [Job 46] Running cat | /usr/bin/ps2pdf13 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                -dDoNumCopies -dPDFSETTINGS=/printer  - -',
               'D [10/Jan/2010:11:43:47 -0500] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [10/Jan/2010:11:43:47 -0500] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [10/Jan/2010:11:43:47 -0500] cupsdAuthorize: No authentication data provided.',
               'D [10/Jan/2010:11:43:47 -0500] Get-Notifications /',
               'D [10/Jan/2010:11:43:47 -0500] cupsdIsAuthorized: requesting-user-name="asia"',
               'D [10/Jan/2010:11:43:47 -0500] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [10/Jan/2010:11:43:47 -0500] cupsdAcceptClient: 13 from localhost (Domain)',
               'D [10/Jan/2010:11:43:47 -0500] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [10/Jan/2010:11:43:47 -0500] cupsdAuthorize: No authentication data provided.',
               'D [10/Jan/2010:11:43:47 -0500] Get-Notifications /',
               'D [10/Jan/2010:11:43:47 -0500] cupsdIsAuthorized: requesting-user-name="asia"',
               'D [10/Jan/2010:11:43:47 -0500] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)',
               'D [10/Jan/2010:11:43:47 -0500] cupsdAcceptClient: 14 from localhost (Domain)',
               'D [10/Jan/2010:11:43:47 -0500] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [10/Jan/2010:11:43:47 -0500] cupsdAuthorize: No authentication data provided.',
               'D [10/Jan/2010:11:43:47 -0500] Get-Job-Attributes ipp://localhost/jobs/46',
               'D [10/Jan/2010:11:43:47 -0500] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [10/Jan/2010:11:43:47 -0500] cupsdReadClient: 14 POST / HTTP/1.1',
               'E [10/Jan/2010:11:43:47 -0500] cupsdAuthorize: Local authentication certificate not found!',
               'D [10/Jan/2010:11:43:47 -0500] Get-Printer-Attributes ipp://localhost/printers/NX215',
               'D [10/Jan/2010:11:43:47 -0500] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)',
               'D [10/Jan/2010:11:43:47 -0500] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [10/Jan/2010:11:43:47 -0500] cupsdAuthorize: No authentication data provided.',
               'D [10/Jan/2010:11:43:47 -0500] Get-Notifications /',
               'D [10/Jan/2010:11:43:47 -0500] cupsdIsAuthorized: requesting-user-name="asia"',
               'D [10/Jan/2010:11:43:47 -0500] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [10/Jan/2010:11:43:47 -0500] cupsdReadClient: 14 POST / HTTP/1.1',
               'E [10/Jan/2010:11:43:47 -0500] cupsdAuthorize: Local authentication certificate not found!',
               'D [10/Jan/2010:11:43:47 -0500] Get-Printer-Attributes ipp://localhost/printers/NX215',
               'D [10/Jan/2010:11:43:47 -0500] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)',
               'D [10/Jan/2010:11:43:47 -0500] cupsdCloseClient: 12',
               'D [10/Jan/2010:11:43:47 -0500] cupsdCloseClient: 13',
               'D [10/Jan/2010:11:43:47 -0500] [Job 46] GPL Ghostscript 8.64: Set UseCIEColor for UseDeviceIndependentColor to work properly.',
               'D [10/Jan/2010:11:43:48 -0500] PID 4546 (/usr/lib/cups/filter/pstopdf) exited with no errors.',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] Ghostscript command line: /usr/bin/gs -dQUIET -dPARANOIDSAFER -dNOPAUSE -dBATCH -sDEVICE=cups -sstdout=%stderr -sOutputFile=%stdout -I/usr/share/cups/fonts -r360x360 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -dcupsBitsPerColor=8 -dcupsColorOrder=0 -dcupsColorSpace=1 -dcupsCompression=1 -scupsPageSizeName=Letter -c -f -_',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] envp[9]="SERVER_ADMIN=root@milo"',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] envp[10]="SOFTWARE=CUPS/1.3.9"',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] envp[11]="TZ=America/Toronto"',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] envp[12]="USER=root"',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] envp[13]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] envp[14]="CUPS_ENCRYPTION=IfRequested"',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] envp[15]="IPP_PORT=631"',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] envp[16]="CHARSET=utf-8"',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] envp[17]="LANG=en_CA.UTF8"',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] envp[18]="PPD=/etc/cups/ppd/NX215.ppd"',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] envp[19]="RIP_MAX_CACHE=8m"',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] envp[20]="CONTENT_TYPE=application/postscript"',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] envp[21]="DEVICE_URI=usb://EPSON/Stylus%20NX210"',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] envp[22]="PRINTER=NX215"',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] envp[23]="FINAL_CONTENT_TYPE=printer/NX215"',
               'D [10/Jan/2010:11:43:48 -0500] PID 4548 (/usr/lib/cups/filter/pdftopdf) exited with no errors.',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] num_components = 1, depth = 1',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] cupsColorSpace = 3, cupsColorOrder = 0',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] cupsBitsPerPixel = 1, cupsBitsPerColor = 1',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] max_gray = 1, dither_grays = 2',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] max_color = 0, dither_colors = 0',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] Updating PageSize to [612 792]...',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] Setting initial media size, [612 792] = 3060x3960 pixels...',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] Setting cupsBitsPerColor to 8...',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] Setting cupsColorOrder to 0...',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] Setting cupsColorSpace to 1...',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] Setting cupsCompression to 1...',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] Setting cupsPageSizeName to "Letter"...',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] num_components = 3, depth = 24',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] cupsColorSpace = 1, cupsColorOrder = 0',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] cupsBitsPerPixel = 24, cupsBitsPerColor = 8',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] max_gray = 0, dither_grays = 0',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] max_color = 255, dither_colors = 256',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] Setting initial media size, [612 792] = 3060x3960 pixels...',
               'I [10/Jan/2010:11:43:48 -0500] Saving subscriptions.conf...',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] num_components = 3, depth = 24',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] cupsColorSpace = 1, cupsColorOrder = 0',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] cupsBitsPerPixel = 24, cupsBitsPerColor = 8',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] max_gray = 0, dither_grays = 0',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] max_color = 255, dither_colors = 256',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] Setting LeadingEdge to 0...',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] num_components = 3, depth = 24',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] cupsColorSpace = 1, cupsColorOrder = 0',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] cupsBitsPerPixel = 24, cupsBitsPerColor = 8',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] max_gray = 0, dither_grays = 0',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] max_color = 255, dither_colors = 256',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] Updating PageSize to [612 792]...',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] size = Letter',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] margins[] = [ 0.116667 0.116667 0.116667 0.116667 ]',
               'D [10/Jan/2010:11:43:48 -0500] PID 4552 (/usr/lib/cups/filter/pdftoraster) exited with no errors.',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] Setting LeadingEdge to 0...',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] num_components = 3, depth = 24',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] cupsColorSpace = 1, cupsColorOrder = 0',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] cupsBitsPerPixel = 24, cupsBitsPerColor = 8',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] max_gray = 0, dither_grays = 0',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] max_color = 255, dither_colors = 256',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] Setting LeadingEdge to 0...',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] num_components = 3, depth = 24',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] cupsColorSpace = 1, cupsColorOrder = 0',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] cupsBitsPerPixel = 24, cupsBitsPerColor = 8',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] max_gray = 0, dither_grays = 0',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] max_color = 255, dither_colors = 256',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] Updating PageSize to [612 792]...',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] size = Letter',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] margins[] = [ 0.116667 0.116667 0.116667 0.116667 ]',
               'D [10/Jan/2010:11:43:48 -0500] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [10/Jan/2010:11:43:48 -0500] cupsdAcceptClient: 13 from localhost (Domain)',
               'D [10/Jan/2010:11:43:48 -0500] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [10/Jan/2010:11:43:48 -0500] cupsdAuthorize: No authentication data provided.',
               'D [10/Jan/2010:11:43:48 -0500] Get-Notifications /',
               'D [10/Jan/2010:11:43:48 -0500] cupsdIsAuthorized: requesting-user-name="asia"',
               'D [10/Jan/2010:11:43:48 -0500] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [10/Jan/2010:11:43:48 -0500] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [10/Jan/2010:11:43:48 -0500] cupsdAuthorize: No authentication data provided.',
               'D [10/Jan/2010:11:43:48 -0500] Get-Notifications /',
               'D [10/Jan/2010:11:43:48 -0500] cupsdIsAuthorized: requesting-user-name="asia"',
               'D [10/Jan/2010:11:43:48 -0500] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)',
               'D [10/Jan/2010:11:43:48 -0500] cupsdReadClient: 14 POST / HTTP/1.1',
               'E [10/Jan/2010:11:43:48 -0500] cupsdAuthorize: Local authentication certificate not found!',
               'D [10/Jan/2010:11:43:48 -0500] Get-Printer-Attributes ipp://localhost/printers/NX215',
               'D [10/Jan/2010:11:43:48 -0500] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)',
               'D [10/Jan/2010:11:43:48 -0500] cupsdCloseClient: 12',
               'D [10/Jan/2010:11:43:48 -0500] cupsdCloseClient: 13',
               'D [10/Jan/2010:11:43:48 -0500] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [10/Jan/2010:11:43:48 -0500] cupsdAuthorize: No authentication data provided.',
               'D [10/Jan/2010:11:43:48 -0500] Get-Notifications /',
               'D [10/Jan/2010:11:43:48 -0500] cupsdIsAuthorized: requesting-user-name="asia"',
               'D [10/Jan/2010:11:43:48 -0500] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] /usr/lib/cups/filter/pipslite-filter: error while loading shared libraries: libltdl.so.3: cannot open shared object file: No such file or directory',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] cups_print_chunked - flip = 0, height = 3876',
               'D [10/Jan/2010:11:43:48 -0500] [Job 46] fwrite: Broken pipe',
               'D [10/Jan/2010:11:43:48 -0500] cupsdCloseClient: 11',
               'E [10/Jan/2010:11:43:48 -0500] PID 4554 (/usr/lib/cups/filter/pipslite-wrapper) stopped with status 8!',
               'D [10/Jan/2010:11:43:48 -0500] PID 4556 (/usr/lib/cups/backend/usb) exited with no errors.',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting AdvanceDistance to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting AdvanceMedia to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting Collate to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting CutMedia to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting Duplex to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting Jog to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting LeadingEdge to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting Margins to 0 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting MirrorPrint to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting NegativePrint to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting OutputFaceUp to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting Separations to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting TraySwitch to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting Tumble to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsMediaType to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsBitsPerColor to 8...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsColorOrder to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsColorSpace to 1...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsCompression to 1...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsRowCount to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsRowFeed to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsRowStep to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsBorderlessScalingFactor to 1.0000...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsInteger0 to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsInteger1 to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsInteger2 to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsInteger3 to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsInteger4 to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsInteger5 to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsInteger6 to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsInteger7 to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsInteger8 to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsInteger9 to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsInteger10 to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsInteger11 to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsInteger12 to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsInteger13 to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsInteger14 to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsInteger15 to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsReal0 to 0.0000...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsReal1 to 0.0000...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsReal2 to 0.0000...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsReal3 to 0.0000...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsReal4 to 0.0000...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsReal5 to 0.0000...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsReal6 to 0.0000...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsReal7 to 0.0000...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsReal8 to 0.0000...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsReal9 to 0.0000...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsReal10 to 0.0000...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsReal11 to 0.0000...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsReal12 to 0.0000...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsReal13 to 0.0000...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsReal14 to 0.0000...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsReal15 to 0.0000...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsString0 to ""...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsString1 to ""...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsString2 to ""...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsString3 to ""...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsString4 to ""...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsString5 to ""...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsString6 to ""...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsString7 to ""...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsString8 to ""...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsString9 to ""...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsString10 to ""...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsString11 to ""...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsString12 to ""...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsString13 to ""...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsString14 to ""...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsString15 to ""...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsMarkerType to ""...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsRenderingIntent to ""...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsPageSizeName to "Letter"...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] num_components = 3, depth = 24',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] cupsColorSpace = 1, cupsColorOrder = 0',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] cupsBitsPerPixel = 24, cupsBitsPerColor = 8',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] max_gray = 0, dither_grays = 0',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] max_color = 255, dither_colors = 256',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Updating PageSize to [612 792]...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] size = Letter',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] margins[] = [ 0.116667 0.116667 0.116667 0.116667 ]',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting AdvanceDistance to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting AdvanceMedia to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting Collate to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting CutMedia to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting Duplex to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting Jog to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting LeadingEdge to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting Margins to 0 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting MirrorPrint to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting NegativePrint to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting OutputFaceUp to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting Separations to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting TraySwitch to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting Tumble to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsMediaType to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsBitsPerColor to 8...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsColorOrder to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsColorSpace to 1...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsCompression to 1...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsRowCount to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsRowFeed to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsRowStep to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsBorderlessScalingFactor to 1.0000...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsInteger0 to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsInteger1 to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsInteger2 to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsInteger3 to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsInteger4 to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsInteger5 to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsInteger6 to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsInteger7 to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsInteger8 to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsInteger9 to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsInteger10 to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsInteger11 to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsInteger12 to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsInteger13 to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsInteger14 to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsInteger15 to 0...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsReal0 to 0.0000...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsReal1 to 0.0000...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsReal2 to 0.0000...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsReal3 to 0.0000...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsReal4 to 0.0000...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsReal5 to 0.0000...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsReal6 to 0.0000...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsReal7 to 0.0000...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsReal8 to 0.0000...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsReal9 to 0.0000...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsReal10 to 0.0000...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsReal11 to 0.0000...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsReal12 to 0.0000...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsReal13 to 0.0000...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsReal14 to 0.0000...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsReal15 to 0.0000...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsString0 to ""...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsString1 to ""...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsString2 to ""...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsString3 to ""...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsString4 to ""...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsString5 to ""...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsString6 to ""...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsString7 to ""...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsString8 to ""...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsString9 to ""...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsString10 to ""...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsString11 to ""...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsString12 to ""...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsString13 to ""...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsString14 to ""...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsString15 to ""...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsMarkerType to ""...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsRenderingIntent to ""...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Setting cupsPageSizeName to "Letter"...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] num_components = 3, depth = 24',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] cupsColorSpace = 1, cupsColorOrder = 0',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] cupsBitsPerPixel = 24, cupsBitsPerColor = 8',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] max_gray = 0, dither_grays = 0',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] max_color = 255, dither_colors = 256',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] Updating PageSize to [612 792]...',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] size = Letter',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] margins[] = [ 0.116667 0.116667 0.116667 0.116667 ]',
               'D [10/Jan/2010:11:43:49 -0500] [Job 46] File 0 is complete.',
               'E [10/Jan/2010:11:43:49 -0500] [Job 46] Job stopped due to filter errors.',
               'I [10/Jan/2010:11:43:49 -0500] Saving subscriptions.conf...',
               'I [10/Jan/2010:11:43:49 -0500] Saving subscriptions.conf...',
               'D [10/Jan/2010:11:43:49 -0500] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [10/Jan/2010:11:43:49 -0500] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [10/Jan/2010:11:43:49 -0500] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [10/Jan/2010:11:43:49 -0500] cupsdAuthorize: No authentication data provided.',
               'D [10/Jan/2010:11:43:49 -0500] Get-Notifications /',
               'D [10/Jan/2010:11:43:49 -0500] cupsdIsAuthorized: requesting-user-name="asia"',
               'D [10/Jan/2010:11:43:49 -0500] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [10/Jan/2010:11:43:49 -0500] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [10/Jan/2010:11:43:49 -0500] cupsdAuthorize: No authentication data provided.',
               'D [10/Jan/2010:11:43:49 -0500] Get-Notifications /',
               'D [10/Jan/2010:11:43:49 -0500] cupsdIsAuthorized: requesting-user-name="asia"',
               'D [10/Jan/2010:11:43:49 -0500] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [10/Jan/2010:11:43:49 -0500] cupsdReadClient: 14 POST / HTTP/1.1',
               'E [10/Jan/2010:11:43:49 -0500] cupsdAuthorize: Local authentication certificate not found!',
               'D [10/Jan/2010:11:43:49 -0500] Get-Printer-Attributes ipp://localhost/printers/NX215',
               'D [10/Jan/2010:11:43:49 -0500] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)',
               'D [10/Jan/2010:11:43:49 -0500] cupsdAcceptClient: 13 from localhost (Domain)',
               'D [10/Jan/2010:11:43:49 -0500] cupsdCloseClient: 9',
               'D [10/Jan/2010:11:43:49 -0500] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [10/Jan/2010:11:43:49 -0500] cupsdAuthorize: No authentication data provided.',
               'D [10/Jan/2010:11:43:49 -0500] Get-Printer-Attributes ipp://milo:631/printers/NX215',
               'D [10/Jan/2010:11:43:49 -0500] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)',
               'D [10/Jan/2010:11:43:49 -0500] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [10/Jan/2010:11:43:49 -0500] cupsdAuthorize: No authentication data provided.',
               'D [10/Jan/2010:11:43:49 -0500] Get-Job-Attributes ipp://localhost/jobs/46',
               'D [10/Jan/2010:11:43:49 -0500] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)',
               'D [10/Jan/2010:11:43:49 -0500] cupsdCloseClient: 12',
               'D [10/Jan/2010:11:43:49 -0500] cupsdCloseClient: 11',
               'D [10/Jan/2010:11:43:49 -0500] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [10/Jan/2010:11:43:49 -0500] cupsdAuthorize: No authentication data provided.',
               'D [10/Jan/2010:11:43:49 -0500] Get-Notifications /',
               'D [10/Jan/2010:11:43:49 -0500] cupsdIsAuthorized: requesting-user-name="asia"',
               'D [10/Jan/2010:11:43:49 -0500] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [10/Jan/2010:11:43:50 -0500] [Job 46] Unloading...',
               'D [10/Jan/2010:11:44:06 -0500] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [10/Jan/2010:11:44:06 -0500] cupsdAuthorize: No authentication data provided.',
               'D [10/Jan/2010:11:44:06 -0500] Get-Job-Attributes ipp://localhost/jobs/44',
               'D [10/Jan/2010:11:44:06 -0500] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [10/Jan/2010:11:44:06 -0500] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [10/Jan/2010:11:44:06 -0500] cupsdAuthorize: No authentication data provided.',
               'D [10/Jan/2010:11:44:06 -0500] Get-Job-Attributes ipp://localhost/jobs/46',
               'D [10/Jan/2010:11:44:06 -0500] [Job 46] Loading attributes...',
               'D [10/Jan/2010:11:44:06 -0500] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [10/Jan/2010:11:44:06 -0500] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [10/Jan/2010:11:44:06 -0500] cupsdAuthorize: No authentication data provided.',
               'D [10/Jan/2010:11:44:06 -0500] Cancel-Subscription /',
               'D [10/Jan/2010:11:44:06 -0500] cupsdIsAuthorized: requesting-user-name="asia"',
               'I [10/Jan/2010:11:44:06 -0500] Saving subscriptions.conf...',
               'D [10/Jan/2010:11:44:06 -0500] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [10/Jan/2010:11:44:06 -0500] cupsdAcceptClient: 9 from localhost (Domain)',
               'D [10/Jan/2010:11:44:06 -0500] cupsdReadClient: 9 GET /admin/log/error_log HTTP/1.1',
               'D [10/Jan/2010:11:44:06 -0500] cupsdAuthorize: No authentication data provided.'],
 'error_log_debug_logging_unset': True}
Page 11 (Locale issues):
{'printer_page_size': u'Letter',
 'system_locale_lang': None,
 'user_locale_ctype': 'en_CA',
 'user_locale_messages': 'en_CA'}

---

### Post by LinuxDeal on 2010-01-10
[http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)
seems like a better way to go.

---

### Post by jolitical on 2010-01-10
i tried that, it didn't work because of a broken package

---

### Post by LinuxDeal on 2010-01-10
OK, well that log is not very helpful for me at least.  Probably something got messed up along the way during the install process.  Did all the setps complete successfully without errors?  Keep in mind that not a lot a people are going to look at a thread marked "solved".

---

### Post by jolitical on 2010-01-10
you make a good point about this being a solved thread, this just seemed like the most relevant place to post my question. 
i got stuck when i tried to install the ppd file. i also don't have the directory /model/ and /ppd/ to place the file into.

please excuse my complete lack of knowledge in this stuff.

---

### Post by LinuxDeal on 2010-01-10
I am not familiar with installing this driver.
However you can make directories from the terminal with the mkdir command.
For instance, this command will create a directory called ppd in /usr/share/
```
sudo mkdir /usr/share/ppd
```

If you need to move a file, you can use the mv command
For instance this will move printer.ppd to /usr/share/ppd
```
sudo mv printer.ppd /usr/share/ppd/
```

"sudo" is used because you are changing system files and need the appropriate permission to do so.  You will need to enter your password at the prompt and hit enter.

If you let me know what exactly you need to do I can probably help.

Kind regards

---

### Post by jolitical on 2010-01-11
thank you for your help!

the error message i get now is:
/usr/ lib/cups/filter/pipslite-wrapper failed

does that mean anything to you?

---

### Post by LinuxDeal on 2010-01-11
nope, maybe this will help: [http://blogs.gnome.org/bolsh/2009/05/26/trial-by-fire-distro-upgrade/](http://blogs.gnome.org/bolsh/2009/05/26/trial-by-fire-distro-upgrade/)

---

### Post by malibusurfer2 on 2010-02-14
Looking for help regarding Epson NX415 3-in-one printer on Ubuntu 9.04. The printer and scanner work fine, but every time I turn it on, Ubuntu thinks it is a new device and starts looking for driver to add it to list of printers. If I let it and pick the printer model, it adds the Epson as a new duplicate printer. If I cancel the search to add a new printer, my printer still works fine. Why does it keep looking to add it? Thanks for your help.

---

### Post by Ryanmt on 2010-09-01
> **LinuxDeal said:**
> [http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)
seems like a better way to go.

Fianlly stopped my SX415 spewing blank pages by downloading the deb in the link and reinstalling the printer to use the new drives. Thanks :)

---

### Post by Mahngiel on 2010-11-19
> **linuxdeal said:**
> [http://www.avasys.jp/lx-bin2/linux_e/spc/dl1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/dl1.do)
seems like a better way to go.

+1

---

### Post by malandro23 on 2011-01-04
> **LinuxDeal said:**
> [http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)
seems like a better way to go.

+2
Thanks!

---

### Post by SVEN1 on 2011-01-30
Had the same problems.
Downloaded the following and installed it.
[http://linux.avasys.jp/drivers/lsb/epson-inkjet/stable/debian/dists/lsb3.2/main/binary-i386/epson-inkjet-printer-escpr_1.0.1-1lsb3.2_i386.deb]("http://linux.avasys.jp/drivers/lsb/epson-inkjet/stable/debian/dists/lsb3.2/main/binary-i386/epson-inkjet-printer-escpr_1.0.1-1lsb3.2_i386.deb")

Plugged the printer in and it works!! But, Ubuntu 10.04 sees it as an Epson NX210
:p

---

