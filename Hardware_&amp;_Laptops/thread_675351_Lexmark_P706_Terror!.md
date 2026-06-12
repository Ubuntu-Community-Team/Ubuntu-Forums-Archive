---
title: "Lexmark P706 Terror!"
date: 2008-01-22
forum: Hardware &amp; Laptops
---

### Post by hatkirby on 2008-01-22
I know that there is another topic about this, but it's in the mailing list and says (CLOSED) next to it.

I have a Lexmark P706 that I used to use to print things with Windows. But now, with Ubuntu, I cannot find a driver for it anywhere! The P700 Series CD only has documentation on it, and the Z700 Series CD is in some strange Windows extract format! I cannot find the RPM the other person is talking about in the other topic as well, so, if anyone can help, please!

**EDIT:** Forgot, I have Ubuntu Gutsy (7.10) Desktop Edition.

**ANOTHER EDIT:** And the CUPS Z700-P700 driver doesn't work because it sends a job to the spool, and the job immediately get the "Stopped" status.

---

### Post by hatkirby on 2008-01-22
Here's the error log if anyone's interested:```
D [23/Jan/2008:09:45:54 +1100] [Job 16] width = 4725, height = 6675
D [23/Jan/2008:09:45:54 +1100] [Job 16] PageSize = [ 595 842 ], HWResolution = [ 600 600 ]
D [23/Jan/2008:09:45:54 +1100] [Job 16] HWMargins = [ 18.000 36.000 10.000 5.000 ]
D [23/Jan/2008:09:45:54 +1100] [Job 16] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6975.000 ]
D [23/Jan/2008:09:45:54 +1100] [Job 16] GPL Ghostscript SVN PRE-RELEASE 8.61: DEBUG2: cups_get_matrix(0x809e374, 0x836e884)
D [23/Jan/2008:09:45:54 +1100] [Job 16] cups->header.Duplex = 0
D [23/Jan/2008:09:45:54 +1100] [Job 16] cups->page = 1
D [23/Jan/2008:09:45:54 +1100] [Job 16] cupsPPD = 0x8190fc0
D [23/Jan/2008:09:45:54 +1100] [Job 16] cupsPPD->flip_duplex = 0
*****************(the previous 9 lines repeat themselves ALOT of times)*********************
D [23/Jan/2008:09:45:54 +1100] [Job 16] width = 4725, height = 6675
D [23/Jan/2008:09:45:54 +1100] [Job 16] PageSize = [ 595 842 ], HWResolution = [ 600 600 ]
D [23/Jan/2008:09:45:54 +1100] [Job 16] HWMargins = [ 18.000 36.000 10.000 5.000 ]
D [23/Jan/2008:09:45:54 +1100] [Job 16] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6975.000 ]
D [23/Jan/2008:09:45:54 +1100] [Job 16] GPL Ghostscript SVN PRE-RELEASE 8.61: DEBUG: cups->header.Duplex = 0
D [23/Jan/2008:09:45:54 +1100] [Job 16] 8.61: DEBUG2: cups_close(0x809e374)
D [23/Jan/2008:09:45:54 +1100] PID 13016 (/usr/lib/cups/filter/pstoraster) exited with no errors.
D [23/Jan/2008:09:45:54 +1100] [Job 16] File 0 is complete.
E [23/Jan/2008:09:45:54 +1100] [Job 16] Job stopped due to filter errors.
D [23/Jan/2008:09:45:54 +1100] Discarding unused printer-state-changed event...
D [23/Jan/2008:09:45:54 +1100] Discarding unused job-stopped event...
D [23/Jan/2008:09:45:55 +1100] [Job 16] Unloading...
D [23/Jan/2008:09:45:55 +1100] cupsdReadClient: 20 GET /printers/Lexmark_Z700-P700_Series HTTP/1.1
D [23/Jan/2008:09:45:55 +1100] cupsdAuthorize: Authorized as hatkirby using Basic
D [23/Jan/2008:09:45:55 +1100] [CGI] /usr/lib/cups/cgi-bin/printers.cgi started - PID = 13020
I [23/Jan/2008:09:45:55 +1100] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=13020)
D [23/Jan/2008:09:45:55 +1100] cupsdSendCommand: 20 file=4
D [23/Jan/2008:09:45:55 +1100] cupsdAcceptClient: 21 from localhost (Domain)
D [23/Jan/2008:09:45:55 +1100] cupsdReadClient: 21 POST / HTTP/1.1
D [23/Jan/2008:09:45:55 +1100] cupsdAuthorize: No authentication data provided.
D [23/Jan/2008:09:45:55 +1100] CUPS-Get-Default
D [23/Jan/2008:09:45:55 +1100] CUPS-Get-Default client-error-not-found: No default printer
D [23/Jan/2008:09:45:55 +1100] cupsdProcessIPPRequest: 21 status_code=406 (client-error-not-found)
D [23/Jan/2008:09:45:55 +1100] [CGI] show_printer(http=0x80761d0, printer="Lexmark_Z700-P700_Series")
D [23/Jan/2008:09:45:55 +1100] cupsdReadClient: 21 POST / HTTP/1.1
D [23/Jan/2008:09:45:55 +1100] cupsdAuthorize: No authentication data provided.
D [23/Jan/2008:09:45:55 +1100] Get-Printer-Attributes ipp://localhost/printers/Lexmark_Z700-P700_Series
D [23/Jan/2008:09:45:55 +1100] cupsdProcessIPPRequest: 21 status_code=0 (successful-ok)
D [23/Jan/2008:09:45:55 +1100] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [23/Jan/2008:09:45:55 +1100] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [23/Jan/2008:09:45:55 +1100] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [23/Jan/2008:09:45:55 +1100] cupsdReadClient: 21 POST / HTTP/1.1
D [23/Jan/2008:09:45:55 +1100] cupsdAuthorize: No authentication data provided.
D [23/Jan/2008:09:45:55 +1100] Get-Jobs ipp://localhost:631/printers/Lexmark_Z700-P700_Series
D [23/Jan/2008:09:45:55 +1100] [Job 16] Loading attributes...
D [23/Jan/2008:09:45:55 +1100] cupsdProcessIPPRequest: 21 status_code=0 (successful-ok)
D [23/Jan/2008:09:45:55 +1100] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [23/Jan/2008:09:45:55 +1100] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [23/Jan/2008:09:45:55 +1100] cupsdCloseClient: 21
D [23/Jan/2008:09:45:55 +1100] PID 13020 (/usr/lib/cups/cgi-bin/printers.cgi) exited with no errors.
D [23/Jan/2008:09:45:55 +1100] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [23/Jan/2008:09:45:55 +1100] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [23/Jan/2008:09:45:55 +1100] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [23/Jan/2008:09:45:55 +1100] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [23/Jan/2008:09:46:05 +1100] cupsdReadClient: 20 GET /admin HTTP/1.1
D [23/Jan/2008:09:46:05 +1100] cupsdAuthorize: Authorized as hatkirby using Basic
D [23/Jan/2008:09:46:05 +1100] [CGI] /usr/lib/cups/cgi-bin/admin.cgi started - PID = 13021
I [23/Jan/2008:09:46:05 +1100] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=13021)
D [23/Jan/2008:09:46:05 +1100] cupsdSendCommand: 20 file=4
D [23/Jan/2008:09:46:05 +1100] [CGI] admin.cgi started...
D [23/Jan/2008:09:46:05 +1100] cupsdAcceptClient: 21 from localhost (Domain)
D [23/Jan/2008:09:46:05 +1100] [CGI] http=0x80790d0
D [23/Jan/2008:09:46:05 +1100] [CGI] No form data, showing main menu...
D [23/Jan/2008:09:46:05 +1100] [CGI] /usr/share/cups/drivers/pscript5.dll: No such file or directory
D [23/Jan/2008:09:46:05 +1100] cupsdReadClient: 21 POST / HTTP/1.1
D [23/Jan/2008:09:46:05 +1100] cupsdAuthorize: No authentication data provided.
D [23/Jan/2008:09:46:05 +1100] Get-Subscriptions ipp://localhost/
D [23/Jan/2008:09:46:05 +1100] Get-Subscriptions client-error-not-found: No subscriptions found.
D [23/Jan/2008:09:46:05 +1100] cupsdProcessIPPRequest: 21 status_code=406 (client-error-not-found)
D [23/Jan/2008:09:46:05 +1100] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [23/Jan/2008:09:46:05 +1100] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [23/Jan/2008:09:46:05 +1100] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [23/Jan/2008:09:46:05 +1100] cupsdCloseClient: 21
D [23/Jan/2008:09:46:05 +1100] PID 13021 (/usr/lib/cups/cgi-bin/admin.cgi) exited with no errors.
D [23/Jan/2008:09:46:08 +1100] cupsdReadClient: 20 GET /admin/log/error_log HTTP/1.1
D [23/Jan/2008:09:46:08 +1100] cupsdAuthorize: Authorized as hatkirby using Basic
D [23/Jan/2008:09:46:18 +1100] cupsdReadClient: 20 GET /admin/log/error_log HTTP/1.1
D [23/Jan/2008:09:46:18 +1100] cupsdAuthorize: Authorized as hatkirby using Basic
D [23/Jan/2008:09:46:26 +1100] [Job 12] Unloading...
D [23/Jan/2008:09:46:26 +1100] [Job 14] Unloading...
D [23/Jan/2008:09:46:26 +1100] [Job 15] Unloading...
D [23/Jan/2008:09:46:57 +1100] [Job 16] Unloading...
D [23/Jan/2008:09:46:57 +1100] cupsdNetIFUpdate: "lo" = localhost...
D [23/Jan/2008:09:46:57 +1100] cupsdNetIFUpdate: "eth1" = 10.0.0.5...
D [23/Jan/2008:09:46:57 +1100] cupsdNetIFUpdate: "lo" = localhost...
D [23/Jan/2008:09:46:57 +1100] cupsdNetIFUpdate: "eth1" = fe80::213:2ff:fe9f:638e%eth1...
D [23/Jan/2008:09:47:30 +1100] cupsdCloseClient: 20
D [23/Jan/2008:09:47:35 +1100] cupsdAcceptClient: 4 from localhost:631 (IPv4)
D [23/Jan/2008:09:47:35 +1100] cupsdReadClient: 4 GET /admin/log/access_log HTTP/1.1
D [23/Jan/2008:09:47:35 +1100] cupsdAuthorize: Authorized as hatkirby using Basic
D [23/Jan/2008:09:47:42 +1100] cupsdReadClient: 4 GET /admin/log/page_log HTTP/1.1
D [23/Jan/2008:09:47:42 +1100] cupsdAuthorize: Authorized as hatkirby using Basic
D [23/Jan/2008:09:47:42 +1100] cupsdSendError: 4 code=404 (Not Found)
D [23/Jan/2008:09:47:42 +1100] cupsdCloseClient: 4
D [23/Jan/2008:09:47:45 +1100] cupsdAcceptClient: 4 from localhost:631 (IPv4)
D [23/Jan/2008:09:47:45 +1100] cupsdReadClient: 4 GET /admin?op=config-server HTTP/1.1
D [23/Jan/2008:09:47:45 +1100] cupsdAuthorize: Authorized as hatkirby using Basic
D [23/Jan/2008:09:47:45 +1100] [CGI] /usr/lib/cups/cgi-bin/admin.cgi started - PID = 13024
I [23/Jan/2008:09:47:45 +1100] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=13024)
D [23/Jan/2008:09:47:45 +1100] cupsdSendCommand: 4 file=20
D [23/Jan/2008:09:47:45 +1100] [CGI] admin.cgi started...
D [23/Jan/2008:09:47:45 +1100] cupsdAcceptClient: 21 from localhost (Domain)
D [23/Jan/2008:09:47:45 +1100] [CGI] http=0x80790d0
D [23/Jan/2008:09:47:45 +1100] [CGI] op="config-server"...
D [23/Jan/2008:09:47:45 +1100] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [23/Jan/2008:09:47:45 +1100] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [23/Jan/2008:09:47:45 +1100] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [23/Jan/2008:09:47:45 +1100] cupsdCloseClient: 21
D [23/Jan/2008:09:47:45 +1100] PID 13024 (/usr/lib/cups/cgi-bin/admin.cgi) exited with no errors.
D [23/Jan/2008:09:47:45 +1100] cupsdReadClient: 4 GET /images/button-save-changes.gif HTTP/1.1
D [23/Jan/2008:09:47:45 +1100] cupsdAuthorize: Authorized as hatkirby using Basic
D [23/Jan/2008:09:47:45 +1100] cupsdAcceptClient: 21 from localhost:631 (IPv4)
D [23/Jan/2008:09:47:45 +1100] cupsdReadClient: 21 GET /images/button-use-default-config.gif HTTP/1.1
D [23/Jan/2008:09:47:45 +1100] cupsdAuthorize: Authorized as hatkirby using Basic
D [23/Jan/2008:09:47:56 +1100] cupsdReadClient: 4 GET /admin/log/error_log HTTP/1.1
D [23/Jan/2008:09:47:56 +1100] cupsdAuthorize: Authorized as hatkirby using Basic

```

---

### Post by squeakyfrommage on 2008-04-29
Did you ever get the printer working?

---

### Post by hatkirby on 2008-04-29
Nope, I was forced to discard the printer, and I am going to purchase a Linux-compatible printer-scanner. Anyone know of a good one?

---

