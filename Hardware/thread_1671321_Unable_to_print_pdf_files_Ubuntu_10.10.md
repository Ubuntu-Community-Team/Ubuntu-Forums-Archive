---
title: "Unable to print pdf files Ubuntu 10.10"
date: 2011-01-19
forum: Hardware
---

### Post by belkira on 2011-01-19
I have installed my printer, a HP Photosmart c5140. I can print all docs except for pdf files. I have tried the following programs:

epdf
Okular
xpdf
Document viewer

All these programs deliver the same result, I get a message saying there was a problem processing the document, and a paper comes out of the printer with the following info on it:

Error: /undefined in --run--
                            Operand stack:
                                              --dict:7/16(L)-- R1 1 FontObj

Below is the print out from the debug log:
```
D [19/Jan/2011:19:18:20 -0700] cupsdSetBusyState: Dirty files
D [19/Jan/2011:19:18:20 -0700] cupsdReadClient: 12 POST / HTTP/1.1
D [19/Jan/2011:19:18:20 -0700] cupsdSetBusyState: Active clients and dirty files
D [19/Jan/2011:19:18:20 -0700] cupsdAuthorize: No authentication data provided.
D [19/Jan/2011:19:18:20 -0700] cupsdReadClient: 12 1.1 Get-Jobs 1
D [19/Jan/2011:19:18:20 -0700] Get-Jobs ipp://localhost/printers/
D [19/Jan/2011:19:18:20 -0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [19/Jan/2011:19:18:20 -0700] cupsdSetBusyState: Dirty files
D [19/Jan/2011:19:18:20 -0700] cupsdReadClient: 12 POST / HTTP/1.1
D [19/Jan/2011:19:18:20 -0700] cupsdSetBusyState: Active clients and dirty files
D [19/Jan/2011:19:18:20 -0700] cupsdAuthorize: No authentication data provided.
D [19/Jan/2011:19:18:20 -0700] cupsdReadClient: 12 1.1 Get-Jobs 1
D [19/Jan/2011:19:18:20 -0700] Get-Jobs ipp://localhost/printers/
D [19/Jan/2011:19:18:20 -0700] [Job 16] Loading attributes...
D [19/Jan/2011:19:18:20 -0700] [Job 17] Loading attributes...
D [19/Jan/2011:19:18:20 -0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [19/Jan/2011:19:18:20 -0700] cupsdSetBusyState: Dirty files
D [19/Jan/2011:19:18:20 -0700] cupsdReadClient: 12 POST / HTTP/1.1
D [19/Jan/2011:19:18:20 -0700] cupsdSetBusyState: Active clients and dirty files
D [19/Jan/2011:19:18:20 -0700] cupsdAuthorize: No authentication data provided.
D [19/Jan/2011:19:18:20 -0700] cupsdReadClient: 12 1.1 Create-Printer-Subscription 1
D [19/Jan/2011:19:18:20 -0700] Create-Printer-Subscription /
D [19/Jan/2011:19:18:20 -0700] cupsdCreateSubscription(con=0x2238c7d8(12), uri="/")
D [19/Jan/2011:19:18:20 -0700] pullmethod="ippget"
D [19/Jan/2011:19:18:20 -0700] notify-lease-duration=86400
D [19/Jan/2011:19:18:20 -0700] notify-time-interval=0
D [19/Jan/2011:19:18:20 -0700] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")
D [19/Jan/2011:19:18:20 -0700] Added subscription 11 for server
D [19/Jan/2011:19:18:20 -0700] cupsdMarkDirty(-----S)
D [19/Jan/2011:19:18:20 -0700] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost
D [19/Jan/2011:19:18:20 -0700] cupsdSetBusyState: Dirty files
D [19/Jan/2011:19:18:21 -0700] cupsdReadClient: 12 POST / HTTP/1.1
D [19/Jan/2011:19:18:21 -0700] cupsdSetBusyState: Active clients and dirty files
D [19/Jan/2011:19:18:21 -0700] cupsdAuthorize: No authentication data provided.
D [19/Jan/2011:19:18:21 -0700] cupsdReadClient: 12 1.1 Get-Notifications 1
D [19/Jan/2011:19:18:21 -0700] Get-Notifications /
D [19/Jan/2011:19:18:21 -0700] cupsdIsAuthorized: requesting-user-name="snelson"
D [19/Jan/2011:19:18:21 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [19/Jan/2011:19:18:21 -0700] cupsdSetBusyState: Dirty files
D [19/Jan/2011:19:18:44 -0700] cupsdAcceptClient: 13 from localhost (Domain)
D [19/Jan/2011:19:18:44 -0700] cupsdReadClient: 13 WAITING Closing on EOF
D [19/Jan/2011:19:18:44 -0700] cupsdCloseClient: 13
D [19/Jan/2011:19:18:44 -0700] cupsdAcceptClient: 13 from localhost (Domain)
D [19/Jan/2011:19:18:44 -0700] cupsdReadClient: 13 POST / HTTP/1.1
D [19/Jan/2011:19:18:44 -0700] cupsdSetBusyState: Active clients and dirty files
D [19/Jan/2011:19:18:44 -0700] cupsdAuthorize: No authentication data provided.
D [19/Jan/2011:19:18:44 -0700] cupsdReadClient: 13 1.1 CUPS-Get-Printers 1
D [19/Jan/2011:19:18:44 -0700] CUPS-Get-Printers
D [19/Jan/2011:19:18:44 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [19/Jan/2011:19:18:44 -0700] cupsdSetBusyState: Dirty files
D [19/Jan/2011:19:18:44 -0700] cupsdAcceptClient: 15 from localhost (Domain)
D [19/Jan/2011:19:18:44 -0700] cupsdReadClient: 13 WAITING Closing on EOF
D [19/Jan/2011:19:18:44 -0700] cupsdCloseClient: 13
D [19/Jan/2011:19:18:44 -0700] cupsdReadClient: 15 GET /printers/HP-Photosmart-C5100-series.ppd HTTP/1.1
D [19/Jan/2011:19:18:44 -0700] cupsdSetBusyState: Active clients and dirty files
D [19/Jan/2011:19:18:44 -0700] cupsdAuthorize: No authentication data provided.
D [19/Jan/2011:19:18:44 -0700] cupsdSetBusyState: Dirty files
D [19/Jan/2011:19:18:44 -0700] cupsdReadClient: 15 WAITING Closing on EOF
D [19/Jan/2011:19:18:44 -0700] cupsdCloseClient: 15
D [19/Jan/2011:19:18:44 -0700] cupsdAcceptClient: 13 from localhost (Domain)
D [19/Jan/2011:19:18:44 -0700] cupsdAcceptClient: 15 from localhost (Domain)
D [19/Jan/2011:19:18:44 -0700] cupsdReadClient: 13 WAITING Closing on EOF
D [19/Jan/2011:19:18:44 -0700] cupsdCloseClient: 13
D [19/Jan/2011:19:18:44 -0700] cupsdReadClient: 15 POST / HTTP/1.1
D [19/Jan/2011:19:18:44 -0700] cupsdSetBusyState: Active clients and dirty files
D [19/Jan/2011:19:18:44 -0700] cupsdAuthorize: No authentication data provided.
D [19/Jan/2011:19:18:44 -0700] cupsdReadClient: 15 1.1 CUPS-Get-Printers 1
D [19/Jan/2011:19:18:44 -0700] CUPS-Get-Printers
D [19/Jan/2011:19:18:44 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [19/Jan/2011:19:18:44 -0700] cupsdSetBusyState: Dirty files
D [19/Jan/2011:19:18:44 -0700] cupsdReadClient: 15 WAITING Closing on EOF
D [19/Jan/2011:19:18:44 -0700] cupsdCloseClient: 15
D [19/Jan/2011:19:18:45 -0700] cupsdAcceptClient: 13 from localhost (Domain)
D [19/Jan/2011:19:18:45 -0700] cupsdAcceptClient: 15 from localhost (Domain)
D [19/Jan/2011:19:18:45 -0700] cupsdReadClient: 13 WAITING Closing on EOF
D [19/Jan/2011:19:18:45 -0700] cupsdCloseClient: 13
D [19/Jan/2011:19:18:45 -0700] cupsdReadClient: 15 POST / HTTP/1.1
D [19/Jan/2011:19:18:45 -0700] cupsdSetBusyState: Active clients and dirty files
D [19/Jan/2011:19:18:45 -0700] cupsdAuthorize: No authentication data provided.
D [19/Jan/2011:19:18:45 -0700] cupsdReadClient: 15 1.1 CUPS-Get-Printers 1
D [19/Jan/2011:19:18:45 -0700] CUPS-Get-Printers
D [19/Jan/2011:19:18:45 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [19/Jan/2011:19:18:45 -0700] cupsdSetBusyState: Dirty files
D [19/Jan/2011:19:18:45 -0700] cupsdReadClient: 15 WAITING Closing on EOF
D [19/Jan/2011:19:18:45 -0700] cupsdCloseClient: 15
D [19/Jan/2011:19:18:45 -0700] cupsdAcceptClient: 13 from localhost (Domain)
D [19/Jan/2011:19:18:45 -0700] cupsdAcceptClient: 15 from localhost (Domain)
D [19/Jan/2011:19:18:45 -0700] cupsdReadClient: 13 WAITING Closing on EOF
D [19/Jan/2011:19:18:45 -0700] cupsdCloseClient: 13
D [19/Jan/2011:19:18:45 -0700] cupsdReadClient: 15 POST / HTTP/1.1
D [19/Jan/2011:19:18:45 -0700] cupsdSetBusyState: Active clients and dirty files
D [19/Jan/2011:19:18:45 -0700] cupsdAuthorize: No authentication data provided.
D [19/Jan/2011:19:18:45 -0700] cupsdReadClient: 15 1.1 CUPS-Get-Printers 1
D [19/Jan/2011:19:18:45 -0700] CUPS-Get-Printers
D [19/Jan/2011:19:18:45 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [19/Jan/2011:19:18:45 -0700] cupsdSetBusyState: Dirty files
D [19/Jan/2011:19:18:45 -0700] cupsdReadClient: 15 WAITING Closing on EOF
D [19/Jan/2011:19:18:45 -0700] cupsdCloseClient: 15
D [19/Jan/2011:19:18:45 -0700] cupsdAcceptClient: 13 from localhost (Domain)
D [19/Jan/2011:19:18:45 -0700] cupsdAcceptClient: 15 from localhost (Domain)
D [19/Jan/2011:19:18:45 -0700] cupsdReadClient: 13 WAITING Closing on EOF
D [19/Jan/2011:19:18:45 -0700] cupsdCloseClient: 13
D [19/Jan/2011:19:18:45 -0700] cupsdReadClient: 15 POST / HTTP/1.1
D [19/Jan/2011:19:18:45 -0700] cupsdSetBusyState: Active clients and dirty files
D [19/Jan/2011:19:18:45 -0700] cupsdAuthorize: No authentication data provided.
D [19/Jan/2011:19:18:45 -0700] cupsdReadClient: 15 1.1 CUPS-Get-Printers 1
D [19/Jan/2011:19:18:45 -0700] CUPS-Get-Printers
D [19/Jan/2011:19:18:45 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [19/Jan/2011:19:18:45 -0700] cupsdSetBusyState: Dirty files
D [19/Jan/2011:19:18:45 -0700] cupsdReadClient: 15 WAITING Closing on EOF
D [19/Jan/2011:19:18:45 -0700] cupsdCloseClient: 15
D [19/Jan/2011:19:18:45 -0700] cupsdAcceptClient: 13 from localhost (Domain)
D [19/Jan/2011:19:18:45 -0700] cupsdAcceptClient: 15 from localhost (Domain)
D [19/Jan/2011:19:18:45 -0700] cupsdReadClient: 13 WAITING Closing on EOF
D [19/Jan/2011:19:18:45 -0700] cupsdCloseClient: 13
D [19/Jan/2011:19:18:45 -0700] cupsdReadClient: 15 POST / HTTP/1.1
D [19/Jan/2011:19:18:45 -0700] cupsdSetBusyState: Active clients and dirty files
D [19/Jan/2011:19:18:45 -0700] cupsdAuthorize: No authentication data provided.
D [19/Jan/2011:19:18:45 -0700] cupsdReadClient: 15 1.1 CUPS-Get-Printers 1
D [19/Jan/2011:19:18:45 -0700] CUPS-Get-Printers
D [19/Jan/2011:19:18:45 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [19/Jan/2011:19:18:45 -0700] cupsdSetBusyState: Dirty files
D [19/Jan/2011:19:18:45 -0700] cupsdReadClient: 15 WAITING Closing on EOF
D [19/Jan/2011:19:18:45 -0700] cupsdCloseClient: 15
D [19/Jan/2011:19:18:45 -0700] cupsdAcceptClient: 13 from localhost (Domain)
D [19/Jan/2011:19:18:45 -0700] cupsdAcceptClient: 15 from localhost (Domain)
D [19/Jan/2011:19:18:45 -0700] cupsdReadClient: 13 WAITING Closing on EOF
D [19/Jan/2011:19:18:45 -0700] cupsdCloseClient: 13
D [19/Jan/2011:19:18:45 -0700] cupsdReadClient: 15 POST / HTTP/1.1
D [19/Jan/2011:19:18:45 -0700] cupsdSetBusyState: Active clients and dirty files
D [19/Jan/2011:19:18:45 -0700] cupsdAuthorize: No authentication data provided.
D [19/Jan/2011:19:18:45 -0700] cupsdReadClient: 15 1.1 CUPS-Get-Printers 1
D [19/Jan/2011:19:18:45 -0700] CUPS-Get-Printers
D [19/Jan/2011:19:18:45 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [19/Jan/2011:19:18:45 -0700] cupsdSetBusyState: Dirty files
D [19/Jan/2011:19:18:45 -0700] cupsdReadClient: 15 WAITING Closing on EOF
D [19/Jan/2011:19:18:45 -0700] cupsdCloseClient: 15
D [19/Jan/2011:19:18:46 -0700] cupsdAcceptClient: 13 from localhost (Domain)
I [19/Jan/2011:19:18:46 -0700] Generating printcap /var/run/cups/printcap...
I [19/Jan/2011:19:18:46 -0700] Saving subscriptions.conf...
D [19/Jan/2011:19:18:46 -0700] cupsdSetBusyState: Not busy
D [19/Jan/2011:19:18:46 -0700] cupsdAcceptClient: 15 from localhost (Domain)
D [19/Jan/2011:19:18:46 -0700] cupsdReadClient: 13 WAITING Closing on EOF
D [19/Jan/2011:19:18:46 -0700] cupsdCloseClient: 13
D [19/Jan/2011:19:18:46 -0700] cupsdReadClient: 15 POST / HTTP/1.1
D [19/Jan/2011:19:18:46 -0700] cupsdSetBusyState: Active clients
D [19/Jan/2011:19:18:46 -0700] cupsdAuthorize: No authentication data provided.
D [19/Jan/2011:19:18:46 -0700] cupsdReadClient: 15 1.1 CUPS-Get-Printers 1
D [19/Jan/2011:19:18:46 -0700] CUPS-Get-Printers
D [19/Jan/2011:19:18:46 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [19/Jan/2011:19:18:46 -0700] cupsdSetBusyState: Not busy
D [19/Jan/2011:19:18:46 -0700] cupsdReadClient: 15 WAITING Closing on EOF
D [19/Jan/2011:19:18:46 -0700] cupsdCloseClient: 15
D [19/Jan/2011:19:18:46 -0700] cupsdAcceptClient: 13 from localhost (Domain)
D [19/Jan/2011:19:18:46 -0700] cupsdAcceptClient: 15 from localhost (Domain)
D [19/Jan/2011:19:18:46 -0700] cupsdReadClient: 13 WAITING Closing on EOF
D [19/Jan/2011:19:18:46 -0700] cupsdCloseClient: 13
D [19/Jan/2011:19:18:46 -0700] cupsdReadClient: 15 POST / HTTP/1.1
D [19/Jan/2011:19:18:46 -0700] cupsdSetBusyState: Active clients
D [19/Jan/2011:19:18:46 -0700] cupsdAuthorize: No authentication data provided.
D [19/Jan/2011:19:18:46 -0700] cupsdReadClient: 15 1.1 CUPS-Get-Printers 1
D [19/Jan/2011:19:18:46 -0700] CUPS-Get-Printers
D [19/Jan/2011:19:18:46 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [19/Jan/2011:19:18:46 -0700] cupsdSetBusyState: Not busy
D [19/Jan/2011:19:18:46 -0700] cupsdReadClient: 15 WAITING Closing on EOF
D [19/Jan/2011:19:18:46 -0700] cupsdCloseClient: 15
D [19/Jan/2011:19:18:46 -0700] cupsdAcceptClient: 13 from localhost (Domain)
D [19/Jan/2011:19:18:46 -0700] cupsdAcceptClient: 15 from localhost (Domain)
D [19/Jan/2011:19:18:46 -0700] cupsdReadClient: 13 WAITING Closing on EOF
D [19/Jan/2011:19:18:46 -0700] cupsdCloseClient: 13
D [19/Jan/2011:19:18:46 -0700] cupsdReadClient: 15 POST / HTTP/1.1
D [19/Jan/2011:19:18:46 -0700] cupsdSetBusyState: Active clients
D [19/Jan/2011:19:18:46 -0700] cupsdAuthorize: No authentication data provided.
D [19/Jan/2011:19:18:46 -0700] cupsdReadClient: 15 1.1 CUPS-Get-Printers 1
D [19/Jan/2011:19:18:46 -0700] CUPS-Get-Printers
D [19/Jan/2011:19:18:46 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [19/Jan/2011:19:18:46 -0700] cupsdSetBusyState: Not busy
D [19/Jan/2011:19:18:46 -0700] cupsdReadClient: 15 WAITING Closing on EOF
D [19/Jan/2011:19:18:46 -0700] cupsdCloseClient: 15
D [19/Jan/2011:19:18:46 -0700] cupsdAcceptClient: 13 from localhost (Domain)
D [19/Jan/2011:19:18:46 -0700] cupsdAcceptClient: 15 from localhost (Domain)
D [19/Jan/2011:19:18:46 -0700] cupsdReadClient: 13 WAITING Closing on EOF
D [19/Jan/2011:19:18:46 -0700] cupsdCloseClient: 13
D [19/Jan/2011:19:18:46 -0700] cupsdReadClient: 15 POST / HTTP/1.1
D [19/Jan/2011:19:18:46 -0700] cupsdSetBusyState: Active clients
D [19/Jan/2011:19:18:46 -0700] cupsdAuthorize: No authentication data provided.
D [19/Jan/2011:19:18:46 -0700] cupsdReadClient: 15 1.1 CUPS-Get-Printers 1
D [19/Jan/2011:19:18:46 -0700] CUPS-Get-Printers
D [19/Jan/2011:19:18:46 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [19/Jan/2011:19:18:46 -0700] cupsdSetBusyState: Not busy
D [19/Jan/2011:19:18:46 -0700] cupsdReadClient: 15 WAITING Closing on EOF
D [19/Jan/2011:19:18:46 -0700] cupsdCloseClient: 15
D [19/Jan/2011:19:18:46 -0700] cupsdAcceptClient: 13 from localhost (Domain)
D [19/Jan/2011:19:18:46 -0700] cupsdReadClient: 13 POST /printers/HP-Photosmart-C5100-series HTTP/1.1
D [19/Jan/2011:19:18:46 -0700] cupsdSetBusyState: Active clients
D [19/Jan/2011:19:18:46 -0700] cupsdAuthorize: No authentication data provided.
D [19/Jan/2011:19:18:46 -0700] cupsdReadClient: 13 1.1 Print-Job 1
D [19/Jan/2011:19:18:46 -0700] Print-Job ipp://localhost:631/printers/HP-Photosmart-C5100-series
D [19/Jan/2011:19:18:46 -0700] [Job ???] Auto-typing file...
I [19/Jan/2011:19:18:46 -0700] [Job ???] Request file type is application/pdf.
D [19/Jan/2011:19:18:46 -0700] cupsdMarkDirty(----J-)
D [19/Jan/2011:19:18:46 -0700] cupsdSetBusyState: Active clients and dirty files
D [19/Jan/2011:19:18:46 -0700] add_job: requesting-user-name="snelson"
I [19/Jan/2011:19:18:46 -0700] [Job 19] Adding start banner page "none".
D [19/Jan/2011:19:18:46 -0700] cupsdMarkDirty(-----S)
D [19/Jan/2011:19:18:46 -0700] cupsdMarkDirty(----J-)
I [19/Jan/2011:19:18:46 -0700] [Job 19] Adding end banner page "none".
I [19/Jan/2011:19:18:46 -0700] [Job 19] File of type application/pdf queued by "snelson".
D [19/Jan/2011:19:18:46 -0700] [Job 19] hold_until=0
I [19/Jan/2011:19:18:46 -0700] [Job 19] Queued on "HP-Photosmart-C5100-series" by "snelson".
D [19/Jan/2011:19:18:46 -0700] cupsdMarkDirty(----J-)
D [19/Jan/2011:19:18:46 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [19/Jan/2011:19:18:46 -0700] cupsdMarkDirty(-----S)
D [19/Jan/2011:19:18:46 -0700] [Job 19] job-sheets=none,none
D [19/Jan/2011:19:18:46 -0700] [Job 19] argv[0]="HP-Photosmart-C5100-series"
D [19/Jan/2011:19:18:46 -0700] [Job 19] argv[1]="19"
D [19/Jan/2011:19:18:46 -0700] [Job 19] argv[2]="snelson"
D [19/Jan/2011:19:18:46 -0700] [Job 19] argv[3]="Invoice #			1060"
D [19/Jan/2011:19:18:46 -0700] [Job 19] argv[4]="1"
D [19/Jan/2011:19:18:46 -0700] [Job 19] argv[5]="DryTime=Zero PageSize=Letter Quality=FromPrintoutMode InputSlot=Default number-up=1 PrintoutMode=Normal Duplex=None job-uuid=urn:uuid:09c1e3f5-9c79-3e23-7f12-60a4291e9b36 job-originating-host-name=localhost"
D [19/Jan/2011:19:18:46 -0700] [Job 19] argv[6]="/var/spool/cups/d00019-001"
D [19/Jan/2011:19:18:46 -0700] [Job 19] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [19/Jan/2011:19:18:46 -0700] [Job 19] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [19/Jan/2011:19:18:46 -0700] [Job 19] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [19/Jan/2011:19:18:46 -0700] [Job 19] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [19/Jan/2011:19:18:46 -0700] [Job 19] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [19/Jan/2011:19:18:46 -0700] [Job 19] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [19/Jan/2011:19:18:46 -0700] [Job 19] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [19/Jan/2011:19:18:46 -0700] [Job 19] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [19/Jan/2011:19:18:46 -0700] [Job 19] envp[8]="HOME=/var/spool/cups/tmp"
D [19/Jan/2011:19:18:46 -0700] [Job 19] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [19/Jan/2011:19:18:46 -0700] [Job 19] envp[10]="SERVER_ADMIN=root@Shons"
D [19/Jan/2011:19:18:46 -0700] [Job 19] envp[11]="SOFTWARE=CUPS/1.4.4"
D [19/Jan/2011:19:18:46 -0700] [Job 19] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [19/Jan/2011:19:18:46 -0700] [Job 19] envp[13]="USER=root"
D [19/Jan/2011:19:18:46 -0700] [Job 19] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [19/Jan/2011:19:18:46 -0700] [Job 19] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [19/Jan/2011:19:18:46 -0700] [Job 19] envp[16]="IPP_PORT=631"
D [19/Jan/2011:19:18:46 -0700] [Job 19] envp[17]="CHARSET=utf-8"
D [19/Jan/2011:19:18:46 -0700] [Job 19] envp[18]="LANG=en_US.UTF-8"
D [19/Jan/2011:19:18:46 -0700] [Job 19] envp[19]="PPD=/etc/cups/ppd/HP-Photosmart-C5100-series.ppd"
D [19/Jan/2011:19:18:46 -0700] [Job 19] envp[20]="RIP_MAX_CACHE=auto"
D [19/Jan/2011:19:18:46 -0700] [Job 19] envp[21]="CONTENT_TYPE=application/pdf"
D [19/Jan/2011:19:18:46 -0700] [Job 19] envp[22]="DEVICE_URI=hp:/net/Photosmart_C5100_series?zc=HP52C24D"
D [19/Jan/2011:19:18:46 -0700] [Job 19] envp[23]="PRINTER_INFO=HP Photosmart C5100 series"
D [19/Jan/2011:19:18:46 -0700] [Job 19] envp[24]="PRINTER_LOCATION="
D [19/Jan/2011:19:18:46 -0700] [Job 19] envp[25]="PRINTER=HP-Photosmart-C5100-series"
D [19/Jan/2011:19:18:46 -0700] [Job 19] envp[26]="CUPS_FILETYPE=document"
D [19/Jan/2011:19:18:46 -0700] [Job 19] envp[27]="FINAL_CONTENT_TYPE=printer/HP-Photosmart-C5100-series"
I [19/Jan/2011:19:18:46 -0700] [Job 19] Started filter /usr/lib/cups/filter/pdftopdf (PID 8630)
I [19/Jan/2011:19:18:46 -0700] [Job 19] Started filter /usr/lib/cups/filter/foomatic-rip (PID 8631)
I [19/Jan/2011:19:18:46 -0700] [Job 19] Started backend /usr/lib/cups/backend/hp (PID 8632)
D [19/Jan/2011:19:18:46 -0700] cupsdMarkDirty(-----S)
D [19/Jan/2011:19:18:46 -0700] Returning IPP successful-ok for Print-Job (ipp://localhost:631/printers/HP-Photosmart-C5100-series) from localhost
D [19/Jan/2011:19:18:46 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [19/Jan/2011:19:18:46 -0700] cupsdReadClient: 13 WAITING Closing on EOF
D [19/Jan/2011:19:18:46 -0700] cupsdCloseClient: 13
D [19/Jan/2011:19:18:46 -0700] [Job 19] Getting input from file
D [19/Jan/2011:19:18:46 -0700] [Job 19] foomatic-rip version 4.0.5.223 running...
D [19/Jan/2011:19:18:46 -0700] [Job 19] Parsing PPD file ...
D [19/Jan/2011:19:18:46 -0700] [Job 19] Added option Resolution
D [19/Jan/2011:19:18:46 -0700] [Job 19] Added option PageSize
D [19/Jan/2011:19:18:46 -0700] [Job 19] Added option Model
D [19/Jan/2011:19:18:46 -0700] [Job 19] Added option PrintoutMode
D [19/Jan/2011:19:18:46 -0700] [Job 19] Added option InputSlot
D [19/Jan/2011:19:18:46 -0700] [Job 19] Added option Duplex
D [19/Jan/2011:19:18:46 -0700] [Job 19] Added option DryTime
D [19/Jan/2011:19:18:46 -0700] [Job 19] Added option Quality
D [19/Jan/2011:19:18:46 -0700] [Job 19] Added option ImageableArea
D [19/Jan/2011:19:18:46 -0700] [Job 19] Added option PaperDimension
D [19/Jan/2011:19:18:46 -0700] [Job 19] Added option Font
D [19/Jan/2011:19:18:46 -0700] [Job 19]
D [19/Jan/2011:19:18:46 -0700] [Job 19] Parameter Summary
D [19/Jan/2011:19:18:46 -0700] [Job 19] -----------------
D [19/Jan/2011:19:18:46 -0700] [Job 19]
D [19/Jan/2011:19:18:46 -0700] [Job 19] Spooler: cups
D [19/Jan/2011:19:18:46 -0700] [Job 19] Printer: HP-Photosmart-C5100-series
D [19/Jan/2011:19:18:46 -0700] [Job 19] Shell: /bin/bash
D [19/Jan/2011:19:18:46 -0700] [Job 19] PPD file: /etc/cups/ppd/HP-Photosmart-C5100-series.ppd
D [19/Jan/2011:19:18:46 -0700] [Job 19] ATTR file:
D [19/Jan/2011:19:18:46 -0700] [Job 19] Printer model: HP Photosmart c5100 Series hpijs, 3.10.6
D [19/Jan/2011:19:18:46 -0700] [Job 19] Job title: Invoice 			1060
D [19/Jan/2011:19:18:46 -0700] [Job 19] File(s) to be printed:
D [19/Jan/2011:19:18:46 -0700] [Job 19] <STDIN>
D [19/Jan/2011:19:18:46 -0700] [Job 19]
D [19/Jan/2011:19:18:46 -0700] [Job 19] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [19/Jan/2011:19:18:46 -0700] [Job 19] Printing system options:
D [19/Jan/2011:19:18:46 -0700] [Job 19] Pondering option 'number-up=1'
D [19/Jan/2011:19:18:46 -0700] [Job 19] Unknown option number-up=1.
D [19/Jan/2011:19:18:46 -0700] [Job 19] Pondering option 'job-uuid=urn:uuid:09c1e3f5-9c79-3e23-7f12-60a4291e9b36'
D [19/Jan/2011:19:18:46 -0700] [Job 19] Unknown option job-uuid=urn:uuid:09c1e3f5-9c79-3e23-7f12-60a4291e9b36.
D [19/Jan/2011:19:18:46 -0700] [Job 19] Pondering option 'job-originating-host-name=localhost'
D [19/Jan/2011:19:18:46 -0700] [Job 19] Unknown option job-originating-host-name=localhost.
D [19/Jan/2011:19:18:46 -0700] [Job 19] Options from the PPD file:
D [19/Jan/2011:19:18:46 -0700] [Job 19] Pondering option 'DryTime=Zero'
D [19/Jan/2011:19:18:46 -0700] [Job 19] Pondering option 'PageSize=Letter'
D [19/Jan/2011:19:18:46 -0700] [Job 19] Pondering option 'Quality=FromPrintoutMode'
D [19/Jan/2011:19:18:46 -0700] [Job 19] Pondering option 'InputSlot=Default'
D [19/Jan/2011:19:18:46 -0700] [Job 19] Pondering option 'PrintoutMode=Normal'
D [19/Jan/2011:19:18:46 -0700] [Job 19] Pondering option 'Duplex=None'
D [19/Jan/2011:19:18:46 -0700] [Job 19]
D [19/Jan/2011:19:18:46 -0700] [Job 19] ================================================
D [19/Jan/2011:19:18:46 -0700] [Job 19]
D [19/Jan/2011:19:18:46 -0700] [Job 19] File: <STDIN>
D [19/Jan/2011:19:18:46 -0700] [Job 19]
D [19/Jan/2011:19:18:46 -0700] [Job 19] ================================================
D [19/Jan/2011:19:18:46 -0700] [Job 19]
D [19/Jan/2011:19:18:46 -0700] [Job 19] Filetype: PDF
D [19/Jan/2011:19:18:46 -0700] [Job 19] Storing temporary files in /var/spool/cups/tmp
D [19/Jan/2011:19:18:46 -0700] PID 8630 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [19/Jan/2011:19:18:47 -0700] [Job 19] File contains 1 pages
D [19/Jan/2011:19:18:47 -0700] [Job 19] Starting renderer with command: gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=ijs -sIjsServer=hpijs -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -sDeviceManufacturer="HEWLETT-PACKARD" -sDeviceModel="deskjet 5600" -dDuplex=false -r300 -sIjsParams=Quality:Quality=0,Quality:ColorMode=2,Quality:MediaType=0,Quality:PenSet=2,PS:MediaPosition=7 -dIjsUseOutputFD -sOutputFile=-   /var/spool/cups/tmp/foomatic-BiEIxT
D [19/Jan/2011:19:18:47 -0700] [Job 19] Starting process "kid3" (generation 1)
D [19/Jan/2011:19:18:47 -0700] [Job 19] Starting process "kid4" (generation 2)
D [19/Jan/2011:19:18:47 -0700] [Job 19] Starting process "renderer" (generation 2)
D [19/Jan/2011:19:18:47 -0700] [Job 19] JCL: %-12345X@PJL
D [19/Jan/2011:19:18:47 -0700] [Job 19] <job data>
D [19/Jan/2011:19:18:47 -0700] [Job 19]
D [19/Jan/2011:19:18:47 -0700] cupsdAcceptClient: 13 from localhost (Domain)
D [19/Jan/2011:19:18:47 -0700] cupsdReadClient: 13 POST / HTTP/1.1
D [19/Jan/2011:19:18:47 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [19/Jan/2011:19:18:47 -0700] cupsdAuthorize: No authentication data provided.
D [19/Jan/2011:19:18:47 -0700] cupsdReadClient: 13 1.1 Get-Jobs 1
D [19/Jan/2011:19:18:47 -0700] Get-Jobs ipp://localhost/printers/
D [19/Jan/2011:19:18:47 -0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [19/Jan/2011:19:18:47 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [19/Jan/2011:19:18:47 -0700] cupsdReadClient: 13 WAITING Closing on EOF
D [19/Jan/2011:19:18:47 -0700] cupsdCloseClient: 13
D [19/Jan/2011:19:18:47 -0700] cupsdAcceptClient: 13 from localhost (Domain)
D [19/Jan/2011:19:18:47 -0700] cupsdReadClient: 13 POST / HTTP/1.1
D [19/Jan/2011:19:18:47 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [19/Jan/2011:19:18:47 -0700] cupsdAuthorize: No authentication data provided.
D [19/Jan/2011:19:18:47 -0700] cupsdReadClient: 13 1.1 Get-Notifications 1
D [19/Jan/2011:19:18:47 -0700] Get-Notifications /
D [19/Jan/2011:19:18:47 -0700] cupsdIsAuthorized: requesting-user-name="snelson"
D [19/Jan/2011:19:18:47 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [19/Jan/2011:19:18:47 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [19/Jan/2011:19:18:47 -0700] cupsdReadClient: 13 POST / HTTP/1.1
D [19/Jan/2011:19:18:47 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [19/Jan/2011:19:18:47 -0700] cupsdAuthorize: No authentication data provided.
D [19/Jan/2011:19:18:47 -0700] cupsdReadClient: 13 1.1 Get-Job-Attributes 1
D [19/Jan/2011:19:18:47 -0700] Get-Job-Attributes ipp://localhost/jobs/19
D [19/Jan/2011:19:18:47 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/19) from localhost
D [19/Jan/2011:19:18:47 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [19/Jan/2011:19:18:47 -0700] cupsdReadClient: 12 POST / HTTP/1.1
D [19/Jan/2011:19:18:47 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [19/Jan/2011:19:18:47 -0700] cupsdAuthorize: No authentication data provided.
D [19/Jan/2011:19:18:47 -0700] cupsdReadClient: 12 1.1 Get-Notifications 1
D [19/Jan/2011:19:18:47 -0700] Get-Notifications /
D [19/Jan/2011:19:18:47 -0700] cupsdIsAuthorized: requesting-user-name="snelson"
D [19/Jan/2011:19:18:47 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [19/Jan/2011:19:18:47 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [19/Jan/2011:19:18:47 -0700] [Job 19] GPL Ghostscript 8.71: Unrecoverable error, exit code 1
D [19/Jan/2011:19:18:47 -0700] [Job 19] renderer exited with status 1
D [19/Jan/2011:19:18:47 -0700] [Job 19] Possible error on renderer command line or PostScript error. Check options.Kid3 exit status: 3
D [19/Jan/2011:19:18:47 -0700] PID 8631 (/usr/lib/cups/filter/foomatic-rip) stopped with status 9!
D [19/Jan/2011:19:18:47 -0700] [Job 19] STATE: +connecting-to-device
D [19/Jan/2011:19:18:47 -0700] cupsdMarkDirty(-----S)
D [19/Jan/2011:19:18:47 -0700] cupsdReadClient: 13 WAITING Closing on EOF
D [19/Jan/2011:19:18:47 -0700] cupsdCloseClient: 13
D [19/Jan/2011:19:18:47 -0700] cupsdAcceptClient: 13 from localhost (Domain)
D [19/Jan/2011:19:18:47 -0700] cupsdReadClient: 13 POST / HTTP/1.1
D [19/Jan/2011:19:18:47 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [19/Jan/2011:19:18:47 -0700] cupsdAuthorize: No authentication data provided.
D [19/Jan/2011:19:18:47 -0700] cupsdReadClient: 13 1.1 Get-Jobs 1
D [19/Jan/2011:19:18:47 -0700] Get-Jobs ipp://localhost/printers/
D [19/Jan/2011:19:18:47 -0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [19/Jan/2011:19:18:47 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [19/Jan/2011:19:18:47 -0700] cupsdReadClient: 13 WAITING Closing on EOF
D [19/Jan/2011:19:18:47 -0700] cupsdCloseClient: 13
D [19/Jan/2011:19:18:47 -0700] cupsdAcceptClient: 13 from localhost (Domain)
D [19/Jan/2011:19:18:47 -0700] cupsdReadClient: 13 POST / HTTP/1.1
D [19/Jan/2011:19:18:47 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [19/Jan/2011:19:18:47 -0700] cupsdAuthorize: No authentication data provided.
D [19/Jan/2011:19:18:47 -0700] cupsdReadClient: 13 1.1 Get-Notifications 1
D [19/Jan/2011:19:18:47 -0700] Get-Notifications /
D [19/Jan/2011:19:18:47 -0700] cupsdIsAuthorized: requesting-user-name="snelson"
D [19/Jan/2011:19:18:47 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [19/Jan/2011:19:18:47 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [19/Jan/2011:19:18:47 -0700] cupsdReadClient: 13 WAITING Closing on EOF
D [19/Jan/2011:19:18:47 -0700] cupsdCloseClient: 13
D [19/Jan/2011:19:18:47 -0700] cupsdReadClient: 12 POST / HTTP/1.1
D [19/Jan/2011:19:18:47 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [19/Jan/2011:19:18:47 -0700] cupsdAuthorize: No authentication data provided.
D [19/Jan/2011:19:18:47 -0700] cupsdReadClient: 12 1.1 Get-Notifications 1
D [19/Jan/2011:19:18:47 -0700] Get-Notifications /
D [19/Jan/2011:19:18:47 -0700] cupsdIsAuthorized: requesting-user-name="snelson"
D [19/Jan/2011:19:18:47 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [19/Jan/2011:19:18:47 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [19/Jan/2011:19:18:48 -0700] [Job 19] STATE: -connecting-to-device
D [19/Jan/2011:19:18:48 -0700] cupsdMarkDirty(-----S)
D [19/Jan/2011:19:18:48 -0700] [Job 19] STATE: -media-empty-error,media-jam-error,hplip.plugin-error,cover-open-error,toner-empty-error,other
I [19/Jan/2011:19:18:48 -0700] [Job 19] ready to print
D [19/Jan/2011:19:18:48 -0700] cupsdMarkDirty(-----S)
D [19/Jan/2011:19:18:48 -0700] cupsdAcceptClient: 13 from localhost (Domain)
D [19/Jan/2011:19:18:48 -0700] cupsdReadClient: 13 POST / HTTP/1.1
D [19/Jan/2011:19:18:48 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [19/Jan/2011:19:18:48 -0700] cupsdAuthorize: No authentication data provided.
D [19/Jan/2011:19:18:48 -0700] cupsdReadClient: 13 1.1 Get-Jobs 1
D [19/Jan/2011:19:18:48 -0700] Get-Jobs ipp://localhost/printers/
D [19/Jan/2011:19:18:48 -0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [19/Jan/2011:19:18:48 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [19/Jan/2011:19:18:48 -0700] cupsdReadClient: 13 WAITING Closing on EOF
D [19/Jan/2011:19:18:48 -0700] cupsdCloseClient: 13
D [19/Jan/2011:19:18:48 -0700] cupsdAcceptClient: 13 from localhost (Domain)
D [19/Jan/2011:19:18:48 -0700] cupsdReadClient: 13 POST / HTTP/1.1
D [19/Jan/2011:19:18:48 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [19/Jan/2011:19:18:48 -0700] cupsdAuthorize: No authentication data provided.
D [19/Jan/2011:19:18:48 -0700] cupsdReadClient: 13 1.1 Get-Notifications 1
D [19/Jan/2011:19:18:48 -0700] Get-Notifications /
D [19/Jan/2011:19:18:48 -0700] cupsdIsAuthorized: requesting-user-name="snelson"
D [19/Jan/2011:19:18:48 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [19/Jan/2011:19:18:48 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [19/Jan/2011:19:18:48 -0700] cupsdReadClient: 12 POST / HTTP/1.1
D [19/Jan/2011:19:18:48 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [19/Jan/2011:19:18:48 -0700] cupsdAuthorize: No authentication data provided.
D [19/Jan/2011:19:18:48 -0700] cupsdReadClient: 12 1.1 Get-Notifications 1
D [19/Jan/2011:19:18:48 -0700] Get-Notifications /
D [19/Jan/2011:19:18:48 -0700] cupsdIsAuthorized: requesting-user-name="snelson"
D [19/Jan/2011:19:18:48 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [19/Jan/2011:19:18:48 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [19/Jan/2011:19:18:48 -0700] cupsdReadClient: 13 WAITING Closing on EOF
D [19/Jan/2011:19:18:48 -0700] cupsdCloseClient: 13
D [19/Jan/2011:19:18:49 -0700] PID 8632 (/usr/lib/cups/backend/hp) exited with no errors.
D [19/Jan/2011:19:18:49 -0700] cupsdMarkDirty(-----S)
E [19/Jan/2011:19:18:49 -0700] [Job 19] Job stopped due to filter errors; please consult the error_log file for details.
D [19/Jan/2011:19:18:49 -0700] cupsdMarkDirty(----J-)
D [19/Jan/2011:19:18:49 -0700] cupsdMarkDirty(-----S)
D [19/Jan/2011:19:18:49 -0700] cupsdAcceptClient: 13 from localhost (Domain)
D [19/Jan/2011:19:18:49 -0700] cupsdReadClient: 13 POST / HTTP/1.1
D [19/Jan/2011:19:18:49 -0700] cupsdSetBusyState: Active clients and dirty files
D [19/Jan/2011:19:18:49 -0700] cupsdAuthorize: No authentication data provided.
D [19/Jan/2011:19:18:49 -0700] cupsdReadClient: 13 1.1 Get-Jobs 1
D [19/Jan/2011:19:18:49 -0700] Get-Jobs ipp://localhost/printers/
D [19/Jan/2011:19:18:49 -0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [19/Jan/2011:19:18:49 -0700] cupsdSetBusyState: Dirty files
D [19/Jan/2011:19:18:49 -0700] cupsdReadClient: 13 WAITING Closing on EOF
D [19/Jan/2011:19:18:49 -0700] cupsdCloseClient: 13
D [19/Jan/2011:19:18:49 -0700] cupsdAcceptClient: 13 from localhost (Domain)
D [19/Jan/2011:19:18:49 -0700] cupsdReadClient: 13 POST / HTTP/1.1
D [19/Jan/2011:19:18:49 -0700] cupsdSetBusyState: Active clients and dirty files
D [19/Jan/2011:19:18:49 -0700] cupsdAuthorize: No authentication data provided.
D [19/Jan/2011:19:18:49 -0700] cupsdReadClient: 13 1.1 Get-Notifications 1
D [19/Jan/2011:19:18:49 -0700] Get-Notifications /
D [19/Jan/2011:19:18:49 -0700] cupsdIsAuthorized: requesting-user-name="snelson"
D [19/Jan/2011:19:18:49 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [19/Jan/2011:19:18:49 -0700] cupsdSetBusyState: Dirty files
D [19/Jan/2011:19:18:49 -0700] cupsdAcceptClient: 15 from localhost (Domain)
D [19/Jan/2011:19:18:49 -0700] cupsdReadClient: 15 POST / HTTP/1.1
D [19/Jan/2011:19:18:49 -0700] cupsdSetBusyState: Active clients and dirty files
D [19/Jan/2011:19:18:49 -0700] cupsdAuthorize: No authentication data provided.
D [19/Jan/2011:19:18:49 -0700] cupsdReadClient: 15 1.1 Get-Printer-Attributes 1
D [19/Jan/2011:19:18:49 -0700] Get-Printer-Attributes ipp://Shons:0/printers/HP-Photosmart-C5100-series
D [19/Jan/2011:19:18:49 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://Shons:0/printers/HP-Photosmart-C5100-series) from localhost
D [19/Jan/2011:19:18:49 -0700] cupsdSetBusyState: Dirty files
D [19/Jan/2011:19:18:49 -0700] cupsdReadClient: 15 POST / HTTP/1.1
D [19/Jan/2011:19:18:49 -0700] cupsdSetBusyState: Active clients and dirty files
D [19/Jan/2011:19:18:49 -0700] cupsdAuthorize: No authentication data provided.
D [19/Jan/2011:19:18:49 -0700] cupsdReadClient: 15 1.1 Get-Job-Attributes 1
D [19/Jan/2011:19:18:49 -0700] Get-Job-Attributes ipp://localhost/jobs/19
D [19/Jan/2011:19:18:49 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/19) from localhost
D [19/Jan/2011:19:18:49 -0700] cupsdSetBusyState: Dirty files
D [19/Jan/2011:19:18:49 -0700] cupsdReadClient: 12 POST / HTTP/1.1
D [19/Jan/2011:19:18:49 -0700] cupsdSetBusyState: Active clients and dirty files
D [19/Jan/2011:19:18:49 -0700] cupsdAuthorize: No authentication data provided.
D [19/Jan/2011:19:18:49 -0700] cupsdReadClient: 12 1.1 Get-Notifications 1
D [19/Jan/2011:19:18:49 -0700] Get-Notifications /
D [19/Jan/2011:19:18:49 -0700] cupsdIsAuthorized: requesting-user-name="snelson"
D [19/Jan/2011:19:18:49 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [19/Jan/2011:19:18:49 -0700] cupsdSetBusyState: Dirty files
D [19/Jan/2011:19:18:49 -0700] cupsdReadClient: 13 WAITING Closing on EOF
D [19/Jan/2011:19:18:49 -0700] cupsdCloseClient: 13
D [19/Jan/2011:19:18:50 -0700] [Job 19] Unloading...
D [19/Jan/2011:19:18:53 -0700] cupsdReadClient: 12 POST / HTTP/1.1
D [19/Jan/2011:19:18:53 -0700] cupsdSetBusyState: Active clients and dirty files
D [19/Jan/2011:19:18:53 -0700] cupsdAuthorize: No authentication data provided.
D [19/Jan/2011:19:18:53 -0700] cupsdReadClient: 12 1.1 Get-Job-Attributes 1
D [19/Jan/2011:19:18:53 -0700] Get-Job-Attributes ipp://localhost/jobs/19
D [19/Jan/2011:19:18:53 -0700] [Job 19] Loading attributes...
D [19/Jan/2011:19:18:53 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/19) from localhost
D [19/Jan/2011:19:18:53 -0700] cupsdSetBusyState: Dirty files
D [19/Jan/2011:19:18:53 -0700] cupsdReadClient: 12 POST / HTTP/1.1
D [19/Jan/2011:19:18:53 -0700] cupsdSetBusyState: Active clients and dirty files
D [19/Jan/2011:19:18:53 -0700] cupsdAuthorize: No authentication data provided.
D [19/Jan/2011:19:18:53 -0700] cupsdReadClient: 12 1.1 Cancel-Subscription 1
D [19/Jan/2011:19:18:53 -0700] Cancel-Subscription /
D [19/Jan/2011:19:18:53 -0700] cupsdIsAuthorized: requesting-user-name="snelson"
D [19/Jan/2011:19:18:53 -0700] cupsdMarkDirty(-----S)
D [19/Jan/2011:19:18:53 -0700] Returning IPP successful-ok for Cancel-Subscription (/) from localhost
D [19/Jan/2011:19:18:53 -0700] cupsdSetBusyState: Dirty files
D [19/Jan/2011:19:18:53 -0700] cupsdReadClient: 12 GET /admin/conf/cupsd.conf HTTP/1.1
D [19/Jan/2011:19:18:53 -0700] cupsdSetBusyState: Active clients and dirty files
D [19/Jan/2011:19:18:53 -0700] cupsdAuthorize: No authentication data provided.
D [19/Jan/2011:19:18:53 -0700] cupsdIsAuthorized: username=""
D [19/Jan/2011:19:18:53 -0700] cupsdSendHeader: 12 WWW-Authenticate: Basic realm="CUPS", trc="y"
D [19/Jan/2011:19:18:53 -0700] cupsdCloseClient: 12
D [19/Jan/2011:19:18:53 -0700] cupsdSetBusyState: Dirty files
D [19/Jan/2011:19:18:53 -0700] cupsdAcceptClient: 12 from localhost (Domain)
D [19/Jan/2011:19:18:53 -0700] cupsdReadClient: 12 GET /admin/conf/cupsd.conf HTTP/1.1
D [19/Jan/2011:19:18:53 -0700] cupsdSetBusyState: Active clients and dirty files
D [19/Jan/2011:19:18:53 -0700] cupsdAuthorize: Authorized as snelson using PeerCred
D [19/Jan/2011:19:18:53 -0700] cupsdIsAuthorized: username="snelson"
D [19/Jan/2011:19:18:53 -0700] cupsdSetBusyState: Dirty files
D [19/Jan/2011:19:18:53 -0700] cupsdReadClient: 12 GET /admin/conf/cupsd.conf HTTP/1.1
D [19/Jan/2011:19:18:53 -0700] cupsdSetBusyState: Active clients and dirty files
D [19/Jan/2011:19:18:53 -0700] cupsdAuthorize: Authorized as snelson using PeerCred
D [19/Jan/2011:19:18:53 -0700] cupsdIsAuthorized: username="snelson"
D [19/Jan/2011:19:18:53 -0700] cupsdSetBusyState: Dirty files
D [19/Jan/2011:19:18:53 -0700] cupsdReadClient: 12 GET /admin/conf/cupsd.conf HTTP/1.1
D [19/Jan/2011:19:18:53 -0700] cupsdSetBusyState: Active clients and dirty files
D [19/Jan/2011:19:18:53 -0700] cupsdAuthorize: Authorized as snelson using PeerCred
D [19/Jan/2011:19:18:53 -0700] cupsdIsAuthorized: username="snelson"
D [19/Jan/2011:19:18:53 -0700] cupsdSetBusyState: Dirty files
D [19/Jan/2011:19:18:53 -0700] cupsdReadClient: 12 PUT /admin/conf/cupsd.conf HTTP/1.1
D [19/Jan/2011:19:18:53 -0700] cupsdSetBusyState: Active clients and dirty files
D [19/Jan/2011:19:18:53 -0700] cupsdAuthorize: Authorized as snelson using PeerCred
D [19/Jan/2011:19:18:53 -0700] cupsdIsAuthorized: username="snelson"
I [19/Jan/2011:19:18:53 -0700] Installing config file "/etc/cups/cupsd.conf"...
D [19/Jan/2011:19:18:53 -0700] cupsdSetBusyState: Dirty files
D [19/Jan/2011:19:18:53 -0700] cupsdCloseClient: 15
D [19/Jan/2011:19:18:53 -0700] cupsdCloseClient: 12
I [19/Jan/2011:19:18:53 -0700] Saving job cache file "/var/cache/cups/job.cache"...
I [19/Jan/2011:19:18:53 -0700] Saving subscriptions.conf...
D [19/Jan/2011:19:18:53 -0700] cupsdSetBusyState: Not busy
```

Anyone have any ideas as to how I can fix this?

---

### Post by IcarusR on 2011-01-20
> D [19/Jan/2011:19:18:47 -0700] [Job 19] GPL Ghostscript 8.71: Unrecoverable error, exit code 1
D [19/Jan/2011:19:18:47 -0700] [Job 19] renderer exited with status 1
D [19/Jan/2011:19:18:47 -0700] [Job 19] Possible error on renderer command line or PostScript error. Check options.Kid3 exit status: 3
D [19/Jan/2011:19:18:47 -0700] PID 8631 (/usr/lib/cups/filter/foomatic-rip) stopped with status 9!

It looks like a ghostscript error & from googling it is fairly common.

I suggest you install a later version of ghostscript. Possibly give this one a go, as it is a .deb it will be easy enough to try.

[http://packages.debian.org/sid/ghostscript]("http://packages.debian.org/sid/ghostscript")

---

### Post by belkira on 2011-01-20
The deb files you pointed me to are older than what I currently have. I have tried to install v9 from source, but it installs in /usr/local/bin instead of /usr/bin so the readers are not seeing it.

Is there an easy way to fix this?

---

### Post by IcarusR on 2011-01-20
> The deb files you pointed me to are older than what I currently have.

Sorry getting confused !

From the install doc in the source package. 

> You can set the installation directory by adding --prefix=path to the configure invocation in the first step.

So if you run configure like this it should install to/usr/bin.

```
configure --prefix=path/usr
```

Alternatively you could create a sym link in usr/local/bin pointing to /usr/bin

---

### Post by IcarusR on 2011-01-20
> The deb files you pointed me to are older than what I currently have.

Sorry getting confused !

From the install doc in the source package. 

> You can set the installation directory by adding --prefix=path to the configure invocation in the first step.

So if you run configure like this it should install to/usr/bin.

```
configure --prefix=path/usr
```

Alternatively you could create a sym link in usr/local/bin pointing to /usr/bin

---

### Post by belkira on 2011-01-20
So I got version 9 of ghostscript installed, and it broke all printing. Back to the version I had. I can print again, but still not able to print pdf

---

### Post by belkira on 2011-01-20
> **IcarusR said:**
> Sorry getting confused !

From the install doc in the source package. 



So if you run configure like this it should install to/usr/bin.

```
configure --prefix=path/usr
```

Alternatively you could create a sym link in usr/local/bin pointing to /usr/bin

Sadly, the source no longer uses a config file, you just make it

---

### Post by belkira on 2011-01-20
Well I just downloaded a pdf file from the IRS website and it was able to be printed just fine. Looking into the pdf files I am having trouble with, it appears they were all made by a web app called mPDF.

Now I guess its time to see what it does that is messing things up.

Thanks for the help!

---

### Post by IcarusR on 2011-01-21
> Sadly, the source no longer uses a config file, you just make it

Strange , as I've just compiled v9 source with the following commands

```
./configure 
```
```
make
```

without any errors !

As stated in previous post the install.hmtl file in the doc subdirectory of the source says 

> Installing Ghostscript on Unix

Ghostscript uses the common configure, build and install method common to many modern software packages. In general the following with suffice to build ghostscript:

    ./configure
    make 

and then it may be installed in the default location with:

    make install 

This last command may need to be performed with super user privileges.

You can set the installation directory by adding --prefix=path to the configure invocation in the first step. The default prefix is /usr/local, which is to say the gs executable is installed as /usr/local/bin/gs.
A list of similar configuration options is available via ./configure --help

Your install will not work without running configure.

I suggest you try it.

---

### Post by belkira on 2011-01-21
Can you link to the source files? Apparently the one I keep getting is the pcl xps and not the actual gs.

Thanks

Edit: NM found it on sourceforge. I will build and see if it helps.

---

### Post by pterosky on 2011-07-03
I was facing the same problem. I got blank pages and an error message when I tried to print a PDF file. I tried to print it from the command line, as described [here]("http://www.linuxquestions.org/questions/linux-desktop-74/unable-to-print-pdf-files-ubuntu-10-10-a-857541/"), which worked fine.

I noticed that there was a question mark, and a line break in the file name when I "ls"-ed the files on my Desktop. After I renamed it to something simple, I could print it from the PDF reader. So try to rename your files, before trying all the other stuff 8o)

---

