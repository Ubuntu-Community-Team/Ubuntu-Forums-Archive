---
title: "HP LaserJet P3015 not printing Ubuntu 12.04"
date: 2014-10-02
forum: Hardware
---

### Post by azile19 on 2014-10-02
I have a new Dell desktop running Ubuntu 12.04 and just got an HP LaserJet P3015 printer.  The first time I plugged it in, it was auto-detected and printed a test page.  Then I tried rearranging some things in my office, which included unplugging and plugging the printer back into the computer (I have no idea if it is still in the same port as the first time).  However, now, when I attempt to print a test page, the printer itself doesn't come out of sleep mode, and the printer queue just says "pending."  Sometimes it will change to "processing," although I can't find the pattern with that. I have tried reinstalling the printer through the Printing GUI, but I haven't had any change.  Below I have attached the error log messages and the diagnostic output from the printing troubleshooter GUI.



```

D [02/Oct/2014:10:12:30 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [02/Oct/2014:10:12:30 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [02/Oct/2014:10:12:30 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:12:30 -0400] cupsdAuthorize: No authentication data provided.
D [02/Oct/2014:10:12:30 -0400] cupsdReadClient: 17 1.1 Get-Jobs 1
D [02/Oct/2014:10:12:30 -0400] Get-Jobs ipp://localhost/printers/
D [02/Oct/2014:10:12:30 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [02/Oct/2014:10:12:30 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [02/Oct/2014:10:12:30 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [02/Oct/2014:10:12:30 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:12:30 -0400] cupsdAuthorize: No authentication data provided.
D [02/Oct/2014:10:12:30 -0400] cupsdReadClient: 17 1.1 Get-Jobs 1
D [02/Oct/2014:10:12:30 -0400] Get-Jobs ipp://localhost/printers/
D [02/Oct/2014:10:12:30 -0400] [Job 13] Loading attributes...
D [02/Oct/2014:10:12:30 -0400] [Job 14] Loading attributes...
D [02/Oct/2014:10:12:30 -0400] [Job 15] Loading attributes...
D [02/Oct/2014:10:12:30 -0400] [Job 16] Loading attributes...
D [02/Oct/2014:10:12:30 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [02/Oct/2014:10:12:30 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [02/Oct/2014:10:12:30 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [02/Oct/2014:10:12:30 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:12:30 -0400] cupsdAuthorize: No authentication data provided.
D [02/Oct/2014:10:12:30 -0400] cupsdReadClient: 17 1.1 Create-Printer-Subscription 1
D [02/Oct/2014:10:12:30 -0400] Create-Printer-Subscription /
D [02/Oct/2014:10:12:30 -0400] cupsdCreateSubscription(con=0x7fbbbcf58d00(17), uri="/")
D [02/Oct/2014:10:12:30 -0400] pullmethod="ippget"
D [02/Oct/2014:10:12:30 -0400] notify-lease-duration=86400
D [02/Oct/2014:10:12:30 -0400] notify-time-interval=0
D [02/Oct/2014:10:12:30 -0400] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")
D [02/Oct/2014:10:12:30 -0400] Added subscription #45 for server.
D [02/Oct/2014:10:12:30 -0400] cupsdMarkDirty(-----S)
D [02/Oct/2014:10:12:30 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"
D [02/Oct/2014:10:12:30 -0400] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost
D [02/Oct/2014:10:12:30 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [02/Oct/2014:10:12:31 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [02/Oct/2014:10:12:31 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:12:31 -0400] cupsdAuthorize: No authentication data provided.
D [02/Oct/2014:10:12:31 -0400] cupsdReadClient: 17 1.1 Get-Notifications 1
D [02/Oct/2014:10:12:31 -0400] Get-Notifications /
D [02/Oct/2014:10:12:31 -0400] cupsdIsAuthorized: requesting-user-name="liz"
D [02/Oct/2014:10:12:31 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [02/Oct/2014:10:12:31 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [02/Oct/2014:10:12:34 -0400] cupsdAcceptClient: 20 from localhost (Domain)
D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 20 POST / HTTP/1.1
D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:12:34 -0400] cupsdAuthorize: No authentication data provided.
D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 20 1.1 Create-Printer-Subscription 1
D [02/Oct/2014:10:12:34 -0400] Create-Printer-Subscription /
D [02/Oct/2014:10:12:34 -0400] cupsdCreateSubscription(con=0x7fbbbce999f0(20), uri="/")
D [02/Oct/2014:10:12:34 -0400] pullmethod="ippget"
D [02/Oct/2014:10:12:34 -0400] notify-lease-duration=86400
D [02/Oct/2014:10:12:34 -0400] notify-time-interval=0
D [02/Oct/2014:10:12:34 -0400] cupsdAddSubscription(mask=1798f, dest=(nil)(), job=(nil)(0), uri="(null)")
D [02/Oct/2014:10:12:34 -0400] Added subscription #46 for server.
D [02/Oct/2014:10:12:34 -0400] cupsdMarkDirty(-----S)
D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"
D [02/Oct/2014:10:12:34 -0400] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost
D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 20 POST / HTTP/1.1
D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:12:34 -0400] cupsdAuthorize: No authentication data provided.
D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 20 1.1 CUPS-Get-Printers 1
D [02/Oct/2014:10:12:34 -0400] CUPS-Get-Printers
D [02/Oct/2014:10:12:34 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 20 POST / HTTP/1.1
D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:12:34 -0400] cupsdAuthorize: No authentication data provided.
D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 20 1.1 CUPS-Get-Printers 1
D [02/Oct/2014:10:12:34 -0400] CUPS-Get-Printers
D [02/Oct/2014:10:12:34 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [02/Oct/2014:10:12:34 -0400] cupsdAcceptClient: 21 from localhost (Domain)
D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:12:34 -0400] cupsdAuthorize: No authentication data provided.
D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 21 1.1 Get-Printer-Attributes 1
D [02/Oct/2014:10:12:34 -0400] Get-Printer-Attributes ipp://localhost/printers/HP-LaserJet-P3010-Series
D [02/Oct/2014:10:12:34 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/HP-LaserJet-P3010-Series) from localhost
D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 21 WAITING Closing on EOF
D [02/Oct/2014:10:12:34 -0400] cupsdCloseClient: 21
D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 20 WAITING Closing on EOF
D [02/Oct/2014:10:12:34 -0400] cupsdCloseClient: 20
D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:12:34 -0400] cupsdAcceptClient: 20 from localhost (Domain)
D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 20 POST / HTTP/1.1
D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:12:34 -0400] cupsdAuthorize: No authentication data provided.
D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 20 1.1 Create-Printer-Subscription 1
D [02/Oct/2014:10:12:34 -0400] Create-Printer-Subscription /
D [02/Oct/2014:10:12:34 -0400] cupsdCreateSubscription(con=0x7fbbbce999f0(20), uri="/")
D [02/Oct/2014:10:12:34 -0400] pullmethod="ippget"
D [02/Oct/2014:10:12:34 -0400] notify-lease-duration=86400
D [02/Oct/2014:10:12:34 -0400] notify-time-interval=0
D [02/Oct/2014:10:12:34 -0400] cupsdAddSubscription(mask=1798f, dest=(nil)(), job=(nil)(0), uri="(null)")
D [02/Oct/2014:10:12:34 -0400] Added subscription #47 for server.
D [02/Oct/2014:10:12:34 -0400] cupsdMarkDirty(-----S)
D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"
D [02/Oct/2014:10:12:34 -0400] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost
D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 20 POST / HTTP/1.1
D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:12:34 -0400] cupsdAuthorize: No authentication data provided.
D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 20 1.1 CUPS-Get-Printers 1
D [02/Oct/2014:10:12:34 -0400] CUPS-Get-Printers
D [02/Oct/2014:10:12:34 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 20 POST / HTTP/1.1
D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:12:34 -0400] cupsdAuthorize: No authentication data provided.
D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 20 1.1 CUPS-Get-Printers 1
D [02/Oct/2014:10:12:34 -0400] CUPS-Get-Printers
D [02/Oct/2014:10:12:34 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 20 WAITING Closing on EOF
D [02/Oct/2014:10:12:34 -0400] cupsdCloseClient: 20
D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:12:34 -0400] cupsdAcceptClient: 20 from localhost (Domain)
D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 20 POST / HTTP/1.1
D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:12:34 -0400] cupsdAuthorize: No authentication data provided.
D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 20 1.1 Get-Jobs 1
D [02/Oct/2014:10:12:34 -0400] Get-Jobs ipp://localhost/printers/
D [02/Oct/2014:10:12:34 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 20 WAITING Closing on EOF
D [02/Oct/2014:10:12:34 -0400] cupsdCloseClient: 20
D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:12:34 -0400] cupsdAcceptClient: 20 from localhost (Domain)
D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 20 POST / HTTP/1.1
D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:12:34 -0400] cupsdAuthorize: No authentication data provided.
D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 20 1.1 Get-Jobs 1
D [02/Oct/2014:10:12:34 -0400] Get-Jobs ipp://localhost/printers/
D [02/Oct/2014:10:12:34 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 20 WAITING Closing on EOF
D [02/Oct/2014:10:12:34 -0400] cupsdCloseClient: 20
D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:12:35 -0400] cupsdAcceptClient: 20 from localhost (Domain)
D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 20 POST /printers/HP-LaserJet-P3010-Series HTTP/1.1
D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:12:35 -0400] cupsdAuthorize: No authentication data provided.
D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 20 1.1 Print-Job 1
D [02/Oct/2014:10:12:35 -0400] Print-Job ipp://localhost/printers/HP-LaserJet-P3010-Series
D [02/Oct/2014:10:12:35 -0400] [Job ???] Auto-typing file...
I [02/Oct/2014:10:12:35 -0400] [Job ???] Request file type is application/vnd.cups-pdf-banner.
D [02/Oct/2014:10:12:35 -0400] cupsdMarkDirty(----J-)
D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"
D [02/Oct/2014:10:12:35 -0400] add_job: requesting-user-name="liz"
D [02/Oct/2014:10:12:35 -0400] Adding default job-sheets values "none,none"...
I [02/Oct/2014:10:12:35 -0400] [Job 18] Adding start banner page "none".
D [02/Oct/2014:10:12:35 -0400] cupsdMarkDirty(-----S)
D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"
D [02/Oct/2014:10:12:35 -0400] cupsdMarkDirty(----J-)
D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"
I [02/Oct/2014:10:12:35 -0400] [Job 18] Adding end banner page "none".
I [02/Oct/2014:10:12:35 -0400] [Job 18] File of type application/vnd.cups-pdf-banner queued by "liz".
D [02/Oct/2014:10:12:35 -0400] [Job 18] hold_until=0
I [02/Oct/2014:10:12:35 -0400] [Job 18] Queued on "HP-LaserJet-P3010-Series" by "liz".
D [02/Oct/2014:10:12:35 -0400] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/HP-LaserJet-P3010-Series) from localhost
D [02/Oct/2014:10:12:35 -0400] [Notifier] state=3
D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [02/Oct/2014:10:12:35 -0400] cupsdAcceptClient: 21 from localhost (Domain)
D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:12:35 -0400] cupsdAuthorize: No authentication data provided.
D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 21 1.1 Get-Notifications 1
D [02/Oct/2014:10:12:35 -0400] Get-Notifications /
D [02/Oct/2014:10:12:35 -0400] cupsdIsAuthorized: requesting-user-name="liz"
D [02/Oct/2014:10:12:35 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 21 WAITING Closing on EOF
D [02/Oct/2014:10:12:35 -0400] cupsdCloseClient: 21
D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:12:35 -0400] cupsdAuthorize: No authentication data provided.
D [02/Oct/2014:10:12:35 -0400] cupsdAcceptClient: 21 from localhost (Domain)
D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"
D [02/Oct/2014:10:12:35 -0400] cupsdAuthorize: No authentication data provided.
D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 17 1.1 Get-Notifications 1
D [02/Oct/2014:10:12:35 -0400] Get-Notifications /
D [02/Oct/2014:10:12:35 -0400] cupsdIsAuthorized: requesting-user-name="liz"
D [02/Oct/2014:10:12:35 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 21 1.1 Get-Notifications 1
D [02/Oct/2014:10:12:35 -0400] Get-Notifications /
D [02/Oct/2014:10:12:35 -0400] cupsdIsAuthorized: requesting-user-name="liz"
D [02/Oct/2014:10:12:35 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"
D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:12:35 -0400] cupsdAuthorize: No authentication data provided.
D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 21 1.1 Get-Job-Attributes 1
D [02/Oct/2014:10:12:35 -0400] Get-Job-Attributes ipp://localhost/jobs/18
D [02/Oct/2014:10:12:35 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/18) from localhost
D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [02/Oct/2014:10:12:35 -0400] cupsdAcceptClient: 22 from localhost (Domain)
D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:12:35 -0400] cupsdAuthorize: No authentication data provided.
D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 22 1.1 Get-Job-Attributes 1
D [02/Oct/2014:10:12:35 -0400] Get-Job-Attributes ipp://localhost/jobs/18
D [02/Oct/2014:10:12:35 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/18) from localhost
D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 22 WAITING Closing on EOF
D [02/Oct/2014:10:12:35 -0400] cupsdCloseClient: 22
D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:12:35 -0400] cupsdAcceptClient: 22 from localhost (Domain)
D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:12:35 -0400] cupsdAuthorize: No authentication data provided.
D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 22 1.1 Get-Printer-Attributes 1
D [02/Oct/2014:10:12:35 -0400] Get-Printer-Attributes ipp://Boromir/printers/HP-LaserJet-P3010-Series
D [02/Oct/2014:10:12:35 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://Boromir/printers/HP-LaserJet-P3010-Series) from localhost
D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 22 WAITING Closing on EOF
D [02/Oct/2014:10:12:35 -0400] cupsdCloseClient: 22
D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:12:35 -0400] cupsdAcceptClient: 22 from localhost (Domain)
D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:12:35 -0400] cupsdAuthorize: No authentication data provided.
D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 22 1.1 Get-Job-Attributes 1
D [02/Oct/2014:10:12:35 -0400] Get-Job-Attributes ipp://localhost/jobs/18
D [02/Oct/2014:10:12:35 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/18) from localhost
D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 22 WAITING Closing on EOF
D [02/Oct/2014:10:12:35 -0400] cupsdCloseClient: 22
D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 21 WAITING Closing on EOF
D [02/Oct/2014:10:12:35 -0400] cupsdCloseClient: 21
D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:12:35 -0400] cupsdAcceptClient: 21 from localhost (Domain)
D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:12:35 -0400] cupsdAuthorize: No authentication data provided.
D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 21 1.1 Get-Notifications 1
D [02/Oct/2014:10:12:35 -0400] Get-Notifications /
D [02/Oct/2014:10:12:35 -0400] cupsdIsAuthorized: requesting-user-name="liz"
D [02/Oct/2014:10:12:35 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:12:35 -0400] cupsdAuthorize: No authentication data provided.
D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 21 1.1 Get-Job-Attributes 1
D [02/Oct/2014:10:12:35 -0400] Get-Job-Attributes ipp://localhost/jobs/18
D [02/Oct/2014:10:12:35 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/18) from localhost
D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [02/Oct/2014:10:12:35 -0400] cupsdAcceptClient: 22 from localhost (Domain)
D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:12:35 -0400] cupsdAuthorize: No authentication data provided.
D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 22 1.1 Get-Printer-Attributes 1
D [02/Oct/2014:10:12:35 -0400] Get-Printer-Attributes
D [02/Oct/2014:10:12:35 -0400] Get-Printer-Attributes client-error-not-found: The printer or class does not exist.
D [02/Oct/2014:10:12:35 -0400] Returning IPP client-error-not-found for Get-Printer-Attributes () from localhost
D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 22 WAITING Closing on EOF
D [02/Oct/2014:10:12:35 -0400] cupsdCloseClient: 22
D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:12:35 -0400] cupsdAcceptClient: 22 from localhost (Domain)
D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:12:35 -0400] cupsdAuthorize: No authentication data provided.
D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 22 1.1 Get-Job-Attributes 1
D [02/Oct/2014:10:12:35 -0400] Get-Job-Attributes ipp://localhost/jobs/18
D [02/Oct/2014:10:12:35 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/18) from localhost
D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 22 WAITING Closing on EOF
D [02/Oct/2014:10:12:35 -0400] cupsdCloseClient: 22
D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 21 WAITING Closing on EOF
D [02/Oct/2014:10:12:35 -0400] cupsdCloseClient: 21
D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
I [02/Oct/2014:10:12:58 -0400] Generating printcap /var/run/cups/printcap...
I [02/Oct/2014:10:12:58 -0400] Saving job.cache...
I [02/Oct/2014:10:12:58 -0400] Saving subscriptions.conf...
D [02/Oct/2014:10:12:59 -0400] cupsdSetBusyState: newbusy="Printing jobs", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:13:24 -0400] cupsdReadClient: 17 POST /jobs/ HTTP/1.1
D [02/Oct/2014:10:13:24 -0400] cupsdSetBusyState: newbusy="Active clients and printing jobs", busy="Printing jobs"
D [02/Oct/2014:10:13:24 -0400] cupsdAuthorize: No authentication data provided.
D [02/Oct/2014:10:13:24 -0400] cupsdReadClient: 17 1.1 Cancel-Job 1
D [02/Oct/2014:10:13:24 -0400] Cancel-Job ipp://localhost/jobs/18
D [02/Oct/2014:10:13:24 -0400] cupsdIsAuthorized: requesting-user-name="liz"
D [02/Oct/2014:10:13:24 -0400] cupsdMarkDirty(-----S)
D [02/Oct/2014:10:13:24 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients and printing jobs"
I [02/Oct/2014:10:13:24 -0400] [Job 18] Job canceled by "liz"
D [02/Oct/2014:10:13:24 -0400] cupsdMarkDirty(----J-)
D [02/Oct/2014:10:13:24 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"
D [02/Oct/2014:10:13:24 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"
I [02/Oct/2014:10:13:24 -0400] [Job 18] Canceled by "liz".
D [02/Oct/2014:10:13:24 -0400] Returning IPP successful-ok for Cancel-Job (ipp://localhost/jobs/18) from localhost
D [02/Oct/2014:10:13:24 -0400] [Notifier] state=3
D [02/Oct/2014:10:13:24 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [02/Oct/2014:10:13:25 -0400] [Job 18] Unloading...
D [02/Oct/2014:10:13:26 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [02/Oct/2014:10:13:26 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:13:26 -0400] cupsdAuthorize: No authentication data provided.
D [02/Oct/2014:10:13:26 -0400] cupsdReadClient: 17 1.1 Get-Job-Attributes 1
D [02/Oct/2014:10:13:26 -0400] Get-Job-Attributes ipp://localhost/jobs/18
D [02/Oct/2014:10:13:26 -0400] [Job 18] Loading attributes...
D [02/Oct/2014:10:13:26 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/18) from localhost
D [02/Oct/2014:10:13:26 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [02/Oct/2014:10:13:26 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [02/Oct/2014:10:13:26 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:13:26 -0400] cupsdAuthorize: No authentication data provided.
D [02/Oct/2014:10:13:26 -0400] cupsdReadClient: 17 1.1 Cancel-Subscription 1
D [02/Oct/2014:10:13:26 -0400] Cancel-Subscription /
D [02/Oct/2014:10:13:26 -0400] cupsdIsAuthorized: requesting-user-name="liz"
D [02/Oct/2014:10:13:26 -0400] cupsdMarkDirty(-----S)
D [02/Oct/2014:10:13:26 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"
D [02/Oct/2014:10:13:26 -0400] Returning IPP successful-ok for Cancel-Subscription (/) from localhost
D [02/Oct/2014:10:13:26 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [02/Oct/2014:10:13:26 -0400] cupsdReadClient: 17 GET /admin/conf/cupsd.conf HTTP/1.1
D [02/Oct/2014:10:13:26 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:13:26 -0400] cupsdAuthorize: No authentication data provided.
D [02/Oct/2014:10:13:26 -0400] cupsdIsAuthorized: username=""
D [02/Oct/2014:10:13:26 -0400] cupsdSendHeader: 17 WWW-Authenticate: Basic realm="CUPS", trc="y"
D [02/Oct/2014:10:13:26 -0400] cupsdCloseClient: 17
D [02/Oct/2014:10:13:26 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [02/Oct/2014:10:13:26 -0400] cupsdAcceptClient: 17 from localhost (Domain)
D [02/Oct/2014:10:13:26 -0400] cupsdReadClient: 17 GET /admin/conf/cupsd.conf HTTP/1.1
D [02/Oct/2014:10:13:26 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:13:26 -0400] cupsdAuthorize: Authorized as liz using PeerCred
D [02/Oct/2014:10:13:26 -0400] cupsdIsAuthorized: username="liz"
D [02/Oct/2014:10:13:26 -0400] cupsdIsAuthorized: username="liz"
D [02/Oct/2014:10:13:26 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [02/Oct/2014:10:13:26 -0400] cupsdReadClient: 17 GET /admin/conf/cupsd.conf HTTP/1.1
D [02/Oct/2014:10:13:26 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:13:26 -0400] cupsdAuthorize: Authorized as liz using PeerCred
D [02/Oct/2014:10:13:26 -0400] cupsdIsAuthorized: username="liz"
D [02/Oct/2014:10:13:26 -0400] cupsdIsAuthorized: username="liz"
D [02/Oct/2014:10:13:26 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [02/Oct/2014:10:13:26 -0400] cupsdReadClient: 17 GET /admin/conf/cupsd.conf HTTP/1.1
D [02/Oct/2014:10:13:26 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:13:26 -0400] cupsdAuthorize: Authorized as liz using PeerCred
D [02/Oct/2014:10:13:26 -0400] cupsdIsAuthorized: username="liz"
D [02/Oct/2014:10:13:26 -0400] cupsdIsAuthorized: username="liz"
D [02/Oct/2014:10:13:26 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [02/Oct/2014:10:13:26 -0400] cupsdReadClient: 17 PUT /admin/conf/cupsd.conf HTTP/1.1
D [02/Oct/2014:10:13:26 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:13:26 -0400] cupsdAuthorize: Authorized as liz using PeerCred
D [02/Oct/2014:10:13:26 -0400] cupsdIsAuthorized: username="liz"
I [02/Oct/2014:10:13:26 -0400] Installing config file "/etc/cups/cupsd.conf"...
D [02/Oct/2014:10:13:27 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [02/Oct/2014:10:13:27 -0400] cupsdCloseClient: 20
D [02/Oct/2014:10:13:27 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [02/Oct/2014:10:13:27 -0400] cupsdCloseClient: 17
D [02/Oct/2014:10:13:27 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
I [02/Oct/2014:10:13:27 -0400] Saving job.cache...
I [02/Oct/2014:10:13:27 -0400] Saving subscriptions.conf...
D [02/Oct/2014:10:13:27 -0400] cupsdSetBusyState: newbusy="Printing jobs", busy="Printing jobs and dirty files"
E [02/Oct/2014:10:13:27 -0400] Unknown directive SystemGroup on line 4 of /etc/cups/cupsd.conf.
E [02/Oct/2014:10:13:27 -0400] Unknown directive JobPrivateAccess on line 88 of /etc/cups/cupsd.conf.
E [02/Oct/2014:10:13:27 -0400] Unknown directive JobPrivateValues on line 89 of /etc/cups/cupsd.conf.
E [02/Oct/2014:10:13:27 -0400] Unknown directive SubscriptionPrivateAccess on line 90 of /etc/cups/cupsd.conf.
E [02/Oct/2014:10:13:27 -0400] Unknown directive SubscriptionPrivateValues on line 91 of /etc/cups/cupsd.conf.
E [02/Oct/2014:10:13:27 -0400] "/etc/cups/ssl/server.crt" is a bad symlink - No such file or directory
E [02/Oct/2014:10:13:27 -0400] "/etc/cups/ssl/server.key" is a bad symlink - No such file or directory
W [02/Oct/2014:10:13:27 -0400] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'HP-LaserJet-P3010-Series-Gray..' already exists
W [02/Oct/2014:10:13:27 -0400] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-HP-LaserJet-P3010-Series' already exists

```

```

Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest HP-LaserJet-P3010-Series (default)>,
 'cups_instance': None,
 'cups_queue': 'HP-LaserJet-P3010-Series',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'hp',
 'cups_printer_dict': {'device-uri': u'hp:/usb/HP_LaserJet_P3010_Series?serial=VND3Q11872',
                       'printer-info': u'Hewlett-Packard HP LaserJet P3010 Series',
                       'printer-is-shared': False,
                       'printer-location': u'Boromir',
                       'printer-make-and-model': u'HP LaserJet P3010 Series Postscript (recommended)',
                       'printer-state': 4,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 10653908,
                       'printer-uri-supported': u'ipp://localhost:631/printers/HP-LaserJet-P3010-Series'},
 'cups_printer_remote': False,
 'hplip_output': (['',
                   '\x1b[01mHP Linux Imaging and Printing System (ver. 3.12.2)\x1b[0m',
                   '\x1b[01mDevice Information Utility ver. 5.2\x1b[0m',
                   '',
                   'Copyright (c) 2001-9 Hewlett-Packard Development Company, LP',
                   'This software comes with ABSOLUTELY NO WARRANTY.',
                   'This is free software, and you are welcome to distribute it',
                   'under certain conditions. See COPYING file for more details.',
                   '',
                   '',
                   '\x1b[01mHP Linux Imaging and Printing System (ver. 3.12.2)\x1b[0m',
                   '\x1b[01mSystem Tray Status Service ver. 2.0\x1b[0m',
                   '',
                   'Copyright (c) 2001-9 Hewlett-Packard Development Company, LP',
                   'This software comes with ABSOLUTELY NO WARRANTY.',
                   'This is free software, and you are welcome to distribute it',
                   'under certain conditions. See COPYING file for more details.',
                   '',
                   '',
                   '\x1b[01mhp:/usb/HP_LaserJet_P3010_Series?serial=VND3Q11872\x1b[0m',
                   '',
                   '\x1b[01mDevice Parameters (dynamic data):\x1b[0m',
                   '\x1b[01m  Parameter                     Value(s)                                                  \x1b[0m',
                   '  ----------------------------  ----------------------------------------------------------',
                   '  back-end                      hp                                                        ',
                   "  cups-printers                 ['HP-LaserJet-P3010-Series']                              ",
                   '  cups-uri                      hp:/usb/HP_LaserJet_P3010_Series?serial=VND3Q11872        ',
                   '  dev-file                                                                                ',
                   '  device-state                  -1                                                        ',
                   '  device-uri                    hp:/usb/HP_LaserJet_P3010_Series?serial=VND3Q11872        ',
                   '  deviceid                                                                                ',
                   '  error-state                   101                                                       ',
                   '  host                                                                                    ',
                   '  is-hp                         True                                                      ',
                   '  panel                         0                                                         ',
                   '  panel-line1                                                                             ',
                   '  panel-line2                                                                             ',
                   '  port                          1                                                         ',
                   '  serial                        VND3Q11872                                                ',
                   '  status-code                   5002                                                      ',
                   '  status-desc                                                                             ',
                   '\x1b[01m',
                   'Model Parameters (static data):\x1b[0m',
                   '\x1b[01m  Parameter                     Value(s)                                                  \x1b[0m',
                   '  ----------------------------  ----------------------------------------------------------',
                   '  align-type                    0                                                         ',
                   '  clean-type                    0                                                         ',
                   '  color-cal-type                0                                                         ',
                   '  copy-type                     0                                                         ',
                   '  embedded-server-type          1                                                         ',
                   '  fax-type                      0                                                         ',
                   '  fw-download                   False                                                     ',
                   '  icon                          laserjet_2410.png                                         ',
                   '  io-mfp-mode                   3                                                         ',
                   '  io-mode                       1                                                         ',
                   '  io-support                    6                                                         ',
                   '  job-storage                   1                                                         ',
                   '  linefeed-cal-type             0                                                         ',
                   '  model                         HP_LaserJet_P3010_Series                                  ',
                   '  model-ui                      HP LaserJet p3010 Series                                  ',
                   '  model1                        HP LaserJet P3015 Printer                                 ',
                   '  model2                        HP LaserJet P3011 Printer                                 ',
                   '  monitor-type                  0                                                         ',
                   '  panel-check-type              1                                                         ',
                   '  pcard-type                    0                                                         ',
                   '  plugin                        0                                                         ',
                   '  plugin-reason                 0                                                         ',
                   '  power-settings                0                                                         ',
                   '  pq-diag-type                  0                                                         ',
                   '  r-type                        0                                                         ',
                   '  r0-agent1-kind                4                                                         ',
                   '  r0-agent1-sku                 CE255A                                                    ',
                   '  r0-agent1-type                1                                                         ',
                   '  scan-style                    0                                                         ',
                   '  scan-type                     0                                                         ',
                   '  status-battery-check          0                                                         ',
                   '  status-dynamic-counters       0                                                         ',
                   '  status-type                   1                                                         ',
                   '  support-released              True                                                      ',
                   '  support-subtype               2202411                                                   ',
                   '  support-type                  2                                                         ',
                   '  support-ver                   3.9.8                                                     ',
                   "  tech-class                    ['LJMono', 'Postscript']                                  ",
                   "  tech-subclass                 ['Normal']                                                ",
                   '  tech-type                     3                                                         ',
                   '  usb-pid                       36119                                                     ',
                   '  usb-vid                       1008                                                      ',
                   '  wifi-config                   0                                                         ',
                   '',
                   'Done.',
                   ''],
                  ['\x1b[35;01mwarning: No display found.\x1b[0m',
                   '\x1b[31;01merror: hp-info -u/--gui requires Qt4 GUI support. Entering interactive mode.\x1b[0m',
                   '\x1b[35;01mwarning: No display found.\x1b[0m',
                   '\x1b[31;01merror: hp-systray requires Qt4 GUI and DBus support. Exiting.\x1b[0m',
                   '\x1b[35;01mwarning: Unable to connect to dbus. Is hp-systray running?\x1b[0m',
                   '\x1b[31;01merror: Device busy: hp:/usb/HP_LaserJet_P3010_Series?serial=VND3Q11872\x1b[0m',
                   '\x1b[31;01merror: Error opening device (Device not found).\x1b[0m',
                   ''],
                  0),
 'is_cups_class': False,
 'local_cups_queue_attributes': {'auth-info-required': u'none',
                                 'charset-configured': u'utf-8',
                                 'charset-supported': [u'us-ascii', u'utf-8'],
                                 'color-supported': False,
                                 'compression-supported': [u'none', u'gzip'],
                                 'copies-default': 1,
                                 'copies-supported': (1, 9999),
                                 'cups-version': u'1.5.3',
                                 'device-uri': u'hp:/usb/HP_LaserJet_P3010_Series?serial=VND3Q11872',
                                 'document-format-default': u'application/octet-stream',
                                 'document-format-supported': [u'application/octet-stream',
                                                               u'application/pdf',
                                                               u'application/postscript',
                                                               u'application/vnd.adobe-reader-postscript',
                                                               u'application/vnd.cups-command',
                                                               u'application/vnd.cups-pdf',
                                                               u'application/vnd.cups-pdf-banner',
                                                               u'application/vnd.cups-postscript',
                                                               u'application/vnd.cups-raw',
                                                               u'application/x-cshell',
                                                               u'application/x-csource',
                                                               u'application/x-perl',
                                                               u'application/x-shell',
                                                               u'image/gif',
                                                               u'image/jpeg',
                                                               u'image/png',
                                                               u'image/tiff',
                                                               u'image/urf',
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
                                 'generated-natural-language-supported': [u'en-us'],
                                 'ipp-versions-supported': [u'1.0',
                                                            u'1.1',
                                                            u'2.0',
                                                            u'2.1'],
                                 'ippget-event-life': 15,
                                 'job-creation-attributes-supported': [u'copies',
                                                                       u'finishings',
                                                                       u'ipp-attribute-fidelity',
                                                                       u'job-hold-until',
                                                                       u'job-name',
                                                                       u'job-priority',
                                                                       u'job-sheets',
                                                                       u'media',
                                                                       u'media-col',
                                                                       u'multiple-document-handling',
                                                                       u'number-up',
                                                                       u'output-bin',
                                                                       u'output-mode',
                                                                       u'orientation-requested',
                                                                       u'page-ranges',
                                                                       u'print-quality',
                                                                       u'printer-resolution',
                                                                       u'sides'],
                                 'job-hold-until-default': u'no-hold',
                                 'job-hold-until-supported': [u'no-hold',
                                                              u'indefinite',
                                                              u'day-time',
                                                              u'evening',
                                                              u'night',
                                                              u'second-shift',
                                                              u'third-shift',
                                                              u'weekend'],
                                 'job-ids-supported': True,
                                 'job-k-limit': 0,
                                 'job-k-octets-supported': (0, 941587044),
                                 'job-page-limit': 0,
                                 'job-priority-default': 50,
                                 'job-priority-supported': [100],
                                 'job-quota-period': 0,
                                 'job-settable-attributes-supported': [u'copies',
                                                                       u'finishings',
                                                                       u'job-hold-until',
                                                                       u'job-name',
                                                                       u'job-priority',
                                                                       u'media',
                                                                       u'media-col',
                                                                       u'multiple-document-handling',
                                                                       u'number-up',
                                                                       u'output-bin',
                                                                       u'output-mode',
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
                                 'jpeg-k-octets-supported': (0, 941587044),
                                 'jpeg-x-dimension-supported': (0, 65535),
                                 'jpeg-y-dimension-supported': (1, 65535),
                                 'marker-change-time': 0,
                                 'media-bottom-margin-supported': [423,
                                                                   1168,
                                                                   428],
                                 'media-col-supported': [u'media-bottom-margin',
                                                         u'media-left-margin',
                                                         u'media-right-margin',
                                                         u'media-size',
                                                         u'media-source',
                                                         u'media-top-margin',
                                                         u'media-type'],
                                 'media-default': u'na_letter_8.5x11in',
                                 'media-left-margin-supported': [423, 339],
                                 'media-right-margin-supported': [423, 339],
                                 'media-source-supported': [u'auto',
                                                            u'tray1',
                                                            u'tray2',
                                                            u'tray3',
                                                            u'tray4',
                                                            u'tray1-man'],
                                 'media-supported': [u'na_letter_8.5x11in',
                                                     u'na_legal_8.5x14in',
                                                     u'na_executive_7.25x10.5in',
                                                     u'oe_half-letter_5.5x8.5in',
                                                     u'oe_w612h935_8.5x13in',
                                                     u'na_index-3x5_3x5in',
                                                     u'na_index-4x6_4x6in',
                                                     u'na_5x7_5x7in',
                                                     u'na_index-5x8_5x8in',
                                                     u'iso_a4_210x297mm',
                                                     u'iso_a5_148x210mm',
                                                     u'iso_a6_105x148mm',
                                                     u'jis_b5_182x257mm',
                                                     u'jis_b6_128x182mm',
                                                     u'om_w553h765_195.09x269.88mm',
                                                     u'om_w522h737_184.15x260mm',
                                                     u'oe_w558h774_7.75x10.75in',
                                                     u'om_double-postcard_147.99x200.03mm',
                                                     u'na_number-10_4.125x9.5in',
                                                     u'na_monarch_3.875x7.5in',
                                                     u'om_env-isob5_176.04x250.12mm',
                                                     u'iso_c5_162x229mm',
                                                     u'iso_dl_110x220mm',
                                                     u'custom_min_3x5in',
                                                     u'custom_max_431.8x594.11mm'],
                                 'media-top-margin-supported': [423,
                                                                106,
                                                                428],
                                 'media-type-supported': [u'unspecified',
                                                          u'stationery',
                                                          u'light6074',
                                                          u'mid-weight96110',
                                                          u'heavy111130',
                                                          u'extra-heavy131175',
                                                          u'cardstock',
                                                          u'mono-transparency',
                                                          u'labels',
                                                          u'stationery-letterhead',
                                                          u'envelope',
                                                          u'stationery-preprinted',
                                                          u'prepunched',
                                                          u'colored',
                                                          u'bond',
                                                          u'stationery-recycled',
                                                          u'rough'],
                                 'multiple-document-handling-supported': [u'separate-documents-uncollated-copies',
                                                                          u'separate-documents-collated-copies'],
                                 'multiple-document-jobs-supported': True,
                                 'multiple-operation-time-out': 300,
                                 'natural-language-configured': u'en-us',
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
                                                          14,
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
                                                          16423],
                                 'orientation-requested-default': None,
                                 'orientation-requested-supported': [3,
                                                                     4,
                                                                     5,
                                                                     6],
                                 'output-bin-default': u'face-down',
                                 'output-bin-supported': [u'face-down'],
                                 'output-mode-default': u'monochrome',
                                 'output-mode-supported': [u'monochrome'],
                                 'page-ranges-supported': True,
                                 'pages-per-minute': 42,
                                 'pdf-k-octets-supported': (0, 941587044),
                                 'pdf-versions-supported': [u'adobe-1.2',
                                                            u'adobe-1.3',
                                                            u'adobe-1.4',
                                                            u'adobe-1.5',
                                                            u'adobe-1.6',
                                                            u'adobe-1.7',
                                                            u'iso-19005-1_2005',
                                                            u'iso-32000-1_2008',
                                                            u'pwg-5102.3'],
                                 'pdl-override-supported': [u'attempted'],
                                 'port-monitor': u'none',
                                 'port-monitor-supported': [u'none', u'tbcp'],
                                 'print-color-mode-default': u'monochrome',
                                 'print-color-mode-supported': [u'monochrome'],
                                 'print-quality-default': 4,
                                 'print-quality-supported': [4],
                                 'printer-commands': [u'AutoConfigure',
                                                      u'Clean',
                                                      u'PrintSelfTestPage'],
                                 'printer-current-time': '(IPP_TAG_DATE)',
                                 'printer-dns-sd-name': None,
                                 'printer-error-policy': u'retry-job',
                                 'printer-error-policy-supported': [u'abort-job',
                                                                    u'retry-current-job',
                                                                    u'retry-job',
                                                                    u'stop-printer'],
                                 'printer-icons': u'http://localhost:631/icons/HP-LaserJet-P3010-Series.png',
                                 'printer-info': u'Hewlett-Packard HP LaserJet P3010 Series',
                                 'printer-is-accepting-jobs': True,
                                 'printer-is-shared': False,
                                 'printer-location': u'Boromir',
                                 'printer-make-and-model': u'HP LaserJet P3010 Series Postscript (recommended)',
                                 'printer-more-info': u'http://localhost:631/printers/HP-LaserJet-P3010-Series',
                                 'printer-name': u'HP-LaserJet-P3010-Series',
                                 'printer-op-policy': u'default',
                                 'printer-op-policy-supported': [u'authenticated',
                                                                 u'default'],
                                 'printer-resolution-default': (600, 600, 3),
                                 'printer-resolution-supported': [(1200,
                                                                   1200,
                                                                   3),
                                                                  (1200,
                                                                   1200,
                                                                   3),
                                                                  (600,
                                                                   600,
                                                                   3)],
                                 'printer-settable-attributes-supported': [u'printer-info',
                                                                           u'printer-location'],
                                 'printer-state': 4,
                                 'printer-state-change-time': 1412259082,
                                 'printer-state-message': u'',
                                 'printer-state-reasons': [u'none'],
                                 'printer-type': 10653908,
                                 'printer-up-time': 1412259118,
                                 'printer-uri-supported': [u'ipp://localhost:631/printers/HP-LaserJet-P3010-Series'],
                                 'printer-uuid': u'urn:uuid:0874c042-c158-3b94-70f4-953372a9aae0',
                                 'queued-job-count': 2,
                                 'server-is-sharing-printers': False,
                                 'sides-default': u'two-sided-long-edge',
                                 'sides-supported': [u'one-sided',
                                                     u'two-sided-long-edge',
                                                     u'two-sided-short-edge'],
                                 'uri-authentication-supported': [u'requesting-user-name'],
                                 'uri-security-supported': [u'none'],
                                 'which-jobs-supported': [u'completed',
                                                          u'not-completed',
                                                          u'aborted',
                                                          u'all',
                                                          u'canceled',
                                                          u'pending',
                                                          u'pending-held',
                                                          u'processing',
                                                          u'processing-stopped']}}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'Collate': u'True',
                                            u'Duplex': u'DuplexNoTumble',
                                            u'InputSlot': u'Auto',
                                            u'PageRegion': u'Letter',
                                            u'PageSize': u'Letter'},
                               u'HPFinishingPanel': {u'HPBookletBackCover': u'False',
                                                     u'HPBookletFilter': u'False',
                                                     u'HPBookletPageOrder': u'Normal',
                                                     u'HPBookletPageSize': u'Letter',
                                                     u'HPBookletScaling': u'Proportional',
                                                     u'HPManualDuplexOrientation': u'DuplexNoTumble',
                                                     u'HPManualDuplexPrintGuide': u'False',
                                                     u'HPManualDuplexSwitch': u'False',
                                                     u'HPRotate180': u'False',
                                                     u'HPStraightPaperPath': u'False',
                                                     u'MediaType': u'Unspecified',
                                                     u'MirrorPrint': u'False'},
                               u'HPImagingOptions': {u'HPEconoMode': u'PrinterDefault',
                                                     u'Resolution': u'600x600dpi'},
                               u'InstallableOptions': {u'HPCollateSupported': u'True128',
                                                       u'HPOption_Disk': u'None',
                                                       u'HPOption_Duplexer': u'True',
                                                       u'HPOption_Tray3': u'False',
                                                       u'HPOption_Tray4': u'False'},
                               u'Services': {u'HPServicesUtility': u'DeviceAndSuppliesStatus',
                                             u'HPServicesWeb': u'SupportAndTroubleshooting'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Choose device):
{'cups_device_dict': {'device-class': u'direct',
                      'device-id': u'MFG:Hewlett-Packard;MDL:HP LaserJet P3010 Series;CLS:PRINTER;DES:HP LaserJet P3010 Series;SN:VND3Q11872;',
                      'device-info': u'HP LaserJet P3010 Series USB VND3Q11872 HPLIP',
                      'device-location': u'',
                      'device-make-and-model': u'HP LaserJet P3010 Series'}}
Page 7 (Error log checkpoint):
{'cups_server_settings': {'BrowseLocalProtocols': 'CUPS dnssd',
                          'DefaultAuthType': 'Basic',
                          'JobPrivateAccess': 'default',
                          'JobPrivateValues': 'default',
                          'MaxLogSize': '0',
                          'SubscriptionPrivateAccess': 'default',
                          'SubscriptionPrivateValues': 'default',
                          'SystemGroup': 'lpadmin',
                          'WebInterface': 'Yes',
                          '_debug_logging': '0',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '0',
                          '_share_printers': '0',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 76514,
 'error_log_debug_logging_set': True}
Page 8 (Print test page):
{'test_page_attempted': '02/Oct/2014:10:12:35 +0000',
 'test_page_job_id': [18],
 'test_page_job_status': [(True,
                           18,
                           'HP-LaserJet-P3010-Series',
                           'Test Page',
                           'Pending',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-us',
                            'document-count': 0,
                            'document-format': u'application/vnd.cups-pdf-banner',
                            'job-hold-until': u'no-hold',
                            'job-id': 18,
                            'job-k-octets': 1,
                            'job-media-progress': 0,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'http://localhost:631/jobs/18',
                            'job-preserved': False,
                            'job-printer-up-time': 1412259206,
                            'job-printer-uri': u'ipp://localhost:631/printers/HP-LaserJet-P3010-Series',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 7,
                            'job-state-reasons': u'job-canceled-by-user',
                            'job-uri': u'ipp://localhost:631/jobs/18',
                            'job-uuid': u'urn:uuid:75d582c1-07b1-3ea5-694a-21e519097c14',
                            'printer-uri': u'ipp://localhost/printers/HP-LaserJet-P3010-Series',
                            'time-at-completed': 1412259204,
                            'time-at-creation': 1412259155,
                            'time-at-processing': None})],
 'test_page_jobs_cancelled': True,
 'test_page_successful': False}
Page 9 (Error log fetch):
{'error_log': ['D [02/Oct/2014:10:12:30 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [02/Oct/2014:10:12:30 -0400] cupsdReadClient: 17 POST / HTTP/1.1',
               'D [02/Oct/2014:10:12:30 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:12:30 -0400] cupsdAuthorize: No authentication data provided.',
               'D [02/Oct/2014:10:12:30 -0400] cupsdReadClient: 17 1.1 Get-Jobs 1',
               'D [02/Oct/2014:10:12:30 -0400] Get-Jobs ipp://localhost/printers/',
               'D [02/Oct/2014:10:12:30 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [02/Oct/2014:10:12:30 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [02/Oct/2014:10:12:30 -0400] cupsdReadClient: 17 POST / HTTP/1.1',
               'D [02/Oct/2014:10:12:30 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:12:30 -0400] cupsdAuthorize: No authentication data provided.',
               'D [02/Oct/2014:10:12:30 -0400] cupsdReadClient: 17 1.1 Get-Jobs 1',
               'D [02/Oct/2014:10:12:30 -0400] Get-Jobs ipp://localhost/printers/',
               'D [02/Oct/2014:10:12:30 -0400] [Job 13] Loading attributes...',
               'D [02/Oct/2014:10:12:30 -0400] [Job 14] Loading attributes...',
               'D [02/Oct/2014:10:12:30 -0400] [Job 15] Loading attributes...',
               'D [02/Oct/2014:10:12:30 -0400] [Job 16] Loading attributes...',
               'D [02/Oct/2014:10:12:30 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [02/Oct/2014:10:12:30 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [02/Oct/2014:10:12:30 -0400] cupsdReadClient: 17 POST / HTTP/1.1',
               'D [02/Oct/2014:10:12:30 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:12:30 -0400] cupsdAuthorize: No authentication data provided.',
               'D [02/Oct/2014:10:12:30 -0400] cupsdReadClient: 17 1.1 Create-Printer-Subscription 1',
               'D [02/Oct/2014:10:12:30 -0400] Create-Printer-Subscription /',
               'D [02/Oct/2014:10:12:30 -0400] cupsdCreateSubscription(con=0x7fbbbcf58d00(17), uri="/")',
               'D [02/Oct/2014:10:12:30 -0400] pullmethod="ippget"',
               'D [02/Oct/2014:10:12:30 -0400] notify-lease-duration=86400',
               'D [02/Oct/2014:10:12:30 -0400] notify-time-interval=0',
               'D [02/Oct/2014:10:12:30 -0400] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [02/Oct/2014:10:12:30 -0400] Added subscription #45 for server.',
               'D [02/Oct/2014:10:12:30 -0400] cupsdMarkDirty(-----S)',
               'D [02/Oct/2014:10:12:30 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [02/Oct/2014:10:12:30 -0400] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost',
               'D [02/Oct/2014:10:12:30 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [02/Oct/2014:10:12:31 -0400] cupsdReadClient: 17 POST / HTTP/1.1',
               'D [02/Oct/2014:10:12:31 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:12:31 -0400] cupsdAuthorize: No authentication data provided.',
               'D [02/Oct/2014:10:12:31 -0400] cupsdReadClient: 17 1.1 Get-Notifications 1',
               'D [02/Oct/2014:10:12:31 -0400] Get-Notifications /',
               'D [02/Oct/2014:10:12:31 -0400] cupsdIsAuthorized: requesting-user-name="liz"',
               'D [02/Oct/2014:10:12:31 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [02/Oct/2014:10:12:31 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [02/Oct/2014:10:12:34 -0400] cupsdAcceptClient: 20 from localhost (Domain)',
               'D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:12:34 -0400] cupsdAuthorize: No authentication data provided.',
               'D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 20 1.1 Create-Printer-Subscription 1',
               'D [02/Oct/2014:10:12:34 -0400] Create-Printer-Subscription /',
               'D [02/Oct/2014:10:12:34 -0400] cupsdCreateSubscription(con=0x7fbbbce999f0(20), uri="/")',
               'D [02/Oct/2014:10:12:34 -0400] pullmethod="ippget"',
               'D [02/Oct/2014:10:12:34 -0400] notify-lease-duration=86400',
               'D [02/Oct/2014:10:12:34 -0400] notify-time-interval=0',
               'D [02/Oct/2014:10:12:34 -0400] cupsdAddSubscription(mask=1798f, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [02/Oct/2014:10:12:34 -0400] Added subscription #46 for server.',
               'D [02/Oct/2014:10:12:34 -0400] cupsdMarkDirty(-----S)',
               'D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [02/Oct/2014:10:12:34 -0400] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost',
               'D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:12:34 -0400] cupsdAuthorize: No authentication data provided.',
               'D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 20 1.1 CUPS-Get-Printers 1',
               'D [02/Oct/2014:10:12:34 -0400] CUPS-Get-Printers',
               'D [02/Oct/2014:10:12:34 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:12:34 -0400] cupsdAuthorize: No authentication data provided.',
               'D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 20 1.1 CUPS-Get-Printers 1',
               'D [02/Oct/2014:10:12:34 -0400] CUPS-Get-Printers',
               'D [02/Oct/2014:10:12:34 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [02/Oct/2014:10:12:34 -0400] cupsdAcceptClient: 21 from localhost (Domain)',
               'D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 21 POST / HTTP/1.1',
               'D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:12:34 -0400] cupsdAuthorize: No authentication data provided.',
               'D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 21 1.1 Get-Printer-Attributes 1',
               'D [02/Oct/2014:10:12:34 -0400] Get-Printer-Attributes ipp://localhost/printers/HP-LaserJet-P3010-Series',
               'D [02/Oct/2014:10:12:34 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/HP-LaserJet-P3010-Series) from localhost',
               'D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 21 WAITING Closing on EOF',
               'D [02/Oct/2014:10:12:34 -0400] cupsdCloseClient: 21',
               'D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 20 WAITING Closing on EOF',
               'D [02/Oct/2014:10:12:34 -0400] cupsdCloseClient: 20',
               'D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:12:34 -0400] cupsdAcceptClient: 20 from localhost (Domain)',
               'D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:12:34 -0400] cupsdAuthorize: No authentication data provided.',
               'D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 20 1.1 Create-Printer-Subscription 1',
               'D [02/Oct/2014:10:12:34 -0400] Create-Printer-Subscription /',
               'D [02/Oct/2014:10:12:34 -0400] cupsdCreateSubscription(con=0x7fbbbce999f0(20), uri="/")',
               'D [02/Oct/2014:10:12:34 -0400] pullmethod="ippget"',
               'D [02/Oct/2014:10:12:34 -0400] notify-lease-duration=86400',
               'D [02/Oct/2014:10:12:34 -0400] notify-time-interval=0',
               'D [02/Oct/2014:10:12:34 -0400] cupsdAddSubscription(mask=1798f, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [02/Oct/2014:10:12:34 -0400] Added subscription #47 for server.',
               'D [02/Oct/2014:10:12:34 -0400] cupsdMarkDirty(-----S)',
               'D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [02/Oct/2014:10:12:34 -0400] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost',
               'D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:12:34 -0400] cupsdAuthorize: No authentication data provided.',
               'D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 20 1.1 CUPS-Get-Printers 1',
               'D [02/Oct/2014:10:12:34 -0400] CUPS-Get-Printers',
               'D [02/Oct/2014:10:12:34 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:12:34 -0400] cupsdAuthorize: No authentication data provided.',
               'D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 20 1.1 CUPS-Get-Printers 1',
               'D [02/Oct/2014:10:12:34 -0400] CUPS-Get-Printers',
               'D [02/Oct/2014:10:12:34 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 20 WAITING Closing on EOF',
               'D [02/Oct/2014:10:12:34 -0400] cupsdCloseClient: 20',
               'D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:12:34 -0400] cupsdAcceptClient: 20 from localhost (Domain)',
               'D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:12:34 -0400] cupsdAuthorize: No authentication data provided.',
               'D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 20 1.1 Get-Jobs 1',
               'D [02/Oct/2014:10:12:34 -0400] Get-Jobs ipp://localhost/printers/',
               'D [02/Oct/2014:10:12:34 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 20 WAITING Closing on EOF',
               'D [02/Oct/2014:10:12:34 -0400] cupsdCloseClient: 20',
               'D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:12:34 -0400] cupsdAcceptClient: 20 from localhost (Domain)',
               'D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:12:34 -0400] cupsdAuthorize: No authentication data provided.',
               'D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 20 1.1 Get-Jobs 1',
               'D [02/Oct/2014:10:12:34 -0400] Get-Jobs ipp://localhost/printers/',
               'D [02/Oct/2014:10:12:34 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [02/Oct/2014:10:12:34 -0400] cupsdReadClient: 20 WAITING Closing on EOF',
               'D [02/Oct/2014:10:12:34 -0400] cupsdCloseClient: 20',
               'D [02/Oct/2014:10:12:34 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:12:35 -0400] cupsdAcceptClient: 20 from localhost (Domain)',
               'D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 20 POST /printers/HP-LaserJet-P3010-Series HTTP/1.1',
               'D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:12:35 -0400] cupsdAuthorize: No authentication data provided.',
               'D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 20 1.1 Print-Job 1',
               'D [02/Oct/2014:10:12:35 -0400] Print-Job ipp://localhost/printers/HP-LaserJet-P3010-Series',
               'D [02/Oct/2014:10:12:35 -0400] [Job ???] Auto-typing file...',
               'I [02/Oct/2014:10:12:35 -0400] [Job ???] Request file type is application/vnd.cups-pdf-banner.',
               'D [02/Oct/2014:10:12:35 -0400] cupsdMarkDirty(----J-)',
               'D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [02/Oct/2014:10:12:35 -0400] add_job: requesting-user-name="liz"',
               'D [02/Oct/2014:10:12:35 -0400] Adding default job-sheets values "none,none"...',
               'I [02/Oct/2014:10:12:35 -0400] [Job 18] Adding start banner page "none".',
               'D [02/Oct/2014:10:12:35 -0400] cupsdMarkDirty(-----S)',
               'D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [02/Oct/2014:10:12:35 -0400] cupsdMarkDirty(----J-)',
               'D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'I [02/Oct/2014:10:12:35 -0400] [Job 18] Adding end banner page "none".',
               'I [02/Oct/2014:10:12:35 -0400] [Job 18] File of type application/vnd.cups-pdf-banner queued by "liz".',
               'D [02/Oct/2014:10:12:35 -0400] [Job 18] hold_until=0',
               'I [02/Oct/2014:10:12:35 -0400] [Job 18] Queued on "HP-LaserJet-P3010-Series" by "liz".',
               'D [02/Oct/2014:10:12:35 -0400] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/HP-LaserJet-P3010-Series) from localhost',
               'D [02/Oct/2014:10:12:35 -0400] [Notifier] state=3',
               'D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [02/Oct/2014:10:12:35 -0400] cupsdAcceptClient: 21 from localhost (Domain)',
               'D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 21 POST / HTTP/1.1',
               'D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:12:35 -0400] cupsdAuthorize: No authentication data provided.',
               'D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 21 1.1 Get-Notifications 1',
               'D [02/Oct/2014:10:12:35 -0400] Get-Notifications /',
               'D [02/Oct/2014:10:12:35 -0400] cupsdIsAuthorized: requesting-user-name="liz"',
               'D [02/Oct/2014:10:12:35 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 21 WAITING Closing on EOF',
               'D [02/Oct/2014:10:12:35 -0400] cupsdCloseClient: 21',
               'D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 17 POST / HTTP/1.1',
               'D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:12:35 -0400] cupsdAuthorize: No authentication data provided.',
               'D [02/Oct/2014:10:12:35 -0400] cupsdAcceptClient: 21 from localhost (Domain)',
               'D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 21 POST / HTTP/1.1',
               'D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [02/Oct/2014:10:12:35 -0400] cupsdAuthorize: No authentication data provided.',
               'D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 17 1.1 Get-Notifications 1',
               'D [02/Oct/2014:10:12:35 -0400] Get-Notifications /',
               'D [02/Oct/2014:10:12:35 -0400] cupsdIsAuthorized: requesting-user-name="liz"',
               'D [02/Oct/2014:10:12:35 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 21 1.1 Get-Notifications 1',
               'D [02/Oct/2014:10:12:35 -0400] Get-Notifications /',
               'D [02/Oct/2014:10:12:35 -0400] cupsdIsAuthorized: requesting-user-name="liz"',
               'D [02/Oct/2014:10:12:35 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 21 POST / HTTP/1.1',
               'D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:12:35 -0400] cupsdAuthorize: No authentication data provided.',
               'D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 21 1.1 Get-Job-Attributes 1',
               'D [02/Oct/2014:10:12:35 -0400] Get-Job-Attributes ipp://localhost/jobs/18',
               'D [02/Oct/2014:10:12:35 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/18) from localhost',
               'D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [02/Oct/2014:10:12:35 -0400] cupsdAcceptClient: 22 from localhost (Domain)',
               'D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 22 POST / HTTP/1.1',
               'D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:12:35 -0400] cupsdAuthorize: No authentication data provided.',
               'D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 22 1.1 Get-Job-Attributes 1',
               'D [02/Oct/2014:10:12:35 -0400] Get-Job-Attributes ipp://localhost/jobs/18',
               'D [02/Oct/2014:10:12:35 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/18) from localhost',
               'D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 22 WAITING Closing on EOF',
               'D [02/Oct/2014:10:12:35 -0400] cupsdCloseClient: 22',
               'D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:12:35 -0400] cupsdAcceptClient: 22 from localhost (Domain)',
               'D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 22 POST / HTTP/1.1',
               'D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:12:35 -0400] cupsdAuthorize: No authentication data provided.',
               'D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 22 1.1 Get-Printer-Attributes 1',
               'D [02/Oct/2014:10:12:35 -0400] Get-Printer-Attributes ipp://Boromir/printers/HP-LaserJet-P3010-Series',
               'D [02/Oct/2014:10:12:35 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://Boromir/printers/HP-LaserJet-P3010-Series) from localhost',
               'D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 22 WAITING Closing on EOF',
               'D [02/Oct/2014:10:12:35 -0400] cupsdCloseClient: 22',
               'D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:12:35 -0400] cupsdAcceptClient: 22 from localhost (Domain)',
               'D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 22 POST / HTTP/1.1',
               'D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:12:35 -0400] cupsdAuthorize: No authentication data provided.',
               'D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 22 1.1 Get-Job-Attributes 1',
               'D [02/Oct/2014:10:12:35 -0400] Get-Job-Attributes ipp://localhost/jobs/18',
               'D [02/Oct/2014:10:12:35 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/18) from localhost',
               'D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 22 WAITING Closing on EOF',
               'D [02/Oct/2014:10:12:35 -0400] cupsdCloseClient: 22',
               'D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 21 WAITING Closing on EOF',
               'D [02/Oct/2014:10:12:35 -0400] cupsdCloseClient: 21',
               'D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:12:35 -0400] cupsdAcceptClient: 21 from localhost (Domain)',
               'D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 21 POST / HTTP/1.1',
               'D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:12:35 -0400] cupsdAuthorize: No authentication data provided.',
               'D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 21 1.1 Get-Notifications 1',
               'D [02/Oct/2014:10:12:35 -0400] Get-Notifications /',
               'D [02/Oct/2014:10:12:35 -0400] cupsdIsAuthorized: requesting-user-name="liz"',
               'D [02/Oct/2014:10:12:35 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 21 POST / HTTP/1.1',
               'D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:12:35 -0400] cupsdAuthorize: No authentication data provided.',
               'D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 21 1.1 Get-Job-Attributes 1',
               'D [02/Oct/2014:10:12:35 -0400] Get-Job-Attributes ipp://localhost/jobs/18',
               'D [02/Oct/2014:10:12:35 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/18) from localhost',
               'D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [02/Oct/2014:10:12:35 -0400] cupsdAcceptClient: 22 from localhost (Domain)',
               'D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 22 POST / HTTP/1.1',
               'D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:12:35 -0400] cupsdAuthorize: No authentication data provided.',
               'D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 22 1.1 Get-Printer-Attributes 1',
               'D [02/Oct/2014:10:12:35 -0400] Get-Printer-Attributes',
               'D [02/Oct/2014:10:12:35 -0400] Get-Printer-Attributes client-error-not-found: The printer or class does not exist.',
               'D [02/Oct/2014:10:12:35 -0400] Returning IPP client-error-not-found for Get-Printer-Attributes () from localhost',
               'D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 22 WAITING Closing on EOF',
               'D [02/Oct/2014:10:12:35 -0400] cupsdCloseClient: 22',
               'D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:12:35 -0400] cupsdAcceptClient: 22 from localhost (Domain)',
               'D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 22 POST / HTTP/1.1',
               'D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:12:35 -0400] cupsdAuthorize: No authentication data provided.',
               'D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 22 1.1 Get-Job-Attributes 1',
               'D [02/Oct/2014:10:12:35 -0400] Get-Job-Attributes ipp://localhost/jobs/18',
               'D [02/Oct/2014:10:12:35 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/18) from localhost',
               'D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 22 WAITING Closing on EOF',
               'D [02/Oct/2014:10:12:35 -0400] cupsdCloseClient: 22',
               'D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:12:35 -0400] cupsdReadClient: 21 WAITING Closing on EOF',
               'D [02/Oct/2014:10:12:35 -0400] cupsdCloseClient: 21',
               'D [02/Oct/2014:10:12:35 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"',
               'I [02/Oct/2014:10:12:58 -0400] Generating printcap /var/run/cups/printcap...',
               'I [02/Oct/2014:10:12:58 -0400] Saving job.cache...',
               'I [02/Oct/2014:10:12:58 -0400] Saving subscriptions.conf...',
               'D [02/Oct/2014:10:12:59 -0400] cupsdSetBusyState: newbusy="Printing jobs", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:13:24 -0400] cupsdReadClient: 17 POST /jobs/ HTTP/1.1',
               'D [02/Oct/2014:10:13:24 -0400] cupsdSetBusyState: newbusy="Active clients and printing jobs", busy="Printing jobs"',
               'D [02/Oct/2014:10:13:24 -0400] cupsdAuthorize: No authentication data provided.',
               'D [02/Oct/2014:10:13:24 -0400] cupsdReadClient: 17 1.1 Cancel-Job 1',
               'D [02/Oct/2014:10:13:24 -0400] Cancel-Job ipp://localhost/jobs/18',
               'D [02/Oct/2014:10:13:24 -0400] cupsdIsAuthorized: requesting-user-name="liz"',
               'D [02/Oct/2014:10:13:24 -0400] cupsdMarkDirty(-----S)',
               'D [02/Oct/2014:10:13:24 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients and printing jobs"',
               'I [02/Oct/2014:10:13:24 -0400] [Job 18] Job canceled by "liz"',
               'D [02/Oct/2014:10:13:24 -0400] cupsdMarkDirty(----J-)',
               'D [02/Oct/2014:10:13:24 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [02/Oct/2014:10:13:24 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'I [02/Oct/2014:10:13:24 -0400] [Job 18] Canceled by "liz".',
               'D [02/Oct/2014:10:13:24 -0400] Returning IPP successful-ok for Cancel-Job (ipp://localhost/jobs/18) from localhost',
               'D [02/Oct/2014:10:13:24 -0400] [Notifier] state=3',
               'D [02/Oct/2014:10:13:24 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [02/Oct/2014:10:13:25 -0400] [Job 18] Unloading...',
               'D [02/Oct/2014:10:13:26 -0400] cupsdReadClient: 17 POST / HTTP/1.1',
               'D [02/Oct/2014:10:13:26 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:13:26 -0400] cupsdAuthorize: No authentication data provided.',
               'D [02/Oct/2014:10:13:26 -0400] cupsdReadClient: 17 1.1 Get-Job-Attributes 1',
               'D [02/Oct/2014:10:13:26 -0400] Get-Job-Attributes ipp://localhost/jobs/18',
               'D [02/Oct/2014:10:13:26 -0400] [Job 18] Loading attributes...',
               'D [02/Oct/2014:10:13:26 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/18) from localhost',
               'D [02/Oct/2014:10:13:26 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [02/Oct/2014:10:13:26 -0400] cupsdReadClient: 17 POST / HTTP/1.1',
               'D [02/Oct/2014:10:13:26 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:13:26 -0400] cupsdAuthorize: No authentication data provided.',
               'D [02/Oct/2014:10:13:26 -0400] cupsdReadClient: 17 1.1 Cancel-Subscription 1',
               'D [02/Oct/2014:10:13:26 -0400] Cancel-Subscription /',
               'D [02/Oct/2014:10:13:26 -0400] cupsdIsAuthorized: requesting-user-name="liz"',
               'D [02/Oct/2014:10:13:26 -0400] cupsdMarkDirty(-----S)',
               'D [02/Oct/2014:10:13:26 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [02/Oct/2014:10:13:26 -0400] Returning IPP successful-ok for Cancel-Subscription (/) from localhost',
               'D [02/Oct/2014:10:13:26 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [02/Oct/2014:10:13:26 -0400] cupsdReadClient: 17 GET /admin/conf/cupsd.conf HTTP/1.1',
               'D [02/Oct/2014:10:13:26 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:13:26 -0400] cupsdAuthorize: No authentication data provided.',
               'D [02/Oct/2014:10:13:26 -0400] cupsdIsAuthorized: username=""',
               'D [02/Oct/2014:10:13:26 -0400] cupsdSendHeader: 17 WWW-Authenticate: Basic realm="CUPS", trc="y"',
               'D [02/Oct/2014:10:13:26 -0400] cupsdCloseClient: 17',
               'D [02/Oct/2014:10:13:26 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [02/Oct/2014:10:13:26 -0400] cupsdAcceptClient: 17 from localhost (Domain)',
               'D [02/Oct/2014:10:13:26 -0400] cupsdReadClient: 17 GET /admin/conf/cupsd.conf HTTP/1.1',
               'D [02/Oct/2014:10:13:26 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:13:26 -0400] cupsdAuthorize: Authorized as liz using PeerCred',
               'D [02/Oct/2014:10:13:26 -0400] cupsdIsAuthorized: username="liz"',
               'D [02/Oct/2014:10:13:26 -0400] cupsdIsAuthorized: username="liz"',
               'D [02/Oct/2014:10:13:26 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [02/Oct/2014:10:13:26 -0400] cupsdReadClient: 17 GET /admin/conf/cupsd.conf HTTP/1.1',
               'D [02/Oct/2014:10:13:26 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:13:26 -0400] cupsdAuthorize: Authorized as liz using PeerCred',
               'D [02/Oct/2014:10:13:26 -0400] cupsdIsAuthorized: username="liz"',
               'D [02/Oct/2014:10:13:26 -0400] cupsdIsAuthorized: username="liz"',
               'D [02/Oct/2014:10:13:26 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [02/Oct/2014:10:13:26 -0400] cupsdReadClient: 17 GET /admin/conf/cupsd.conf HTTP/1.1',
               'D [02/Oct/2014:10:13:26 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:13:26 -0400] cupsdAuthorize: Authorized as liz using PeerCred',
               'D [02/Oct/2014:10:13:26 -0400] cupsdIsAuthorized: username="liz"',
               'D [02/Oct/2014:10:13:26 -0400] cupsdIsAuthorized: username="liz"',
               'D [02/Oct/2014:10:13:26 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [02/Oct/2014:10:13:26 -0400] cupsdReadClient: 17 PUT /admin/conf/cupsd.conf HTTP/1.1',
               'D [02/Oct/2014:10:13:26 -0400] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:13:26 -0400] cupsdAuthorize: Authorized as liz using PeerCred',
               'D [02/Oct/2014:10:13:26 -0400] cupsdIsAuthorized: username="liz"',
               'I [02/Oct/2014:10:13:26 -0400] Installing config file "/etc/cups/cupsd.conf"...',
               'D [02/Oct/2014:10:13:27 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [02/Oct/2014:10:13:27 -0400] cupsdCloseClient: 20',
               'D [02/Oct/2014:10:13:27 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"',
               'D [02/Oct/2014:10:13:27 -0400] cupsdCloseClient: 17',
               'D [02/Oct/2014:10:13:27 -0400] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"',
               'I [02/Oct/2014:10:13:27 -0400] Saving job.cache...',
               'I [02/Oct/2014:10:13:27 -0400] Saving subscriptions.conf...',
               'D [02/Oct/2014:10:13:27 -0400] cupsdSetBusyState: newbusy="Printing jobs", busy="Printing jobs and dirty files"',
               'E [02/Oct/2014:10:13:27 -0400] Unknown directive SystemGroup on line 4 of /etc/cups/cupsd.conf.',
               'E [02/Oct/2014:10:13:27 -0400] Unknown directive JobPrivateAccess on line 88 of /etc/cups/cupsd.conf.',
               'E [02/Oct/2014:10:13:27 -0400] Unknown directive JobPrivateValues on line 89 of /etc/cups/cupsd.conf.',
               'E [02/Oct/2014:10:13:27 -0400] Unknown directive SubscriptionPrivateAccess on line 90 of /etc/cups/cupsd.conf.',
               'E [02/Oct/2014:10:13:27 -0400] Unknown directive SubscriptionPrivateValues on line 91 of /etc/cups/cupsd.conf.',
               'E [02/Oct/2014:10:13:27 -0400] "/etc/cups/ssl/server.crt" is a bad symlink - No such file or directory',
               'E [02/Oct/2014:10:13:27 -0400] "/etc/cups/ssl/server.key" is a bad symlink - No such file or directory',
               "W [02/Oct/2014:10:13:27 -0400] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'HP-LaserJet-P3010-Series-Gray..' already exists",
               "W [02/Oct/2014:10:13:27 -0400] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-HP-LaserJet-P3010-Series' already exists"],
 'error_log_debug_logging_unset': True}
Page 10 (Locale issues):
{'printer_page_size': u'Letter',
 'system_locale_lang': None,
 'user_locale_ctype': 'en_US',
 'user_locale_messages': 'en_US'}

```

---

### Post by Vladlenin5000 on 2014-10-02
What do you mean by > I have tried reinstalling the printer through the Printing GUI, but I haven't had any change. ??????

Disconnect th USB cable.
Select and delete the printer you already have in System Settings > Printers.
Reconnect the cable *and* turn on the printer.

It should be detected by now. Install HPLIP for better driver support and additional functionality.

---

### Post by azile19 on 2014-10-02
Thanks for your response!  Yup, that's exactly what I meant by "reinstalling the printer." I just tried doing exactly what you said, including powering off.  The test page still says "Processing" and the printer has gone to sleep.

---

