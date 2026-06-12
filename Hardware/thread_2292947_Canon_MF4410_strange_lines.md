---
title: "Canon MF4410 strange lines"
date: 2015-09-01
forum: Hardware
---

### Post by theodor-h-michailow on 2015-09-01
hi guys, i installed lubuntu and now i have problems with the printer setup. the priner is MF4410 canon i have instaled the drivers from the site. now the printer is printing but with strange lines across the whole page horizontally.
hire is the error log i guess... on windows the printer is working just fine... hase someone some ideas??? 10x in advance.


```
D [01/Sep/2015:14:15:03 +0300] cupsdSetBusyState: newbusy="Not busy", busy="Active clients"
D [01/Sep/2015:14:15:03 +0300] cupsdReadClient: 26 POST / HTTP/1.1
D [01/Sep/2015:14:15:03 +0300] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [01/Sep/2015:14:15:03 +0300] cupsdAuthorize: Authorized as mgc-svetatroica using PeerCred
D [01/Sep/2015:14:15:03 +0300] cupsdReadClient: 26 1.1 Get-Jobs 1
D [01/Sep/2015:14:15:03 +0300] Get-Jobs ipp://localhost/printers/
D [01/Sep/2015:14:15:03 +0300] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [01/Sep/2015:14:15:03 +0300] cupsdSetBusyState: newbusy="Not busy", busy="Active clients"
D [01/Sep/2015:14:15:03 +0300] cupsdReadClient: 26 POST / HTTP/1.1
D [01/Sep/2015:14:15:03 +0300] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [01/Sep/2015:14:15:03 +0300] cupsdAuthorize: Authorized as mgc-svetatroica using PeerCred
D [01/Sep/2015:14:15:03 +0300] cupsdReadClient: 26 1.1 Get-Jobs 1
D [01/Sep/2015:14:15:03 +0300] Get-Jobs ipp://localhost/printers/
D [01/Sep/2015:14:15:03 +0300] [Job 46] Loading attributes...
D [01/Sep/2015:14:15:03 +0300] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [01/Sep/2015:14:15:03 +0300] cupsdSetBusyState: newbusy="Not busy", busy="Active clients"
D [01/Sep/2015:14:15:03 +0300] cupsdReadClient: 26 POST / HTTP/1.1
D [01/Sep/2015:14:15:03 +0300] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [01/Sep/2015:14:15:03 +0300] cupsdAuthorize: Authorized as mgc-svetatroica using PeerCred
D [01/Sep/2015:14:15:03 +0300] cupsdReadClient: 26 1.1 Create-Printer-Subscription 1
D [01/Sep/2015:14:15:03 +0300] Create-Printer-Subscription /
D [01/Sep/2015:14:15:03 +0300] cupsdCreateSubscription(con=0x218fb068(26), uri="/")
D [01/Sep/2015:14:15:03 +0300] pullmethod="ippget"
D [01/Sep/2015:14:15:03 +0300] notify-lease-duration=86400
D [01/Sep/2015:14:15:03 +0300] notify-time-interval=0
D [01/Sep/2015:14:15:03 +0300] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")
D [01/Sep/2015:14:15:03 +0300] Added subscription #16 for server.
D [01/Sep/2015:14:15:03 +0300] cupsdMarkDirty(-----S)
D [01/Sep/2015:14:15:03 +0300] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients"
D [01/Sep/2015:14:15:03 +0300] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost
D [01/Sep/2015:14:15:03 +0300] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [01/Sep/2015:14:15:05 +0300] cupsdReadClient: 26 POST / HTTP/1.1
D [01/Sep/2015:14:15:05 +0300] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [01/Sep/2015:14:15:05 +0300] cupsdAuthorize: Authorized as mgc-svetatroica using PeerCred
D [01/Sep/2015:14:15:05 +0300] cupsdReadClient: 26 1.1 Get-Notifications 1
D [01/Sep/2015:14:15:05 +0300] Get-Notifications /
D [01/Sep/2015:14:15:05 +0300] cupsdIsAuthorized: username="mgc-svetatroica"
D [01/Sep/2015:14:15:05 +0300] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [01/Sep/2015:14:15:05 +0300] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [01/Sep/2015:14:15:13 +0300] cupsdAcceptClient: 27 from localhost (Domain)
D [01/Sep/2015:14:15:13 +0300] cupsdReadClient: 27 POST /printers/Canon-MF4400-Series HTTP/1.1
D [01/Sep/2015:14:15:13 +0300] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [01/Sep/2015:14:15:13 +0300] cupsdAuthorize: No authentication data provided.
D [01/Sep/2015:14:15:13 +0300] cupsdReadClient: 27 1.1 Print-Job 1
D [01/Sep/2015:14:15:13 +0300] Print-Job ipp://localhost/printers/Canon-MF4400-Series
D [01/Sep/2015:14:15:13 +0300] [Job ???] Auto-typing file...
I [01/Sep/2015:14:15:13 +0300] [Job ???] Request file type is application/vnd.cups-pdf-banner.
D [01/Sep/2015:14:15:13 +0300] cupsdMarkDirty(----J-)
D [01/Sep/2015:14:15:13 +0300] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [01/Sep/2015:14:15:13 +0300] add_job: requesting-user-name="mgc-svetatroica"
D [01/Sep/2015:14:15:13 +0300] Adding default job-sheets values "none,none"...
I [01/Sep/2015:14:15:13 +0300] [Job 47] Adding start banner page "none".
D [01/Sep/2015:14:15:13 +0300] cupsdMarkDirty(-----S)
D [01/Sep/2015:14:15:13 +0300] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [01/Sep/2015:14:15:13 +0300] cupsdMarkDirty(----J-)
D [01/Sep/2015:14:15:13 +0300] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
I [01/Sep/2015:14:15:13 +0300] [Job 47] Adding end banner page "none".
I [01/Sep/2015:14:15:13 +0300] [Job 47] File of type application/vnd.cups-pdf-banner queued by "mgc-svetatroica".
D [01/Sep/2015:14:15:13 +0300] [Job 47] hold_until=0
I [01/Sep/2015:14:15:13 +0300] [Job 47] Queued on "Canon-MF4400-Series" by "mgc-svetatroica".
D [01/Sep/2015:14:15:13 +0300] cupsdMarkDirty(----J-)
D [01/Sep/2015:14:15:13 +0300] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [01/Sep/2015:14:15:13 +0300] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [01/Sep/2015:14:15:13 +0300] cupsdMarkDirty(-----S)
D [01/Sep/2015:14:15:13 +0300] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [01/Sep/2015:14:15:13 +0300] [Job 47] job-sheets=none,none
D [01/Sep/2015:14:15:13 +0300] [Job 47] argv[0]="Canon-MF4400-Series"
D [01/Sep/2015:14:15:13 +0300] [Job 47] argv[1]="47"
D [01/Sep/2015:14:15:13 +0300] [Job 47] argv[2]="mgc-svetatroica"
D [01/Sep/2015:14:15:13 +0300] [Job 47] argv[3]="Test Page"
D [01/Sep/2015:14:15:13 +0300] [Job 47] argv[4]="1"
D [01/Sep/2015:14:15:13 +0300] [Job 47] argv[5]="job-uuid=urn:uuid:3cc74d71-02a9-36e9-7f72-3f21f2a9dc20 job-originating-host-name=localhost time-at-creation=1441106113 time-at-processing=1441106113"
D [01/Sep/2015:14:15:13 +0300] [Job 47] argv[6]="/var/spool/cups/d00047-001"
D [01/Sep/2015:14:15:13 +0300] [Job 47] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [01/Sep/2015:14:15:13 +0300] [Job 47] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [01/Sep/2015:14:15:13 +0300] [Job 47] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [01/Sep/2015:14:15:13 +0300] [Job 47] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [01/Sep/2015:14:15:13 +0300] [Job 47] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [01/Sep/2015:14:15:13 +0300] [Job 47] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [01/Sep/2015:14:15:13 +0300] [Job 47] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [01/Sep/2015:14:15:13 +0300] [Job 47] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [01/Sep/2015:14:15:13 +0300] [Job 47] envp[8]="HOME=/var/spool/cups/tmp"
D [01/Sep/2015:14:15:13 +0300] [Job 47] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [01/Sep/2015:14:15:13 +0300] [Job 47] envp[10]="SERVER_ADMIN=root@mgcsvetatroica-ThinkCentre-M55"
D [01/Sep/2015:14:15:13 +0300] [Job 47] envp[11]="SOFTWARE=CUPS/1.5.3"
D [01/Sep/2015:14:15:13 +0300] [Job 47] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [01/Sep/2015:14:15:13 +0300] [Job 47] envp[13]="USER=root"
D [01/Sep/2015:14:15:13 +0300] [Job 47] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [01/Sep/2015:14:15:13 +0300] [Job 47] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [01/Sep/2015:14:15:13 +0300] [Job 47] envp[16]="IPP_PORT=631"
D [01/Sep/2015:14:15:13 +0300] [Job 47] envp[17]="CHARSET=utf-8"
D [01/Sep/2015:14:15:13 +0300] [Job 47] envp[18]="LANG=en_US.UTF-8"
D [01/Sep/2015:14:15:13 +0300] [Job 47] envp[19]="PPD=/etc/cups/ppd/Canon-MF4400-Series.ppd"
D [01/Sep/2015:14:15:13 +0300] [Job 47] envp[20]="RIP_MAX_CACHE=128m"
D [01/Sep/2015:14:15:13 +0300] [Job 47] envp[21]="CONTENT_TYPE=application/vnd.cups-pdf-banner"
D [01/Sep/2015:14:15:13 +0300] [Job 47] envp[22]="DEVICE_URI=usb://Canon/MF4400%20Series?serial=000000000000&interface=1"
D [01/Sep/2015:14:15:13 +0300] [Job 47] envp[23]="PRINTER_INFO=Canon MF4400 Series"
D [01/Sep/2015:14:15:13 +0300] [Job 47] envp[24]="PRINTER_LOCATION=mgcsvetatroica-ThinkCentre-M55"
D [01/Sep/2015:14:15:13 +0300] [Job 47] envp[25]="PRINTER=Canon-MF4400-Series"
D [01/Sep/2015:14:15:13 +0300] [Job 47] envp[26]="PRINTER_STATE_REASONS=none"
D [01/Sep/2015:14:15:13 +0300] [Job 47] envp[27]="CUPS_FILETYPE=document"
D [01/Sep/2015:14:15:13 +0300] [Job 47] envp[28]="FINAL_CONTENT_TYPE=printer/Canon-MF4400-Series"
D [01/Sep/2015:14:15:13 +0300] [Job 47] envp[29]="AUTH_I****"
I [01/Sep/2015:14:15:13 +0300] [Job 47] Started filter /usr/lib/cups/filter/bannertopdf (PID 20489)
I [01/Sep/2015:14:15:13 +0300] [Job 47] Started filter /usr/lib/cups/filter/pdftopdf (PID 20490)
I [01/Sep/2015:14:15:13 +0300] [Job 47] Started filter /usr/lib/cups/filter/pdftops (PID 20491)
I [01/Sep/2015:14:15:13 +0300] [Job 47] Started filter /usr/lib/cups/filter/pstoufr2cpca (PID 20492)
I [01/Sep/2015:14:15:13 +0300] [Job 47] Started backend /usr/lib/cups/backend/usb (PID 20493)
D [01/Sep/2015:14:15:13 +0300] cupsdMarkDirty(-----S)
D [01/Sep/2015:14:15:13 +0300] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients and dirty files"
D [01/Sep/2015:14:15:13 +0300] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/Canon-MF4400-Series) from localhost
D [01/Sep/2015:14:15:13 +0300] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [01/Sep/2015:14:15:13 +0300] [Job 47] Printing on printer with URI: usb://Canon/MF4400%20Series?serial=000000000000&interface=1
D [01/Sep/2015:14:15:13 +0300] [Job 47] pdftops - copying to temp print file "/tmp/0500b55f37fdf"
D [01/Sep/2015:14:15:13 +0300] [Job 47] libusb_get_device_list=10
D [01/Sep/2015:14:15:13 +0300] [Job 47] pstoufr2cpca start.
D [01/Sep/2015:14:15:13 +0300] PID 20489 (/usr/lib/cups/filter/bannertopdf) exited with no errors.
D [01/Sep/2015:14:15:14 +0300] PID 20490 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [01/Sep/2015:14:15:14 +0300] [Job 47] Using image rendering resolution 300 dpi
D [01/Sep/2015:14:15:14 +0300] [Job 47] Started filter pdftops (PID 20494)
D [01/Sep/2015:14:15:14 +0300] [Job 47] Started filter pstops (PID 20495)
D [01/Sep/2015:14:15:14 +0300] [Job 47] Page = 612x792; 14,14 to 598,778
D [01/Sep/2015:14:15:14 +0300] [Job 47] slow_collate=0, slow_duplex=0, slow_order=0
D [01/Sep/2015:14:15:14 +0300] [Job 47] Before copy_comments - %!PS-Adobe-3.0
D [01/Sep/2015:14:15:14 +0300] [Job 47] %!PS-Adobe-3.0
D [01/Sep/2015:14:15:14 +0300] [Job 47] %Produced by poppler pdftops version: 0.18.4 (http://poppler.freedesktop.org)
D [01/Sep/2015:14:15:14 +0300] [Job 47] %%LanguageLevel: 2
D [01/Sep/2015:14:15:14 +0300] [Job 47] %%DocumentSuppliedResources: (atend)
D [01/Sep/2015:14:15:14 +0300] [Job 47] %%DocumentMedia: plain 612 792 0 () ()
D [01/Sep/2015:14:15:14 +0300] [Job 47] %%BoundingBox: 0 0 612 792
D [01/Sep/2015:14:15:14 +0300] [Job 47] %%Pages: 1
D [01/Sep/2015:14:15:14 +0300] [Job 47] %%EndComments
D [01/Sep/2015:14:15:14 +0300] [Job 47] Before copy_prolog - %%BeginDefaults
D [01/Sep/2015:14:15:14 +0300] [Job 47] Before copy_setup - %%BeginSetup
D [01/Sep/2015:14:15:14 +0300] [Job 47] STATE: +connecting-to-device
D [01/Sep/2015:14:15:14 +0300] cupsdMarkDirty(-----S)
D [01/Sep/2015:14:15:14 +0300] cupsdSetBusyState: newbusy="Dirty files", busy="Printing jobs and dirty files"
D [01/Sep/2015:14:15:14 +0300] [Job 47] STATE: -connecting-to-device
D [01/Sep/2015:14:15:14 +0300] cupsdMarkDirty(-----S)
D [01/Sep/2015:14:15:14 +0300] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Dirty files"
D [01/Sep/2015:14:15:14 +0300] [Job 47] Device protocol: 2
I [01/Sep/2015:14:15:14 +0300] [Job 47] Sending data to printer.
D [01/Sep/2015:14:15:14 +0300] [Job 47] Set job-printer-state-message to "Sending data to printer.", current level=INFO
D [01/Sep/2015:14:15:14 +0300] cupsdMarkDirty(-----S)
D [01/Sep/2015:14:15:14 +0300] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [01/Sep/2015:14:15:14 +0300] cupsdMarkDirty(-----S)
D [01/Sep/2015:14:15:14 +0300] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [01/Sep/2015:14:15:14 +0300] [Job 47] Before page loop - %%Page: 1 1
D [01/Sep/2015:14:15:14 +0300] [Job 47] Copying page 1...
D [01/Sep/2015:14:15:14 +0300] [Job 47] pagew = 583.7, pagel = 763.7
D [01/Sep/2015:14:15:14 +0300] [Job 47] bboxx = 0, bboxy = 0, bboxw = 612, bboxl = 792
D [01/Sep/2015:14:15:14 +0300] [Job 47] PageLeft = 14.2, PageRight = 597.8
D [01/Sep/2015:14:15:14 +0300] [Job 47] PageTop = 777.8, PageBottom = 14.2
D [01/Sep/2015:14:15:14 +0300] [Job 47] PageWidth = 612.0, PageLength = 792.0
D [01/Sep/2015:14:15:14 +0300] [Job 47] opvpOpenPrinter(463)
D [01/Sep/2015:14:15:14 +0300] [Job 47] CStubOpenPrinter(397)
D [01/Sep/2015:14:15:14 +0300] cupsdAcceptClient: 29 from localhost (Domain)
D [01/Sep/2015:14:15:14 +0300] cupsdReadClient: 29 POST / HTTP/1.1
D [01/Sep/2015:14:15:14 +0300] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [01/Sep/2015:14:15:14 +0300] cupsdAuthorize: No authentication data provided.
D [01/Sep/2015:14:15:14 +0300] cupsdReadClient: 29 1.1 Get-Notifications 1
D [01/Sep/2015:14:15:14 +0300] Get-Notifications /
D [01/Sep/2015:14:15:14 +0300] cupsdIsAuthorized: requesting-user-name="mgc-svetatroica"
D [01/Sep/2015:14:15:14 +0300] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [01/Sep/2015:14:15:14 +0300] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [01/Sep/2015:14:15:14 +0300] cupsdReadClient: 29 WAITING Closing on EOF
D [01/Sep/2015:14:15:14 +0300] cupsdCloseClient: 29
D [01/Sep/2015:14:15:14 +0300] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [01/Sep/2015:14:15:14 +0300] [Job 47] opvpOpenPrinter(463)
D [01/Sep/2015:14:15:14 +0300] [Job 47] CStubOpenPrinter(397)
D [01/Sep/2015:14:15:14 +0300] cupsdReadClient: 26 POST / HTTP/1.1
D [01/Sep/2015:14:15:14 +0300] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [01/Sep/2015:14:15:14 +0300] cupsdAuthorize: Authorized as mgc-svetatroica using PeerCred
D [01/Sep/2015:14:15:14 +0300] cupsdReadClient: 26 1.1 Get-Notifications 1
D [01/Sep/2015:14:15:14 +0300] Get-Notifications /
D [01/Sep/2015:14:15:14 +0300] cupsdIsAuthorized: username="mgc-svetatroica"
D [01/Sep/2015:14:15:14 +0300] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [01/Sep/2015:14:15:14 +0300] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
E [01/Sep/2015:14:15:14 +0300] [Job 47] src = bidiCommon.c, line = 1011, err = 0¥nDEBUG: Read 93 bytes of print data...
D [01/Sep/2015:14:15:14 +0300] [Job 47] Set job-printer-state-message to "src = bidiCommon.c, line = 1011, err = 0¥nDEBUG: Read 93 bytes of print data...", current level=ERROR
D [01/Sep/2015:14:15:14 +0300] cupsdMarkDirty(-----S)
D [01/Sep/2015:14:15:14 +0300] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [01/Sep/2015:14:15:14 +0300] cupsdMarkDirty(-----S)
D [01/Sep/2015:14:15:14 +0300] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [01/Sep/2015:14:15:14 +0300] [Job 47] Wrote 93 bytes of print data...
D [01/Sep/2015:14:15:14 +0300] [Job 47] Read 24 bytes of print data...
D [01/Sep/2015:14:15:14 +0300] [Job 47] Wrote 24 bytes of print data...
D [01/Sep/2015:14:15:14 +0300] [Job 47] Read 353 bytes of print data...
D [01/Sep/2015:14:15:14 +0300] [Job 47] Wrote 353 bytes of print data...
D [01/Sep/2015:14:15:14 +0300] cupsdReadClient: 19 POST / HTTP/1.1
D [01/Sep/2015:14:15:14 +0300] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [01/Sep/2015:14:15:14 +0300] cupsdAuthorize: Authorized as mgc-svetatroica using PeerCred
D [01/Sep/2015:14:15:14 +0300] cupsdReadClient: 19 1.1 CUPS-Get-Printers 1
D [01/Sep/2015:14:15:14 +0300] CUPS-Get-Printers
D [01/Sep/2015:14:15:14 +0300] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [01/Sep/2015:14:15:14 +0300] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [01/Sep/2015:14:15:14 +0300] cupsdReadClient: 19 POST / HTTP/1.1
D [01/Sep/2015:14:15:14 +0300] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [01/Sep/2015:14:15:14 +0300] cupsdAuthorize: Authorized as mgc-svetatroica using PeerCred
D [01/Sep/2015:14:15:14 +0300] cupsdReadClient: 19 1.1 CUPS-Get-Classes 1
D [01/Sep/2015:14:15:14 +0300] CUPS-Get-Classes
D [01/Sep/2015:14:15:14 +0300] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [01/Sep/2015:14:15:14 +0300] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [01/Sep/2015:14:15:14 +0300] cupsdReadClient: 19 POST / HTTP/1.1
D [01/Sep/2015:14:15:14 +0300] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [01/Sep/2015:14:15:14 +0300] cupsdAuthorize: Authorized as mgc-svetatroica using PeerCred
D [01/Sep/2015:14:15:14 +0300] cupsdReadClient: 19 1.1 CUPS-Get-Default 1
D [01/Sep/2015:14:15:14 +0300] CUPS-Get-Default
D [01/Sep/2015:14:15:14 +0300] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [01/Sep/2015:14:15:14 +0300] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [01/Sep/2015:14:15:14 +0300] cupsdAcceptClient: 29 from localhost (Domain)
D [01/Sep/2015:14:15:14 +0300] cupsdReadClient: 29 POST / HTTP/1.1
D [01/Sep/2015:14:15:14 +0300] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [01/Sep/2015:14:15:14 +0300] cupsdAuthorize: No authentication data provided.
D [01/Sep/2015:14:15:14 +0300] cupsdReadClient: 29 1.1 Get-Notifications 1
D [01/Sep/2015:14:15:14 +0300] Get-Notifications /
D [01/Sep/2015:14:15:14 +0300] cupsdIsAuthorized: requesting-user-name="mgc-svetatroica"
D [01/Sep/2015:14:15:14 +0300] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [01/Sep/2015:14:15:14 +0300] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [01/Sep/2015:14:15:14 +0300] cupsdReadClient: 29 WAITING Closing on EOF
D [01/Sep/2015:14:15:14 +0300] cupsdCloseClient: 29
D [01/Sep/2015:14:15:14 +0300] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [01/Sep/2015:14:15:14 +0300] cupsdReadClient: 19 POST / HTTP/1.1
D [01/Sep/2015:14:15:14 +0300] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [01/Sep/2015:14:15:14 +0300] cupsdAuthorize: Authorized as mgc-svetatroica using PeerCred
D [01/Sep/2015:14:15:14 +0300] cupsdReadClient: 19 1.1 CUPS-Get-Printers 1
D [01/Sep/2015:14:15:14 +0300] CUPS-Get-Printers
D [01/Sep/2015:14:15:14 +0300] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [01/Sep/2015:14:15:14 +0300] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [01/Sep/2015:14:15:14 +0300] cupsdReadClient: 19 POST / HTTP/1.1
D [01/Sep/2015:14:15:14 +0300] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [01/Sep/2015:14:15:14 +0300] cupsdAuthorize: Authorized as mgc-svetatroica using PeerCred
D [01/Sep/2015:14:15:14 +0300] cupsdReadClient: 19 1.1 CUPS-Get-Classes 1
D [01/Sep/2015:14:15:14 +0300] CUPS-Get-Classes
D [01/Sep/2015:14:15:14 +0300] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [01/Sep/2015:14:15:14 +0300] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [01/Sep/2015:14:15:14 +0300] cupsdReadClient: 19 POST / HTTP/1.1
D [01/Sep/2015:14:15:14 +0300] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [01/Sep/2015:14:15:14 +0300] cupsdAuthorize: Authorized as mgc-svetatroica using PeerCred
D [01/Sep/2015:14:15:14 +0300] cupsdReadClient: 19 1.1 CUPS-Get-Default 1
D [01/Sep/2015:14:15:14 +0300] CUPS-Get-Default
D [01/Sep/2015:14:15:14 +0300] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [01/Sep/2015:14:15:14 +0300] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [01/Sep/2015:14:15:16 +0300] [Job 47] PID 20494 (pdftops) exited with no errors.
D [01/Sep/2015:14:15:16 +0300] [Job 47] Wrote 1 pages...
D [01/Sep/2015:14:15:16 +0300] [Job 47] PID 20495 (pstops) exited with no errors.
D [01/Sep/2015:14:15:16 +0300] PID 20491 (/usr/lib/cups/filter/pdftops) exited with no errors.
D [01/Sep/2015:14:15:16 +0300] [Job 47] Read 97 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Wrote 97 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Read 79 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Wrote 79 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Read 43 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Wrote 43 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Read 34 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Wrote 34 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Read 77 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Wrote 77 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Read 43 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Wrote 43 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Read 3454 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Wrote 3454 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Read 43 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Wrote 43 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Read 2587 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Wrote 2587 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Read 43 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Wrote 43 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Read 471 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Wrote 471 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Read 43 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Wrote 43 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Read 8192 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Wrote 8192 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Read 323 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Wrote 323 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Read 43 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Wrote 43 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Read 8192 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Wrote 8192 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Read 3246 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Wrote 3246 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Read 43 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Wrote 43 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Read 8192 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Wrote 8192 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Read 2587 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Wrote 2587 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Read 43 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Wrote 43 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Read 2962 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Wrote 2962 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Read 43 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Wrote 43 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] [Job 47] Read 8192 bytes of print data...
D [01/Sep/2015:14:15:16 +0300] PID 20492 (/usr/lib/cups/filter/pstoufr2cpca) exited with no errors.
I [01/Sep/2015:14:15:34 +0300] Saving job.cache...
I [01/Sep/2015:14:15:35 +0300] Saving subscriptions.conf...
D [01/Sep/2015:14:15:35 +0300] cupsdSetBusyState: newbusy="Printing jobs", busy="Printing jobs and dirty files"
D [01/Sep/2015:14:15:48 +0300] [Job 47] Wrote 8192 bytes of print data...
D [01/Sep/2015:14:15:48 +0300] [Job 47] Read 8192 bytes of print data...
D [01/Sep/2015:14:15:48 +0300] [Job 47] Wrote 8192 bytes of print data...
D [01/Sep/2015:14:15:48 +0300] [Job 47] Read 8192 bytes of print data...
D [01/Sep/2015:14:15:48 +0300] [Job 47] Wrote 8192 bytes of print data...
D [01/Sep/2015:14:15:48 +0300] [Job 47] Read 8192 bytes of print data...
D [01/Sep/2015:14:15:48 +0300] [Job 47] Wrote 8192 bytes of print data...
D [01/Sep/2015:14:15:48 +0300] [Job 47] Read 8192 bytes of print data...
D [01/Sep/2015:14:15:48 +0300] [Job 47] Wrote 8192 bytes of print data...
D [01/Sep/2015:14:15:48 +0300] [Job 47] Read 8192 bytes of print data...
D [01/Sep/2015:14:15:48 +0300] [Job 47] Wrote 8192 bytes of print data...
D [01/Sep/2015:14:15:48 +0300] [Job 47] Read 8192 bytes of print data...
D [01/Sep/2015:14:15:48 +0300] [Job 47] Wrote 8192 bytes of print data...
D [01/Sep/2015:14:15:48 +0300] [Job 47] Read 1233 bytes of print data...
D [01/Sep/2015:14:15:48 +0300] [Job 47] Wrote 1233 bytes of print data...
D [01/Sep/2015:14:15:48 +0300] [Job 47] Sent 99927 bytes...
D [01/Sep/2015:14:15:48 +0300] [Job 47] Waiting for read thread to exit...
D [01/Sep/2015:14:15:55 +0300] [Job 47] Read thread still active, aborting the pending read...
D [01/Sep/2015:14:15:56 +0300] PID 20493 (/usr/lib/cups/backend/usb) exited with no errors.
D [01/Sep/2015:14:15:56 +0300] cupsdMarkDirty(-----S)
D [01/Sep/2015:14:15:56 +0300] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs"
I [01/Sep/2015:14:15:56 +0300] [Job 47] Job completed.
D [01/Sep/2015:14:15:56 +0300] cupsdMarkDirty(----J-)
D [01/Sep/2015:14:15:56 +0300] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [01/Sep/2015:14:15:56 +0300] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [01/Sep/2015:14:15:56 +0300] cupsdMarkDirty(-----S)
D [01/Sep/2015:14:15:56 +0300] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [01/Sep/2015:14:15:56 +0300] cupsdAcceptClient: 28 from localhost (Domain)
D [01/Sep/2015:14:15:56 +0300] cupsdReadClient: 28 POST / HTTP/1.1
D [01/Sep/2015:14:15:56 +0300] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Printing jobs and dirty files"
D [01/Sep/2015:14:15:56 +0300] cupsdAuthorize: No authentication data provided.
D [01/Sep/2015:14:15:56 +0300] cupsdReadClient: 28 1.1 Get-Notifications 1
D [01/Sep/2015:14:15:56 +0300] Get-Notifications /
D [01/Sep/2015:14:15:56 +0300] cupsdIsAuthorized: requesting-user-name="mgc-svetatroica"
D [01/Sep/2015:14:15:56 +0300] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [01/Sep/2015:14:15:56 +0300] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [01/Sep/2015:14:15:56 +0300] cupsdReadClient: 28 WAITING Closing on EOF
D [01/Sep/2015:14:15:56 +0300] cupsdCloseClient: 28
D [01/Sep/2015:14:15:56 +0300] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [01/Sep/2015:14:15:56 +0300] cupsdReadClient: 26 POST / HTTP/1.1
D [01/Sep/2015:14:15:56 +0300] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [01/Sep/2015:14:15:56 +0300] cupsdAuthorize: Authorized as mgc-svetatroica using PeerCred
D [01/Sep/2015:14:15:56 +0300] cupsdReadClient: 26 1.1 Get-Notifications 1
D [01/Sep/2015:14:15:56 +0300] Get-Notifications /
D [01/Sep/2015:14:15:56 +0300] cupsdIsAuthorized: username="mgc-svetatroica"
D [01/Sep/2015:14:15:56 +0300] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [01/Sep/2015:14:15:56 +0300] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [01/Sep/2015:14:15:57 +0300] cupsdReadClient: 19 POST / HTTP/1.1
D [01/Sep/2015:14:15:57 +0300] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [01/Sep/2015:14:15:57 +0300] cupsdAuthorize: Authorized as mgc-svetatroica using PeerCred
D [01/Sep/2015:14:15:57 +0300] [Job 47] Unloading...
D [01/Sep/2015:14:15:57 +0300] cupsdReadClient: 19 1.1 CUPS-Get-Printers 1
D [01/Sep/2015:14:15:57 +0300] CUPS-Get-Printers
D [01/Sep/2015:14:15:57 +0300] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [01/Sep/2015:14:15:57 +0300] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [01/Sep/2015:14:15:57 +0300] cupsdReadClient: 19 POST / HTTP/1.1
D [01/Sep/2015:14:15:57 +0300] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [01/Sep/2015:14:15:57 +0300] cupsdAuthorize: Authorized as mgc-svetatroica using PeerCred
D [01/Sep/2015:14:15:57 +0300] cupsdReadClient: 19 1.1 CUPS-Get-Classes 1
D [01/Sep/2015:14:15:57 +0300] CUPS-Get-Classes
D [01/Sep/2015:14:15:57 +0300] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [01/Sep/2015:14:15:57 +0300] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [01/Sep/2015:14:15:57 +0300] cupsdReadClient: 19 POST / HTTP/1.1
D [01/Sep/2015:14:15:57 +0300] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [01/Sep/2015:14:15:57 +0300] cupsdAuthorize: Authorized as mgc-svetatroica using PeerCred
D [01/Sep/2015:14:15:57 +0300] cupsdReadClient: 19 1.1 CUPS-Get-Default 1
D [01/Sep/2015:14:15:57 +0300] CUPS-Get-Default
D [01/Sep/2015:14:15:57 +0300] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [01/Sep/2015:14:15:57 +0300] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [01/Sep/2015:14:16:13 +0300] cupsdReadClient: 26 POST / HTTP/1.1
D [01/Sep/2015:14:16:13 +0300] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [01/Sep/2015:14:16:13 +0300] cupsdAuthorize: Authorized as mgc-svetatroica using PeerCred
D [01/Sep/2015:14:16:13 +0300] [Job 46] Unloading...
D [01/Sep/2015:14:16:13 +0300] Report: clients=13
D [01/Sep/2015:14:16:13 +0300] Report: jobs=2
D [01/Sep/2015:14:16:13 +0300] Report: jobs-active=0
D [01/Sep/2015:14:16:13 +0300] Report: printers=1
D [01/Sep/2015:14:16:13 +0300] Report: printers-implicit=0
D [01/Sep/2015:14:16:13 +0300] Report: stringpool-string-count=3518
D [01/Sep/2015:14:16:13 +0300] Report: stringpool-alloc-bytes=11488
D [01/Sep/2015:14:16:13 +0300] Report: stringpool-total-bytes=71720
D [01/Sep/2015:14:16:13 +0300] cupsdReadClient: 26 1.1 Get-Job-Attributes 1
D [01/Sep/2015:14:16:13 +0300] Get-Job-Attributes ipp://localhost/jobs/47
D [01/Sep/2015:14:16:13 +0300] [Job 47] Loading attributes...
D [01/Sep/2015:14:16:13 +0300] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/47) from localhost
D [01/Sep/2015:14:16:13 +0300] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [01/Sep/2015:14:16:13 +0300] cupsdReadClient: 26 POST / HTTP/1.1
D [01/Sep/2015:14:16:13 +0300] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [01/Sep/2015:14:16:13 +0300] cupsdAuthorize: Authorized as mgc-svetatroica using PeerCred
D [01/Sep/2015:14:16:13 +0300] cupsdReadClient: 26 1.1 Cancel-Subscription 1
D [01/Sep/2015:14:16:13 +0300] Cancel-Subscription /
D [01/Sep/2015:14:16:13 +0300] cupsdIsAuthorized: username="mgc-svetatroica"
D [01/Sep/2015:14:16:13 +0300] cupsdMarkDirty(-----S)
D [01/Sep/2015:14:16:13 +0300] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [01/Sep/2015:14:16:13 +0300] Returning IPP successful-ok for Cancel-Subscription (/) from localhost
D [01/Sep/2015:14:16:13 +0300] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [01/Sep/2015:14:16:13 +0300] cupsdAcceptClient: 28 from localhost (Domain)
D [01/Sep/2015:14:16:13 +0300] cupsdReadClient: 28 GET /admin/log/error_log HTTP/1.1
D [01/Sep/2015:14:16:13 +0300] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [01/Sep/2015:14:16:13 +0300] cupsdAuthorize: No authentication data provided.
```

Canon MF4400 Series UFRII LT ver.2.2   <-- Driver

---

