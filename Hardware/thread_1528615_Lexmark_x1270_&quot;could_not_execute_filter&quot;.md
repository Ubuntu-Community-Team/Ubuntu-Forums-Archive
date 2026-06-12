---
title: "Lexmark x1270 &quot;could not execute filter&quot;"
date: 2010-07-11
forum: Hardware
---

### Post by VietCanada on 2010-07-11
My Lexmark x1270 worked fine with Koala version but after upgrading to Lucid and following the most recent instructions I could find on this site I cannot print.

I get an error message "Stopping job because the scheduler could not execute a filter." Clicking on the "Diagnose" leads to the message that *rasteroz600 *is required but not installed. I've searched all over this forum.

Debug gives me this list:

```
D [11/Jul/2010:11:14:46 +0700] cupsdSetBusyState: Dirty files
D [11/Jul/2010:11:14:46 +0700] cupsdReadClient: 12 POST / HTTP/1.1
D [11/Jul/2010:11:14:46 +0700] cupsdSetBusyState: Active clients and dirty files
D [11/Jul/2010:11:14:46 +0700] cupsdAuthorize: No authentication data provided.
D [11/Jul/2010:11:14:46 +0700] cupsdReadClient: 12 1.1 Get-Jobs 1
D [11/Jul/2010:11:14:46 +0700] Get-Jobs ipp://localhost/printers/
D [11/Jul/2010:11:14:46 +0700] [Job 1] Loading attributes...
D [11/Jul/2010:11:14:46 +0700] [Job 5] Loading attributes...
D [11/Jul/2010:11:14:46 +0700] [Job 6] Loading attributes...
D [11/Jul/2010:11:14:46 +0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [11/Jul/2010:11:14:46 +0700] cupsdSetBusyState: Dirty files
D [11/Jul/2010:11:14:46 +0700] cupsdReadClient: 12 POST / HTTP/1.1
D [11/Jul/2010:11:14:46 +0700] cupsdSetBusyState: Active clients and dirty files
D [11/Jul/2010:11:14:46 +0700] cupsdAuthorize: No authentication data provided.
D [11/Jul/2010:11:14:46 +0700] cupsdReadClient: 12 1.1 Get-Jobs 1
D [11/Jul/2010:11:14:46 +0700] Get-Jobs ipp://localhost/printers/
D [11/Jul/2010:11:14:46 +0700] [Job 2] Loading attributes...
D [11/Jul/2010:11:14:47 +0700] [Job 3] Loading attributes...
D [11/Jul/2010:11:14:47 +0700] [Job 4] Loading attributes...
D [11/Jul/2010:11:14:47 +0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [11/Jul/2010:11:14:47 +0700] cupsdSetBusyState: Dirty files
D [11/Jul/2010:11:14:47 +0700] cupsdReadClient: 12 POST / HTTP/1.1
D [11/Jul/2010:11:14:47 +0700] cupsdSetBusyState: Active clients and dirty files
D [11/Jul/2010:11:14:47 +0700] cupsdAuthorize: No authentication data provided.
D [11/Jul/2010:11:14:47 +0700] cupsdReadClient: 12 1.1 Create-Printer-Subscription 1
D [11/Jul/2010:11:14:47 +0700] Create-Printer-Subscription /
D [11/Jul/2010:11:14:47 +0700] cupsdCreateSubscription(con=0x213913a0(12), uri="/")
D [11/Jul/2010:11:14:47 +0700] pullmethod="ippget"
D [11/Jul/2010:11:14:47 +0700] notify-lease-duration=86400
D [11/Jul/2010:11:14:47 +0700] notify-time-interval=0
D [11/Jul/2010:11:14:47 +0700] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")
D [11/Jul/2010:11:14:47 +0700] Added subscription 16 for server
D [11/Jul/2010:11:14:47 +0700] cupsdMarkDirty(-----S)
D [11/Jul/2010:11:14:47 +0700] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost
D [11/Jul/2010:11:14:47 +0700] cupsdSetBusyState: Dirty files
D [11/Jul/2010:11:14:48 +0700] cupsdReadClient: 12 POST / HTTP/1.1
D [11/Jul/2010:11:14:48 +0700] cupsdSetBusyState: Active clients and dirty files
D [11/Jul/2010:11:14:48 +0700] cupsdAuthorize: No authentication data provided.
D [11/Jul/2010:11:14:48 +0700] cupsdReadClient: 12 1.1 Get-Notifications 1
D [11/Jul/2010:11:14:48 +0700] Get-Notifications /
D [11/Jul/2010:11:14:48 +0700] cupsdIsAuthorized: requesting-user-name="don"
D [11/Jul/2010:11:14:48 +0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [11/Jul/2010:11:14:48 +0700] cupsdSetBusyState: Dirty files
D [11/Jul/2010:11:14:48 +0700] cupsdAcceptClient: 14 from localhost (Domain)
D [11/Jul/2010:11:14:49 +0700] cupsdReadClient: 14 POST /printers/Lexmark HTTP/1.1
D [11/Jul/2010:11:14:49 +0700] cupsdSetBusyState: Active clients and dirty files
D [11/Jul/2010:11:14:49 +0700] cupsdAuthorize: No authentication data provided.
D [11/Jul/2010:11:14:49 +0700] cupsdReadClient: 14 1.1 Print-Job 1
D [11/Jul/2010:11:14:49 +0700] Print-Job ipp://localhost/printers/Lexmark
D [11/Jul/2010:11:14:49 +0700] [Job ???] Auto-typing file...
I [11/Jul/2010:11:14:49 +0700] [Job ???] Request file type is application/vnd.cups-banner.
D [11/Jul/2010:11:14:49 +0700] cupsdMarkDirty(----J-)
D [11/Jul/2010:11:14:49 +0700] add_job: requesting-user-name="don"
D [11/Jul/2010:11:14:49 +0700] Adding default job-sheets values "none,none"...
I [11/Jul/2010:11:14:49 +0700] [Job 7] Adding start banner page "none".
D [11/Jul/2010:11:14:49 +0700] cupsdMarkDirty(-----S)
D [11/Jul/2010:11:14:49 +0700] cupsdMarkDirty(----J-)
I [11/Jul/2010:11:14:49 +0700] [Job 7] Adding end banner page "none".
I [11/Jul/2010:11:14:49 +0700] [Job 7] File of type application/vnd.cups-banner queued by "don".
D [11/Jul/2010:11:14:49 +0700] [Job 7] hold_until=0
I [11/Jul/2010:11:14:49 +0700] [Job 7] Queued on "Lexmark" by "don".
D [11/Jul/2010:11:14:49 +0700] cupsdMarkDirty(----J-)
D [11/Jul/2010:11:14:49 +0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jul/2010:11:14:49 +0700] cupsdMarkDirty(-----S)
D [11/Jul/2010:11:14:49 +0700] [Job 7] job-sheets=none,none
D [11/Jul/2010:11:14:49 +0700] [Job 7] argv[0]="Lexmark"
D [11/Jul/2010:11:14:49 +0700] [Job 7] argv[1]="7"
D [11/Jul/2010:11:14:49 +0700] [Job 7] argv[2]="don"
D [11/Jul/2010:11:14:49 +0700] [Job 7] argv[3]="Test Page"
D [11/Jul/2010:11:14:49 +0700] [Job 7] argv[4]="1"
D [11/Jul/2010:11:14:49 +0700] [Job 7] argv[5]="job-uuid=urn:uuid:d7fdd334-4b7a-3458-7660-b4bc5760b24f job-originating-host-name=localhost"
D [11/Jul/2010:11:14:49 +0700] [Job 7] argv[6]="/var/spool/cups/d00007-001"
D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[8]="HOME=/var/spool/cups/tmp"
D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[10]="SERVER_ADMIN=root@VietCanada"
D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[11]="SOFTWARE=CUPS/1.4.3"
D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[13]="TZ=Asia/Ho_Chi_Minh"
D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[14]="USER=root"
D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[17]="IPP_PORT=631"
D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[18]="CHARSET=utf-8"
D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[19]="LANG=en_US.UTF-8"
D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[20]="PPD=/etc/cups/ppd/Lexmark.ppd"
D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[21]="RIP_MAX_CACHE=771817k"
D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[22]="CONTENT_TYPE=application/vnd.cups-banner"
D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[23]="DEVICE_URI=usb://Lexmark/1200%20Series"
D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[24]="PRINTER_INFO=Lexmark  x1270"
D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[25]="PRINTER_LOCATION=VietCanada"
D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[26]="PRINTER=Lexmark"
D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[27]="CUPS_FILETYPE=document"
D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[28]="FINAL_CONTENT_TYPE=printer/Lexmark"
I [11/Jul/2010:11:14:49 +0700] [Job 7] Started filter /usr/lib/cups/filter/bannertops (PID 7696)
I [11/Jul/2010:11:14:49 +0700] [Job 7] Started filter /usr/lib/cups/filter/pstopdf (PID 7697)
I [11/Jul/2010:11:14:49 +0700] [Job 7] Started filter /usr/lib/cups/filter/pdftopdf (PID 7698)
I [11/Jul/2010:11:14:49 +0700] [Job 7] Started filter /usr/lib/cups/filter/pdftoraster (PID 7699)
E [11/Jul/2010:11:14:49 +0700] Unable to execute /usr/lib/cups/filter/rastertoz600: No such file or directory
E [11/Jul/2010:11:14:49 +0700] [Job 7] Unable to start filter "rastertoz600" - Success.
D [11/Jul/2010:11:14:49 +0700] cupsdMarkDirty(-----S)
E [11/Jul/2010:11:14:49 +0700] [Job 7] Stopping job because the scheduler could not execute a filter.
D [11/Jul/2010:11:14:49 +0700] cupsdMarkDirty(----J-)
D [11/Jul/2010:11:14:49 +0700] cupsdMarkDirty(-----S)
D [11/Jul/2010:11:14:49 +0700] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/Lexmark) from localhost
D [11/Jul/2010:11:14:49 +0700] PID 7696 (/usr/lib/cups/filter/bannertops) was terminated normally with signal 15.
D [11/Jul/2010:11:14:49 +0700] PID 7697 (/usr/lib/cups/filter/pstopdf) was terminated normally with signal 15.
D [11/Jul/2010:11:14:49 +0700] cupsdSetBusyState: Dirty files
D [11/Jul/2010:11:14:49 +0700] PID 7698 (/usr/lib/cups/filter/pdftopdf) was terminated normally with signal 15.
D [11/Jul/2010:11:14:49 +0700] PID 7699 (/usr/lib/cups/filter/pdftoraster) was terminated normally with signal 15.
D [11/Jul/2010:11:14:49 +0700] cupsdAcceptClient: 15 from localhost (Domain)
D [11/Jul/2010:11:14:49 +0700] cupsdReadClient: 15 POST / HTTP/1.1
D [11/Jul/2010:11:14:49 +0700] cupsdSetBusyState: Active clients and dirty files
D [11/Jul/2010:11:14:49 +0700] cupsdAuthorize: No authentication data provided.
D [11/Jul/2010:11:14:49 +0700] cupsdReadClient: 15 1.1 Get-Notifications 1
D [11/Jul/2010:11:14:49 +0700] Get-Notifications /
D [11/Jul/2010:11:14:49 +0700] cupsdIsAuthorized: requesting-user-name="don"
D [11/Jul/2010:11:14:49 +0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [11/Jul/2010:11:14:49 +0700] cupsdSetBusyState: Dirty files
D [11/Jul/2010:11:14:49 +0700] cupsdReadClient: 15 POST / HTTP/1.1
D [11/Jul/2010:11:14:49 +0700] cupsdSetBusyState: Active clients and dirty files
D [11/Jul/2010:11:14:49 +0700] cupsdAuthorize: No authentication data provided.
D [11/Jul/2010:11:14:49 +0700] cupsdReadClient: 15 1.1 Get-Job-Attributes 1
D [11/Jul/2010:11:14:49 +0700] Get-Job-Attributes ipp://localhost/jobs/7
D [11/Jul/2010:11:14:49 +0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/7) from localhost
D [11/Jul/2010:11:14:49 +0700] cupsdSetBusyState: Dirty files
D [11/Jul/2010:11:14:49 +0700] cupsdAcceptClient: 16 from localhost (Domain)
D [11/Jul/2010:11:14:49 +0700] cupsdReadClient: 16 POST / HTTP/1.1
D [11/Jul/2010:11:14:49 +0700] cupsdSetBusyState: Active clients and dirty files
D [11/Jul/2010:11:14:49 +0700] cupsdAuthorize: No authentication data provided.
D [11/Jul/2010:11:14:49 +0700] cupsdReadClient: 16 1.1 Get-Printer-Attributes 1
D [11/Jul/2010:11:14:49 +0700] Get-Printer-Attributes ipp://VietCanada:631/printers/Lexmark
D [11/Jul/2010:11:14:49 +0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://VietCanada:631/printers/Lexmark) from localhost
D [11/Jul/2010:11:14:49 +0700] cupsdSetBusyState: Dirty files
D [11/Jul/2010:11:14:49 +0700] cupsdReadClient: 16 POST / HTTP/1.1
D [11/Jul/2010:11:14:49 +0700] cupsdSetBusyState: Active clients and dirty files
D [11/Jul/2010:11:14:49 +0700] cupsdAuthorize: No authentication data provided.
D [11/Jul/2010:11:14:49 +0700] cupsdReadClient: 16 1.1 Get-Job-Attributes 1
D [11/Jul/2010:11:14:49 +0700] Get-Job-Attributes ipp://localhost/jobs/7
D [11/Jul/2010:11:14:49 +0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/7) from localhost
D [11/Jul/2010:11:14:49 +0700] cupsdSetBusyState: Dirty files
D [11/Jul/2010:11:14:49 +0700] cupsdReadClient: 12 POST / HTTP/1.1
D [11/Jul/2010:11:14:49 +0700] cupsdSetBusyState: Active clients and dirty files
D [11/Jul/2010:11:14:49 +0700] cupsdAuthorize: No authentication data provided.
D [11/Jul/2010:11:14:49 +0700] cupsdReadClient: 12 1.1 Get-Notifications 1
D [11/Jul/2010:11:14:49 +0700] Get-Notifications /
D [11/Jul/2010:11:14:49 +0700] cupsdIsAuthorized: requesting-user-name="don"
D [11/Jul/2010:11:14:49 +0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [11/Jul/2010:11:14:49 +0700] cupsdSetBusyState: Dirty files
D [11/Jul/2010:11:14:49 +0700] cupsdAcceptClient: 17 from localhost (Domain)
D [11/Jul/2010:11:14:49 +0700] cupsdReadClient: 17 POST / HTTP/1.1
D [11/Jul/2010:11:14:49 +0700] cupsdSetBusyState: Active clients and dirty files
D [11/Jul/2010:11:14:49 +0700] cupsdAuthorize: No authentication data provided.
D [11/Jul/2010:11:14:49 +0700] cupsdReadClient: 17 1.1 Get-Printer-Attributes 1
D [11/Jul/2010:11:14:49 +0700] Get-Printer-Attributes ipp://VietCanada:631/printers/Lexmark
D [11/Jul/2010:11:14:49 +0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://VietCanada:631/printers/Lexmark) from localhost
D [11/Jul/2010:11:14:49 +0700] cupsdSetBusyState: Dirty files
D [11/Jul/2010:11:14:49 +0700] cupsdReadClient: 17 POST / HTTP/1.1
D [11/Jul/2010:11:14:49 +0700] cupsdSetBusyState: Active clients and dirty files
D [11/Jul/2010:11:14:49 +0700] cupsdAuthorize: No authentication data provided.
D [11/Jul/2010:11:14:49 +0700] cupsdReadClient: 17 1.1 Get-Job-Attributes 1
D [11/Jul/2010:11:14:49 +0700] Get-Job-Attributes ipp://localhost/jobs/7
D [11/Jul/2010:11:14:49 +0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/7) from localhost
D [11/Jul/2010:11:14:49 +0700] cupsdSetBusyState: Dirty files
D [11/Jul/2010:11:14:50 +0700] [Job 7] Unloading...
D [11/Jul/2010:11:14:55 +0700] cupsdReadClient: 12 POST / HTTP/1.1
D [11/Jul/2010:11:14:55 +0700] cupsdSetBusyState: Active clients and dirty files
D [11/Jul/2010:11:14:55 +0700] cupsdAuthorize: No authentication data provided.
D [11/Jul/2010:11:14:55 +0700] cupsdReadClient: 12 1.1 Get-Job-Attributes 1
D [11/Jul/2010:11:14:55 +0700] Get-Job-Attributes ipp://localhost/jobs/7
D [11/Jul/2010:11:14:55 +0700] [Job 7] Loading attributes...
D [11/Jul/2010:11:14:55 +0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/7) from localhost
D [11/Jul/2010:11:14:55 +0700] cupsdSetBusyState: Dirty files
D [11/Jul/2010:11:14:55 +0700] cupsdReadClient: 12 POST / HTTP/1.1
D [11/Jul/2010:11:14:55 +0700] cupsdSetBusyState: Active clients and dirty files
D [11/Jul/2010:11:14:55 +0700] cupsdAuthorize: No authentication data provided.
D [11/Jul/2010:11:14:55 +0700] cupsdReadClient: 12 1.1 Cancel-Subscription 1
D [11/Jul/2010:11:14:55 +0700] Cancel-Subscription /
D [11/Jul/2010:11:14:55 +0700] cupsdIsAuthorized: requesting-user-name="don"
D [11/Jul/2010:11:14:55 +0700] cupsdMarkDirty(-----S)
D [11/Jul/2010:11:14:55 +0700] Returning IPP successful-ok for Cancel-Subscription (/) from localhost
D [11/Jul/2010:11:14:55 +0700] cupsdSetBusyState: Dirty files
D [11/Jul/2010:11:14:55 +0700] cupsdAcceptClient: 18 from localhost (Domain)
D [11/Jul/2010:11:14:55 +0700] cupsdReadClient: 18 GET /admin/log/error_log HTTP/1.1
D [11/Jul/2010:11:14:55 +0700] cupsdSetBusyState: Active clients and dirty files
D [11/Jul/2010:11:14:55 +0700] cupsdAuthorize: No authentication data provided.
```

Sorry I don't the code to put that in a window.

Advanced diagnostic output gives this list:

```
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Is local server publishing?):
{'local_server_exporting_printers': False}
Page 3 (Choose printer):
{'cups_dest': <cups.Dest Lexmark (default)>,
 'cups_instance': None,
 'cups_queue': 'Lexmark',
 'cups_queue_listed': True}
Page 4 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://Lexmark/1200%20Series',
                       'printer-info': u'Lexmark  x1270',
                       'printer-is-shared': True,
                       'printer-location': u'VietCanada',
                       'printer-make-and-model': u'Lexmark Z600 v1.0-1',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'cups-missing-filter-warning'],
                       'printer-type': 167948,
                       'printer-uri-supported': u'ipp://localhost:631/printers/Lexmark'},
 'cups_printer_remote': False,
 'is_cups_class': False,
 'local_cups_queue_attributes': {'auth-info-required': u'none',
                                 'charset-configured': u'utf-8',
                                 'charset-supported': [u'us-ascii', u'utf-8'],
                                 'color-supported': True,
                                 'compression-supported': [u'none', u'gzip'],
                                 'copies-default': 1,
                                 'copies-supported': (1, 9999),
                                 'cups-version': u'1.4.3',
                                 'device-uri': u'usb://Lexmark/1200%20Series',
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
                                                     u'iso_a4_210x297mm',
                                                     u'na_invoice_5.5x8.5in',
                                                     u'na_legal_8.5x14in',
                                                     u'jis_b5_182x257mm',
                                                     u'na_executive_7.25x10.5in',
                                                     u'iso_a5_148x210mm',
                                                     u'iso_a6_105x148mm',
                                                     u'na_index-3x5_3x5in',
                                                     u'na_index-4x6_4x6in',
                                                     u'jpn_hagaki_100x148mm',
                                                     u'na_personal_3.625x6.5in',
                                                     u'na_number-9_3.875x8.875in',
                                                     u'na_number-10_4.125x9.5in',
                                                     u'iso_dl_110x220mm',
                                                     u'iso_c5_162x229mm',
                                                     u'iso_c6_114x162mm',
                                                     u'iso_b5_176x250mm',
                                                     u'na_monarch_3.875x7.5in',
                                                     u'na_a2_4.375x5.75in',
                                                     u'jpn_chou3_120x235mm',
                                                     u'jpn_chou4_90x205mm',
                                                     u'adobe_Chokei40_89.9583x240.947mm',
                                                     u'adobe_Kakugata3_8.5x10.9028in',
                                                     u'adobe_Kakugata4_7.75x10.5139in',
                                                     u'adobe_Kakugata5_190.147x239.889mm',
                                                     u'iso_c5_162x229mm',
                                                     u'adobe_L_3.5x5in',
                                                     u'na_5x7_5x7in',
                                                     u'custom_min_2x4in',
                                                     u'custom_max_8.58333x13in'],
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
                                 'printer-info': u'Lexmark  x1270',
                                 'printer-is-accepting-jobs': True,
                                 'printer-is-shared': True,
                                 'printer-location': u'VietCanada',
                                 'printer-make-and-model': u'Lexmark Z600 v1.0-1',
                                 'printer-more-info': u'http://localhost:631/printers/Lexmark',
                                 'printer-name': u'Lexmark',
                                 'printer-op-policy': u'default',
                                 'printer-op-policy-supported': [u'authenticated',
                                                                 u'default'],
                                 'printer-settable-attributes-supported': [u'printer-info',
                                                                           u'printer-location'],
                                 'printer-state': 3,
                                 'printer-state-change-time': 1278821556,
                                 'printer-state-message': u'',
                                 'printer-state-reasons': [u'cups-missing-filter-warning'],
                                 'printer-type': 167948,
                                 'printer-up-time': 1278821567,
                                 'printer-uri-supported': [u'ipp://localhost:631/printers/Lexmark'],
                                 'queued-job-count': 3,
                                 'server-is-sharing-printers': True,
                                 'uri-authentication-supported': [u'requesting-user-name'],
                                 'uri-security-supported': [u'none']}}
Page 5 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'MediaType': u'Plain',
                                            u'PageRegion': u'Letter',
                                            u'PageSize': u'Letter'},
                               u'Others': {u'ColorModel': u'Color',
                                           u'Inkset': u'CMY',
                                           u'PrintQuality': u'Normal'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], ['rastertoz600'])}
Page 6 (Local or remote?):
{'printer_is_remote': False}
Page 7 (Choose device):
{'cups_device_dict': {'device-class': u'direct',
                      'device-id': u'MFG:Lexmark ;CMD:CPDNPA001;MODEL:1200 Series;CLASS:Printer;DES:Lexmark 1200 Series;COMMENT:060309-1;',
                      'device-info': u'Lexmark 1200 Series',
                      'device-location': u'',
                      'device-make-and-model': u'Lexmark 1200 Series'}}
Page 8 (Printer state reasons):
{'printer-state-message': u'',
 'printer-state-reasons': [u'cups-missing-filter-warning']}
Page 9 (Error log checkpoint):
{'cups_server_settings': {'BrowseLocalProtocols': 'CUPS dnssd',
                          'BrowseRemoteProtocols': 'CUPS',
                          'DefaultAuthType': 'Basic',
                          'MaxLogSize': '0',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '0',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '1',
                          '_share_printers': '1',
                          '_user_cancel_any': '1'},
 'error_log_checkpoint': 27718L,
 'error_log_debug_logging_set': True}
Page 10 (Print test page):
{'test_page_attempted': '11/Jul/2010:11:14:48 +0000',
 'test_page_job_id': [7],
 'test_page_job_status': [(True,
                           7,
                           'Lexmark',
                           'Test Page',
                           'Stopped',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-us',
                            'document-count': 1,
                            'document-format': u'application/vnd.cups-banner',
                            'job-hold-until': u'no-hold',
                            'job-id': 7,
                            'job-k-octets': 1,
                            'job-media-progress': 0,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/7',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'don',
                            'job-preserved': True,
                            'job-printer-state-message': u'',
                            'job-printer-state-reasons': [u'cups-missing-filter-warning'],
                            'job-printer-up-time': 1278821695,
                            'job-printer-uri': u'ipp://VietCanada:631/printers/Lexmark',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 6,
                            'job-state-reasons': u'job-stopped',
                            'job-uri': u'ipp://localhost:631/jobs/7',
                            'job-uuid': u'urn:uuid:d7fdd334-4b7a-3458-7660-b4bc5760b24f',
                            'printer-uri': u'ipp://localhost/printers/Lexmark',
                            'time-at-completed': None,
                            'time-at-creation': 1278821689,
                            'time-at-processing': 1278821689})],
 'test_page_successful': False}
Page 11 (Error log fetch):
{'error_log': ['D [11/Jul/2010:11:14:46 +0700] cupsdSetBusyState: Dirty files',
               'D [11/Jul/2010:11:14:46 +0700] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [11/Jul/2010:11:14:46 +0700] cupsdSetBusyState: Active clients and dirty files',
               'D [11/Jul/2010:11:14:46 +0700] cupsdAuthorize: No authentication data provided.',
               'D [11/Jul/2010:11:14:46 +0700] cupsdReadClient: 12 1.1 Get-Jobs 1',
               'D [11/Jul/2010:11:14:46 +0700] Get-Jobs ipp://localhost/printers/',
               'D [11/Jul/2010:11:14:46 +0700] [Job 1] Loading attributes...',
               'D [11/Jul/2010:11:14:46 +0700] [Job 5] Loading attributes...',
               'D [11/Jul/2010:11:14:46 +0700] [Job 6] Loading attributes...',
               'D [11/Jul/2010:11:14:46 +0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [11/Jul/2010:11:14:46 +0700] cupsdSetBusyState: Dirty files',
               'D [11/Jul/2010:11:14:46 +0700] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [11/Jul/2010:11:14:46 +0700] cupsdSetBusyState: Active clients and dirty files',
               'D [11/Jul/2010:11:14:46 +0700] cupsdAuthorize: No authentication data provided.',
               'D [11/Jul/2010:11:14:46 +0700] cupsdReadClient: 12 1.1 Get-Jobs 1',
               'D [11/Jul/2010:11:14:46 +0700] Get-Jobs ipp://localhost/printers/',
               'D [11/Jul/2010:11:14:46 +0700] [Job 2] Loading attributes...',
               'D [11/Jul/2010:11:14:47 +0700] [Job 3] Loading attributes...',
               'D [11/Jul/2010:11:14:47 +0700] [Job 4] Loading attributes...',
               'D [11/Jul/2010:11:14:47 +0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [11/Jul/2010:11:14:47 +0700] cupsdSetBusyState: Dirty files',
               'D [11/Jul/2010:11:14:47 +0700] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [11/Jul/2010:11:14:47 +0700] cupsdSetBusyState: Active clients and dirty files',
               'D [11/Jul/2010:11:14:47 +0700] cupsdAuthorize: No authentication data provided.',
               'D [11/Jul/2010:11:14:47 +0700] cupsdReadClient: 12 1.1 Create-Printer-Subscription 1',
               'D [11/Jul/2010:11:14:47 +0700] Create-Printer-Subscription /',
               'D [11/Jul/2010:11:14:47 +0700] cupsdCreateSubscription(con=0x213913a0(12), uri="/")',
               'D [11/Jul/2010:11:14:47 +0700] pullmethod="ippget"',
               'D [11/Jul/2010:11:14:47 +0700] notify-lease-duration=86400',
               'D [11/Jul/2010:11:14:47 +0700] notify-time-interval=0',
               'D [11/Jul/2010:11:14:47 +0700] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [11/Jul/2010:11:14:47 +0700] Added subscription 16 for server',
               'D [11/Jul/2010:11:14:47 +0700] cupsdMarkDirty(-----S)',
               'D [11/Jul/2010:11:14:47 +0700] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost',
               'D [11/Jul/2010:11:14:47 +0700] cupsdSetBusyState: Dirty files',
               'D [11/Jul/2010:11:14:48 +0700] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [11/Jul/2010:11:14:48 +0700] cupsdSetBusyState: Active clients and dirty files',
               'D [11/Jul/2010:11:14:48 +0700] cupsdAuthorize: No authentication data provided.',
               'D [11/Jul/2010:11:14:48 +0700] cupsdReadClient: 12 1.1 Get-Notifications 1',
               'D [11/Jul/2010:11:14:48 +0700] Get-Notifications /',
               'D [11/Jul/2010:11:14:48 +0700] cupsdIsAuthorized: requesting-user-name="don"',
               'D [11/Jul/2010:11:14:48 +0700] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [11/Jul/2010:11:14:48 +0700] cupsdSetBusyState: Dirty files',
               'D [11/Jul/2010:11:14:48 +0700] cupsdAcceptClient: 14 from localhost (Domain)',
               'D [11/Jul/2010:11:14:49 +0700] cupsdReadClient: 14 POST /printers/Lexmark HTTP/1.1',
               'D [11/Jul/2010:11:14:49 +0700] cupsdSetBusyState: Active clients and dirty files',
               'D [11/Jul/2010:11:14:49 +0700] cupsdAuthorize: No authentication data provided.',
               'D [11/Jul/2010:11:14:49 +0700] cupsdReadClient: 14 1.1 Print-Job 1',
               'D [11/Jul/2010:11:14:49 +0700] Print-Job ipp://localhost/printers/Lexmark',
               'D [11/Jul/2010:11:14:49 +0700] [Job ???] Auto-typing file...',
               'I [11/Jul/2010:11:14:49 +0700] [Job ???] Request file type is application/vnd.cups-banner.',
               'D [11/Jul/2010:11:14:49 +0700] cupsdMarkDirty(----J-)',
               'D [11/Jul/2010:11:14:49 +0700] add_job: requesting-user-name="don"',
               'D [11/Jul/2010:11:14:49 +0700] Adding default job-sheets values "none,none"...',
               'I [11/Jul/2010:11:14:49 +0700] [Job 7] Adding start banner page "none".',
               'D [11/Jul/2010:11:14:49 +0700] cupsdMarkDirty(-----S)',
               'D [11/Jul/2010:11:14:49 +0700] cupsdMarkDirty(----J-)',
               'I [11/Jul/2010:11:14:49 +0700] [Job 7] Adding end banner page "none".',
               'I [11/Jul/2010:11:14:49 +0700] [Job 7] File of type application/vnd.cups-banner queued by "don".',
               'D [11/Jul/2010:11:14:49 +0700] [Job 7] hold_until=0',
               'I [11/Jul/2010:11:14:49 +0700] [Job 7] Queued on "Lexmark" by "don".',
               'D [11/Jul/2010:11:14:49 +0700] cupsdMarkDirty(----J-)',
               'D [11/Jul/2010:11:14:49 +0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [11/Jul/2010:11:14:49 +0700] cupsdMarkDirty(-----S)',
               'D [11/Jul/2010:11:14:49 +0700] [Job 7] job-sheets=none,none',
               'D [11/Jul/2010:11:14:49 +0700] [Job 7] argv[0]="Lexmark"',
               'D [11/Jul/2010:11:14:49 +0700] [Job 7] argv[1]="7"',
               'D [11/Jul/2010:11:14:49 +0700] [Job 7] argv[2]="don"',
               'D [11/Jul/2010:11:14:49 +0700] [Job 7] argv[3]="Test Page"',
               'D [11/Jul/2010:11:14:49 +0700] [Job 7] argv[4]="1"',
               'D [11/Jul/2010:11:14:49 +0700] [Job 7] argv[5]="job-uuid=urn:uuid:d7fdd334-4b7a-3458-7660-b4bc5760b24f job-originating-host-name=localhost"',
               'D [11/Jul/2010:11:14:49 +0700] [Job 7] argv[6]="/var/spool/cups/d00007-001"',
               'D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[8]="HOME=/var/spool/cups/tmp"',
               'D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[10]="SERVER_ADMIN=root@VietCanada"',
               'D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[11]="SOFTWARE=CUPS/1.4.3"',
               'D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[12]="TMPDIR=/var/spool/cups/tmp"',
               'D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[13]="TZ=Asia/Ho_Chi_Minh"',
               'D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[14]="USER=root"',
               'D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[16]="CUPS_ENCRYPTION=IfRequested"',
               'D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[17]="IPP_PORT=631"',
               'D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[18]="CHARSET=utf-8"',
               'D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[19]="LANG=en_US.UTF-8"',
               'D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[20]="PPD=/etc/cups/ppd/Lexmark.ppd"',
               'D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[21]="RIP_MAX_CACHE=771817k"',
               'D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[22]="CONTENT_TYPE=application/vnd.cups-banner"',
               'D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[23]="DEVICE_URI=usb://Lexmark/1200%20Series"',
               'D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[24]="PRINTER_INFO=Lexmark  x1270"',
               'D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[25]="PRINTER_LOCATION=VietCanada"',
               'D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[26]="PRINTER=Lexmark"',
               'D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[27]="CUPS_FILETYPE=document"',
               'D [11/Jul/2010:11:14:49 +0700] [Job 7] envp[28]="FINAL_CONTENT_TYPE=printer/Lexmark"',
               'I [11/Jul/2010:11:14:49 +0700] [Job 7] Started filter /usr/lib/cups/filter/bannertops (PID 7696)',
               'I [11/Jul/2010:11:14:49 +0700] [Job 7] Started filter /usr/lib/cups/filter/pstopdf (PID 7697)',
               'I [11/Jul/2010:11:14:49 +0700] [Job 7] Started filter /usr/lib/cups/filter/pdftopdf (PID 7698)',
               'I [11/Jul/2010:11:14:49 +0700] [Job 7] Started filter /usr/lib/cups/filter/pdftoraster (PID 7699)',
               'E [11/Jul/2010:11:14:49 +0700] Unable to execute /usr/lib/cups/filter/rastertoz600: No such file or directory',
               'E [11/Jul/2010:11:14:49 +0700] [Job 7] Unable to start filter "rastertoz600" - Success.',
               'D [11/Jul/2010:11:14:49 +0700] cupsdMarkDirty(-----S)',
               'E [11/Jul/2010:11:14:49 +0700] [Job 7] Stopping job because the scheduler could not execute a filter.',
               'D [11/Jul/2010:11:14:49 +0700] cupsdMarkDirty(----J-)',
               'D [11/Jul/2010:11:14:49 +0700] cupsdMarkDirty(-----S)',
               'D [11/Jul/2010:11:14:49 +0700] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/Lexmark) from localhost',
               'D [11/Jul/2010:11:14:49 +0700] PID 7696 (/usr/lib/cups/filter/bannertops) was terminated normally with signal 15.',
               'D [11/Jul/2010:11:14:49 +0700] PID 7697 (/usr/lib/cups/filter/pstopdf) was terminated normally with signal 15.',
               'D [11/Jul/2010:11:14:49 +0700] cupsdSetBusyState: Dirty files',
               'D [11/Jul/2010:11:14:49 +0700] PID 7698 (/usr/lib/cups/filter/pdftopdf) was terminated normally with signal 15.',
               'D [11/Jul/2010:11:14:49 +0700] PID 7699 (/usr/lib/cups/filter/pdftoraster) was terminated normally with signal 15.',
               'D [11/Jul/2010:11:14:49 +0700] cupsdAcceptClient: 15 from localhost (Domain)',
               'D [11/Jul/2010:11:14:49 +0700] cupsdReadClient: 15 POST / HTTP/1.1',
               'D [11/Jul/2010:11:14:49 +0700] cupsdSetBusyState: Active clients and dirty files',
               'D [11/Jul/2010:11:14:49 +0700] cupsdAuthorize: No authentication data provided.',
               'D [11/Jul/2010:11:14:49 +0700] cupsdReadClient: 15 1.1 Get-Notifications 1',
               'D [11/Jul/2010:11:14:49 +0700] Get-Notifications /',
               'D [11/Jul/2010:11:14:49 +0700] cupsdIsAuthorized: requesting-user-name="don"',
               'D [11/Jul/2010:11:14:49 +0700] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [11/Jul/2010:11:14:49 +0700] cupsdSetBusyState: Dirty files',
               'D [11/Jul/2010:11:14:49 +0700] cupsdReadClient: 15 POST / HTTP/1.1',
               'D [11/Jul/2010:11:14:49 +0700] cupsdSetBusyState: Active clients and dirty files',
               'D [11/Jul/2010:11:14:49 +0700] cupsdAuthorize: No authentication data provided.',
               'D [11/Jul/2010:11:14:49 +0700] cupsdReadClient: 15 1.1 Get-Job-Attributes 1',
               'D [11/Jul/2010:11:14:49 +0700] Get-Job-Attributes ipp://localhost/jobs/7',
               'D [11/Jul/2010:11:14:49 +0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/7) from localhost',
               'D [11/Jul/2010:11:14:49 +0700] cupsdSetBusyState: Dirty files',
               'D [11/Jul/2010:11:14:49 +0700] cupsdAcceptClient: 16 from localhost (Domain)',
               'D [11/Jul/2010:11:14:49 +0700] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [11/Jul/2010:11:14:49 +0700] cupsdSetBusyState: Active clients and dirty files',
               'D [11/Jul/2010:11:14:49 +0700] cupsdAuthorize: No authentication data provided.',
               'D [11/Jul/2010:11:14:49 +0700] cupsdReadClient: 16 1.1 Get-Printer-Attributes 1',
               'D [11/Jul/2010:11:14:49 +0700] Get-Printer-Attributes ipp://VietCanada:631/printers/Lexmark',
               'D [11/Jul/2010:11:14:49 +0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://VietCanada:631/printers/Lexmark) from localhost',
               'D [11/Jul/2010:11:14:49 +0700] cupsdSetBusyState: Dirty files',
               'D [11/Jul/2010:11:14:49 +0700] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [11/Jul/2010:11:14:49 +0700] cupsdSetBusyState: Active clients and dirty files',
               'D [11/Jul/2010:11:14:49 +0700] cupsdAuthorize: No authentication data provided.',
               'D [11/Jul/2010:11:14:49 +0700] cupsdReadClient: 16 1.1 Get-Job-Attributes 1',
               'D [11/Jul/2010:11:14:49 +0700] Get-Job-Attributes ipp://localhost/jobs/7',
               'D [11/Jul/2010:11:14:49 +0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/7) from localhost',
               'D [11/Jul/2010:11:14:49 +0700] cupsdSetBusyState: Dirty files',
               'D [11/Jul/2010:11:14:49 +0700] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [11/Jul/2010:11:14:49 +0700] cupsdSetBusyState: Active clients and dirty files',
               'D [11/Jul/2010:11:14:49 +0700] cupsdAuthorize: No authentication data provided.',
               'D [11/Jul/2010:11:14:49 +0700] cupsdReadClient: 12 1.1 Get-Notifications 1',
               'D [11/Jul/2010:11:14:49 +0700] Get-Notifications /',
               'D [11/Jul/2010:11:14:49 +0700] cupsdIsAuthorized: requesting-user-name="don"',
               'D [11/Jul/2010:11:14:49 +0700] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [11/Jul/2010:11:14:49 +0700] cupsdSetBusyState: Dirty files',
               'D [11/Jul/2010:11:14:49 +0700] cupsdAcceptClient: 17 from localhost (Domain)',
               'D [11/Jul/2010:11:14:49 +0700] cupsdReadClient: 17 POST / HTTP/1.1',
               'D [11/Jul/2010:11:14:49 +0700] cupsdSetBusyState: Active clients and dirty files',
               'D [11/Jul/2010:11:14:49 +0700] cupsdAuthorize: No authentication data provided.',
               'D [11/Jul/2010:11:14:49 +0700] cupsdReadClient: 17 1.1 Get-Printer-Attributes 1',
               'D [11/Jul/2010:11:14:49 +0700] Get-Printer-Attributes ipp://VietCanada:631/printers/Lexmark',
               'D [11/Jul/2010:11:14:49 +0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://VietCanada:631/printers/Lexmark) from localhost',
               'D [11/Jul/2010:11:14:49 +0700] cupsdSetBusyState: Dirty files',
               'D [11/Jul/2010:11:14:49 +0700] cupsdReadClient: 17 POST / HTTP/1.1',
               'D [11/Jul/2010:11:14:49 +0700] cupsdSetBusyState: Active clients and dirty files',
               'D [11/Jul/2010:11:14:49 +0700] cupsdAuthorize: No authentication data provided.',
               'D [11/Jul/2010:11:14:49 +0700] cupsdReadClient: 17 1.1 Get-Job-Attributes 1',
               'D [11/Jul/2010:11:14:49 +0700] Get-Job-Attributes ipp://localhost/jobs/7',
               'D [11/Jul/2010:11:14:49 +0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/7) from localhost',
               'D [11/Jul/2010:11:14:49 +0700] cupsdSetBusyState: Dirty files',
               'D [11/Jul/2010:11:14:50 +0700] [Job 7] Unloading...',
               'D [11/Jul/2010:11:14:55 +0700] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [11/Jul/2010:11:14:55 +0700] cupsdSetBusyState: Active clients and dirty files',
               'D [11/Jul/2010:11:14:55 +0700] cupsdAuthorize: No authentication data provided.',
               'D [11/Jul/2010:11:14:55 +0700] cupsdReadClient: 12 1.1 Get-Job-Attributes 1',
               'D [11/Jul/2010:11:14:55 +0700] Get-Job-Attributes ipp://localhost/jobs/7',
               'D [11/Jul/2010:11:14:55 +0700] [Job 7] Loading attributes...',
               'D [11/Jul/2010:11:14:55 +0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/7) from localhost',
               'D [11/Jul/2010:11:14:55 +0700] cupsdSetBusyState: Dirty files',
               'D [11/Jul/2010:11:14:55 +0700] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [11/Jul/2010:11:14:55 +0700] cupsdSetBusyState: Active clients and dirty files',
               'D [11/Jul/2010:11:14:55 +0700] cupsdAuthorize: No authentication data provided.',
               'D [11/Jul/2010:11:14:55 +0700] cupsdReadClient: 12 1.1 Cancel-Subscription 1',
               'D [11/Jul/2010:11:14:55 +0700] Cancel-Subscription /',
               'D [11/Jul/2010:11:14:55 +0700] cupsdIsAuthorized: requesting-user-name="don"',
               'D [11/Jul/2010:11:14:55 +0700] cupsdMarkDirty(-----S)',
               'D [11/Jul/2010:11:14:55 +0700] Returning IPP successful-ok for Cancel-Subscription (/) from localhost',
               'D [11/Jul/2010:11:14:55 +0700] cupsdSetBusyState: Dirty files',
               'D [11/Jul/2010:11:14:55 +0700] cupsdAcceptClient: 18 from localhost (Domain)',
               'D [11/Jul/2010:11:14:55 +0700] cupsdReadClient: 18 GET /admin/log/error_log HTTP/1.1',
               'D [11/Jul/2010:11:14:55 +0700] cupsdSetBusyState: Active clients and dirty files',
               'D [11/Jul/2010:11:14:55 +0700] cupsdAuthorize: No authentication data provided.'],
 'error_log_debug_logging_unset': True}
Page 12 (Printer state reasons):
{'printer-state-message': u'Filter "/usr/lib/cups/filter/rastertoz600" for printer "Lexmark" not available: No such file or directory',
 'printer-state-reasons': [u'cups-missing-filter-warning']}
Page 13 (Locale issues):
{'printer_page_size': u'Letter',
 'system_locale_lang': None,
 'user_locale_ctype': 'en_US',
 'user_locale_messages': 'en_US'}



```I would appreciate any help with this. 

I would also appreciate the code for putting the above long lists into little windows.

---

### Post by afrodeity on 2011-11-29
me too

---

### Post by nothingspecial on 2011-11-29
> **VietCanada said:**
> . 

I would also appreciate the code for putting the above long lists into little windows.

The easiest way is to highlight the text then click the # in the formatting options at the top of the posting box.

---

### Post by VietCanada on 2011-12-02
Wow, that's an old post. I use 10.10 (Maverick) 64 bit now and long ago found a solution for properly installing my Lexmark x1270. That means I don't have the problem I posted about anymore. This is a copy of a post I made of the solution that worked for me. Hope it helps!

*Installing Lexmark x1270 on a desktop with Ubuntu 10.10 amd64 installed.*

I followed the steps outlined here: [http://ubuntuforums.org/showthread.p...=Lexmark+x1270]("http://ubuntuforums.org/showthread.php?t=1507972&highlight=Lexmark+x1270")

At the part where I double clicked on the  libstdc++5_3.3.6-17ubuntu1_i386.deb icon to install it, I was informed  that it was the wrong version since I have amd64.

So after some searching around this _**[Link]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters#Lexmark%20Z600%20Series%20Printers")**_ worked.

What I did:

1) I installed libstdc++5 from synaptic.

2)  I dl'd and installed _**[getlibs-all.deb]("http://frozenfox.freehostia.com/cappy/")**_ by double clicking on it's icon. 

3) I dl'd and installed _**[lexmark.z600-0.4.deb]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters?action=AttachFile&do=view&target=lexmark.z600-0.4.deb")**_ by double clicking on it's icon. 

4) I went to System/Administration/Printing.

   Added my printer from the list and chose 
   the z600 colour inkjet driver.

5) I printed a test page. Now I need to buy ink.

BTW thanks for the help with the little box thing. :D

---

