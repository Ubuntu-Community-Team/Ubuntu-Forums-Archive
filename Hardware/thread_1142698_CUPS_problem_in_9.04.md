---
title: "CUPS problem in 9.04"
date: 2009-04-29
forum: Hardware
---

### Post by gewitty on 2009-04-29
Just installed 9.04 and more or less everything works. However, when I tried to install my Canon iP4300 printer, which was working fine in 8.10, I find that CUPS freezes.

I also tried using Turboprint, which has always worked well for me in the past, but the same thing happens. As soon as I press the 'Add Printer' button, Turboprint locks up.

It looks like a problem in the CUPS system, but I can't figure out what is wrong. The error log appear to show an authorisation problem:

E [29/Apr/2009:15:21:24 +0100] CUPS-Add-Modify-Printer: Unauthorized
E [29/Apr/2009:15:25:29 +0100] PID 17703 (/usr/lib/cups/cgi-bin/admin.cgi) crashed on signal 9!
E [29/Apr/2009:15:25:54 +0100] Cancel-Job: Unauthorized
E [29/Apr/2009:15:31:01 +0100] Cancel-Job: Unauthorized
E [29/Apr/2009:15:31:46 +0100] Pause-Printer: Unauthorized
E [29/Apr/2009:15:31:46 +0100] Pause-Printer: Unauthorized
E [29/Apr/2009:15:31:55 +0100] CUPS-Add-Modify-Printer: Unauthorized
E [29/Apr/2009:15:32:40 +0100] CUPS-Delete-Printer: Unauthorized
E [29/Apr/2009:15:32:40 +0100] CUPS-Delete-Printer: Unauthorized
E [29/Apr/2009:15:32:59 +0100] PID 5944 (/usr/lib/cups/cgi-bin/admin.cgi) crashed on signal 9!

... as does the Access Log:

localhost - - [29/Apr/2009:15:51:45 +0100] "POST / HTTP/1.1" 200 411 CUPS-Get-Printers client-error-not-found
localhost - - [29/Apr/2009:15:51:45 +0100] "POST / HTTP/1.1" 200 409 CUPS-Get-Printers client-error-not-found
localhost - - [29/Apr/2009:15:51:45 +0100] "POST / HTTP/1.1" 200 411 CUPS-Get-Printers client-error-not-found
localhost - - [29/Apr/2009:15:51:45 +0100] "POST / HTTP/1.1" 200 177 CUPS-Get-Printers client-error-not-found
localhost - - [29/Apr/2009:15:51:45 +0100] "POST / HTTP/1.1" 200 411 CUPS-Get-Printers client-error-not-found
localhost - - [29/Apr/2009:15:51:45 +0100] "POST / HTTP/1.1" 200 409 CUPS-Get-Printers client-error-not-found
localhost - - [29/Apr/2009:15:51:45 +0100] "POST / HTTP/1.1" 200 411 CUPS-Get-Printers client-error-not-found
localhost - - [29/Apr/2009:15:51:45 +0100] "POST / HTTP/1.1" 200 177 CUPS-Get-Printers client-error-not-found
localhost - dave [29/Apr/2009:15:51:58 +0100] "GET /admin HTTP/1.1" 200 0 - -
localhost - - [29/Apr/2009:15:51:58 +0100] "POST / HTTP/1.1" 200 107 Get-Subscriptions client-error-not-found
localhost - dave [29/Apr/2009:15:51:58 +0100] "GET /admin HTTP/1.1" 200 6007 - -
localhost - dave [29/Apr/2009:15:52:06 +0100] "GET /admin/log/error_log HTTP/1.1" 200 689 - -
localhost - dave [29/Apr/2009:15:52:44 +0100] "GET /admin/log/access_log HTTP/1.1" 200 67534 - -
localhost - - [29/Apr/2009:15:50:30 +0100] "POST / HTTP/1.1" 200 1746 CUPS-Get-Devices -
localhost - - [29/Apr/2009:15:50:51 +0100] "POST / HTTP/1.1" 200 1746 CUPS-Get-Devices -
localhost - dave [29/Apr/2009:15:53:52 +0100] "GET /admin/log/page_log HTTP/1.1" 200 294 - -
localhost - dave [29/Apr/2009:15:54:10 +0100] "GET /printers/ HTTP/1.1" 200 0 - -
localhost - - [29/Apr/2009:15:54:10 +0100] "POST / HTTP/1.1" 200 138 CUPS-Get-Default client-error-not-found
localhost - - [29/Apr/2009:15:54:10 +0100] "POST / HTTP/1.1" 200 552 CUPS-Get-Printers client-error-not-found
localhost - dave [29/Apr/2009:15:54:10 +0100] "GET /printers/ HTTP/1.1" 200 3591 - -
localhost - - [29/Apr/2009:15:58:01 +0100] "POST / HTTP/1.1" 200 2278416 CUPS-Get-PPDs -
localhost - - [29/Apr/2009:15:58:03 +0100] "POST / HTTP/1.1" 200 2278416 CUPS-Get-PPDs -
localhost - - [29/Apr/2009:15:58:05 +0100] "POST / HTTP/1.1" 200 2278416 CUPS-Get-PPDs -
localhost - - [29/Apr/2009:15:58:30 +0100] "POST / HTTP/1.1" 200 416 CUPS-Get-Printers client-error-not-found
localhost - - [29/Apr/2009:15:58:30 +0100] "POST / HTTP/1.1" 200 112 CUPS-Get-Default client-error-not-found
localhost - - [29/Apr/2009:15:58:30 +0100] "POST /printers/ HTTP/1.1" 200 204 CUPS-Get-Printers client-error-not-found
localhost - - [29/Apr/2009:15:59:46 +0100] "POST / HTTP/1.1" 200 411 CUPS-Get-Printers client-error-not-found
localhost - - [29/Apr/2009:15:59:46 +0100] "POST / HTTP/1.1" 200 409 CUPS-Get-Printers client-error-not-found
localhost - - [29/Apr/2009:15:59:46 +0100] "POST / HTTP/1.1" 200 411 CUPS-Get-Printers client-error-not-found
localhost - - [29/Apr/2009:15:59:46 +0100] "POST / HTTP/1.1" 200 177 CUPS-Get-Printers client-error-not-found
localhost - - [29/Apr/2009:15:58:32 +0100] "POST / HTTP/1.1" 200 1746 CUPS-Get-Devices -
localhost - dave [29/Apr/2009:16:02:49 +0100] "GET /admin/ HTTP/1.1" 200 0 - -
localhost - - [29/Apr/2009:16:02:49 +0100] "POST / HTTP/1.1" 200 107 Get-Subscriptions client-error-not-found
localhost - dave [29/Apr/2009:16:02:49 +0100] "GET /admin/ HTTP/1.1" 200 6007 - -
localhost - dave [29/Apr/2009:16:02:52 +0100] "GET /admin/log/error_log HTTP/1.1" 304 0 - -
localhost - dave [29/Apr/2009:16:07:47 +0100] "GET /admin/log/page_log HTTP/1.1" 304 0 - -


Does this give any clue as to what's wrong?

---

