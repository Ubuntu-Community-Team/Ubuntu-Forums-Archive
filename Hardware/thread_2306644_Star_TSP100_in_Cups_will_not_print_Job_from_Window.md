---
title: "Star TSP100 in Cups will not print Job from Windows 10"
date: 2015-12-17
forum: Hardware
---

### Post by kara4 on 2015-12-17
Hi,

I am not sure if the Problem mainly from Windows 10 but Drivers are compiled and installed. Printer has been added to Cups and can print a Test Page over Cups without any Problem. If I add the Printer to a Windows 10 PC and want to print anything, than Cups is getting the the Job but does not do anything. Windows is giving immediately an Error. Somehow strange.. Any ideas what it could be?

Regards
kara

---

### Post by yancek on 2015-12-17
What error are you getting?  Configuring CUPS clients for windows at the page below.  More detailed explanation at the second link.

[https://www.freebsd.org/doc/en/articles/cups/printing-cups-clients.html](https://www.freebsd.org/doc/en/articles/cups/printing-cups-clients.html)

[https://wiki.archlinux.org/index.php/CUPS/Printer_sharing](https://wiki.archlinux.org/index.php/CUPS/Printer_sharing)

---

### Post by kara4 on 2015-12-18
Cups is reporting: [B]Free - "Sending data to printer."
[/B]
But nothing is forwarded to the Printer and will not print. I have also a Zebra GK420 installed and thats working without any problem. You can see also in log. [B]

Bondrucker = TSP100

Connection Type: usb://Star/TSP113%20(STR_T-001)[/B]

**access_log**
```
192.168.0.40 - - [18/Dec/2015:10:35:00 +0100] "POST /printers/Bondrucker HTTP/1.1" 426 190 Cancel-Job successful-ok
192.168.0.40 - - [18/Dec/2015:10:35:06 +0100] "POST /printers/Bondrucker HTTP/1.1" 426 190 Cancel-Job successful-ok
192.168.0.40 - - [18/Dec/2015:10:35:06 +0100] "POST /printers/Bondrucker HTTP/1.1" 426 190 Cancel-Job successful-ok
192.168.0.40 - - [18/Dec/2015:10:35:16 +0100] "POST /printers/Bondrucker HTTP/1.1" 426 80457 Print-Job successful-ok
192.168.0.40 - - [18/Dec/2015:11:03:58 +0100] "POST /printers/Bondrucker HTTP/1.1" 200 75 windows-ext client-error-bad-request
192.168.0.40 - - [18/Dec/2015:11:04:08 +0100] "POST /printers/Bondrucker HTTP/1.1" 426 190 Cancel-Job successful-ok
localhost - - [18/Dec/2015:11:04:19 +0100] "POST /jobs HTTP/1.1" 401 138 Restart-Job successful-ok
localhost - - [18/Dec/2015:11:04:29 +0100] "POST /jobs HTTP/1.1" 401 138 Restart-Job successful-ok
localhost - [18/Dec/2015:11:04:29 +0100] "POST /jobs HTTP/1.1" 200 138 Restart-Job successful-ok
localhost - - [18/Dec/2015:11:04:33 +0100] "POST /jobs HTTP/1.1" 401 138 Cancel-Job successful-ok
localhost - [18/Dec/2015:11:04:33 +0100] "POST /jobs HTTP/1.1" 200 138 Cancel-Job successful-ok
192.168.0.40 - - [18/Dec/2015:11:04:42 +0100] "POST /printers/Bondrucker HTTP/1.1" 426 190 Cancel-Job successful-ok
192.168.0.40 - - [18/Dec/2015:11:04:52 +0100] "POST /printers/Bondrucker HTTP/1.1" 426 6756 Print-Job successful-ok
192.168.0.40 - - [18/Dec/2015:11:05:56 +0100] "POST /printers/Bondrucker HTTP/1.1" 426 6756 Print-Job successful-ok
213.xxx.xxx.xxx - - [18/Dec/2015:11:09:32 +0100] "POST /printers/Bondrucker HTTP/1.1" 200 75 windows-ext client-error-bad-request
213.xxx.xxx.xxx - - [18/Dec/2015:11:15:53 +0100] "POST /printers/Bondrucker HTTP/1.1" 426 104420 Print-Job successful-ok
213.xxx.xxx.xxx - - [18/Dec/2015:11:19:00 +0100] "POST /printers/Bondrucker HTTP/1.1" 426 104426 Print-Job successful-ok
192.168.0.40 - - [18/Dec/2015:11:20:06 +0100] "POST /printers/Bondrucker HTTP/1.1" 426 15677 Print-Job successful-ok
192.168.0.40 - - [18/Dec/2015:11:23:37 +0100] "POST /printers/Brother_HL-2250DN_series HTTP/1.1" 200 75 windows-ext client-error-bad-request
192.168.0.40 - - [18/Dec/2015:11:23:53 +0100] "POST /printers/Brother_HL-2250DN_series HTTP/1.1" 426 247271 Print-Job successful-ok
192.168.0.40 - - [18/Dec/2015:11:24:47 +0100] "POST /printers/Brother_HL-2250DN_series HTTP/1.1" 426 247492 Print-Job successful-ok
192.168.0.40 - - [18/Dec/2015:11:25:34 +0100] "POST /printers/Zebra HTTP/1.1" 200 1146 Print-Job successful-ok
```


**error_log**
```
I [18/Dec/2015:11:18:34 +0100] Listening to /var/run/cups/cups.sock (Domain)
E [18/Dec/2015:11:18:34 +0100] Unknown directive Order on line 20 of /etc/cups/cupsd.conf.
E [18/Dec/2015:11:18:34 +0100] Unknown directive Allow on line 21 of /etc/cups/cupsd.conf.
I [18/Dec/2015:11:18:34 +0100] Remote access is enabled.
I [18/Dec/2015:11:18:34 +0100] Loaded configuration file "/etc/cups/cupsd.conf"
I [18/Dec/2015:11:18:34 +0100] Using default TempDir of /var/spool/cups/tmp...
I [18/Dec/2015:11:18:34 +0100] Configured for up to 100 clients.
I [18/Dec/2015:11:18:34 +0100] Allowing up to 100 client connections per host.
I [18/Dec/2015:11:18:34 +0100] Using policy "default" as the default.
I [18/Dec/2015:11:18:34 +0100] Full reload is required.
I [18/Dec/2015:11:18:34 +0100] Loaded MIME database from "/usr/share/cups/mime" and "/etc/cups": 39 types, 56 filters...
I [18/Dec/2015:11:18:34 +0100] Registering ICC color profiles for "Bondrucker"
I [18/Dec/2015:11:18:34 +0100] Registering ICC color profiles for "Brother_HL-2250DN_series"
W [18/Dec/2015:11:18:34 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Brother_HL-2250DN_series-Gray..' already exists
I [18/Dec/2015:11:18:34 +0100] Registering ICC color profiles for "Brother_HL-2250DN_series"
W [18/Dec/2015:11:18:34 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Brother_HL-2250DN_series' already exists
I [18/Dec/2015:11:18:34 +0100] Registering ICC color profiles for "Officejet_Pro_8600"
I [18/Dec/2015:11:18:34 +0100] Registering ICC color profiles for "Officejet_Pro_8600_fax"
I [18/Dec/2015:11:18:34 +0100] Registering ICC color profiles for "Zebra"
I [18/Dec/2015:11:18:34 +0100] Loading job cache file "/var/cache/cups/job.cache"...
I [18/Dec/2015:11:18:34 +0100] Full reload complete.
I [18/Dec/2015:11:18:34 +0100] Cleaning out old files in "/var/spool/cups/tmp"...
I [18/Dec/2015:11:18:34 +0100] Cleaning out old files in "/var/cache/cups"...
I [18/Dec/2015:11:18:34 +0100] Listening to 0.0.0.0:631 on fd 9...
I [18/Dec/2015:11:18:34 +0100] Listening to [v1.::]:631 on fd 10...
I [18/Dec/2015:11:18:34 +0100] Listening to /var/run/cups/cups.sock:631 on fd 11...
I [18/Dec/2015:11:18:34 +0100] Resuming new connection processing...
E [18/Dec/2015:11:18:34 +0100] Need to set BrowseLDAPDN to use LDAP browsing!
I [18/Dec/2015:11:18:40 +0100] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=6023)
I [18/Dec/2015:11:19:00 +0100] [Job ???] Request file type is application/octet-stream.
I [18/Dec/2015:11:20:06 +0100] [Job ???] Request file type is application/octet-stream.
I [18/Dec/2015:11:23:29 +0100] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=6090)
E [18/Dec/2015:11:23:37 +0100] Missing printer-uri, job-uri, or ppd-name attribute
E [18/Dec/2015:11:23:37 +0100] Returning IPP client-error-bad-request for windows-ext (no URI) from 192.168.0.40
I [18/Dec/2015:11:23:53 +0100] [Job ???] Request file type is application/vnd.cups-raw.
I [18/Dec/2015:11:23:56 +0100] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=6091)
I [18/Dec/2015:11:23:58 +0100] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=6092)
I [18/Dec/2015:11:24:47 +0100] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=6093)
I [18/Dec/2015:11:24:47 +0100] [Job ???] Request file type is application/vnd.cups-raw.
I [18/Dec/2015:11:24:49 +0100] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=6094)
I [18/Dec/2015:11:24:50 +0100] Started "/usr/lib/cups/cgi-bin/jobs.cgi" (pid=6095)
I [18/Dec/2015:11:25:34 +0100] [Job ???] Request file type is application/octet-stream.

```

From Windows XP Cups receive a Job and has the Status ***"Sending data to printer." ***but does not send data to printer and keeps the Status.

---

### Post by kara4 on 2015-12-23
So I installed on another PC Ubuntu 14.04 Server and have the same Problem with CUPS 1.7.2

I have tried also Printing from an iPhone 6 and it is working like a charm but not over Windows.

On Cups 1.7.2 was compiling a Problem but I did it by changing some lines:
[URL="http://ubuntuforums.org/showthread.php?t=2307131"]http://ubuntuforums.org/showthread.php?t=2307131
[/URL]

---

