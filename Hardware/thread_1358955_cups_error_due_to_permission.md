---
title: "cups error due to permission"
date: 2009-12-19
forum: Hardware
---

### Post by baosheng on 2009-12-19
My CUPS worked fine all the time on my 9.04 Jaunty Jacklope box until I restarted it today. 

Now my printing setup utility, "System"->"Administration"->"Printing" can detect and install printers via USB, LPT or IPP. 

But, I just can't print anything, even using cups-pdf to generate PDFs. I checked CUPS queues from my browser via localhost:631, it says those jobs are completed. But I can not find any generated PDF under either ~/PDF or /var/spool/cups-pdf/ANONYMOUS

For the IPP case, the queue never comes to the computer that shares the printer. 

I dig in to the logs of CUPS and think it might because of some permission issue related to CUPS.

In /var/log/cups/cups-pdf_log, I found this: ```
Sat Dec 19 00:33:12 2009  [ERROR] failed to create directory (/home/forrest/PDF)
Sat Dec 19 00:33:12 2009  [ERROR] failed to create user output directory (/home/forrest/PDF)

```

In /var/log/cups/error_log, I found this: ```
E [19/Dec/2009:00:20:34 -0600] CUPS-Add-Modify-Printer: Unauthorized
E [19/Dec/2009:00:23:40 -0600] PID 5422 (/usr/lib/cups/backend/cups-pdf) stopped with status 5!
E [19/Dec/2009:00:25:48 -0600] PID 5562 (/usr/lib/cups/backend/cups-pdf) stopped with status 5!
E [19/Dec/2009:00:32:58 -0600] PID 5948 (/usr/lib/cups/backend/cups-pdf) stopped with status 5!
E [19/Dec/2009:00:33:12 -0600] PID 5990 (/usr/lib/cups/backend/cups-pdf) stopped with status 5!
E [19/Dec/2009:00:36:18 -0600] CUPS-Add-Modify-Printer: Unauthorized
E [19/Dec/2009:00:36:25 -0600] CUPS-Add-Modify-Printer: Unauthorized
E [19/Dec/2009:00:40:50 -0600] CUPS-Add-Modify-Printer: Unauthorized

```

Do you think this might is due to the settings to users related to CUPS? 

```
$ ls /var/spool/cups-pdf/ -l
total 8
drwxrwxrwt 2 nobody nogroup 4096 2009-02-14 15:48 ANONYMOUS
drwxr-x--x 2 root   lpadmin 4096 2009-12-19 00:23 SPOOL
$ ls /var/spool/ -l | grep cups
drwx--x--- 3 root lp   4096 2009-12-19 00:40 cups


```

---

