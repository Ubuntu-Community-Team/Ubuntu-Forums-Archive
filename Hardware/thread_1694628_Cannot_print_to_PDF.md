---
title: "Cannot print to PDF"
date: 2011-02-24
forum: Hardware
---

### Post by ranger_cole on 2011-02-24
Using 10.10 and cannot print to PDF.  Here is the error log message:

D [24/Feb/2011:15:46:38 -0600] cupsdSetBusyState: Dirty files
D [24/Feb/2011:15:46:38 -0600] cupsdReadClient: 12 POST / HTTP/1.1
D [24/Feb/2011:15:46:38 -0600] cupsdSetBusyState: Active clients and dirty files
D [24/Feb/2011:15:46:38 -0600] cupsdAuthorize: No authentication data provided.
D [24/Feb/2011:15:46:38 -0600] cupsdReadClient: 12 1.1 Get-Jobs 1
D [24/Feb/2011:15:46:38 -0600] Get-Jobs ipp://localhost/printers/
D [24/Feb/2011:15:46:38 -0600] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [24/Feb/2011:15:46:38 -0600] cupsdSetBusyState: Dirty files
D [24/Feb/2011:15:46:38 -0600] cupsdReadClient: 12 POST / HTTP/1.1
D [24/Feb/2011:15:46:38 -0600] cupsdSetBusyState: Active clients and dirty files
D [24/Feb/2011:15:46:38 -0600] cupsdAuthorize: No authentication data provided.
D [24/Feb/2011:15:46:38 -0600] cupsdReadClient: 12 1.1 Get-Jobs 1
D [24/Feb/2011:15:46:38 -0600] Get-Jobs ipp://localhost/printers/
D [24/Feb/2011:15:46:38 -0600] [Job 1] Loading attributes...
D [24/Feb/2011:15:46:38 -0600] [Job 2] Loading attributes...
D [24/Feb/2011:15:46:38 -0600] [Job 3] Loading attributes...
D [24/Feb/2011:15:46:38 -0600] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [24/Feb/2011:15:46:38 -0600] cupsdSetBusyState: Dirty files
D [24/Feb/2011:15:46:38 -0600] cupsdReadClient: 12 POST / HTTP/1.1
D [24/Feb/2011:15:46:38 -0600] cupsdSetBusyState: Active clients and dirty files
D [24/Feb/2011:15:46:38 -0600] cupsdAuthorize: No authentication data provided.
D [24/Feb/2011:15:46:38 -0600] cupsdReadClient: 12 1.1 Create-Printer-Subscription 1
D [24/Feb/2011:15:46:38 -0600] Create-Printer-Subscription /
D [24/Feb/2011:15:46:38 -0600] cupsdCreateSubscription(con=0x21abd7e0(12), uri="/")
D [24/Feb/2011:15:46:38 -0600] pullmethod="ippget"
D [24/Feb/2011:15:46:38 -0600] notify-lease-duration=86400
D [24/Feb/2011:15:46:38 -0600] notify-time-interval=0
D [24/Feb/2011:15:46:38 -0600] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")
D [24/Feb/2011:15:46:38 -0600] Added subscription 4 for server
D [24/Feb/2011:15:46:38 -0600] cupsdMarkDirty(-----S)
D [24/Feb/2011:15:46:38 -0600] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost
D [24/Feb/2011:15:46:38 -0600] cupsdSetBusyState: Dirty files
D [24/Feb/2011:15:46:40 -0600] cupsdReadClient: 12 POST / HTTP/1.1
D [24/Feb/2011:15:46:40 -0600] cupsdSetBusyState: Active clients and dirty files
D [24/Feb/2011:15:46:40 -0600] cupsdAuthorize: No authentication data provided.
D [24/Feb/2011:15:46:40 -0600] cupsdReadClient: 12 1.1 Get-Notifications 1
D [24/Feb/2011:15:46:40 -0600] Get-Notifications /
D [24/Feb/2011:15:46:40 -0600] cupsdIsAuthorized: requesting-user-name="jaypugh"
D [24/Feb/2011:15:46:40 -0600] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [24/Feb/2011:15:46:40 -0600] cupsdSetBusyState: Dirty files
D [24/Feb/2011:15:46:41 -0600] cupsdAcceptClient: 13 from localhost (Domain)
D [24/Feb/2011:15:46:41 -0600] cupsdReadClient: 13 POST /printers/Generic-CUPS-PDF-Printer HTTP/1.1
D [24/Feb/2011:15:46:41 -0600] cupsdSetBusyState: Active clients and dirty files
D [24/Feb/2011:15:46:41 -0600] cupsdAuthorize: No authentication data provided.
D [24/Feb/2011:15:46:41 -0600] cupsdReadClient: 13 1.1 Print-Job 1
D [24/Feb/2011:15:46:41 -0600] Print-Job ipp://localhost/printers/Generic-CUPS-PDF-Printer
D [24/Feb/2011:15:46:41 -0600] [Job ???] Auto-typing file...
I [24/Feb/2011:15:46:41 -0600] [Job ???] Request file type is application/vnd.cups-banner.
D [24/Feb/2011:15:46:41 -0600] cupsdMarkDirty(----J-)
D [24/Feb/2011:15:46:41 -0600] add_job: requesting-user-name="jaypugh"
D [24/Feb/2011:15:46:41 -0600] Adding default job-sheets values "none,none"...
I [24/Feb/2011:15:46:41 -0600] [Job 4] Adding start banner page "none".
D [24/Feb/2011:15:46:41 -0600] cupsdMarkDirty(-----S)
D [24/Feb/2011:15:46:41 -0600] cupsdMarkDirty(----J-)
I [24/Feb/2011:15:46:41 -0600] [Job 4] Adding end banner page "none".
I [24/Feb/2011:15:46:41 -0600] [Job 4] File of type application/vnd.cups-banner queued by "jaypugh".
D [24/Feb/2011:15:46:41 -0600] [Job 4] hold_until=0
I [24/Feb/2011:15:46:41 -0600] [Job 4] Queued on "Generic-CUPS-PDF-Printer" by "jaypugh".
D [24/Feb/2011:15:46:41 -0600] cupsdMarkDirty(----J-)
D [24/Feb/2011:15:46:41 -0600] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [24/Feb/2011:15:46:41 -0600] cupsdMarkDirty(-----S)
D [24/Feb/2011:15:46:41 -0600] [Job 4] job-sheets=none,none
D [24/Feb/2011:15:46:41 -0600] [Job 4] argv[0]="Generic-CUPS-PDF-Printer"
D [24/Feb/2011:15:46:41 -0600] [Job 4] argv[1]="4"
D [24/Feb/2011:15:46:41 -0600] [Job 4] argv[2]="jaypugh"
D [24/Feb/2011:15:46:41 -0600] [Job 4] argv[3]="Test Page"
D [24/Feb/2011:15:46:41 -0600] [Job 4] argv[4]="1"
D [24/Feb/2011:15:46:41 -0600] [Job 4] argv[5]="job-uuid=urn:uuid:b86315e9-0a69-348d-4c3e-043675d690e2 job-originating-host-name=localhost"
D [24/Feb/2011:15:46:41 -0600] [Job 4] argv[6]="/var/spool/cups/d00004-001"
D [24/Feb/2011:15:46:41 -0600] [Job 4] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [24/Feb/2011:15:46:41 -0600] [Job 4] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [24/Feb/2011:15:46:41 -0600] [Job 4] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [24/Feb/2011:15:46:41 -0600] [Job 4] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [24/Feb/2011:15:46:41 -0600] [Job 4] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [24/Feb/2011:15:46:41 -0600] [Job 4] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [24/Feb/2011:15:46:41 -0600] [Job 4] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [24/Feb/2011:15:46:41 -0600] [Job 4] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [24/Feb/2011:15:46:41 -0600] [Job 4] envp[8]="HOME=/var/spool/cups/tmp"
D [24/Feb/2011:15:46:41 -0600] [Job 4] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [24/Feb/2011:15:46:41 -0600] [Job 4] envp[10]="SERVER_ADMIN=root@ubuntu"
D [24/Feb/2011:15:46:41 -0600] [Job 4] envp[11]="SOFTWARE=CUPS/1.4.4"
D [24/Feb/2011:15:46:41 -0600] [Job 4] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [24/Feb/2011:15:46:41 -0600] [Job 4] envp[13]="USER=root"
D [24/Feb/2011:15:46:41 -0600] [Job 4] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [24/Feb/2011:15:46:41 -0600] [Job 4] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [24/Feb/2011:15:46:41 -0600] [Job 4] envp[16]="IPP_PORT=631"
D [24/Feb/2011:15:46:41 -0600] [Job 4] envp[17]="CHARSET=utf-8"
D [24/Feb/2011:15:46:41 -0600] [Job 4] envp[18]="LANG=en_US.UTF-8"
D [24/Feb/2011:15:46:41 -0600] [Job 4] envp[19]="PPD=/etc/cups/ppd/Generic-CUPS-PDF-Printer.ppd"
D [24/Feb/2011:15:46:41 -0600] [Job 4] envp[20]="RIP_MAX_CACHE=auto"
D [24/Feb/2011:15:46:41 -0600] [Job 4] envp[21]="CONTENT_TYPE=application/vnd.cups-banner"
D [24/Feb/2011:15:46:41 -0600] [Job 4] envp[22]="DEVICE_URI=cups-pdf:/"
D [24/Feb/2011:15:46:41 -0600] [Job 4] envp[23]="PRINTER_INFO=Generic CUPS-PDF Printer"
D [24/Feb/2011:15:46:41 -0600] [Job 4] envp[24]="PRINTER_LOCATION="
D [24/Feb/2011:15:46:41 -0600] [Job 4] envp[25]="PRINTER=Generic-CUPS-PDF-Printer"
D [24/Feb/2011:15:46:41 -0600] [Job 4] envp[26]="CUPS_FILETYPE=document"
D [24/Feb/2011:15:46:41 -0600] [Job 4] envp[27]="FINAL_CONTENT_TYPE=application/vnd.cups-pdf"
I [24/Feb/2011:15:46:41 -0600] [Job 4] Started filter /usr/lib/cups/filter/bannertops (PID 25069)
I [24/Feb/2011:15:46:41 -0600] [Job 4] Started filter /usr/lib/cups/filter/pstopdf (PID 25070)
I [24/Feb/2011:15:46:41 -0600] [Job 4] Started filter /usr/lib/cups/filter/pdftopdf (PID 25071)
E [24/Feb/2011:15:46:41 -0600] Unable to execute /usr/lib/cups/backend/cups-pdf: insecure file permissions (0106700)
D [24/Feb/2011:15:46:41 -0600] cupsdMarkDirty(P-----)
D [24/Feb/2011:15:46:41 -0600] cupsdMarkDirty(-----S)
D [24/Feb/2011:15:46:41 -0600] cupsdMarkDirty(-----S)
E [24/Feb/2011:15:46:41 -0600] [Job 4] Stopping job because the sheduler could not execute the backend.
D [24/Feb/2011:15:46:41 -0600] cupsdMarkDirty(----J-)
D [24/Feb/2011:15:46:41 -0600] cupsdMarkDirty(-----S)
D [24/Feb/2011:15:46:41 -0600] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/Generic-CUPS-PDF-Printer) from localhost
D [24/Feb/2011:15:46:41 -0600] cupsdSetBusyState: Dirty files
D [24/Feb/2011:15:46:41 -0600] PID 25070 (/usr/lib/cups/filter/pstopdf) was terminated normally with signal 15.
D [24/Feb/2011:15:46:41 -0600] PID 25069 (/usr/lib/cups/filter/bannertops) was terminated normally with signal 15.
D [24/Feb/2011:15:46:41 -0600] PID 25071 (/usr/lib/cups/filter/pdftopdf) was terminated normally with signal 15.
D [24/Feb/2011:15:46:41 -0600] cupsdAcceptClient: 15 from localhost (Domain)
D [24/Feb/2011:15:46:41 -0600] cupsdReadClient: 15 POST / HTTP/1.1
D [24/Feb/2011:15:46:41 -0600] cupsdSetBusyState: Active clients and dirty files
D [24/Feb/2011:15:46:41 -0600] cupsdAuthorize: No authentication data provided.
D [24/Feb/2011:15:46:41 -0600] cupsdReadClient: 15 1.1 Get-Jobs 1
D [24/Feb/2011:15:46:41 -0600] Get-Jobs ipp://localhost/printers/
D [24/Feb/2011:15:46:41 -0600] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [24/Feb/2011:15:46:41 -0600] cupsdSetBusyState: Dirty files
D [24/Feb/2011:15:46:41 -0600] cupsdReadClient: 15 WAITING Closing on EOF
D [24/Feb/2011:15:46:41 -0600] cupsdCloseClient: 15
D [24/Feb/2011:15:46:41 -0600] cupsdAcceptClient: 15 from localhost (Domain)
D [24/Feb/2011:15:46:41 -0600] cupsdReadClient: 15 POST / HTTP/1.1
D [24/Feb/2011:15:46:41 -0600] cupsdSetBusyState: Active clients and dirty files
D [24/Feb/2011:15:46:41 -0600] cupsdAuthorize: No authentication data provided.
D [24/Feb/2011:15:46:41 -0600] cupsdReadClient: 15 1.1 Get-Notifications 1
D [24/Feb/2011:15:46:41 -0600] Get-Notifications /
D [24/Feb/2011:15:46:41 -0600] cupsdIsAuthorized: requesting-user-name="jaypugh"
D [24/Feb/2011:15:46:41 -0600] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [24/Feb/2011:15:46:41 -0600] cupsdSetBusyState: Dirty files
D [24/Feb/2011:15:46:41 -0600] cupsdReadClient: 15 POST / HTTP/1.1
D [24/Feb/2011:15:46:41 -0600] cupsdSetBusyState: Active clients and dirty files
D [24/Feb/2011:15:46:41 -0600] cupsdAuthorize: No authentication data provided.
D [24/Feb/2011:15:46:41 -0600] cupsdReadClient: 15 1.1 Get-Job-Attributes 1
D [24/Feb/2011:15:46:41 -0600] Get-Job-Attributes ipp://localhost/jobs/4
D [24/Feb/2011:15:46:41 -0600] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/4) from localhost
D [24/Feb/2011:15:46:41 -0600] cupsdSetBusyState: Dirty files
D [24/Feb/2011:15:46:41 -0600] cupsdAcceptClient: 16 from localhost (Domain)
D [24/Feb/2011:15:46:41 -0600] cupsdReadClient: 16 POST / HTTP/1.1
D [24/Feb/2011:15:46:41 -0600] cupsdSetBusyState: Active clients and dirty files
D [24/Feb/2011:15:46:41 -0600] cupsdAuthorize: No authentication data provided.
D [24/Feb/2011:15:46:41 -0600] cupsdReadClient: 16 1.1 Get-Printer-Attributes 1
D [24/Feb/2011:15:46:41 -0600] Get-Printer-Attributes ipp://ubuntu:0/printers/Generic-CUPS-PDF-Printer
D [24/Feb/2011:15:46:41 -0600] Returning IPP successful-ok for Get-Printer-Attributes (ipp://ubuntu:0/printers/Generic-CUPS-PDF-Printer) from localhost
D [24/Feb/2011:15:46:41 -0600] cupsdSetBusyState: Dirty files
D [24/Feb/2011:15:46:41 -0600] cupsdReadClient: 16 POST / HTTP/1.1
D [24/Feb/2011:15:46:41 -0600] cupsdSetBusyState: Active clients and dirty files
D [24/Feb/2011:15:46:41 -0600] cupsdAuthorize: No authentication data provided.
D [24/Feb/2011:15:46:41 -0600] cupsdReadClient: 16 1.1 Get-Job-Attributes 1
D [24/Feb/2011:15:46:41 -0600] Get-Job-Attributes ipp://localhost/jobs/4
D [24/Feb/2011:15:46:41 -0600] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/4) from localhost
D [24/Feb/2011:15:46:41 -0600] cupsdSetBusyState: Dirty files
D [24/Feb/2011:15:46:41 -0600] cupsdReadClient: 12 POST / HTTP/1.1
D [24/Feb/2011:15:46:41 -0600] cupsdSetBusyState: Active clients and dirty files
D [24/Feb/2011:15:46:41 -0600] cupsdAuthorize: No authentication data provided.
D [24/Feb/2011:15:46:41 -0600] cupsdReadClient: 12 1.1 Get-Notifications 1
D [24/Feb/2011:15:46:41 -0600] Get-Notifications /
D [24/Feb/2011:15:46:41 -0600] cupsdIsAuthorized: requesting-user-name="jaypugh"
D [24/Feb/2011:15:46:41 -0600] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [24/Feb/2011:15:46:41 -0600] cupsdSetBusyState: Dirty files
D [24/Feb/2011:15:46:41 -0600] cupsdAcceptClient: 17 from localhost (Domain)
D [24/Feb/2011:15:46:41 -0600] cupsdReadClient: 13 WAITING Closing on EOF
D [24/Feb/2011:15:46:41 -0600] cupsdCloseClient: 13
D [24/Feb/2011:15:46:41 -0600] cupsdReadClient: 16 WAITING Closing on EOF
D [24/Feb/2011:15:46:41 -0600] cupsdCloseClient: 16
D [24/Feb/2011:15:46:41 -0600] cupsdReadClient: 17 POST / HTTP/1.1
D [24/Feb/2011:15:46:41 -0600] cupsdSetBusyState: Active clients and dirty files
D [24/Feb/2011:15:46:41 -0600] cupsdAuthorize: No authentication data provided.
D [24/Feb/2011:15:46:41 -0600] cupsdReadClient: 17 1.1 Get-Printer-Attributes 1
D [24/Feb/2011:15:46:41 -0600] Get-Printer-Attributes ipp://ubuntu:0/printers/Generic-CUPS-PDF-Printer
D [24/Feb/2011:15:46:41 -0600] Returning IPP successful-ok for Get-Printer-Attributes (ipp://ubuntu:0/printers/Generic-CUPS-PDF-Printer) from localhost
D [24/Feb/2011:15:46:41 -0600] cupsdSetBusyState: Dirty files
D [24/Feb/2011:15:46:41 -0600] cupsdReadClient: 17 POST / HTTP/1.1
D [24/Feb/2011:15:46:41 -0600] cupsdSetBusyState: Active clients and dirty files
D [24/Feb/2011:15:46:41 -0600] cupsdAuthorize: No authentication data provided.
D [24/Feb/2011:15:46:41 -0600] cupsdReadClient: 17 1.1 Get-Job-Attributes 1
D [24/Feb/2011:15:46:41 -0600] Get-Job-Attributes ipp://localhost/jobs/4
D [24/Feb/2011:15:46:41 -0600] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/4) from localhost
D [24/Feb/2011:15:46:41 -0600] cupsdSetBusyState: Dirty files
D [24/Feb/2011:15:46:42 -0600] [Job 4] Unloading...
D [24/Feb/2011:15:46:51 -0600] cupsdAcceptClient: 13 from localhost (Domain)
D [24/Feb/2011:15:46:51 -0600] cupsdReadClient: 13 POST /jobs/ HTTP/1.1
D [24/Feb/2011:15:46:51 -0600] cupsdSetBusyState: Active clients and dirty files
D [24/Feb/2011:15:46:51 -0600] cupsdAuthorize: No authentication data provided.
D [24/Feb/2011:15:46:51 -0600] cupsdReadClient: 13 1.1 Cancel-Job 1
D [24/Feb/2011:15:46:51 -0600] Cancel-Job ipp://localhost/jobs/4
D [24/Feb/2011:15:46:51 -0600] cupsdIsAuthorized: requesting-user-name="jaypugh"
D [24/Feb/2011:15:46:51 -0600] [Job 4] Loading attributes...
D [24/Feb/2011:15:46:51 -0600] cupsdMarkDirty(-----S)
I [24/Feb/2011:15:46:51 -0600] [Job 4] Job canceled by "jaypugh"
D [24/Feb/2011:15:46:51 -0600] cupsdMarkDirty(----J-)
I [24/Feb/2011:15:46:51 -0600] [Job 4] Canceled by "jaypugh".
D [24/Feb/2011:15:46:51 -0600] Returning IPP successful-ok for Cancel-Job (ipp://localhost/jobs/4) from localhost
D [24/Feb/2011:15:46:51 -0600] cupsdSetBusyState: Dirty files
D [24/Feb/2011:15:46:51 -0600] cupsdReadClient: 13 WAITING Closing on EOF
D [24/Feb/2011:15:46:51 -0600] cupsdCloseClient: 13
D [24/Feb/2011:15:46:51 -0600] cupsdAcceptClient: 13 from localhost (Domain)
D [24/Feb/2011:15:46:51 -0600] cupsdReadClient: 13 POST / HTTP/1.1
D [24/Feb/2011:15:46:51 -0600] cupsdSetBusyState: Active clients and dirty files
D [24/Feb/2011:15:46:51 -0600] cupsdAuthorize: No authentication data provided.
D [24/Feb/2011:15:46:51 -0600] cupsdReadClient: 13 1.1 Get-Notifications 1
D [24/Feb/2011:15:46:51 -0600] Get-Notifications /
D [24/Feb/2011:15:46:51 -0600] cupsdIsAuthorized: requesting-user-name="jaypugh"
D [24/Feb/2011:15:46:51 -0600] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [24/Feb/2011:15:46:51 -0600] cupsdSetBusyState: Dirty files
D [24/Feb/2011:15:46:51 -0600] cupsdReadClient: 13 WAITING Closing on EOF
D [24/Feb/2011:15:46:51 -0600] cupsdCloseClient: 13
D [24/Feb/2011:15:46:56 -0600] cupsdReadClient: 12 POST / HTTP/1.1
D [24/Feb/2011:15:46:56 -0600] cupsdSetBusyState: Active clients and dirty files
D [24/Feb/2011:15:46:56 -0600] cupsdAuthorize: No authentication data provided.
D [24/Feb/2011:15:46:56 -0600] cupsdReadClient: 12 1.1 Get-Job-Attributes 1
D [24/Feb/2011:15:46:56 -0600] Get-Job-Attributes ipp://localhost/jobs/4
D [24/Feb/2011:15:46:56 -0600] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/4) from localhost
D [24/Feb/2011:15:46:56 -0600] cupsdSetBusyState: Dirty files
D [24/Feb/2011:15:46:56 -0600] cupsdReadClient: 12 POST / HTTP/1.1
D [24/Feb/2011:15:46:56 -0600] cupsdSetBusyState: Active clients and dirty files
D [24/Feb/2011:15:46:56 -0600] cupsdAuthorize: No authentication data provided.
D [24/Feb/2011:15:46:56 -0600] cupsdReadClient: 12 1.1 Cancel-Subscription 1
D [24/Feb/2011:15:46:56 -0600] Cancel-Subscription /
D [24/Feb/2011:15:46:56 -0600] cupsdIsAuthorized: requesting-user-name="jaypugh"
D [24/Feb/2011:15:46:56 -0600] cupsdMarkDirty(-----S)
D [24/Feb/2011:15:46:56 -0600] Returning IPP successful-ok for Cancel-Subscription (/) from localhost
D [24/Feb/2011:15:46:56 -0600] cupsdSetBusyState: Dirty files
D [24/Feb/2011:15:46:56 -0600] cupsdReadClient: 12 PUT /admin/conf/cupsd.conf HTTP/1.1
D [24/Feb/2011:15:46:56 -0600] cupsdSetBusyState: Active clients and dirty files
D [24/Feb/2011:15:46:56 -0600] cupsdAuthorize: No authentication data provided.
D [24/Feb/2011:15:46:56 -0600] cupsdIsAuthorized: username=""
D [24/Feb/2011:15:46:56 -0600] cupsdSendHeader: 12 WWW-Authenticate: Basic realm="CUPS", trc="y"
D [24/Feb/2011:15:46:56 -0600] cupsdCloseClient: 12
D [24/Feb/2011:15:46:56 -0600] cupsdSetBusyState: Dirty files
D [24/Feb/2011:15:46:56 -0600] cupsdAcceptClient: 12 from localhost (Domain)
D [24/Feb/2011:15:46:56 -0600] cupsdReadClient: 12 PUT /admin/conf/cupsd.conf HTTP/1.1
D [24/Feb/2011:15:46:56 -0600] cupsdSetBusyState: Active clients and dirty files
D [24/Feb/2011:15:46:56 -0600] cupsdAuthorize: Authorized as jaypugh using PeerCred
D [24/Feb/2011:15:46:56 -0600] cupsdIsAuthorized: username="jaypugh"
I [24/Feb/2011:15:46:56 -0600] Installing config file "/etc/cups/cupsd.conf"...
D [24/Feb/2011:15:46:56 -0600] cupsdSetBusyState: Dirty files
D [24/Feb/2011:15:46:56 -0600] cupsdCloseClient: 15
D [24/Feb/2011:15:46:56 -0600] cupsdCloseClient: 17
D [24/Feb/2011:15:46:56 -0600] cupsdCloseClient: 12
I [24/Feb/2011:15:46:56 -0600] Saving printers.conf...
I [24/Feb/2011:15:46:56 -0600] Generating printcap /var/run/cups/printcap...
I [24/Feb/2011:15:46:56 -0600] Saving job cache file "/var/cache/cups/job.cache"...
I [24/Feb/2011:15:46:56 -0600] Saving subscriptions.conf...
D [24/Feb/2011:15:46:56 -0600] cupsdSetBusyState: Not busy




The error screen when you print is: Scheduler could not execute the backednd.

---

### Post by ranger_cole on 2011-02-24
[https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/472468](https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/472468) had this:
Amir Khosroshahi wrote on 2009-11-13: 	#5

The issue is resolved for me by executing:

sudo chmod 700 /usr/lib/cups/backend/cups-pdf
sudo chmod 700 /usr/lib/cups/backend

The error went away but I cannot find the printed pdfs.  Where are they saved to?:confused:

---

### Post by Chronon on 2011-02-24
I believe they should be saved to ~/PDF/.

---

### Post by ranger_cole on 2011-02-24
My PDF folder is empty.

---

### Post by ranger_cole on 2011-02-24
I tried print to file and clicked the pdf output button and saved to desktop.  There was no pdf file created on the desktop.   How is it that I can print to pdf in 8.04 LTS with no problem?????:confused:

---

