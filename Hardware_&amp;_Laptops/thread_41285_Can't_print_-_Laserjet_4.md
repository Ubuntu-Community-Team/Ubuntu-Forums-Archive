---
title: "Can't print - Laserjet 4"
date: 2005-06-12
forum: Hardware &amp; Laptops
---

### Post by RichA on 2005-06-12
Hi all,

Have had my Laserjet 4 working under WinXP, Mandrake, Fedora, etc, etc.  Just can't get the damned thing working under Ubuntu!

I install the printer through the Gnome printing thingy(manually, the LJ4 is too old to be detected), and it comes up as ready.  As soon as I try a test page or try printing from an application the status changes to "Printing: Printer not connected; will retry in 30 seconds..."

I've tried using the hpijs and ljet4 drivers but the same happens with both.

Any help would be most appreciated...

--Rich

---

### Post by desdinova on 2005-06-12
[QUOTE=RichA]Hi all,

Have had my Laserjet 4 working under WinXP, Mandrake, Fedora, etc, etc.  Just can't get the damned thing working under Ubuntu!

I install the printer through the Gnome printing thingy(manually, the LJ4 is too old to be detected), and it comes up as ready.  As soon as I try a test page or try printing from an application the status changes to "Printing: Printer not connected; will retry in 30 seconds..."

I've tried using the hpijs and ljet4 drivers but the same happens with both.

Any help would be most appreciated...

--Rich[/QUOTE]
 Is your LJ4 postscript compatible by any chance - I ask as I've found HP probably the best supported printers under Linux

does [http://www.linuxprinting.org](http://www.linuxprinting.org) offer any help for you?

---

### Post by RichA on 2005-06-12
[QUOTE=desdinova]Is your LJ4 postscript compatible by any chance - I ask as I've found HP probably the best supported printers under Linux

does [http://www.linuxprinting.org](http://www.linuxprinting.org) offer any help for you?[/QUOTE]
 Yup, it's PostScript compatible.  I've tried using the generic PS drivers but the same error occurs.  It's connected via the parallel port, which is selected correctly in the configuration.

The printer has worked flawlessly under other Linux distributions, I just cannot get it going under Ubuntu.  I've scanned through that site(I'd looked at it before you suggested it) but cannot find anything that appears to be relevant to me, nor can I find anything using the search function on this forum.

--Rich

---

### Post by desdinova on 2005-06-12
[QUOTE=RichA]Yup, it's PostScript compatible.  I've tried using the generic PS drivers but the same error occurs.  It's connected via the parallel port, which is selected correctly in the configuration.

The printer has worked flawlessly under other Linux distributions, I just cannot get it going under Ubuntu.  I've scanned through that site(I'd looked at it before you suggested it) but cannot find anything that appears to be relevant to me, nor can I find anything using the search function on this forum.

--Rich[/QUOTE]
 what do the cups logs show - namely error_log in (IIRC /var/log/cups)

---

### Post by RichA on 2005-06-12
[QUOTE=desdinova]what do the cups logs show - namely error_log in (IIRC /var/log/cups)[/QUOTE]
 I [13/Jun/2005:02:06:01 +0100] Listening to 7f000001:631
I [13/Jun/2005:02:06:01 +0100] Loaded configuration file "/etc/cups/cupsd.conf"
I [13/Jun/2005:02:06:01 +0100] Configured for up to 100 clients.
I [13/Jun/2005:02:06:01 +0100] Allowing up to 100 client connections per host.
I [13/Jun/2005:02:06:01 +0100] Full reload is required.
I [13/Jun/2005:02:06:01 +0100] LoadPPDs: Read "/etc/cups/ppds.dat", 2348 PPDs...I [13/Jun/2005:02:06:02 +0100] LoadPPDs: No new or changed PPDs...
I [13/Jun/2005:02:06:02 +0100] Full reload complete.
I [13/Jun/2005:02:06:02 +0100] Started filter /usr/lib/cups/filter/pstops (PID 4479) for job 13.
I [13/Jun/2005:02:06:02 +0100] Started filter /usr/lib/cups/filter/foomatic-rip (PID 4480) for job 13.
I [13/Jun/2005:02:06:02 +0100] Started backend /usr/lib/cups/backend/parallel (PID 4481) for job 13.
I [13/Jun/2005:02:06:31 +0100] Adding start banner page "none" to job 14.
I [13/Jun/2005:02:06:31 +0100] Adding end banner page "none" to job 14.
I [13/Jun/2005:02:06:31 +0100] Job 14 queued on 'LaserJet-4' by 'rich'.
I [13/Jun/2005:02:06:51 +0100] Started filter /usr/lib/cups/filter/pstops (PID 4556) for job 14.
I [13/Jun/2005:02:06:51 +0100] Started filter /usr/lib/cups/filter/foomatic-rip (PID 4557) for job 14.
I [13/Jun/2005:02:06:51 +0100] Started backend /usr/lib/cups/backend/parallel (PID 4558) for job 14.
I [13/Jun/2005:02:06:51 +0100] Job 13 was cancelled by 'root'.
I [13/Jun/2005:02:06:59 +0100] Job 14 was cancelled by 'root'.

I cancelled the jobs through the print manager when the status changed to printer not connected, retrying in 30 secs...

---

### Post by desdinova on 2005-06-12
[QUOTE=RichA]I [13/Jun/2005:02:06:01 +0100] Listening to 7f000001:631
I [13/Jun/2005:02:06:01 +0100] Loaded configuration file "/etc/cups/cupsd.conf"
I [13/Jun/2005:02:06:01 +0100] Configured for up to 100 clients.
I [13/Jun/2005:02:06:01 +0100] Allowing up to 100 client connections per host.
I [13/Jun/2005:02:06:01 +0100] Full reload is required.
I [13/Jun/2005:02:06:01 +0100] LoadPPDs: Read "/etc/cups/ppds.dat", 2348 PPDs...I [13/Jun/2005:02:06:02 +0100] LoadPPDs: No new or changed PPDs...
I [13/Jun/2005:02:06:02 +0100] Full reload complete.
I [13/Jun/2005:02:06:02 +0100] Started filter /usr/lib/cups/filter/pstops (PID 4479) for job 13.
I [13/Jun/2005:02:06:02 +0100] Started filter /usr/lib/cups/filter/foomatic-rip (PID 4480) for job 13.
I [13/Jun/2005:02:06:02 +0100] Started backend /usr/lib/cups/backend/parallel (PID 4481) for job 13.
I [13/Jun/2005:02:06:31 +0100] Adding start banner page "none" to job 14.
I [13/Jun/2005:02:06:31 +0100] Adding end banner page "none" to job 14.
I [13/Jun/2005:02:06:31 +0100] Job 14 queued on 'LaserJet-4' by 'rich'.
I [13/Jun/2005:02:06:51 +0100] Started filter /usr/lib/cups/filter/pstops (PID 4556) for job 14.
I [13/Jun/2005:02:06:51 +0100] Started filter /usr/lib/cups/filter/foomatic-rip (PID 4557) for job 14.
I [13/Jun/2005:02:06:51 +0100] Started backend /usr/lib/cups/backend/parallel (PID 4558) for job 14.
I [13/Jun/2005:02:06:51 +0100] Job 13 was cancelled by 'root'.
I [13/Jun/2005:02:06:59 +0100] Job 14 was cancelled by 'root'.

I cancelled the jobs through the print manager when the status changed to printer not connected, retrying in 30 secs...[/QUOTE]
 In cupsd.conf is a log option which you can set to "debug" - it will put a LOT more info in those log files....

edit it, restart cups and try again....

---

### Post by RichA on 2005-06-12
> **desdinova]In cupsd.conf is a log option which you can set to "debug" - it will put a LOT more info in those log files....

edit it, restart cups and try again....[/QUOTE]
 [quote]I [13/Jun/2005:02:06:01 +0100] Listening to 7f000001:631
I [13/Jun/2005:02:06:01 +0100] Loaded configuration file "/etc/cups/cupsd.conf"
I [13/Jun/2005:02:06:01 +0100] Configured for up to 100 clients.
I [13/Jun/2005:02:06:01 +0100] Allowing up to 100 client connections per host.
I [13/Jun/2005:02:06:01 +0100] Full reload is required.
I [13/Jun/2005:02:06:01 +0100] LoadPPDs: Read "/etc/cups/ppds.dat", 2348 PPDs...
I [13/Jun/2005:02:06:02 +0100] LoadPPDs: No new or changed PPDs...
I [13/Jun/2005:02:06:02 +0100] Full reload complete.
I [13/Jun/2005:02:06:02 +0100] Started filter /usr/lib/cups/filter/pstops (PID 4479) for job 13.
I [13/Jun/2005:02:06:02 +0100] Started filter /usr/lib/cups/filter/foomatic-rip (PID 4480) for job 13.
I [13/Jun/2005:02:06:02 +0100] Started backend /usr/lib/cups/backend/parallel (PID 4481) for job 13.
I [13/Jun/2005:02:06:31 +0100] Adding start banner page "none" to job 14.
I [13/Jun/2005:02:06:31 +0100] Adding end banner page "none" to job 14.
I [13/Jun/2005:02:06:31 +0100] Job 14 queued on 'LaserJet-4' by 'rich'.
I [13/Jun/2005:02:06:51 +0100] Started filter /usr/lib/cups/filter/pstops (PID 4556) for job 14.
I [13/Jun/2005:02:06:51 +0100] Started filter /usr/lib/cups/filter/foomatic-rip (PID 4557) for job 14.
I [13/Jun/2005:02:06:51 +0100] Started backend /usr/lib/cups/backend/parallel (PID 4558) for job 14.
I [13/Jun/2005:02:06:51 +0100] Job 13 was cancelled by 'root'.
I [13/Jun/2005:02:06:59 +0100] Job 14 was cancelled by 'root'.
I [13/Jun/2005:02:11:45 +0100] Scheduler shutting down normally.
I [13/Jun/2005:02:11:45 +0100] Listening to 7f000001:631
D [13/Jun/2005:02:11:45 +0100] AddLocation: added location '/'
D [13/Jun/2005:02:11:45 +0100] DenyIP: / deny 00000000/00000000
D [13/Jun/2005:02:11:45 +0100] AllowIP: / allow 7f000001/ffffffff
D [13/Jun/2005:02:11:45 +0100] AddLocation: added location '/jobs'
D [13/Jun/2005:02:11:45 +0100] AddLocation: added location '/admin'
D [13/Jun/2005:02:11:45 +0100] DenyIP: /admin deny 00000000/00000000
D [13/Jun/2005:02:11:45 +0100] AllowIP: /admin allow 7f000001/ffffffff
I [13/Jun/2005:02:11:45 +0100] Loaded configuration file "/etc/cups/cupsd.conf"
I [13/Jun/2005:02:11:45 +0100] Configured for up to 100 clients.
I [13/Jun/2005:02:11:45 +0100] Allowing up to 100 client connections per host.
I [13/Jun/2005:02:11:45 +0100] Full reload is required.
D [13/Jun/2005:02:11:45 +0100] LoadAllPrinters: Loading printer LaserJet-4...
D [13/Jun/2005:02:11:45 +0100] LoadDevices: Added device "ipp"...
D [13/Jun/2005:02:11:45 +0100] LoadDevices: Added device "lpd"...
D [13/Jun/2005:02:11:45 +0100] LoadDevices: Added device "smb"...
D [13/Jun/2005:02:11:45 +0100] LoadDevices: Added device "usb:/dev/usb/lp0"...
D [13/Jun/2005:02:11:45 +0100] LoadDevices: Added device "usb:/dev/usb/lp1"...
D [13/Jun/2005:02:11:45 +0100] LoadDevices: Added device "usb:/dev/usb/lp2"...
D [13/Jun/2005:02:11:45 +0100] LoadDevices: Added device "usb:/dev/usb/lp3"...
D [13/Jun/2005:02:11:45 +0100] LoadDevices: Added device "usb:/dev/usb/lp4"...
D [13/Jun/2005:02:11:45 +0100] LoadDevices: Added device "usb:/dev/usb/lp5"...
D [13/Jun/2005:02:11:45 +0100] LoadDevices: Added device "usb:/dev/usb/lp6"...
D [13/Jun/2005:02:11:45 +0100] LoadDevices: Added device "usb:/dev/usb/lp7"...
D [13/Jun/2005:02:11:45 +0100] LoadDevices: Added device "usb:/dev/usb/lp8"...
D [13/Jun/2005:02:11:45 +0100] LoadDevices: Added device "usb:/dev/usb/lp9"...
D [13/Jun/2005:02:11:45 +0100] LoadDevices: Added device "usb:/dev/usb/lp10"...
D [13/Jun/2005:02:11:45 +0100] LoadDevices: Added device "usb:/dev/usb/lp11"...
D [13/Jun/2005:02:11:45 +0100] LoadDevices: Added device "usb:/dev/usb/lp12"...
D [13/Jun/2005:02:11:45 +0100] LoadDevices: Added device "usb:/dev/usb/lp13"...
D [13/Jun/2005:02:11:45 +0100] LoadDevices: Added device "usb:/dev/usb/lp14"...
D [13/Jun/2005:02:11:45 +0100] LoadDevices: Added device "usb:/dev/usb/lp15"...
D [13/Jun/2005:02:11:45 +0100] LoadDevices: Added device "http"...
D [13/Jun/2005:02:11:45 +0100] LoadDevices: Added device "parallel:/dev/unknown-parallel0"...
D [13/Jun/2005:02:11:45 +0100] LoadDevices: Added device "socket"...
I [13/Jun/2005:02:11:45 +0100] LoadPPDs: Read "/etc/cups/ppds.dat", 2348 PPDs...
I [13/Jun/2005:02:11:45 +0100] LoadPPDs: No new or changed PPDs...
D [13/Jun/2005:02:11:45 +0100] LoadAllJobs: Scanning /var/spool/cups...
D [13/Jun/2005:02:11:45 +0100] LoadAllJobs: Loading attributes for job 13...
D [13/Jun/2005:02:11:45 +0100] LoadAllJobs: Loading attributes for job 14...
I [13/Jun/2005:02:11:45 +0100] Full reload complete.
D [13/Jun/2005:02:11:45 +0100] StartListening: NumListeners=1
D [13/Jun/2005:02:11:45 +0100] StartListening: address=7f000001 port=631
D [13/Jun/2005:02:11:45 +0100] ResumeListening: setting input bits...
D [13/Jun/2005:02:11:47 +0100] AcceptClient: 4 from localhost:631.
D [13/Jun/2005:02:11:47 +0100] ReadClient: 4 POST / HTTP/1.1
D [13/Jun/2005:02:11:47 +0100] ProcessIPPRequest: 4 status_code=0
D [13/Jun/2005:02:11:47 +0100] ReadClient: 4 POST / HTTP/1.1
D [13/Jun/2005:02:11:47 +0100] ProcessIPPRequest: 4 status_code=1
D [13/Jun/2005:02:11:47 +0100] ReadClient: 4 POST / HTTP/1.1
D [13/Jun/2005:02:11:47 +0100] ProcessIPPRequest: 4 status_code=0
D [13/Jun/2005:02:11:48 +0100] ReadClient: 4 POST / HTTP/1.1
D [13/Jun/2005:02:11:48 +0100] ProcessIPPRequest: 4 status_code=0
D [13/Jun/2005:02:11:48 +0100] ReadClient: 4 POST / HTTP/1.1
D [13/Jun/2005:02:11:48 +0100] ProcessIPPRequest: 4 status_code=1
D [13/Jun/2005:02:11:49 +0100] AcceptClient: 5 from localhost:631.
D [13/Jun/2005:02:11:49 +0100] ReadClient: 5 POST / HTTP/1.1
D [13/Jun/2005:02:11:49 +0100] ProcessIPPRequest: 5 status_code=0
D [13/Jun/2005:02:11:49 +0100] ReadClient: 5 POST / HTTP/1.1
D [13/Jun/2005:02:11:49 +0100] ProcessIPPRequest: 5 status_code=1
D [13/Jun/2005:02:11:51 +0100] ReadClient: 4 GET /printers/LaserJet-4.ppd HTTP/1.1
D [13/Jun/2005:02:11:51 +0100] SendFile: 4 file=6
D [13/Jun/2005:02:11:51 +0100] ReadClient: 4 POST / HTTP/1.1
D [13/Jun/2005:02:11:51 +0100] ProcessIPPRequest: 4 status_code=0
D [13/Jun/2005:02:11:52 +0100] ReadClient: 4 POST / HTTP/1.1
D [13/Jun/2005:02:11:52 +0100] ProcessIPPRequest: 4 status_code=0
D [13/Jun/2005:02:11:53 +0100] ReadClient: 4 POST / HTTP/1.1
D [13/Jun/2005:02:11:53 +0100] ProcessIPPRequest: 4 status_code=0
D [13/Jun/2005:02:11:53 +0100] ReadClient: 4 POST / HTTP/1.1
D [13/Jun/2005:02:11:53 +0100] ProcessIPPRequest: 4 status_code=1
D [13/Jun/2005:02:11:54 +0100] AcceptClient: 6 from localhost:631.
D [13/Jun/2005:02:11:54 +0100] ReadClient: 6 POST /printers/LaserJet-4 HTTP/1.1
D [13/Jun/2005:02:11:54 +0100] print_job: auto-typing file...
D [13/Jun/2005:02:11:54 +0100] print_job: request file type is application/postscript.
D [13/Jun/2005:02:11:54 +0100] check_quotas: requesting-user-name = 'rich'
D [13/Jun/2005:02:11:54 +0100] print_job: requesting-user-name = 'rich'
D [13/Jun/2005:02:11:54 +0100] Adding default job-sheets values "none,none"...
I [13/Jun/2005:02:11:54 +0100] Adding start banner page "none" to job 15.
I [13/Jun/2005:02:11:54 +0100] Adding end banner page "none" to job 15.
I [13/Jun/2005:02:11:54 +0100] Job 15 queued on 'LaserJet-4' by 'rich'.
D [13/Jun/2005:02:11:54 +0100] Job 15 hold_until = 0
D [13/Jun/2005:02:11:54 +0100] StartJob(15, 0x8096878)
D [13/Jun/2005:02:11:54 +0100] StartJob() id = 15, file = 0/1
D [13/Jun/2005:02:11:54 +0100] job-sheets=none,none
D [13/Jun/2005:02:11:54 +0100] banner_page = 0
D [13/Jun/2005:02:11:54 +0100] StartJob: argv = "LaserJet-4","15","rich","Test Page","1","","/var/spool/cups/d00015-001"
D [13/Jun/2005:02:11:54 +0100] StartJob: envp[0]="PATH=/usr/lib/cups/filter:/bin:/usr/bin"
D [13/Jun/2005:02:11:54 +0100] StartJob: envp[1]="SOFTWARE=CUPS/1.1"
D [13/Jun/2005:02:11:54 +0100] StartJob: envp[2]="USER=root"
D [13/Jun/2005:02:11:54 +0100] StartJob: envp[3]="CHARSET=utf-8"
D [13/Jun/2005:02:11:54 +0100] StartJob: envp[4]="LANG=en"
D [13/Jun/2005:02:11:54 +0100] StartJob: envp[5]="TZ=Europe/London"
D [13/Jun/2005:02:11:54 +0100] StartJob: envp[6]="PPD=/etc/cups/ppd/LaserJet-4.ppd"
D [13/Jun/2005:02:11:54 +0100] StartJob: envp[7]="CUPS_SERVERROOT=/etc/cups"
D [13/Jun/2005:02:11:54 +0100] StartJob: envp[8]="RIP_MAX_CACHE=8m"
D [13/Jun/2005:02:11:54 +0100] StartJob: envp[9]="TMPDIR=/var/spool/cups/tmp"
D [13/Jun/2005:02:11:54 +0100] StartJob: envp[10]="CONTENT_TYPE=application/postscript"
D [13/Jun/2005:02:11:54 +0100] StartJob: envp[11]="DEVICE_URI=parallel:/dev/unknown-parallel0"
D [13/Jun/2005:02:11:54 +0100] StartJob: envp[12]="PRINTER=LaserJet-4"
D [13/Jun/2005:02:11:54 +0100] StartJob: envp[13]="CUPS_DATADIR=/usr/share/cups"
D [13/Jun/2005:02:11:54 +0100] StartJob: envp[14]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [13/Jun/2005:02:11:54 +0100] StartJob: envp[15]="CUPS_SERVER=localhost"
D [13/Jun/2005:02:11:54 +0100] StartJob: envp[16]="IPP_PORT=631"
D [13/Jun/2005:02:11:54 +0100] StartJob: statusfds = [ 7 8 ]
D [13/Jun/2005:02:11:54 +0100] StartJob: filterfds[1] = [ 9 -1 ]
D [13/Jun/2005:02:11:54 +0100] StartJob: filter = "/usr/lib/cups/filter/pstops"
D [13/Jun/2005:02:11:54 +0100] StartJob: filterfds[0] = [ 10 11 ]
D [13/Jun/2005:02:11:54 +0100] start_process("/usr/lib/cups/filter/pstops", 0xbffefc40, 0xbffeefb0, 9, 11, 8)
I [13/Jun/2005:02:11:54 +0100] Started filter /usr/lib/cups/filter/pstops (PID 4919) for job 15.
D [13/Jun/2005:02:11:54 +0100] StartJob: filter = "/usr/lib/cups/filter/foomatic-rip"
D [13/Jun/2005:02:11:54 +0100] StartJob: filterfds[1] = [ 9 12 ]
D [13/Jun/2005:02:11:54 +0100] start_process("/usr/lib/cups/filter/foomatic-rip", 0xbffefc40, 0xbffeefb0, 10, 12, 8)
I [13/Jun/2005:02:11:54 +0100] Started filter /usr/lib/cups/filter/foomatic-rip (PID 4920) for job 15.
D [13/Jun/2005:02:11:54 +0100] StartJob: backend = "/usr/lib/cups/backend/parallel"
D [13/Jun/2005:02:11:54 +0100] StartJob: filterfds[0] = [ -1 10 ]
D [13/Jun/2005:02:11:54 +0100] start_process("/usr/lib/cups/backend/parallel", 0xbffefc40, 0xbffeefb0, 9, 10, 8)
I [13/Jun/2005:02:11:54 +0100] Started backend /usr/lib/cups/backend/parallel (PID 4921) for job 15.
D [13/Jun/2005:02:11:54 +0100] ProcessIPPRequest: 6 status_code=0
D [13/Jun/2005:02:11:54 +0100] [Job 15] Page = 595x842 said:**
>  [Job 15] slowcollate=0, slowduplex=0, sloworder=0
D [13/Jun/2005:02:11:54 +0100] [Job 15] 0 %%Title: PPR Test Page
D [13/Jun/2005:02:11:54 +0100] [Job 15] 0 %%Pages: 1
D [13/Jun/2005:02:11:54 +0100] [Job 15] 0 %%DocumentNeededResources: font Helvetica
D [13/Jun/2005:02:11:54 +0100] [Job 15] 0 %%EndComments
D [13/Jun/2005:02:11:54 +0100] [Job 15] 0 %%BeginProlog
D [13/Jun/2005:02:11:54 +0100] [Job 15] 0 %%EndProlog
D [13/Jun/2005:02:11:54 +0100] [Job 15] 0 %%BeginSetup
D [13/Jun/2005:02:11:54 +0100] [Job 15] 0 %%IncludeResource: font Helvetica
D [13/Jun/2005:02:11:54 +0100] [Job 15] 0 %%IncludeFeature: *PageSize A4
D [13/Jun/2005:02:11:54 +0100] [Job 15] 0 %%EndSetup
D [13/Jun/2005:02:11:54 +0100] [Job 15] 0 %%Page: 1 1
D [13/Jun/2005:02:11:54 +0100] [Job 15] 0 %%Page: 1 1
D [13/Jun/2005:02:11:54 +0100] [Job 15] pw = 559.0, pl = 813.2
D [13/Jun/2005:02:11:54 +0100] [Job 15] PageLeft = 18.0, PageRight = 577.0
D [13/Jun/2005:02:11:54 +0100] [Job 15] PageTop = 827.6, PageBottom = 14.4
D [13/Jun/2005:02:11:54 +0100] [Job 15] PageWidth = 595.0, PageLength = 842.0
D [13/Jun/2005:02:11:54 +0100] [Job 15] 0 %%BeginDocument: /home/jdub/Documents/Canonical/Logos/Ubuntu_logo.eps
D [13/Jun/2005:02:11:54 +0100] [Job 15] 1 %%Title: Ubuntu final logo
D [13/Jun/2005:02:11:54 +0100] [Job 15] 1 %%Creator: FreeHand 10.0
D [13/Jun/2005:02:11:54 +0100] [Job 15] 1 %%CreationDate: 15/9/04 11:16 am
D [13/Jun/2005:02:11:54 +0100] [Job 15] 1 %%BoundingBox: 0 0 350 81
D [13/Jun/2005:02:11:54 +0100] [Job 15] 1 %%FHPathName:Work:CANONICAL SOFTWARE:Ubuntu:UBUNTU Identity:Ubuntu final logo
D [13/Jun/2005:02:11:54 +0100] [Job 15] 1 %%FHPageNum:1
D [13/Jun/2005:02:11:54 +0100] [Job 15] 1 %%DocumentSuppliedResources: procset Altsys_header 4 0
D [13/Jun/2005:02:11:54 +0100] [Job 15] 1 %%ColorUsage: Color
D [13/Jun/2005:02:11:54 +0100] [Job 15] 1 %%DocumentProcessColors: Black
D [13/Jun/2005:02:11:54 +0100] [Job 15] 1 %%DocumentCustomColors: (PANTONE 2965 CVC)
D [13/Jun/2005:02:11:54 +0100] [Job 15] 1 %%+ (PANTONE 151 CVC)
D [13/Jun/2005:02:11:54 +0100] [Job 15] 1 %%+ (PANTONE 1235 CVC)
D [13/Jun/2005:02:11:54 +0100] [Job 15] 1 %%+ (PANTONE 179 CVC)
D [13/Jun/2005:02:11:54 +0100] [Job 15] 1 %%+ (0r 43g 61b)
D [13/Jun/2005:02:11:54 +0100] [Job 15] 1 %%+ (244r 72g 0b)
D [13/Jun/2005:02:11:54 +0100] [Job 15] 1 %%+ (251r 139g 0b)
D [13/Jun/2005:02:11:54 +0100] [Job 15] 1 %%+ (212r 0g 0b)
D [13/Jun/2005:02:11:54 +0100] [Job 15] 1 %%CMYKCustomColor: 1 0.38 0 0.69 (PANTONE 2965 CVC)
D [13/Jun/2005:02:11:54 +0100] [Job 15] 1 %%+ 0 0.43 0.87 0 (PANTONE 151 CVC)
D [13/Jun/2005:02:11:54 +0100] [Job 15] 1 %%+ 0 0.275 0.76 0 (PANTONE 1235 CVC)
D [13/Jun/2005:02:11:54 +0100] [Job 15] 1 %%+ 0 0.79 0.94 0 (PANTONE 179 CVC)
D [13/Jun/2005:02:11:54 +0100] [Job 15] 1 %%+ 0.7613 0.5271 0.6244 0.7124 (0r 43g 61b)
D [13/Jun/2005:02:11:54 +0100] [Job 15] 1 %%+ 0.0017 0.7251 0.8508 0 (244r 72g 0b)
D [13/Jun/2005:02:11:54 +0100] [Job 15] 1 %%+ 0.0032 0.4248 0.8274 0 (251r 139g 0b)
D [13/Jun/2005:02:11:54 +0100] [Job 15] 1 %%+ 0.0176 0.9327 0.9184 0 (212r 0g 0b)
D [13/Jun/2005:02:11:54 +0100] [Job 15] 1 %%EndComments
D [13/Jun/2005:02:11:54 +0100] [Job 15] 1 %%BeginFont: Times-Roman
D [13/Jun/2005:02:11:54 +0100] [Job 15] perl: warning: Setting locale failed.
D [13/Jun/2005:02:11:54 +0100] [Job 15] perl: warning: Please check that your locale settings:
D [13/Jun/2005:02:11:54 +0100] [Job 15] LANGUAGE = (unset),
D [13/Jun/2005:02:11:54 +0100] [Job 15] LC_ALL = (unset),
D [13/Jun/2005:02:11:54 +0100] [Job 15] LANG = "en"
D [13/Jun/2005:02:11:54 +0100] [Job 15] are supported and installed on your system.
D [13/Jun/2005:02:11:54 +0100] [Job 15] perl: warning: Falling back to the standard locale ("C").
D [13/Jun/2005:02:11:54 +0100] [Job 15] foomatic-rip version $Revision: 3.43.2.6 $ running...
D [13/Jun/2005:02:11:54 +0100] [Job 15] Parsing PPD file ...
D [13/Jun/2005:02:11:54 +0100] [Job 15] *cupsFilter: "application/vnd.cups-postscript 0 foomatic-rip"
D [13/Jun/2005:02:11:54 +0100] [Job 15] Added option ColorSpace
D [13/Jun/2005:02:11:54 +0100] [Job 15] Added option Resolution
D [13/Jun/2005:02:11:54 +0100] [Job 15] Added option PageSize
D [13/Jun/2005:02:11:54 +0100] [Job 15] Added option PageRegion
D [13/Jun/2005:02:11:54 +0100] [Job 15] Added option Model
D [13/Jun/2005:02:11:54 +0100] [Job 15] Added option PrintoutMode
D [13/Jun/2005:02:11:54 +0100] [Job 15] Added option ImageableArea
D [13/Jun/2005:02:11:54 +0100] [Job 15] Added option PaperDimension
D [13/Jun/2005:02:11:54 +0100] [Job 15] Added option InputSlot
D [13/Jun/2005:02:11:54 +0100] [Job 15] Added option Manualfeed
D [13/Jun/2005:02:11:54 +0100] [Job 15] Added option Duplex
D [13/Jun/2005:02:11:54 +0100] [Job 15] Added option Economode
D [13/Jun/2005:02:11:54 +0100] [Job 15] Added option Copies
D [13/Jun/2005:02:11:54 +0100] [Job 15] Added option REt
D [13/Jun/2005:02:11:54 +0100] [Job 15] Added option TonerDensity
D [13/Jun/2005:02:11:54 +0100] [Job 15] Added option Quality
D [13/Jun/2005:02:11:54 +0100] [Job 15] Added option Font
D [13/Jun/2005:02:11:54 +0100] [Job 15] 
D [13/Jun/2005:02:11:54 +0100] [Job 15] Parameter Summary
D [13/Jun/2005:02:11:54 +0100] [Job 15] -----------------
D [13/Jun/2005:02:11:54 +0100] [Job 15] 
D [13/Jun/2005:02:11:54 +0100] [Job 15] Spooler: cups
D [13/Jun/2005:02:11:54 +0100] [Job 15] Printer: LaserJet-4
D [13/Jun/2005:02:11:54 +0100] [Job 15] PPD file: /etc/cups/ppd/LaserJet-4.ppd
D [13/Jun/2005:02:11:54 +0100] [Job 15] Printer model: HP LaserJet 4 Foomatic/hpijs (recommended)
D [13/Jun/2005:02:11:54 +0100] [Job 15] Job title: Test Page
D [13/Jun/2005:02:11:54 +0100] [Job 15] File(s) to be printed: 
D [13/Jun/2005:02:11:54 +0100] [Job 15] <STDIN>
D [13/Jun/2005:02:11:54 +0100] [Job 15] 
D [13/Jun/2005:02:11:54 +0100] [Job 15] 
D [13/Jun/2005:02:11:54 +0100] [Job 15] ================================================
D [13/Jun/2005:02:11:54 +0100] [Job 15] 
D [13/Jun/2005:02:11:54 +0100] [Job 15] File: <STDIN>
D [13/Jun/2005:02:11:54 +0100] [Job 15] 
D [13/Jun/2005:02:11:54 +0100] [Job 15] ================================================
D [13/Jun/2005:02:11:54 +0100] [Job 15] 
D [13/Jun/2005:02:11:54 +0100] [Job 15] Reading PostScript input ...
D [13/Jun/2005:02:11:54 +0100] [Job 15] --> This document is DSC-conforming!
D [13/Jun/2005:02:11:54 +0100] [Job 15] 
D [13/Jun/2005:02:11:54 +0100] [Job 15] -----------
D [13/Jun/2005:02:11:54 +0100] [Job 15] Found: %%BeginProlog
D [13/Jun/2005:02:11:54 +0100] [Job 15] Found: %%EndProlog
D [13/Jun/2005:02:11:54 +0100] [Job 15] 
D [13/Jun/2005:02:11:54 +0100] [Job 15] -----------
D [13/Jun/2005:02:11:54 +0100] [Job 15] Found: %%BeginSetup
D [13/Jun/2005:02:11:54 +0100] [Job 15] Inserting PostScript code for CUPS' page accounting
D [13/Jun/2005:02:11:54 +0100] [Job 15] Found: %%BeginFeature: *PrintoutMode Normal
D [13/Jun/2005:02:11:54 +0100] [Job 15] Option: PrintoutMode=Normal --> Setting option
D [13/Jun/2005:02:11:54 +0100] [Job 15] Found: %% FoomaticRIPOptionSetting: PrintoutMode=Normal
D [13/Jun/2005:02:11:54 +0100] [Job 15] Option: PrintoutMode=Normal --> Setting option
D [13/Jun/2005:02:11:54 +0100] [Job 15] Found: %%BeginFeature: *REt Medium
D [13/Jun/2005:02:11:54 +0100] [Job 15] Option: REt=Medium --> Setting option
D [13/Jun/2005:02:11:54 +0100] [Job 15] Found: %% FoomaticRIPOptionSetting: REt=Medium
D [13/Jun/2005:02:11:54 +0100] [Job 15] Option: REt=Medium --> Setting option
D [13/Jun/2005:02:11:54 +0100] [Job 15] Found: %%BeginFeature: *TonerDensity 5
D [13/Jun/2005:02:11:54 +0100] [Job 15] Option: TonerDensity=5 --> Setting option
D [13/Jun/2005:02:11:54 +0100] [Job 15] Found: %% FoomaticRIPOptionSetting: TonerDensity=5
D [13/Jun/2005:02:11:54 +0100] [Job 15] Option: TonerDensity=5 --> Setting option
D [13/Jun/2005:02:11:54 +0100] [Job 15] Found: %%BeginFeature: *InputSlot Default
D [13/Jun/2005:02:11:54 +0100] [Job 15] Option: InputSlot=Default --> Setting option
D [13/Jun/2005:02:11:54 +0100] [Job 15] Found: %% FoomaticRIPOptionSetting: InputSlot=Default
D [13/Jun/2005:02:11:54 +0100] [Job 15] Option: InputSlot=Default --> Setting option
D [13/Jun/2005:02:11:54 +0100] [Job 15] Found: %%BeginFeature: *Copies 1
D [13/Jun/2005:02:11:54 +0100] [Job 15] Option: Copies=1 --> Setting option
D [13/Jun/2005:02:11:54 +0100] [Job 15] Found: %% FoomaticRIPOptionSetting: Copies=1
D [13/Jun/2005:02:11:54 +0100] [Job 15] Option: Copies=1 --> Setting option
D [13/Jun/2005:02:11:54 +0100] [Job 15] Found: %%BeginFeature: *Economode Off
D [13/Jun/2005:02:11:54 +0100] [Job 15] Option: Economode=Off --> Setting option
D [13/Jun/2005:02:11:54 +0100] [Job 15] Found: %% FoomaticRIPOptionSetting: Economode=Off
D [13/Jun/2005:02:11:54 +0100] [Job 15] Option: Economode=Off --> Setting option
D [13/Jun/2005:02:11:54 +0100] [Job 15] Found: %%BeginFeature: *Quality FromPrintoutMode
D [13/Jun/2005:02:11:54 +0100] [Job 15] Option: Quality=FromPrintoutMode --> Setting option
D [13/Jun/2005:02:11:54 +0100] [Job 15] Found: %% FoomaticRIPOptionSetting: Quality=@PrintoutMode
D [13/Jun/2005:02:11:54 +0100] [Job 15] Option: Quality=FromPrintoutMode --> Setting option
D [13/Jun/2005:02:11:54 +0100] [Job 15] Found: %%BeginFeature: *PageRegion A4
D [13/Jun/2005:02:11:54 +0100] [Job 15] Option: PageRegion=A4 --> Option will be set by PostScript interpreter
D [13/Jun/2005:02:11:54 +0100] [Job 15] Found: %% FoomaticRIPOptionSetting: PageSize=A4
D [13/Jun/2005:02:11:54 +0100] [Job 15] Option: PageSize=A4 --> Setting option
D [13/Jun/2005:02:11:54 +0100] [Job 15] Found: %%BeginFeature: *Duplex None
D [13/Jun/2005:02:11:54 +0100] [Job 15] Option: Duplex=None --> Setting option
D [13/Jun/2005:02:11:54 +0100] [Job 15] Found: %% FoomaticRIPOptionSetting: Duplex=None
D [13/Jun/2005:02:11:54 +0100] [Job 15] Option: Duplex=None --> Setting option
D [13/Jun/2005:02:11:54 +0100] [Job 15] Found: %%EndSetup
D [13/Jun/2005:02:11:54 +0100] [Job 15] 
D [13/Jun/2005:02:11:54 +0100] [Job 15] -----------
D [13/Jun/2005:02:11:54 +0100] [Job 15] New page:  1 1
D [13/Jun/2005:02:11:54 +0100] [Job 15] Inserting option code into "PageSetup" section.
D [13/Jun/2005:02:11:54 +0100] [Job 15] No page header or page header not DSC-conforming
D [13/Jun/2005:02:11:54 +0100] [Job 15] Stopping search for page header options
D [13/Jun/2005:02:11:54 +0100] [Job 15] Found:
D [13/Jun/2005:02:11:54 +0100] [Job 15] 66BA0F2FBD4C92D25121A2647E8081BF05241DF408C9CE4EED2A630C3018869E51E7F90C030031A6E8FEE178DF9A598A4F1D8CA4C7741AA2C40081C0D48C29A8B4B60A0FE5D7BA4DD1F7CC51282CEF697AC70713546B0933B65246AAAC6A881DFB16
D [13/Jun/2005:02:11:54 +0100] [Job 15] --> Output goes directly to the renderer now.
D [13/Jun/2005:02:11:54 +0100] [Job 15] 
D [13/Jun/2005:02:11:54 +0100] [Job 15] 
D [13/Jun/2005:02:11:54 +0100] [Job 15] Starting renderer
D [13/Jun/2005:02:11:54 +0100] [Job 15] JCL: %-12345X@PJL
D [13/Jun/2005:02:11:54 +0100] [Job 15] @PJL SET MANUALFEED=OFF
D [13/Jun/2005:02:11:54 +0100] [Job 15] @PJL SET ECONOMODE=OFF
D [13/Jun/2005:02:11:54 +0100] [Job 15] @PJL SET COPIES=1
D [13/Jun/2005:02:11:54 +0100] [Job 15] @PJL SET RET=MEDIUM
D [13/Jun/2005:02:11:54 +0100] [Job 15] @PJL SET DENSITY=5
D [13/Jun/2005:02:11:54 +0100] [Job 15] <job data> 
D [13/Jun/2005:02:11:54 +0100] [Job 15] %-12345X@PJL RESET
D [13/Jun/2005:02:11:54 +0100] [Job 15] 
D [13/Jun/2005:02:11:54 +0100] [Job 15] renderer PID kid4=4923
D [13/Jun/2005:02:11:54 +0100] [Job 15] renderer command: gs -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=ijs -sIjsServer=hpijs -sDeviceManufacturer="HEWLETT-PACKARD" -sDeviceModel="HP LaserJet" -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842 -dDuplex=false -r300 -sIjsParams=Quality:Quality=0,Quality:ColorMode=0,Quality:MediaType=0,Quality:PenSet=0,PS:MediaPosition=7 -dIjsUseOutputFD -sOutputFile=- -
D [13/Jun/2005:02:11:54 +0100] [Job 15] perl: warning: Setting locale failed.
D [13/Jun/2005:02:11:54 +0100] [Job 15] perl: warning: Please check that your locale settings:
D [13/Jun/2005:02:11:54 +0100] [Job 15] LANGUAGE = (unset),
D [13/Jun/2005:02:11:54 +0100] [Job 15] LC_ALL = (unset),
D [13/Jun/2005:02:11:54 +0100] [Job 15] LANG = "en"
D [13/Jun/2005:02:11:54 +0100] [Job 15] are supported and installed on your system.
D [13/Jun/2005:02:11:54 +0100] [Job 15] perl: warning: Falling back to the standard locale ("C").
D [13/Jun/2005:02:11:54 +0100] [Job 15] foomatic-gswrapper: gs '-dBATCH' '-dPARANOIDSAFER' '-dQUIET' '-dNOPAUSE' '-sDEVICE=ijs' '-sIjsServer=hpijs' '-sDeviceManufacturer=HEWLETT-PACKARD' '-sDeviceModel=HP LaserJet' '-dDEVICEWIDTHPOINTS=595' '-dDEVICEHEIGHTPOINTS=842' '-dDuplex=false' '-r300' '-sIjsParams=Quality:Quality=0,Quality:ColorMode=0,Quality:MediaType=0,Quality:PenSet=0,PS:MediaPosition=7' '-dIjsUseOutputFD' '-sOutputFile=/dev/fd/3' '/dev/fd/0' 3>&1 1>&2
D [13/Jun/2005:02:11:54 +0100] [Job 15] 1 %%EndFont
D [13/Jun/2005:02:11:54 +0100] [Job 15] 1 %%BeginResource: procset Altsys_header 4 0
D [13/Jun/2005:02:11:54 +0100] [Job 15] 1 %%EndResource
D [13/Jun/2005:02:11:54 +0100] [Job 15] 1 %%EndProlog
D [13/Jun/2005:02:11:54 +0100] [Job 15] 1 %%BeginSetup
D [13/Jun/2005:02:11:54 +0100] [Job 15] 1 %%IncludeResource: font Times-Roman
D [13/Jun/2005:02:11:54 +0100] [Job 15] 1 %%EndSetup
D [13/Jun/2005:02:11:54 +0100] [Job 15] Found: %%EndProlog
D [13/Jun/2005:02:11:54 +0100] [Job 15] 
D [13/Jun/2005:02:11:54 +0100] [Job 15] -----------
D [13/Jun/2005:02:11:54 +0100] [Job 15] Found: %%BeginSetup
D [13/Jun/2005:02:11:54 +0100] [Job 15] "%%BeginSetup" in page header
D [13/Jun/2005:02:11:54 +0100] [Job 15] Found: %%EndSetup
D [13/Jun/2005:02:11:54 +0100] [Job 15] 1 %%Trailer
D [13/Jun/2005:02:11:54 +0100] [Job 15] 1 %%EndDocument
D [13/Jun/2005:02:11:54 +0100] [Job 15] 0 %%Trailer
D [13/Jun/2005:02:11:54 +0100] [Job 15] Saw Trailer!
D [13/Jun/2005:02:11:54 +0100] [Job 15] Saw EOF!
D [13/Jun/2005:02:11:54 +0100] [Job 15] 
D [13/Jun/2005:02:11:54 +0100] [Job 15] Closing renderer
D [13/Jun/2005:02:11:54 +0100] ReadClient: 5 POST / HTTP/1.1
D [13/Jun/2005:02:11:54 +0100] ProcessIPPRequest: 5 status_code=0
D [13/Jun/2005:02:11:54 +0100] ReadClient: 5 POST / HTTP/1.1
D [13/Jun/2005:02:11:54 +0100] ProcessIPPRequest: 5 status_code=1
D [13/Jun/2005:02:11:57 +0100] ReadClient: 4 GET /printers/LaserJet-4.ppd HTTP/1.1
D [13/Jun/2005:02:11:57 +0100] SendFile: 4 file=8
D [13/Jun/2005:02:11:57 +0100] ReadClient: 4 POST / HTTP/1.1
D [13/Jun/2005:02:11:57 +0100] ProcessIPPRequest: 4 status_code=0
D [13/Jun/2005:02:11:58 +0100] ReadClient: 4 POST / HTTP/1.1
D [13/Jun/2005:02:11:58 +0100] ProcessIPPRequest: 4 status_code=0
D [13/Jun/2005:02:11:58 +0100] ReadClient: 4 POST / HTTP/1.1
D [13/Jun/2005:02:11:58 +0100] ProcessIPPRequest: 4 status_code=0
D [13/Jun/2005:02:11:58 +0100] ReadClient: 4 POST / HTTP/1.1
D [13/Jun/2005:02:11:58 +0100] ProcessIPPRequest: 4 status_code=1
D [13/Jun/2005:02:11:59 +0100] ReadClient: 5 POST / HTTP/1.1
D [13/Jun/2005:02:11:59 +0100] ProcessIPPRequest: 5 status_code=0
D [13/Jun/2005:02:11:59 +0100] ReadClient: 5 POST / HTTP/1.1
D [13/Jun/2005:02:11:59 +0100] ProcessIPPRequest: 5 status_code=1
D [13/Jun/2005:02:12:03 +0100] ReadClient: 4 POST / HTTP/1.1
D [13/Jun/2005:02:12:03 +0100] ProcessIPPRequest: 4 status_code=0
D [13/Jun/2005:02:12:03 +0100] ReadClient: 4 POST / HTTP/1.1
D [13/Jun/2005:02:12:03 +0100] ProcessIPPRequest: 4 status_code=1
D [13/Jun/2005:02:12:04 +0100] ReadClient: 5 POST / HTTP/1.1
D [13/Jun/2005:02:12:04 +0100] ProcessIPPRequest: 5 status_code=0
D [13/Jun/2005:02:12:04 +0100] ReadClient: 5 POST / HTTP/1.1
D [13/Jun/2005:02:12:04 +0100] ProcessIPPRequest: 5 status_code=1
D [13/Jun/2005:02:12:06 +0100] ReadClient: 4 GET /printers/LaserJet-4.ppd HTTP/1.1
D [13/Jun/2005:02:12:06 +0100] SendFile: 4 file=8
D [13/Jun/2005:02:12:06 +0100] ReadClient: 4 POST / HTTP/1.1
D [13/Jun/2005:02:12:06 +0100] ProcessIPPRequest: 4 status_code=0


Keeps adding the ReadClient and ProcessIPPRequest lines after that :).

---

### Post by desdinova on 2005-06-12
Can you perhaps try getting a ppd from linuxprinting.org and using that? there's a definte rendering error and a last time I saw something like that I had to experiment with foomatic/hpijs to get the right renderer

---

### Post by RichA on 2005-06-12
[QUOTE=desdinova]Can you perhaps try getting a ppd from linuxprinting.org and using that? there's a definte rendering error and a last time I saw something like that I had to experiment with foomatic/hpijs to get the right renderer[/QUOTE]
 Have tried the hpijs and hpijs-rss ppd downloads from linuxprinting.org but I'm still getting the same error coming up - and my logfile is far too big to post on here now ;).

Cheers for the help so far :).

--Rich

---

### Post by RichA on 2005-06-13
Anyone?  Please?  I'm really quite keen to get this sorted...

--Rich

---

### Post by desdinova on 2005-06-13
[QUOTE=RichA]Anyone?  Please?  I'm really quite keen to get this sorted...

--Rich[/QUOTE]
 Just for a test - try installing it as an HPLJ 2 perhaps?

---

### Post by RichA on 2005-06-13
[QUOTE=desdinova]Just for a test - try installing it as an HPLJ 2 perhaps?[/QUOTE]
 Nope, 'tis exactly the same...

--Rich

---

### Post by desdinova on 2005-06-13
[QUOTE=RichA]Nope, 'tis exactly the same...

--Rich[/QUOTE]
 Ouch - something is broken - reinstall cups/foomatic and gimp-print perhaps?

---

### Post by jrhodes on 2005-06-13
Try feeding the printer a raw postscript stream.

Get a .ps file from somewhere- i.e. a linux documentation site- and send it directly to the parallel port with the following command:

```
dd if=filenamehere.ps of=/dev/lp0 conv=notrunc
```

If that works, then yes, reinstall cups and/or foomatic and follow other software troubleshooting avenues. 

If that does not work, then there's either a problem with a) your printer, b) your kernel's /dev/ interface, or c) the cable between your computer and your printer.

---

### Post by RichA on 2005-06-13
> rich@vfr:~/Desktop$ dd if=logo_9-2.ps of=/dev/lp0 conv=notrunc
dd: opening `/dev/lp0': Permission denied


I'm running the standard, default kernel...

I've also tried reinstalling cups and whatnot, with no difference to my problem...  The printer is good, as is the cable - I'm quite sure of that :).

--Rich

---

### Post by desdinova on 2005-06-13
[QUOTE=RichA]I'm running the standard, default kernel...

I've also tried reinstalling cups and whatnot, with no difference to my problem...  The printer is good, as is the cable - I'm quite sure of that :).

--Rich[/QUOTE]
 try

sudo dd if=filenamehere.ps of=/dev/lp0 conv=notrunc

---

### Post by RichA on 2005-06-13
[QUOTE=desdinova]try

sudo dd if=filenamehere.ps of=/dev/lp0 conv=notrunc[/QUOTE]
 My bad!  Why didn't I think of that? :)

> dd: opening `/dev/lp0': Device or resource busy

Meh...

--Rich

---

### Post by desdinova on 2005-06-13
Very odd - something is locking /dev/lp0 - perhaps try stopping cups then do it again?

---

### Post by km4hr on 2005-06-16
Similar problem here except I can't print to Laserjet 5.

This is my second attempt to figure out what all the hoopla is about concerning Ubuntu. Printing works fine for me under Fedora so I guess I'll be doing a reload shortly.  Honestly, how can anything claiming to be a serious distro not handle printing correctly.

---

### Post by David Haas on 2005-06-18
Might this recent posting be of help to you? [http://www.ubuntuforums.org/showthread.php?t=39640](http://www.ubuntuforums.org/showthread.php?t=39640)
David

---

### Post by RichA on 2005-06-22
[QUOTE=David Haas]Might this recent posting be of help to you? [http://www.ubuntuforums.org/showthread.php?t=39640](http://www.ubuntuforums.org/showthread.php?t=39640)
David[/QUOTE]
 Just tried it, but with no joy.  Will likely drop Ubuntu and move back to Mandrake or something.  It's really annoying; I've had no problems with other distributions and I'm sure my hardware is good - I just don't understand what the problem can be.

Cheers!

--Rich

---

### Post by Poldi on 2005-06-28
same problem here with a HP LaserJet 1100 (local pport). always busy. 

if I try to print a testpage, the job gets queued and nothing  more happens.

BUT: when I shut off the printer, the testpage comes out fine.
it never gets out of the queue, though. that means whenever I want to print something the sequence goes: print -> shut off printer -> kill printjob manually in queue. 

this did worked better with any other OS, including Ubuntu Warty 4.10 where I had no problems at all.

please, help. 

kind regards,
Carsten

---

