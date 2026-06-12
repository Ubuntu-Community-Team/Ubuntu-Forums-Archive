---
title: "canon printer problem in 9.04"
date: 2009-05-30
forum: Hardware
---

### Post by vbdanl on 2009-05-30
hi.  my canon mp160 printer works fine in 8.04, but not in 9.04.  i installed the same drivers.  it says it is printing and completed, but nothing actually gets printed.  i have installed and deleted and reinstalled the printer multiple times - nothing has worked.
i get this in the /var/log/cups/error_log file:
E [30/May/2009:11:04:26 -0500] CUPS-Add-Modify-Printer: Unauthorized
:/var/log/cups$

the access_log has this:
localhost - - [30/May/2009:11:06:42 -0500] "POST / HTTP/1.1" 200 406 CUPS-Get-Printers successful-ok
localhost - - [30/May/2009:11:06:42 -0500] "GET /ppd/MP160.ppd HTTP/1.1" 200 11038 - -
localhost - - [30/May/2009:11:06:44 -0500] "POST / HTTP/1.1" 200 406 CUPS-Get-Printers successful-ok
localhost - - [30/May/2009:11:06:48 -0500] "POST / HTTP/1.1" 200 406 CUPS-Get-Printers successful-ok
localhost - - [30/May/2009:11:06:50 -0500] "POST / HTTP/1.1" 200 406 CUPS-Get-Printers successful-ok
localhost - - [30/May/2009:11:06:53 -0500] "POST / HTTP/1.1" 200 406 CUPS-Get-Printers successful-ok
localhost - - [30/May/2009:11:06:56 -0500] "POST /printers/MP160 HTTP/1.1" 200 15630 Print-Job successful-ok
localhost - - [30/May/2009:11:06:56 -0500] "POST / HTTP/1.1" 200 199 Get-Jobs successful-ok
localhost - - [30/May/2009:11:06:57 -0500] "POST / HTTP/1.1" 200 323 Create-Printer-Subscription successful-ok
localhost - - [30/May/2009:11:06:57 -0500] "POST / HTTP/1.1" 200 327 CUPS-Get-Printers successful-ok
localhost - - [30/May/2009:11:06:57 -0500] "POST / HTTP/1.1" 200 327 CUPS-Get-Printers successful-ok
localhost - - [30/May/2009:11:06:57 -0500] "POST / HTTP/1.1" 200 220 Get-Jobs successful-ok
localhost - - [30/May/2009:11:06:57 -0500] "POST / HTTP/1.1" 200 206 Get-Printer-Attributes successful-ok
localhost - - [30/May/2009:11:06:57 -0500] "POST / HTTP/1.1" 200 220 Get-Jobs successful-ok
localhost - - [30/May/2009:11:06:58 -0500] "POST / HTTP/1.1" 200 152 Get-Notifications successful-ok
localhost - - [30/May/2009:11:06:59 -0500] "POST / HTTP/1.1" 200 199 Get-Jobs successful-ok
localhost - - [30/May/2009:11:06:59 -0500] "POST / HTTP/1.1" 200 152 Get-Notifications successful-ok
:/var/log/cups$ 

any ideas on what i should try ?
thanks for your help..

---

### Post by vbdanl on 2009-05-30
well, after some trial and error, the printer works from some apps, but not all..  i have been able to print using gedit, OO word and calc, and adobe pdf reader.  i have not been able to print with abiword, and have tried 3 or 4 times:
this error is in the cups error_log: E [30/May/2009:13:39:41 -0500] PID 5391 (/usr/lib/cups/filter/pstocanonij) crashed on signal 11!

only thing i did as far as i know to get it to partially work was created the gtkrc file as suggested in this post:
[http://http://ubuntuforums.org/showthread.php?t=1037983&highlight=cupsys&page=2]("http://http://ubuntuforums.org/showthread.php?t=1037983&highlight=cupsys&page=2")

---

